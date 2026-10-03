# Student ReCraft 🎓🔄

A peer-to-peer campus circular economy platform built with **Python, Flask, SQLite, and Bootstrap 5**.

Students often need equipment, books, or lab supplies for a short period (a single exam, a course, or a weekend project), while other students have unused items lying around in their dorm rooms. **ReCraft** connects students within the same campus to rent, borrow for free, or giveaway unused items safely.

---

## 1. What the Project Does

* **Rent:** Rent calculators, drafting machines, cameras, bikes, or monitors by the day.
* **Borrow for Free:** Share textbooks, lab coats, and revision notes with peers at no charge.
* **Reuse / Giveaway:** Pass on items you no longer need when graduating or moving.
* **Campus Trust:** Peer accounts, verified student profiles, request workflows, and safe meeting spot coordination.

---

## 2. Requirements & Installation

This project requires **Python 3.10+**.

### Step 1: Open Terminal / Command Prompt
Open your terminal in the project directory:
```bash
cd c:\Users\User\Downloads\project1
```

### Step 2: Install Dependencies
Install Flask:
```bash
python -m pip install -r requirements.txt
```
*(Only Flask and its built-in utility Werkzeug are required; SQLite is already built into Python!)*

---

## 3. How to Run the Website

### Step 1: Initialize / Seed the Database (Optional)
The database comes pre-seeded, but you can re-seed sample items and demo accounts at any time:
```bash
python seed_data.py
```

### Step 2: Start the Web Server
```bash
python app.py
```

### Step 3: Open in Your Browser
Open your browser and navigate to:
```
http://127.0.0.1:5000
```

---

## 4. Pre-configured Demo Accounts

All sample accounts use the password: `password123`

| Student Name | Campus Email | Role in Demo |
| :--- | :--- | :--- |
| **Alex Chen** | `alex@campus.edu` | Owner of the Mini Drafter & Graphing Calculator |
| **Priya Sharma** | `priya@campus.edu` | Owner of the Chemistry Lab Coat & Calculus Bundle |
| **Marcus Miller** | `marcus@campus.edu` | Owner of the Campus Bicycle & Drawing Box |

*You can also click **Sign Up** to create your own student account at any time!*

---

## 5. Main Features

1. **Student Landing Page:** Clean hero banner with quick search, category pills, and featured items.
2. **Search & Filters:** Search by keyword and filter by category (Stationery, Electronics, Books, Lab Gear, Bikes), listing type (Rent vs. Borrow vs. Giveaway), and price.
3. **Item Details:** High-res preview, daily rate, security deposit, availability window, and campus handover spot.
4. **Post an Item:** Students can list an unused item, upload photos or automatically assign clean category graphics, set dates and prices.
5. **Rental Request Workflow:** 
   - Borrower submits a request with dates and a message.
   - Owner sees the alert on their **Requests** dashboard.
   - Owner can click **Accept** or **Decline**.
6. **Internal Messages & Handover:** Once approved, direct contact info (email, phone, meetup spot) and an internal message thread are unlocked for smooth communication.
7. **User Profile & Trust Badge:** View a student's listings, campus department, and rental history.
8. **Trust & Safety Reporting:** Built-in form to flag inappropriate items or unresponsive users.

---

## 6. Project Structure

```
project1/
│
├── app.py                  # Main Flask backend with routes & controllers
├── database.py             # SQLite database connection & table definitions
├── seed_data.py            # Pre-populates realistic student items and accounts
├── test_app.py             # Automated unit & integration tests
├── requirements.txt        # Python dependency manifest
├── README.md               # Beginner guide & documentation
│
├── static/
│   ├── css/
│   │   └── custom.css      # Custom styling, badges, and card hover effects
│   ├── images/             # Vector SVG assets (Drafter, Calculator, Bicycle, etc.)
│   └── uploads/            # Storage for student-uploaded photos
│
└── templates/              # HTML templates rendered by Flask & Jinja2
    ├── base.html           # Base layout (Navbar, alert banners, footer)
    ├── index.html          # Landing home page
    ├── browse.html         # Catalog browse, filter & search
    ├── item_detail.html    # Detailed item page & request form
    ├── post_item.html      # Form to post an item
    ├── edit_item.html      # Form to edit a listed item
    ├── my_items.html       # Management dashboard for items you posted
    ├── requests.html       # Incoming & outgoing request tracker
    ├── request_detail.html # Request status & internal messaging thread
    ├── profile.html        # Student profile & trust statistics
    ├── login.html          # Login page with demo account hints
    ├── signup.html         # Student registration form
    ├── report.html         # Trust & safety report form
    └── 404.html            # User-friendly 404 page
```

---

## 7. Database Structure (SQLite)

* **`users`:** Student identity (`id`, `name`, `email`, `password_hash`, `college`, `phone`, `bio`, `created_at`).
* **`items`:** Equipment and books listed (`id`, `owner_id`, `title`, `description`, `category`, `item_type`, `price`, `deposit`, `location`, `available_from`, `available_until`, `image_path`, `is_available`).
* **`rental_requests`:** Booking workflows (`id`, `item_id`, `requester_id`, `owner_id`, `start_date`, `end_date`, `message`, `status`).
* **`request_messages`:** Internal communication thread between owner and requester (`id`, `request_id`, `sender_id`, `message`, `created_at`).
* **`reports`:** Campus safety logs (`id`, `reporter_id`, `target_type`, `target_id`, `reason`, `details`).

---

## 8. Running Automated Tests

Run the test suite to verify all core workflows:
```bash
python test_app.py
```
All 7 unit and integration tests should pass with `OK`.

