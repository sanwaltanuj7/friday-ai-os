# Database Design

# FRIDAY AI OS

Version: 1.0

Status: Draft

Owner: Tanuj Sanwal

---

# Table of Contents

1. Database Overview
2. Database Technologies
3. PostgreSQL Schema
4. MongoDB Collections
5. Vector Database
6. Entity Relationships
7. Naming Conventions
8. Indexing Strategy
9. Audit Strategy
10. Backup Strategy
11. Future Expansion
# 1. Database Overview

FRIDAY AI OS uses a hybrid database architecture to balance
performance, flexibility, and AI capabilities.

The system uses:

- PostgreSQL for structured relational data.
- MongoDB for semi-structured documents.
- Qdrant (or pgvector) for semantic memory.
- Redis for caching and background tasks.

Each database is responsible for a specific type of data,
ensuring scalability and maintainability.
# 2. Database Technologies

## PostgreSQL

Purpose:

- User Accounts
- Authentication
- Chats
- Messages
- Tasks
- Notifications
- User Profiles

---

## MongoDB

Purpose:

- Resume JSON
- Uploaded Documents
- AI Context
- Tool Outputs
- Logs

---

## Vector Database

Purpose:

- Resume Embeddings
- Chat Embeddings
- Memory Embeddings
- Knowledge Retrieval

---

## Redis

Purpose:

- Session Cache
- Rate Limiting
- Background Jobs
- Temporary Data

# 3. PostgreSQL Schema

The relational database stores structured application data.

## Tables

- users
- profiles
- sessions
- chats
- messages
- tasks
- notifications
- skills
- goals
- jobs
- applications
- settings
- audit_logs
### users

| Column | Type | Description |
|----------|------|-------------|
| id | UUID | Primary Key |
| email | VARCHAR | Unique Email |
| password_hash | TEXT | Encrypted Password |
| provider | VARCHAR | Email / Google |
| is_verified | BOOLEAN | Email Verified |
| role | VARCHAR | User Role |
| created_at | TIMESTAMP | Creation Time |
| updated_at | TIMESTAMP | Last Update |
| deleted_at | TIMESTAMP | Soft Delete |

### profiles

| Column | Type |
|----------|------|
| id | UUID |
| user_id | UUID |
| full_name | VARCHAR |
| avatar_url | TEXT |
| bio | TEXT |
| experience | TEXT |
| education | TEXT |
| github | TEXT |
| linkedin | TEXT |
| portfolio | TEXT |
| created_at | TIMESTAMP |
| updated_at | TIMESTAMP |
### chats

| Column | Type |
|----------|------|
| id | UUID |
| user_id | UUID |
| title | TEXT |
| created_at | TIMESTAMP |
| updated_at | TIMESTAMP |

### messages

| Column | Type |
|----------|------|
| id | UUID |
| chat_id | UUID |
| sender | VARCHAR |
| content | TEXT |
| model | VARCHAR |
| token_count | INTEGER |
| created_at | TIMESTAMP |
