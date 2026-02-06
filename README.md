# EVM

### Auth

- [ ]  Implement authentication using **JWT** for protected routes
- [ ]  Hash passwords using **bcrypt** (no plaintext storage)
- [ ]  Protect **all frontend pages except login/signup** using role-based access control
- [ ]  Session rules
    - [ ]  Redirect user to **their respective dashboard** after login
    - [ ]  Sessions must persist across browser restarts unless explicitly logged out
    - [ ]  Logout must clear all authentication tokens

### Registration & Login

- [ ]  Participant registration:
    - [ ]  IIIT participants must register using **IIIT-issued email ID only** (domain validation mandatory)
    - [ ]  Non-IIIT participants register using **email + password**
- [ ]  Organizer authentication:
    - [ ]  No self-registration; organizer accounts are provisioned by Admin
    - [ ]  Organizers login using credentials provided by Admin
    - [ ]  Organizer password resets requested + handled by Admin (see Advanced Tier B option)
- [ ]  Admin provisioning:
    - [ ]  Admin is the **first user** in the system
    - [ ]  Admin email/password provisioned and handled by backend only (**no UI registration**)
    - [ ]  Admin can create/remove clubs/organizers

## Roles

- [ ]  **[MUST]** Each user can have **exactly one role**
- [ ]  **[MUST]** Role switching is **strictly prohibited**
- [ ]  **[MUST]** Roles supported:
    - [ ]  Participant (IIIT Student / Non-IIIT Participant)
    - [ ]  Organizer (Clubs / Councils / Fest Teams)
    - [ ]  Admin (System-level administrator)

## Participant

### Navigation

- [ ]  **[MUST]** Navbar: Dashboard, Browse Events, Clubs/Organizers, Profile, Logout

### My Events Dashboard

- [ ]  **[MUST]** Upcoming events list includes event name, type, organizer, schedule
- [ ]  **[MUST]** Participation history tabs:
    - [ ]  Normal
    - [ ]  Merchandise
    - [ ]  Completed
    - [ ]  Cancelled/Rejected
- [ ]  **[MUST]** Event record includes:
    - [ ]  event name, event type, organizer
    - [ ]  participation status
    - [ ]  team name (if applicable)
    - [ ]  clickable ticket ID

### Browse Events Page

- [ ]  **[MUST]** Search supports partial + fuzzy matching (Event/Organizer names)
- [ ]  **[MUST]** Trending: Top 5 / 24h
- [ ]  **[MUST]** Filters (works with search):
    - [ ]  Event Type
    - [ ]  Eligibility
    - [ ]  Date Range
    - [ ]  Followed Clubs
    - [ ]  All Events

### Event Details Page

- [ ]  **[MUST]** Show complete details + type + Register/Purchase button (with validation)
- [ ]  **[MUST]** Block registration/purchase if:
    - [ ]  deadline passed
    - [ ]  registration limit reached OR stock exhausted

### Event Registration Workflows

- [ ]  **[MUST]** Normal event:
    - [ ]  Ticket emailed on successful submission
    - [ ]  Ticket visible in Participation History
- [ ]  **[MUST]** Merchandise event:
    - [ ]  Purchase implies registration
    - [ ]  Stock decremented upon purchase
    - [ ]  Ticket with QR generated
    - [ ]  Confirmation email sent
    - [ ]  Out-of-stock purchases blocked
- [ ]  **[MUST]** Tickets & QR include:
    - [ ]  event + participant details
    - [ ]  QR code
    - [ ]  unique Ticket ID

### Profile Page (Participant)

- [ ]  **[MUST]** Editable:
    - [ ]  First Name, Last Name
    - [ ]  Contact Number
    - [ ]  College/Organization Name
    - [ ]  Selected Interests
    - [ ]  Followed Clubs
- [ ]  **[MUST]** Non-editable:
    - [ ]  Email Address
    - [ ]  Participant Type (IIIT / Non-IIIT)
- [ ]  **[MUST]** Security settings: password reset/change mechanism (auth + validation)

---

## Organizer

### Navigation

- [ ]  **[MUST]** Navbar: Dashboard, Create Event, Profile, Logout, Ongoing Events

### Organizer Dashboard

- [ ]  **[MUST]** Events carousel/cards show Name, Type, Status (Draft/Published/Ongoing/Closed)
- [ ]  **[MUST]** Completed event analytics: registrations/sales/revenue/attendance stats

### Event Detail Page (Organizer View)

- [ ]  **[MUST]** Overview: Name, Type, Status, Dates, Eligibility, Pricing
- [ ]  **[MUST]** Analytics: Registrations/Sales, Attendance, Team completion, Revenue
- [ ]  **[MUST]** Participants list:
    - [ ]  Name, Email, Reg Date, Payment, Team, Attendance
    - [ ]  Search/Filter
    - [ ]  Export CSV

### Event Creation & Editing

- [ ]  **[MUST]** Flow: Create (Draft) → Define required fields → Publish
- [ ]  **[MUST]** Editing rules:
    - [ ]  Draft: free edits, can publish
    - [ ]  Published: only description update, extend deadline, increase limit, close registrations
    - [ ]  Ongoing/Completed: no edits except status change (mark completed/closed)
- [ ]  **[MUST]** Form Builder:
    - [ ]  Custom registration forms
    - [ ]  Field types: text, dropdown, checkbox, file upload, etc.
    - [ ]  Required/optional + reorder fields
    - [ ]  Form locks after first registration

### Profile Page (Organizer)

- [ ]  **[MUST]** Editable: Name, Category, Description, Contact Email/Number
- [ ]  **[MUST]** Login email non-editable
- [ ]  **[MUST]** Discord webhook auto-post new events

---

## Admin

### Navigation

- [ ]  **[MUST]** Navbar: Dashboard, Manage Clubs/Organizers, Password Reset Requests, Logout

### Club/Organizer Management

- [ ]  **[MUST]** Add new club/organizer:
    - [ ]  Admin creates account
    - [ ]  System auto-generates login email + password
    - [ ]  Admin receives and shares credentials
    - [ ]  New account can log in immediately
- [ ]  **[MUST]** Remove/disable club/organizer:
    - [ ]  Admin views list of all clubs/organizers
    - [ ]  Remove or disable accounts (disabled cannot log in)
    - [ ]  Option to archive or permanently delete

---

## Events

### Technology Stack

- [ ]  **[MUST]** MERN stack only:
    - [ ]  MongoDB
    - [ ]  Express (REST APIs)
    - [ ]  React / React-based framework
    - [ ]  Node.js

### Event Types

- [ ]  **[MUST]** All activities modeled as Events
- [ ]  **[MUST]** Each event has exactly one type:
    - [ ]  Normal (individual)
    - [ ]  Merchandise (individual purchase only)

### Event Attributes

- [ ]  **[MUST]** Store at minimum:
    - [ ]  Event Name
    - [ ]  Event Description
    - [ ]  Event Type
    - [ ]  Eligibility
    - [ ]  Registration Deadline
    - [ ]  Event Start Date
    - [ ]  Event End Date
    - [ ]  Registration Limit
    - [ ]  Registration Fee
    - [ ]  Organizer ID
    - [ ]  Event Tags
- [ ]  **[MUST]** Additional by type:
    - [ ]  Normal: dynamic form builder
    - [ ]  Merchandise: item details (size/color/variants), stock qty, purchase limit per participant

---

## Merch

- [ ]  **[MUST]** Merch items: variants, stock quantity, purchase limit per participant
- [ ]  **[MUST]** Out-of-stock blocked
- [ ]  **[MUST]** Stock decremented upon purchase
- [ ]  **[MUST]** Ticket + QR generated, confirmation email sent

---

## Tickets/QR

- [ ]  **[MUST]** Unique Ticket ID
- [ ]  **[MUST]** QR included on ticket
- [ ]  **[MUST]** Ticket includes event + participant details
- [ ]  **[MUST]** Ticket accessible in Participation History
- [ ]  **[MUST]** Ticket emailed on successful submission (Normal event)

---

## Deployment

- [ ]  **[MUST]** Frontend deployed (Vercel/Netlify/etc.) + production URL
- [ ]  **[MUST]** Backend deployed (Render/Railway/Fly/Heroku/etc.) + base API URL
- [ ]  **[MUST]** MongoDB Atlas used; connection via env var
- [ ]  **[MUST]** `deployment.txt` (root-level) contains Frontend URL

---

## Advanced tiers (Part 2) — implement exactly 30 marks

- [ ]  **[ADV]** Implement advanced features totaling exactly 30 marks
- [ ]  **[ADV]** Mention implemented features + justification in README
- [ ]  **[ADV]** Tier rule:
    - [ ]  Tier A: choose 2 (8 marks each)
    - [ ]  Tier B: choose 2 (6 marks each)
    - [ ]  Tier C: choose 1 (2 marks each)

### Tier A (Choose 2)

- [ ]  **[ADV]** Hackathon Team Registration
- [ ]  **[ADV]** Merchandise Payment Approval Workflow
- [ ]  **[ADV]** QR Scanner & Attendance Tracking

### Tier B (Choose 2)

- [ ]  **[ADV]** Real-time Discussion Forum
- [ ]  **[ADV]** Organizer Password Reset Workflow
- [ ]  **[ADV]** Team Chat (requires Tier A Hackathon feature)

### Tier C (Choose 1)

- [ ]  **[ADV]** Anonymous Feedback System
- [ ]  **[ADV]** Add to Calendar Integration
- [ ]  **[ADV]** Bot Protection (CAPTCHA + rate limits + IP block + admin monitoring)

---

## Deliverables

- [ ]  **[MUST]** Submit a single ZIP file
- [ ]  **[MUST]** ZIP structure exactly:
    - [ ]  `<roll_no>/backend/`
    - [ ]  `<roll_no>/frontend/`
    - [ ]  `<roll_no>/README.md`
    - [ ]  `<roll_no>/deployment.txt`
- [ ]  **[MUST]** ZIP must not be corrupt (corrupt ZIP = 0 marks)

---