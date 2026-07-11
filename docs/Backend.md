# Backend Architecture

## Overview

The Employee Management System backend is built using **ASP.NET Core 8 Web API** following **Clean Architecture** principles.

The goal is to create a scalable, maintainable, testable, and enterprise-grade backend that can support Android, iOS, and Web applications.

---

# Technology Stack

| Technology | Version |
|------------|---------|
| .NET | 8 |
| ASP.NET Core Web API | 8 |
| Entity Framework Core | 8 |
| SQL Server | Latest |
| JWT Authentication | Yes |
| Swagger/OpenAPI | Yes |
| AutoMapper | Yes |
| FluentValidation | Yes |
| Serilog | Yes |
| xUnit | Yes |

---

# Solution Structure

```
EmployeeManagementSystem.sln

backend/

├── Employee.API
├── Employee.Application
├── Employee.Domain
├── Employee.Infrastructure
└── Employee.Tests
```

---

# Project Responsibilities

## Employee.API

Project Type

```
ASP.NET Core Web API
```

Purpose

- Entry point of the application
- Exposes REST APIs
- Configures Dependency Injection
- JWT Authentication
- Swagger
- Middleware
- Global Exception Handling

Folders

```
Controllers/

Middleware/

Extensions/

Configuration/

Properties/

Program.cs

appsettings.json
```

Depends On

```
Employee.Application

Employee.Infrastructure
```

---

## Employee.Application

Project Type

```
Class Library
```

Purpose

Contains all business logic.

Responsibilities

- DTOs
- Interfaces
- Services
- Validation
- AutoMapper
- Business Rules

Folders

```
DTOs/

Interfaces/

Services/

Validators/

Mappings/

Common/
```

Depends On

```
Employee.Domain
```

---

## Employee.Domain

Project Type

```
Class Library
```

Purpose

Contains business entities.

This project has **NO external dependencies**.

Responsibilities

- Entities
- Enums
- Constants
- Exceptions
- Value Objects

Folders

```
Entities/

Enums/

Constants/

Common/

Exceptions/
```

Example Entities

```
Employee

Department

Role

Attendance

LeaveRequest
```

Depends On

```
None
```

---

## Employee.Infrastructure

Project Type

```
Class Library
```

Purpose

Contains all infrastructure implementations.

Responsibilities

- Entity Framework Core
- SQL Server
- DbContext
- Repository Implementations
- Authentication
- File Storage
- Email Service

Folders

```
Persistence/

Repositories/

Configurations/

Authentication/

Identity/

Migrations/

Services/
```

Depends On

```
Employee.Domain

Employee.Application
```

---

## Employee.Tests

Project Type

```
xUnit Test Project
```

Purpose

Contains

- Unit Tests
- Integration Tests

Folders

```
Application/

Infrastructure/

API/
```

---

# Project References

```
Employee.API
    │
    ├────────────► Employee.Application
    │
    └────────────► Employee.Infrastructure


Employee.Application
            │
            ▼
     Employee.Domain


Employee.Infrastructure
            │
            ├────────────► Employee.Application
            │
            ▼
     Employee.Domain


Employee.Tests
      │
      ├────────────► Employee.API
      ├────────────► Employee.Application
      ├────────────► Employee.Infrastructure
      └────────────► Employee.Domain
```

---

# Folder Structure

## Employee.API

```
Employee.API

Controllers/

Configuration/

Extensions/

Middleware/

Properties/

Program.cs

appsettings.json
```

---

## Employee.Application

```
Employee.Application

DTOs/

Interfaces/

Mappings/

Services/

Validators/

Common/
```

---

## Employee.Domain

```
Employee.Domain

Entities/

Enums/

Constants/

Exceptions/

Common/
```

---

## Employee.Infrastructure

```
Employee.Infrastructure

Persistence/

Repositories/

Configurations/

Authentication/

Identity/

Services/

Migrations/
```

---

## Employee.Tests

```
Employee.Tests

Application/

Infrastructure/

API/
```

---

# NuGet Packages

## Employee.API

| Package | Purpose |
|----------|----------|
| Swashbuckle.AspNetCore | Swagger UI |
| Microsoft.AspNetCore.Authentication.JwtBearer | JWT Authentication |
| Serilog.AspNetCore | Logging |
| Serilog.Sinks.Console | Console Logging |
| Serilog.Sinks.File | File Logging |

---

## Employee.Application

| Package | Purpose |
|----------|----------|
| AutoMapper | Object Mapping |
| AutoMapper.Extensions.Microsoft.DependencyInjection | Dependency Injection |
| FluentValidation | Request Validation |
| FluentValidation.DependencyInjectionExtensions | DI Support |

---

## Employee.Infrastructure

| Package | Purpose |
|----------|----------|
| Microsoft.EntityFrameworkCore.SqlServer | SQL Server Provider |
| Microsoft.EntityFrameworkCore.Design | EF Design Tools |
| Microsoft.EntityFrameworkCore.Tools | Migrations |
| Microsoft.AspNetCore.Identity.EntityFrameworkCore | Identity Support |

---

## Employee.Tests

| Package | Purpose |
|----------|----------|
| xUnit | Unit Testing |
| xunit.runner.visualstudio | Test Runner |
| Microsoft.NET.Test.Sdk | Test SDK |
| FluentAssertions | Readable Assertions |
| Moq | Mocking Framework |

---

# Design Principles

The backend follows:

- Clean Architecture
- SOLID Principles
- Dependency Injection
- Repository Pattern (where appropriate)
- Unit of Work (if required)
- CQRS (future enhancement)
- Separation of Concerns
- Single Responsibility Principle

---

# Future Enhancements

- CQRS using MediatR
- Redis Caching
- Background Jobs (Hangfire)
- Azure Service Bus
- Azure Blob Storage
- Health Checks
- API Versioning
- Docker Support
- Kubernetes Deployment
- GitHub Actions CI/CD