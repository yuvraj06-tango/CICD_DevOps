📘 Full-Stack Automation Journey with FastAPI, Pytest, and CI/CD
In the evolving landscape of modern software development, the fusion of backend API development, automated testing, and DevOps practices has become essential. This project is a comprehensive demonstration of building a simple yet powerful REST API using FastAPI, automating its testing with Pytest, and integrating everything into a seamless CI/CD pipeline using GitHub Actions.

The motivation behind this project is to learn and implement the full development workflow — from writing backend code to automating its quality assurance and deploying with confidence.

🌐 Building the FastAPI Backend
We start by creating a backend using FastAPI — a modern, fast (high-performance) web framework for building APIs with Python 3.6+ based on standard Python type hints. In our case, we implemented a simple endpoint:

css
Copy
Edit
GET /add/{a}/{b}
This route takes two numbers, adds them, and returns the result in JSON format. The server is run using Uvicorn, a lightning-fast ASGI server suitable for production. The server can be started with the command:

bash
Copy
Edit
uvicorn main:app --reload
Once running, accessing /add/2/3 would return { "result": 5 }. Though basic in logic, it serves as a strong base for test-driven and DevOps-enabled development.

🧪 Automated Testing with Pytest
Testing is crucial in modern software. To ensure our API works as expected, we implemented two types of testing:

Manual Testing using the requests library in a Python script (testAutomation.py), which sends GET requests to the API and checks the response.

Automated Testing with Pytest in testAutomationPytest.py, which runs test cases asserting correct responses from the API.

The automated tests are simple but effective. For instance, they ensure /add/2/2 always returns {"result": 4}. This eliminates human error and ensures our API is reliable.

To run the tests locally:

bash
Copy
Edit
python -m pytest testAutomationPytest.py
Note: If pytest isn’t recognized in PowerShell, it might not be added to your PATH. Instead, using python -m pytest always works reliably across environments.

⚙️ Integrating CI/CD with GitHub Actions
Once testing is automated, the next natural step is integrating it into the deployment pipeline. Using GitHub Actions, we created a workflow (ci.yml) that triggers on every push to the repository.

This CI/CD pipeline:

Installs dependencies like fastapi, pytest, and uvicorn.

Launches the FastAPI server in the background.

Runs all Pytest test cases to ensure nothing is broken.

This setup guarantees that every commit is automatically verified — a modern DevOps practice that enhances collaboration and code reliability.

🧩 Challenges and Fixes
While setting up, common issues were encountered:

ConnectionRefusedError occurred when testing without running the API. Solution: Always start the server (uvicorn main:app --reload) before testing.

'pytest' is not recognized happened when pytest wasn’t in the system PATH. Solution: Use python -m pytest instead.

CI tests failing due to missing background server execution. Solution: Use & (for background execution) in GitHub Actions or set up the service properly.

Overcoming these hitches provided valuable real-world debugging experience.
