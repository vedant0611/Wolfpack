# Wolfpack Django Project

## Overview

This project is a demonstration of a Django application with Django Rest Framework (DRF) for JWT-based authentication. Users can register and log in using their email and password. This project includes customization of the default User model and creation of serializers for user authentication. It showcases the integration of Django and DRF to build a robust authentication system suitable for modern web applications.

## Applications

This project can be used as a base for building various types of web applications that require user authentication, such as:

- **E-commerce platforms**: Secure user accounts for shopping and order management.
- **Social networks**: User authentication for social interactions and content sharing.
- **Content management systems**: User roles and permissions for managing content.
- **Project management tools**: Authentication for collaborative project tracking and task management.

## Requirements

- Python 3.11.1
- Django 5.0.6
- Django Rest Framework
- Django Rest Framework SimpleJWT
- Virtualenv

## Technology Stack

- Python
- Django
- Django Rest Framework
- Django Rest Framework SimpleJWT

## Project Structure

```
wolfpack_project/
│
├── wolfpack_project/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── users/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── serializers.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
│
├── manage.py
├── db.sqlite3
└── README.md
```

## Setup Instructions

### Prerequisites

- Python 3.x installed
- Virtualenv installed

### Installation

1. **Clone the repository**:

    ```bash
    git clone https://github.com/yourusername/wolfpack_project.git
    cd wolfpack_project
    ```

2. **Create and activate a virtual environment**:

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. **Install dependencies**:

    ```bash
    pip install -r requirements.txt
    ```

### Configuration

1. **Update `settings.py`**:

    Ensure the following settings are in your `settings.py`:

    ```python
    INSTALLED_APPS = [
        ...
        'rest_framework',
        'users',
        'rest_framework_simplejwt',
    ]

    AUTH_USER_MODEL = 'users.User'

    REST_FRAMEWORK = {
        'DEFAULT_AUTHENTICATION_CLASSES': (
            'rest_framework_simplejwt.authentication.JWTAuthentication',
        ),
    }
    ```

### Migrations

1. **Apply migrations**:

    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```

2. **Create a superuser**:

    ```bash
    python manage.py createsuperuser
    ```

### Running the Server

1. **Start the development server**:

    ```bash
    python manage.py runserver
    ```

### API Endpoints

- **User Registration**: `POST /api/users/register/`
    - Request body: 
        ```json
        {
            "email": "user@example.com",
            "password": "password123"
        }
        ```

- **User Login**: `POST /api/users/login/`
    - Request body:
        ```json
        {
            "email": "user@example.com",
            "password": "password123"
        }
        ```
    - Response:
        ```json
        {
            "refresh": "<refresh_token>",
            "access": "<access_token>"
        }
        ```

### Project Highlights

- **Custom User Model**: The default Django User model has been replaced with a custom model that uses email for authentication.
- **JWT Authentication**: Integrated JWT authentication using `rest_framework_simplejwt`.
- **DRF Serializers**: Created custom serializers for user registration and login.

## Contributing

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/fooBar`).
3. Commit your changes (`git commit -am 'Add some fooBar'`).
4. Push to the branch (`git push origin feature/fooBar`).
5. Create a new Pull Request.

