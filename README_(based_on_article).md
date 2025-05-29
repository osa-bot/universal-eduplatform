# universal-eduplatform

---

![License](https://img.shields.io/github/license/LISA-ITMO/universal-eduplatform?style=flat&logo=opensourceinitiative&logoColor=white&color=blue)
[![OSA-improved](https://img.shields.io/badge/improved%20by-OSA-yellow)](https://github.com/aimclub/OSA)

---

## Overview

This platform aims to create a comprehensive online learning environment, connecting educational content with student progress and user management. It provides tools for teachers to build courses organized by subject matter, and allows students to easily find and enroll in those courses. Core features include secure user accounts with different access levels – for students, instructors, and administrators – ensuring appropriate permissions for each role. Students can submit work, track their learning journey, and potentially benefit from a moderation system. 

A key objective is building detailed digital profiles of learners through intelligent testing and assessment. These profiles are designed to be portable and verifiable, acting as valuable portfolios for both educational pursuits and future employment opportunities. The platform prioritizes flexibility and scalability by using independent components that communicate effectively, ensuring it can adapt to evolving needs and integrate with other systems via standard web technologies like REST APIs.

---

## Repository content

The universal-eduplatform repository builds a continuous education platform, aiming to create dynamic digital profiles for users based on their learning and assessment data. The project's core functionality revolves around building these 'digital portfolios' which can be used for professional and educational evaluation.

The system is composed of several interconnected services orchestrated by Docker Compose. These include:

1. **User Management (users):** This service handles user authentication, authorization (using OAuth 2.0 as indicated in the PDF summary), and role management (student, teacher, admin). It utilizes a SQLite database (users_db.sqlite3) to store user credentials and related information.

2. **Subjects & Courses (subjects):** This component defines the structure of educational content – subjects, themes within those subjects, and courses offered.  It also manages relationships between students, experts/teachers, and these learning resources using a SQLite database (subjects_db.sqlite3). Models include Subject, Theme, and Course.

3. **Tests (tests):** This service likely handles the creation, delivery, and evaluation of tests or quizzes. It uses another SQLite database (tests_db.sqlite3) to store test-related data.

4. **Client (web-new):**  This is the frontend application built with React and Chakra UI, providing a user interface for interacting with the platform. It includes pages for login, profile management, courses, requests, creation of content, solution submission, student lists, and potentially moderation. The client interacts with backend services through API calls.

RESTful APIs are used to facilitate communication between these components, allowing independent development and loose coupling.  A gateway service (nginx) acts as a reverse proxy, routing requests to the appropriate backend services.

The project also includes provisions for an analytics component (currently commented out in docker-compose.yml), which would likely process user data to provide insights into learning patterns and platform usage. The system utilizes SQLite databases for each core function – users, subjects/courses, and tests – suggesting a modular design where each service manages its own persistent data.

---

## Used algorithms

The codebase utilizes several algorithms, though they are not explicitly detailed in the provided summaries. Here's a breakdown of those inferred from the project description:

1. **Authentication Algorithm:** A standard authentication flow is used to verify user credentials (email/username and password). This likely involves hashing passwords for secure storage and comparing them against entered credentials during login.

2. **Authorization Algorithm:** Role-Based Access Control (RBAC) governs access to different functionalities within the platform.  This algorithm determines what actions a user can perform based on their assigned role (student, teacher, admin). It checks if a user's role has permission for a requested action before granting access.

3. **Course Enrollment Algorithm:** This manages the process of students joining courses. It likely involves checking course capacity, verifying prerequisites (if any), and updating student records to reflect their enrollment status.

4. **Progress Tracking Algorithm:**  This algorithm monitors a student's advancement through a course. It tracks submitted solutions, test scores, and potentially time spent on learning materials to determine overall progress.

5. **Testing/Assessment Algorithms (within the testing service):** These algorithms are used for evaluating student submissions. The theses mentions 'intelligent cross-testing algorithms' creating digital portfolios; these likely involve comparing a student’s answers against correct solutions, grading based on predefined criteria, and potentially identifying areas where a student needs improvement.

6. **RESTful API Communication (as favored by the research):** While not an algorithm *within* the platform itself, the project intends to use REST principles for communication between services and external systems. This involves algorithms related to request/response handling, data serialization (e.g., JSON), and routing requests to appropriate endpoints.

The theses also highlights algorithms used in creating 'digital portfolios' which are essentially a compilation of assessment results – these likely involve data aggregation and potentially some form of scoring or ranking based on performance.

---
