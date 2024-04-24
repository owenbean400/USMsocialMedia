# Login Diagrams

## Sequence Diagrams

### User Register

- Password must be longer than 8 characters with one number and one special character
- User must have a @maine.edu email domain during registration

```mermaid
sequenceDiagram
    User->>Front End: Fill out register
    Front End->>Back End: Creates new user
    Back End->>User: Sends email to verify account with verification token
    Back End->>Front End: Success
    Front End->>User: Directs user to waiting for verification
    User->>Front End: Opens email to verify account
    Front End->>Back End: Send verification
    Back End->>Front End: Success
    Front End->>User: Detect verification and redirect user to main page
```

### User Register Through Google

- Google account handles verification of email as the user logs in with user

```mermaid
sequenceDiagram
    User->>Front End: Fill out Google signin
    Front End->>Back End: Creates new user
    Back End->>Front End: Returns token
    Front End->>User: Directs user to main page
```

### User Login

_We could setup a browser to remember me on login in future feature_

```mermaid
sequenceDiagram
    User->>Front End: Supplies login credentials
    Front End->>Back End: Send credentials
    Back End->>Front End: Returns token
    Front End->>User: Directs user to main page
```

### User Forgot Password

- User must be verified

```mermaid
sequenceDiagram
    User->>Front End: Fill out email
    Front End->>Back End: Request password request
    Back End->>User: Sends email to reset password with link that includes reset token
    User->>Front End: Opens email and fills out new password
    Front End->>Back End: Verify token and resets password
    Back End->>Front End: Success
    Front End->>User: Redirects user to login page
```