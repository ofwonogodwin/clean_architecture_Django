#  Django Clean Architecture – School Management System (First Try)

Welcome to my first attempt at applying **Clean Architecture** in a Django project!  
This is a simple **School Management System** built using layered architecture principles to make the codebase clean, testable, and scalable.

---

##  Project Structure (Clean Architecture Style)

Each Django app (like `students`, `teachers`, etc.) follows a layered structure:


This helps separate concerns and keeps your codebase clean and organized.

---

##  Apps in This Project

- `students/` – Handles student registration and management
- `teachers/` – Manages teacher assignments
- `classes/` – Deals with class scheduling and enrollment

---

##  Example: Registering a Student

- **Domain**: Defines what a `Student` is
- **Use Case**: `RegisterStudent` logic (validates and saves the student)
- **Interface**: Django view that calls the use case
- **Infrastructure**: Uses Django ORM to save to the database

---

##  Testing Logic Without Django

Because the business logic is separate, you can test it without setting up Django or a database:

```python
def test_register_student():
    class FakeRepo:
        def save(self, student): pass

    use_case = RegisterStudent(FakeRepo())
    use_case.execute("Alice", 12)
