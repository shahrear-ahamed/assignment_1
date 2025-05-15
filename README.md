# Setting Up an Express, Node.js, and Mongoose Project

Follow these steps to create a project using Express, Node.js, and Mongoose:

## 1. Initialize the Project

Run the following command to create a new project and initialize `package.json`:

```bash
mkdir my-project
cd my-project
npm init -y
```

## 2. Install Dependencies

Install the required packages:

```bash
npm install express mongoose
npm install --save-dev nodemon
```

## 3. Create the Project Structure

Organize your project as follows:

```
my-project/
├── node_modules/
├── package.json
├── server.js
└── models/
```

## 4. Create the Entry Point (`server.js`)

Add the following code to `server.js`:

```javascript
const express = require("express");
const mongoose = require("mongoose");

const app = express();
const PORT = 3000;

// Middleware
app.use(express.json());

// Connect to MongoDB
mongoose
  .connect("mongodb://localhost:27017/mydatabase", {
    useNewUrlParser: true,
    useUnifiedTopology: true,
  })
  .then(() => console.log("MongoDB connected"))
  .catch((err) => console.error(err));

// Routes
app.get("/", (req, res) => {
  res.send("Hello, World!");
});

// Start the server
app.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});
```

## 5. Add a Script for Development

Update the `scripts` section in `package.json`:

```json
"scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
}
```

## 6. Run the Project

Start the server in development mode:

```bash
npm run dev
```

Your Express, Node.js, and Mongoose project is now set up!
