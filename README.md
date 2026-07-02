# Job Board API

REST API cho hệ thống tuyển dụng việc làm được xây dựng bằng Spring Boot.

## Công nghệ sử dụng

- **Java 17** - Programming language
- **Spring Boot 3.5.0** - Framework
- **Spring Web** - RESTful API
- **Spring Data JPA** - Database access layer
- **Spring Security** - Authentication & Authorization
- **MySQL** - Relational database
- **Lombok** - Reduce boilerplate code
- **Hibernate Validator** - Input validation
- **Maven** - Build tool

## Cấu trúc dự án

```
src/main/java/com/jobboard/
├── controller/          # REST API endpoints
├── service/             # Business logic
├── repository/          # Database access
├── entity/              # JPA entities
├── dto/                 # Data Transfer Objects
├── exception/           # Custom exceptions & handlers
└── JobBoardApiApplication.java
```

### Giải thích các layers:

- **Controller**: Tiếp nhận HTTP requests, validate input, trả về responses
- **Service**: Xử lý business logic, transaction management
- **Repository**: CRUD operations với database
- **Entity**: Java objects map với database tables
- **DTO**: Transfer data giữa client và server (ẩn thông tin nhạy cảm)
- **Exception**: Custom exceptions và global exception handling

## Yêu cầu hệ thống

- Java Development Kit (JDK) 17 trở lên
- MySQL 8.0 trở lên
- Maven 3.6+ (hoặc dùng Maven wrapper có sẵn)

## Cài đặt

### 1. Clone repository

```bash
git clone <repository-url>
cd Job-board
```

### 2. Cấu hình database

Tạo database trong MySQL:

```sql
CREATE DATABASE job_board_db;
```

Cập nhật thông tin kết nối trong `src/main/resources/application.yml`:

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/job_board_db
    username: root
    password: your_password_here  # Thay bằng password MySQL của bạn
```

### 3. Build project

```bash
# Windows
mvnw.cmd clean install

# Linux/Mac
./mvnw clean install
```

### 4. Chạy ứng dụng

```bash
# Windows
mvnw.cmd spring-boot:run

# Linux/Mac
./mvnw spring-boot:run
```

Ứng dụng sẽ chạy tại: `http://localhost:8080/api`

## Configuration

### Database Configuration

File `application.yml` chứa các cấu hình quan trọng:

- **ddl-auto: update** - Tự động tạo/cập nhật database schema
- **show-sql: true** - Hiển thị SQL queries trong console (tốt cho learning)
- **port: 8080** - Port của ứng dụng
- **context-path: /api** - Base path cho tất cả endpoints

### Hibernate DDL Options

- `create`: Xóa và tạo lại tables mỗi lần chạy (mất dữ liệu)
- `create-drop`: Tạo khi start, xóa khi stop
- `update`: Tự động cập nhật schema, giữ nguyên dữ liệu (khuyên dùng cho dev)
- `validate`: Chỉ validate schema, không thay đổi
- `none`: Không làm gì cả

## API Documentation

Base URL: `http://localhost:8080/api`

API endpoints sẽ được documented sau khi implement các features.

## Development Branch

- `main` - Production-ready code
- `feature/project-setup` - Initial project setup (current)

## Roadmap

- [x] Setup project structure
- [x] Configure database connection
- [x] Create package structure
- [ ] Implement User authentication
- [ ] Implement Job CRUD operations
- [ ] Implement Job application system
- [ ] Add API documentation (Swagger)

## Học Spring Boot

### Tài nguyên hữu ích:

- [Spring Boot Official Docs](https://spring.io/projects/spring-boot)
- [Spring Data JPA Docs](https://spring.io/projects/spring-data-jpa)
- [Baeldung Spring Tutorials](https://www.baeldung.com/spring-boot)

### Workflow cơ bản:

1. **Tạo Entity** - Define database structure
2. **Tạo Repository** - Data access methods
3. **Tạo Service** - Business logic
4. **Tạo Controller** - API endpoints
5. **Tạo DTOs** - Request/Response objects
6. **Handle Exceptions** - Error handling

## Troubleshooting

### Lỗi kết nối MySQL:

```
Error: Access denied for user 'root'@'localhost'
```

**Giải pháp**: Kiểm tra username/password trong `application.yml`

### Lỗi port đã được sử dụng:

```
Error: Port 8080 is already in use
```

**Giải pháp**: Đổi port trong `application.yml` hoặc kill process đang dùng port 8080

### Lỗi Lombok không hoạt động:

**Giải pháp**: Enable annotation processing trong IDE:
- IntelliJ: Settings > Build, Execution, Deployment > Compiler > Annotation Processors

## License

MIT License

## Author

[Your Name]

---

**Note**: Đây là project setup cơ bản. Business logic và features sẽ được implement ở các branches tiếp theo.
