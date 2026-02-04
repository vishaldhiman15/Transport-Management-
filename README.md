# TransportPro - Transport Management System

A complete transport/ride-booking management system with real-time tracking, similar to Uber/Ola. Built with Node.js, Express, MongoDB, and Socket.IO.

## Features

- **User Dashboard**: Book rides, track drivers in real-time, view ride history
- **Driver Dashboard**: Accept/reject rides, manage availability, earnings tracking
- **Admin Dashboard**: Manage users, drivers, bookings, vehicle types, and analytics
- **Real-time Tracking**: Live location updates using Socket.IO
- **Location Services**: Automatic location detection with browser Geolocation API
- **Multiple Vehicle Types**: Bike, Auto, Sedan, SUV, Premium
- **Fare Calculation**: Dynamic pricing based on distance and time

## Tech Stack

- **Backend**: Node.js, Express.js
- **Database**: MongoDB with Mongoose ODM
- **Real-time**: Socket.IO
- **Authentication**: JWT (JSON Web Tokens)
- **Frontend**: Pure HTML, CSS, JavaScript (no frameworks)
- **Password Hashing**: bcryptjs

## Project Structure

```
Transport management system/
├── server.js              # Main Express server
├── package.json           # Dependencies
├── .env                   # Environment variables
├── seed.js                # Database seeding script
├── models/
│   ├── User.js            # User schema
│   ├── Driver.js          # Driver profile schema
│   ├── Booking.js         # Booking schema
│   └── VehicleType.js     # Vehicle type schema
├── routes/
│   ├── auth.js            # Authentication routes
│   ├── user.js            # User routes
│   ├── driver.js          # Driver routes
│   ├── admin.js           # Admin routes
│   ├── booking.js         # Booking routes
│   └── location.js        # Location routes
├── middleware/
│   └── auth.js            # JWT authentication middleware
└── public/
    ├── index.html         # Landing page
    ├── css/
    │   ├── style.css      # Main styles
    │   └── dashboard.css  # Dashboard styles
    ├── js/
    │   ├── app.js         # Landing page JS
    │   ├── user-dashboard.js
    │   ├── driver-dashboard.js
    │   └── admin-dashboard.js
    ├── user/
    │   └── dashboard.html
    ├── driver/
    │   └── dashboard.html
    ├── admin/
    │   └── dashboard.html
    └── images/
        └── default-avatar.svg
```

## Installation

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or MongoDB Atlas)
- npm or yarn

### Steps

1. **Navigate to project directory**
   ```bash
   cd "Transport management system"
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   
   Edit the `.env` file if needed:
   ```env
   PORT=3000
   MONGODB_URI=mongodb://localhost:27017/transport_management
   JWT_SECRET=your-super-secret-jwt-key-change-in-production
   JWT_EXPIRE=7d
   ```

4. **Start MongoDB**
   ```bash
   # If using local MongoDB
   mongod
   ```

5. **Seed the database (optional but recommended)**
   ```bash
   node seed.js
   ```
   This creates:
   - Default vehicle types (Bike, Auto, Sedan, SUV, Premium)
   - Admin user
   - Test user
   - Test drivers
   - Sample completed booking

6. **Start the server**
   ```bash
   npm start
   # or for development with auto-reload:
   npm run dev
   ```

7. **Open in browser**
   ```
   http://localhost:3000
   ```

## Default Login Credentials

After running `node seed.js`:

| Role   | Email                    | Password   |
|--------|--------------------------|------------|
| Admin  | admin@transportpro.com   | admin123   |
| User   | user@test.com            | user123    |
| Driver | driver1@test.com         | driver123  |

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/register-driver` - Register new driver
- `POST /api/auth/login` - Login
- `GET /api/auth/me` - Get current user

### Bookings
- `POST /api/booking/estimate` - Get fare estimate
- `POST /api/booking/create` - Create booking
- `GET /api/booking/vehicle-types` - Get available vehicle types
- `GET /api/booking/:id` - Get booking details
- `PUT /api/booking/:id/cancel` - Cancel booking

### Driver
- `GET /api/driver/profile` - Get driver profile
- `PUT /api/driver/toggle-online` - Toggle online status
- `GET /api/driver/pending-requests` - Get pending ride requests
- `PUT /api/driver/accept/:bookingId` - Accept ride request
- `PUT /api/driver/reject/:bookingId` - Reject ride request
- `PUT /api/driver/arrived/:bookingId` - Mark arrived at pickup
- `PUT /api/driver/start/:bookingId` - Start ride (requires OTP)
- `PUT /api/driver/complete/:bookingId` - Complete ride

### Admin
- `GET /api/admin/stats` - Dashboard statistics
- `GET /api/admin/users` - List all users
- `GET /api/admin/drivers` - List all drivers
- `PUT /api/admin/drivers/:id/approve` - Approve driver
- `PUT /api/admin/drivers/:id/reject` - Reject driver
- `GET /api/admin/bookings` - List all bookings
- `GET /api/admin/analytics` - Analytics data

## Usage Guide

### For Users
1. Visit the homepage and allow location access
2. Register or login
3. Enter pickup and dropoff locations
4. Select vehicle type and view fare estimate
5. Confirm booking
6. Track driver in real-time
7. Share OTP with driver to start ride

### For Drivers
1. Register as a driver with vehicle details
2. Wait for admin approval
3. Once approved, login to driver dashboard
4. Toggle "Online" to receive ride requests
5. Accept or reject incoming requests
6. Navigate to pickup, enter OTP from user
7. Complete the ride

### For Admins
1. Login with admin credentials
2. View dashboard statistics
3. Approve/reject pending drivers
4. Manage users and bookings
5. Configure vehicle types and pricing
6. View analytics and reports

## Real-time Features

The application uses Socket.IO for:
- Live driver location updates
- New booking notifications
- Booking status changes
- Driver availability updates

## License

MIT License

## Support

For issues or questions, please create an issue in the repository.
# Transport-Management-
