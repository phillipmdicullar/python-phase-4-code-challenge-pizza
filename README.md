# Phase 4 Code Challenge: Pizza Restaurant

This project demonstrates building a full-stack web application using a Flask API backend and a React frontend to manage Pizza Restaurants.

![piizza](https://github.com/user-attachments/assets/f74d1a89-2b17-48ce-b398-69035c4d8f99)
# Overview
This project implements an API for managing restaurants, pizzas, and their relationships. The app allows users to:

- Retrieve restaurant and pizza data.
- Manage restaurant-pizza relationships.
- Validate inputs during API interactions.

# Features
**Backend**: Flask API with SQLAlchemy for database management.
**Frontend**: React application for interacting with the API.
**Database**: SQLite3 for development.
**Validation**: Ensures valid price ranges for restaurant-pizza relationships.
**Testing**: Comprehensive tests using pytest.

# Setup Instructions
## Backend
### Clone the repository:

- **git clone <repository-url>**
- **cd code-challenge**

### Install dependencies:

- **pipenv install**
- **pipenv shell**

### Set up the database:

***
export FLASK_APP=server/app.py
flask db init
flask db migrate -m "Initial migration"
flask db upgrade
python server/seed.py
***
##Start the Flask server:**

**python server/app.py**

### Frontend
- Navigate to the client directory:

**cd client**
- Install frontend dependencies:

**npm install**
- Start the React application:

**npm start**


# Data Models
### Restaurant
***
id: Integer, primary key
name: String
address: String
***
### Pizza
***
id: Integer, primary key
name: String
ingredients: String
****

### RestaurantPizza
***
id: Integer, primary key
price: Integer (between 1 and 30)
restaurant_id: Foreign key to Restaurant
pizza_id: Foreign key to Pizza
***

### API Endpoints
***
GET /restaurants
***
- Retrieve all restaurants.

- json
Copy
***
[
  {
    "id": 1,
    "name": "Karen's Pizza Shack",
    "address": "address1"
  }
]
***
### GET /restaurants/<id>
- Retrieve a specific restaurant and its associated pizzas.

- **404** Error: If the restaurant is not found.
- json
Copy
***
{
  "error": "Restaurant not found"
}
### DELETE /restaurants/<id>
***
- Delete a restaurant and its associated RestaurantPizza records.

- **404 Error:** If the restaurant is not found.
### GET /pizzas
- Retrieve all pizzas.

json
Copy
***
[
  {
    "id": 1,
    "name": "Emma",
    "ingredients": "Dough, Tomato Sauce, Cheese"
  }
]
***
### POST /restaurant_pizzas
- Create a new RestaurantPizza.

- Request Body:
- json
Copy
***
{
  "price": 5,
  "pizza_id": 1,
  "restaurant_id": 3
}
***
# Validation Error:
- json
- Copy
***
{
  "errors": ["Price must be between 1 and 30"]
}
***
### Testing
- Run tests to ensure functionality:

- bash
- Copy

***pytest -x**

### Postman Collection
- Use the included challenge-1-pizzas.postman_collection.json file to test the API:

### Open Postman.
- Import the collection.
- Use the predefined requests for testing.
- Validations
- RestaurantPizza requires:
- price to be between 1 and 30.
- Validation errors return appropriate JSON responses and HTTP status codes.
### Frontend
- The React frontend provides an interface for interacting with the backend API. Features include:

- Viewing restaurants and pizzas.
- Testing CRUD operations via the UI.
### Development Notes
- **Cascade Deletes:** Ensure relationships are properly set up to cascade deletions.
- **Serialization Rules:** Limit recursion depth when serializing models to JSON.
- **Environment:** Use pipenv for dependency management and a virtual environment.
