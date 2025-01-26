#project
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multi-Page Application</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background: url('/mnt/data/earth-1756274.jpg') no-repeat center center fixed;
            background-size: cover;
            color: #f0f0f0;
        }
        header {
            background-color: rgba(30, 60, 114, 0.8);
            color: #f0f0f0;
            padding: 1.5rem;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .container {
            margin: 2rem auto;
            padding: 2rem;
            max-width: 600px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 12px;
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
            color: #333;
        }
        form {
            display: flex;
            flex-direction: column;
        }
        label {
            margin-bottom: 0.5rem;
            font-weight: bold;
            color: #555;
        }
        input {
            margin-bottom: 1rem;
            padding: 0.8rem;
            font-size: 1rem;
            border: 1px solid #ccc;
            border-radius: 8px;
            background: #f9f9f9;
            transition: border-color 0.3s;
        }
        input:focus {
            outline: none;
            border-color: #1e3c72;
        }
        button {
            padding: 0.8rem;
            font-size: 1rem;
            color: #fff;
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: background 0.3s;
        }
        button:hover {
            background: linear-gradient(135deg, #2a5298, #1e3c72);
        }
        .nav-links {
            text-align: center;
            margin-top: 1.5rem;
        }
        .nav-links a {
            margin: 0 1rem;
            text-decoration: none;
            color: #1e3c72;
            font-weight: bold;
            transition: color 0.3s;
        }
        .nav-links a:hover {
            color: #2a5298;
        }
        .highlight {
            color: #1e3c72;
            font-weight: bold;
        }
    </style>
    <script>
        function validateLogin(event) {
            event.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            if (username === "roshan" && password === "password") {
                document.getElementById('user-name').innerText = "Roshan";
                document.getElementById('user-details').innerHTML = `
                    <p><span class="highlight">Name:</span> Roshan</p>
                    <p><span class="highlight">Gender:</span> Male</p>
                    <p><span class="highlight">Age:</span> 20</p>
                    <p><span class="highlight">Occupation:</span> Defence Forces</p>
                    <p><span class="highlight">UGC:</span> Jain</p>
                `;
                showPage('user-info');
            } else {
                alert("Invalid username or password.");
            }
        }

        function showPage(pageId) {
            const pages = document.querySelectorAll('.container');
            pages.forEach(page => page.style.display = 'none');

            document.getElementById(pageId).style.display = 'block';
        }

        window.onload = function() {
            showPage('login-page');
        };
    </script>
</head>
<body>
    <header>
        <h1>Welcome to the Multi-Page App</h1>
    </header>
    
    <div class="container" id="login-page">
        <h2>Login Page</h2>
        <form onsubmit="validateLogin(event)">
            <label for="username">Username:</label>
            <input type="text" id="username" name="username" required>

            <label for="password">Password:</label>
            <input type="password" id="password" name="password" required>

            <button type="submit">Login</button>
        </form>
    </div>

    <div class="container" id="user-info" style="display: none;">
        <h2>User Information Page</h2>
        <p>Welcome, <span id="user-name">[User]</span>!</p>
        <div id="user-details"></div>
        <div class="nav-links">
            <a href="#" onclick="showPage('profile-page')">Go to Profile</a>
            <a href="#" onclick="showPage('login-page')">Logout</a>
        </div>
    </div>

    <div class="container" id="profile-page" style="display: none;">
        <h2>Personal Profile Page</h2>
        <p><span class="highlight">Name:</span> Roshan</p>
        <p><span class="highlight">Email:</span> roshan@example.com</p>
        <p><span class="highlight">Bio:</span> Aspiring member of the Defence Forces.</p>
        <div class="nav-links">
            <a href="#" onclick="showPage('user-info')">Back to User Info</a>
            <a href="#" onclick="showPage('login-page')">Logout</a>
        </div>
    </div>
</body>
</html>
