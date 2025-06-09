# Uber Microservices

This project is a microservices-based application, likely designed for a ride-sharing or similar service. It demonstrates the use of multiple independent services that communicate with each other to provide a complete application.

## Architecture Overview

The project is structured into several microservices, each responsible for a specific domain. The key services include:

- **Gateway Service**: Acts as an API Gateway, routing requests to the appropriate backend services and handling cross-cutting concerns like authentication and load balancing.
- **User Service**: Manages user-related functionalities, including user registration, login, and profile management.
- **Captain Service**: Manages driver (captain) related functionalities, such as captain registration, location updates, and ride acceptance.
- **Ride Service**: Handles ride-related operations, including ride requests, ride matching, real-time tracking, and ride completion.

Each service is an independent Node.js application, likely using Express.js for routing and MongoDB for data persistence.

## Technologies Used

- **Node.js**: As the runtime environment for all microservices.
- **Express.js**: A fast, unopinionated, minimalist web framework for Node.js, used for building APIs.
- **MongoDB**: A NoSQL database used for storing data for each service.
- **RabbitMQ**: A message broker used for inter-service communication.
- **NPM**: Package manager for Node.js.
- **Git**: Version control system.

## Setup and Installation

To set up and run this project, follow these steps for each microservice:

### Prerequisites

- Node.js (v14 or higher recommended)
- MongoDB (running instance)
- Git

### General Setup for Each Service (User, Ride, Captain, Gateway)

1.  **Clone the repository:**
    ```bash
    git remote add origin https://github.com/rahulbamnuya/uber-microservices-backend.git
    cd uber-microservices-backend
    ```

2.  **Navigate to a service directory:**
    ```bash
    cd <service_name> # e.g., cd user, cd ride, cd captain, cd gateway
    ```

3.  **Install dependencies:**
    ```bash
    npm install
    ```

4.  **Configure Environment Variables:**
    Each service will likely require its own environment variables (e.g., database connection strings, port numbers, API keys). You should create a `.env` file in each service directory based on a `.env.example` (if available) or relevant documentation.

    _Example user environment variables:_
    - `PORT`: The port on which the service will run.exam port 3001
    - `MONGODB_URI`: Connection string for the MongoDB database.
    - `RABBIT_URL=`:Paste url after login CloudAMQP.
    - `JWT_SECRET`=user_secret_key.
      
    Example captain environment variables:_
    - `PORT`: The port on which the service will run. example port 3002
    - `MONGODB_URI`: Connection string for the MongoDB database.
    - `RABBIT_URL=`:Paste url after login CloudAMQP.
    - `JWT_SECRET`=user_secret_key.
      
    Example ride environment variables:_
    - `PORT`: The port on which the service will run. exapmle port 3003
    - `MONGODB_URI`: Connection string for the MongoDB database.
    - `RABBIT_URL=`:Paste url after login CloudAMQP.
    - `JWT_SECRET`=user_secret_key.
    - `BASE_URL`=http://localhost:3000 or local host of gatewayservice
   



### Running the Application

To run the entire application, you will need to start each microservice independently.

1.  **Start MongoDB:** Ensure your MongoDB instance is running.

2.  **Start each service in separate terminal windows:**

    For each service (User, Ride, Captain, Gateway):
    ```bash
    cd <service_name>
    npm start # or node server.js / node app.js depending on the service's entry point
    ```

    _Note: You might need to check the `package.json` file of each service to confirm the exact command to start the service (e.g., `npm start`, `node server.js`, `node app.js`)._

## API Endpoints (General Overview)

Each service exposes its own set of RESTful API endpoints. The API Gateway service will be the primary entry point for client applications.

-   **User Service:**
    -   `/api/users/register` (POST)
    -   `/api/users/login` (POST)
    -   `/api/users/profile` (GET, PUT)
    -   ... (other user-related endpoints)

-   **Captain Service:**
    -   `/api/captains/register` (POST)
    -   `/api/captains/login` (POST)
    -   `/api/captains/location` (PUT)
    -   ... (other captain-related endpoints)

-   **Ride Service:**
    -   `/api/rides/request` (POST)
    -   `/api/rides/<ride_id>` (GET, PUT)
    -   `/api/rides/active` (GET)
    -   ... (other ride-related endpoints)

-   **Gateway Service:**
    -   Handles routing to the above services. Specific endpoints will depend on the routing configuration.

## Contributing

1.  Fork the repository.
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

## License

Distributed under the MIT License. See `LICENSE` for more information.

--- 
