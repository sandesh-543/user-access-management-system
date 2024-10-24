# User Access Management System 🚀

## Overview
The User Access Management System is a web-based application that enables users to sign up, request access to software applications, and allows managers to approve or reject these requests. It enhances security and efficiency within an organization.

## Features 🌟
- **User Registration (Sign-Up) 📝**
- **User Authentication (Login) 🔑**
- **Software Management (Admin) 🛠️**
- **Access Request Submission (Employee) 📥**
- **Access Request Approval (Manager) ✅**

## Roles 👥
- **Employee**: Requests access to software.
- **Manager**: Approves or rejects access requests.
- **Admin**: Manages software applications.

## Technologies 💻
- **Java Servlets**
- **JavaServer Pages (JSP)**
- **PostgreSQL**

## Setup Instructions ⚙️

### Prerequisites 📋
- **Java** (JDK 8+)
- **Apache Tomcat**
- **PostgreSQL**
- **Maven**

### Steps to Run the Project 🏃‍♂️
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/user-access-management-system.git
   ```

2. **Build the Project**:
   ```bash
   cd user-access-management-system
   mvn clean install
   ```

3. **Set Up PostgreSQL**: 📊
    - Create a database and execute the following SQL scripts:
   ```sql
   -- Create the 'users' table
    CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username TEXT UNIQUE NOT NULL,
    password TEXT NOT NULL,
    role TEXT CHECK (role IN ('Employee', 'Manager', 'Admin')) NOT NULL
    );
    
    -- Create the 'software' table
    CREATE TABLE software (
    id SERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    description TEXT,
    access_levels TEXT CHECK (access_levels IN ('Read', 'Write', 'Admin')) NOT NULL
    );
    
    -- Create the 'requests' table
    CREATE TABLE requests (
    id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(id),
    software_id INT REFERENCES software(id),
    access_type TEXT CHECK (access_type IN ('Read', 'Write', 'Admin')) NOT NULL,
    reason TEXT,
    status TEXT CHECK (status IN ('Pending', 'Approved', 'Rejected')) NOT NULL
    );

   ```
4. **Deploy the Application**: 🚀
    - Copy the generated `.war` file from the `target` directory to the `webapps` folder of your Tomcat installation.

5. **Start Tomcat**: 🔥
   ```bash
   cd /path/to/tomcat/bin
   ./startup.sh   # For Unix/Linux
   startup.bat    # For Windows
   ```
6. **Access the Application**: 🌐
    - Open your web browser and navigate to `http://localhost:8080/your-app-context`.

## Deliverables 📦
- **Source Code**:
    - Java Servlets:
        - `SignUpServlet.java`
        - `LoginServlet.java`
        - `SoftwareServlet.java`
        - `RequestServlet.java`
        - `ApprovalServlet.java`
    - JSP Pages:
        - `signup.jsp`
        - `login.jsp`
        - `createSoftware.jsp`
        - `requestAccess.jsp`
        - `pendingRequests.jsp`
- **Database Scripts**: SQL scripts to create the necessary tables.
- **Documentation**: README file with setup and run instructions.

## Evaluation Criteria ✅
- **Basic Functionality**: System should allow users to sign up, log in, create software (Admin), and request access (Employee).
- **Code Structure**: Organized servlets, JSP files, and database interactions.
- **Database Interaction**: Proper handling of requests and approvals in PostgreSQL.
- **Completeness**: All required features should function as described.

## Contribution 🤝
Feel free to contribute by raising issues or submitting pull requests in the GitHub repository.

---
For further assistance, please open an issue in the GitHub repository. 🐛


