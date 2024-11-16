🚗 OWN CAR SHOWROOM
===================

A full-stack application to manage cars where users can create, view, edit, and delete cars. Each car can contain up to 10 images, a title, a description, and tags like car type, company, dealer, etc. The application includes user authentication, product ownership, and search functionality.

🛠 Features
-----------

*   **User Authentication**: Secure login and registration.
    
*   **Car Management**: Users can create, update, delete, and view cars.
    
*   **Image Upload**: Upload up to 10 car images per entry.
  
*   **CAR MODEL/Price /Buying Date**:  Add car Model buy date . price etc.
    
*   **Tags**: Add car-related tags like type, company, and dealer.
    
*   **Search Functionality**: Search cars by title, description, or tags.
    
*   **User Authorization**: Users can manage only their own cars.
    

📋 Schema Design
----------------

### Car Schema
```javascript
const mongoose = require("mongoose");

const carSchema = new mongoose.Schema(
  {
    user: {
      type: mongoose.Schema.Types.ObjectId,
      ref: "User",
      required: true,
    },
    carName: {
      type: String,
      required: true,
      trim: true,
    },
    modelName: {
      type: String,
      required: true,
      trim: true,
    },
    buyDate: {
      type: Date,
      required: true,
    },
    buyPrice: {
      type: Number,
      required: true,
    },
    description: {
      type: String,
      trim: true,
    },
    tags: {
      type: [String],
      validate: [arrayLimit, "You can only upload up to 10 tags."],
    },
    images: {
      type: [String],
      validate: [arrayLimit, "You can only upload up to 10 images."],
    },
  },
  {
    timestamps: true,
  }
);

function arrayLimit(val) {
  return val.length <= 10;
}

module.exports = mongoose.model("Car", carSchema);

```


💻 Tech Stack
-------------

*   **Frontend**: React.js, Tailwind CSS
    
*   **Backend**: Node.js, Express.js
    
*   **Database**: MongoDB (Mongoose)
    
*   **Authentication**: JSON Web Tokens (JWT)
    
*   **Image Upload**: Multer (with file upload validation)
    

🚀 Installation
---------------

### 1\. Clone the repository:
` bash  git clone https://github.com/yourusername/car-management-app.git  cd car-management-app   `

### 2\. Install dependencies:

For **backend**:
` bash  cd backend  npm install   `

For **frontend**:
` bash   cd ../frontend  npm install   `

### 3\. Environment variables:

Create a .env file in the **backend** directory with the following variables:

` env  
PORT=5000  MONGO_URI= YOUR_MONGO_URI  
JWT_SECRET=your_jwt_secret  
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name  
CLOUDINARY_API_KEY=your_cloudinary_api_key  
CLOUDINARY_API_SECRET=your_cloudinary_api_secret   `

### 4\. Run the application:

Start the **backend**:
` bash  cd backend  npm start   `

Start the **frontend**:
` bash  cd ../frontend  npm run dev   `

### 5\. Access the application:

Visit [http://localhost:5173](http://localhost:5173) in your browser.

### 🔑 Initial Credentials

Use the following credentials for an initial experience (you can change them later):

*   **Email**: demo@example.com
    
*   **Password**: Password123!
