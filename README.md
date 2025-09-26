# Task Management Dashboard - Backend

This is the backend server for the task management dashboard application. It provides a REST API for managing tasks with CRUD operations.

## Technologies Used

- Node.js
- Express.js
- MongoDB with Mongoose ODM
- CORS
- Dotenv for environment variables

## Setup Instructions

1. Make sure you have Node.js and MongoDB installed on your system.
2. Clone this repository.
3. Navigate to the backend directory: `cd task-management-dashboard/backend`
4. Install dependencies: `npm install`
5. Create a `.env` file in the root of the backend directory with the following content:

```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/taskdb
NODE_ENV=development
```

6. Start the server in development mode: `npm run dev` (requires nodemon) or `npm start`

## API Endpoints

### `GET /api/tasks`
Retrieve all tasks sorted by creation date (newest first).

### `GET /api/tasks/:id`
Retrieve a specific task by its ID.

### `POST /api/tasks`
Create a new task. Expects a JSON body with:
- `title` (string, required)
- `description` (string, optional)
- `status` (string, one of: 'pending', 'in-progress', 'completed', default: 'pending')
- `dueDate` (date, optional)

### `PUT /api/tasks/:id`
Update an existing task by its ID. Same body parameters as POST.

### `DELETE /api/tasks/:id`
Delete a task by its ID.

## Database Schema

The application uses MongoDB with a Task schema that includes:
- `title`: Required string (max 100 characters)
- `description`: Optional string (max 500 characters)
- `status`: Enum of 'pending', 'in-progress', 'completed' (default: 'pending')
- `dueDate`: Optional date
- `createdAt` and `updatedAt`: Automatically managed timestamps