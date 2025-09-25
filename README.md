# scalable-microservices-assignment

# Microservices Architecture Example (Python + Flask)

This project demonstrates a simple **microservices architecture** using Python and Flask.  
The application is composed of two independent services that communicate over HTTP.

## Services

### 1. User Service (port 5001)
- Manages users: create and retrieve user details.
- Stores user data in an in-memory dictionary.
- Endpoints:
  - `GET /users/<user_id>` → Retrieve user details.
  - `POST /users` → Create a new user.

### 2. Order Service (port 5002)
- Manages orders: create and retrieve order details.
- Calls the User Service to fetch user details for each order.
- Endpoints:
  - `GET /orders/<order_id>` → Retrieve order details (with user info).
  - `POST /orders` → Create a new order.

---

## Environment Setup

It’s recommended to use a virtual environment for managing dependencies.
# Create a virtual environment
python -m venv myenv

# Activate the environment
# On Windows:
myenv\Scripts\activate
# On macOS/Linux:
source myenv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Running the Services
Start both services in separate terminals:

Terminal 1: Start the User Service
python user_service.py

Terminal 2: Start the Order Service
python order_service.py

User Service runs on port 5001
Order Service runs on port 5002

Example Requests
User Service

Get a user

curl http://localhost:5001/users/1


Create a user

curl -X POST -H "Content-Type: application/json" \ -d '{"name":"Charlie","email":"charlie@example.com"}' \ http://localhost:5001/users

Order Service

Create an order

curl -X POST -H "Content-Type: application/json" \ -d '{"user_id":1,"product":"Tablet"}' \ http://localhost:5002/orders


Get an order (with user details)

curl http://localhost:5002/orders/1

