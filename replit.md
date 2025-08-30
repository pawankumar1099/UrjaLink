# Energy Management System

## Overview

This is a comprehensive energy management system built as a full-stack web application for monitoring and controlling renewable energy systems. The application provides real-time monitoring of solar panels, wind turbines, battery storage, and household energy consumption through an intuitive dashboard interface.

The system features live energy flow visualization, battery health monitoring, grid status tracking, alert management, and detailed analytics with historical data trends. Users can control battery charging schedules, optimize energy usage, and access comprehensive reporting for energy generation and consumption patterns.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
The client-side is built with React using Vite as the build tool and development server. The application uses a component-based architecture with shadcn/ui components for consistent UI design and Tailwind CSS for styling with a dark theme configuration.

**State Management**: React Query (@tanstack/react-query) handles server state management, caching, and API data synchronization with automatic refetching intervals for real-time updates.

**Routing**: Uses Wouter for lightweight client-side routing with dedicated pages for Dashboard, Alerts, Household Usage, Control Panel, Reports, Settings, and Help.

**UI Components**: Radix UI primitives provide accessible, unstyled components that are styled with Tailwind CSS through the shadcn/ui system, ensuring consistent design patterns and accessibility standards.

### Backend Architecture
The server is built with Express.js using TypeScript and ESM modules. It follows a modular structure with separate route handlers and storage abstraction.

**Data Layer**: Currently uses an in-memory storage implementation (MemStorage) that can be easily swapped with a database-backed implementation through the IStorage interface. The system is configured for PostgreSQL with Drizzle ORM.

**API Design**: RESTful API endpoints handle energy data CRUD operations, alerts management, and system control commands. All endpoints include proper error handling and data validation using Zod schemas.

**Real-time Updates**: The API supports frequent polling with optimized response caching and includes middleware for request logging and performance monitoring.

### Data Storage Solutions
The application uses Drizzle ORM with PostgreSQL for production data persistence. The schema defines three main entities:

**Energy Data**: Stores comprehensive energy metrics including solar/wind generation, battery status, grid information, and household consumption with timestamps.

**Alerts**: Manages system notifications with categorization (info, warning, error, success) and read status tracking.

**Users**: Basic user management structure for future authentication implementation.

The current implementation includes a memory-based storage adapter with sample data for development and testing purposes.

### Authentication and Authorization
The system currently includes basic user schema structure but authentication is not actively implemented. The infrastructure is prepared for session-based authentication with connect-pg-simple for PostgreSQL session storage.

## External Dependencies

### Database
- **Neon Database**: Configured for PostgreSQL hosting with connection pooling
- **Drizzle ORM**: Type-safe database queries and migrations
- **connect-pg-simple**: PostgreSQL session store for Express sessions

### UI and Styling
- **Tailwind CSS**: Utility-first CSS framework with custom dark theme configuration
- **Radix UI**: Accessible, unstyled UI primitives for complex components
- **Lucide React**: Icon library for consistent iconography
- **Recharts**: Charting library for data visualization and analytics

### Development Tools
- **Vite**: Fast build tool and development server with HMR
- **TypeScript**: Static type checking across the entire codebase
- **Replit Integration**: Development environment integration with error overlay and debugging tools

### Runtime and Deployment
- **Node.js**: Runtime environment with ESM support
- **esbuild**: Fast bundler for production builds
- **Express.js**: Web framework for API and static file serving