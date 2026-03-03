<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MomCare - Pregnancy SOS</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
            min-height: 100vh;
        }

        /* Login/Register Screen */
        .auth-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .auth-box {
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.1);
            width: 100%;
            max-width: 400px;
        }

        .auth-logo {
            text-align: center;
            margin-bottom: 30px;
        }

        .auth-logo h1 {
            color: #e91e63;
            font-size: 32px;
        }

        .auth-logo span {
            font-size: 50px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #333;
            font-weight: 600;
        }

        .form-group input {
            width: 100%;
            padding: 15px;
            border: 2px solid #eee;
            border-radius: 10px;
            font-size: 16px;
            transition: 0.3s;
        }

        .form-group input:focus {
            outline: none;
            border-color: #e91e63;
        }

        .btn {
            width: 100%;
            padding: 15px;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
        }

        .btn-primary {
            background: #e91e63;
            color: white;
        }

        .btn-primary:hover {
            background: #c2185b;
        }

        .btn-secondary {
            background: #f8bbd0;
            color: #e91e63;
            margin-top: 10px;
        }

        .btn-secondary:hover {
            background: #f48fb1;
        }

        .toggle-auth {
            text-align: center;
            margin-top: 20px;
            color: #666;
        }

        .toggle-auth a {
            color: #e91e63;
            text-decoration: none;
            font-weight: 600;
        }

        /* Main Dashboard */
        .dashboard {
            display: none;
            padding: 20px;
            max-width: 600px;
            margin: 0 auto;
        }

        .dashboard-header {
            background: white;
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .dashboard-header h2 {
            color: #e91e63;
        }

        .logout-btn {
            background: #ff6b6b;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
        }

        /* SOS Button */
        .sos-section {
            background: white;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            margin-bottom: 20px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .sos-btn {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: linear-gradient(135deg, #ff416c, #ff4b2b);
            border: 8px solid white;
            color: white;
            font-size: 36px;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 10px 40px rgba(255, 65, 108, 0.4);
            transition: 0.3s;
            animation: pulse 2s infinite;
        }

        .sos-btn:hover {
            transform: scale(1.05);
        }

        .sos-btn:active {
            transform: scale(0.95);
        }

        @keyframes pulse {
            0%, 100% { box-shadow: 0 10px 40px rgba(255, 65, 108, 0.4); }
            50% { box-shadow: 0 10px 60px rgba(255, 65, 108, 0.6); }
        }

        /* Quick Contacts */
        .contacts-section {
            background: white;
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .contacts-section h3 {
            color: #333;
            margin-bottom: 15px;
        }

        .contact-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
        }

        .contact-btn {
            padding: 20px;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            transition: 0.3s;
        }

        .contact-btn span {
            font-size: 28px;
        }

        .contact-husband { background: #e3f2fd; color: #1976d2; }
        .contact-doctor { background: #e8f5e9; color: #388e3c; }
        .contact-ambulance { background: #ffebee; color: #d32f2f; }
        .contact-family { background: #fff3e0; color: #f57c00; }

        .contact-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        /* Due Date & Contraction Timer */
        .info-section {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
            margin-bottom: 20px;
        }

        .info-card {
            background: white;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .info-card h4 {
            color: #666;
            margin-bottom: 10px;
            font-size: 14px;
        }

        .info-card .value {
            font-size: 28px;
            font-weight: bold;
            color: #e91e63;
        }

        .info-card .sub-text {
            font-size: 12px;
            color: #999;
            margin-top: 5px;
        }

        /* Contraction Timer */
        .timer-section {
            background: white;
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .timer-section h3 {
            color: #333;
            margin-bottom: 15px;
            text-align: center;
        }

        .timer-display {
            font-size: 48px;
            font-weight: bold;
            color: #e91e63;
            text-align: center;
            margin: 20px 0;
        }

        .timer-controls {
            display: flex;
            gap: 10px;
            justify-content: center;
        }

        .timer-btn {
            padding: 15px 30px;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
        }

        .timer-btn.start {
            background: #4caf50;
            color: white;
        }

        .timer-btn.stop {
            background: #f44336;
            color: white;
        }

        .timer-btn.reset {
            background: #ff9800;
            color: white;
        }

        .contractions-count {
            text-align: center;
            margin-top: 15px;
            color: #666;
        }

        /* Medical Info */
        .medical-section {
            background: white;
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .medical-section h3 {
            color: #333;
            margin-bottom: 15px;
        }

        .medical-info {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
        }

        .medical-item {
            padding: 15px;
            background: #f8f9fa;
            border-radius: 10px;
        }

        .medical-item label {
            font-size: 12px;
            color: #666;
            display: block;
            margin-bottom: 5px;
        }

        .medical-item span {
            font-size: 16px;
            font-weight: 600;
            color: #333;
        }

        /* Location */
        .location-section {
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .location-section h3 {
            color: #333;
            margin-bottom: 15px;
        }

        .location-btn {
            width: 100%;
            padding: 15px;
            background: #9c27b0;
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            margin-bottom: 10px;
        }

        .location-text {
            text-align: center;
            color: #666;
            font-size: 14px;
        }

        /* Hidden class */
        .hidden {
            display: none !important;
        }
        h1{
            text-align: center;
            color: #e91e63;
            background:fixed;
        }
    </style>
</head>
<body>
    <h1>EMERGENCY HELP FOR PREGNANCY</h1>

    <!-- Login/Register Section -->
    <div class="auth-container" id="authSection">
        <div class="auth-box">
            <div class="auth-logo">
                <span>🤰</span>
                <h1>MomCare</h1>
            </div>

            <!-- Login Form -->
            <form id="loginForm">
                <div class="form-group">
                    <label>Username</label>
                    <input type="text" id="loginUsername" placeholder="Enter username" required>
                </div>
                <div class="form-group">
                    <label>Password</label>
                    <input type="password" id="loginPassword" placeholder="Enter password" required>
                </div>
                <button type="submit" class="btn btn-primary">Login</button>
            </form>

            <div class="toggle-auth">
                Don't have an account? <a href="#" onclick="showRegister()">Register</a>
            </div>

            <!-- Register Form (Hidden by default) -->
            <form id="registerForm" class="hidden">
                <div class="form-group">
                    <label>Your Name</label>
                    <input type="text" id="regName" placeholder="Enter your name" required>
                </div>
                <div class="form-group">
                    <label>Username</label>
                    <input type="text" id="regUsername" placeholder="Choose username" required>
                </div>
                <div class="form-group">
                    <label>Password</label>
                    <input type="password" id="regPassword" placeholder="Choose password" required>
                </div>
                <div class="form-group">
                    <label>Due Date</label>
                    <input type="date" id="regDueDate" required>
                </div>
                <button type="submit" class="btn btn-primary">Register</button>
            </form>

            <div class="toggle-auth hidden" id="toggleToLogin">
                Already have an account? <a href="#" onclick="showLogin()">Login</a>
            </div>
        </div>
    </div>

    <!-- Dashboard Section -->
    <div class="dashboard" id="dashboard">
        <div class="dashboard-header">
            <h2>🤰Welcome, <span id="userName">Mom</span>!</h2>
            <button class="logout-btn" onclick="logout()">Logout</button>
        </div>

        <!-- SOS Button -->
        <div class="sos-section">
            <button class="sos-btn" onclick="triggerEHP()">EHP</button>
            <p style="margin-top: 15px; color: #666;">Press in case of emergency</p>
        </div>

        <!-- Due Date & Days Pregnant -->
        <div class="info-section">
            <div class="info-card">
                <h4>Due Date</h4>
                <div class="value" id="dueDateDisplay">--</div>
                <div class="sub-text" id="daysLeft">-- days left</div>
            </div>
            <div class="info-card">
                <h4>Current Week</h4>
                <div class="value" id="pregnancyWeek">--</div>
                <div class="sub-text">pregnant</div>
            </div>
        </div>

        <!-- Quick Contacts -->
        <div class="contacts-section">
            <h3>📞 Quick Contacts</h3>
            <div class="contact-grid">
                <button class="contact-btn contact-husband" onclick="callContact('husband')">
                    <span>👨</span>
                    Husband
                </button>
                <button class="contact-btn contact-doctor" onclick="callContact('doctor')">
                    <span>👩‍⚕️</span>
                    Doctor
                </button>
                <button class="contact-btn contact-ambulance" onclick="callContact('ambulance')">
                    <span>🚑</span>
                    Ambulance
                </button>
                <button class="contact-btn contact-family" onclick="callContact('family')">
                    <span>👨‍👩‍👧</span>
                    Family
                </button>
            </div>
            <a href="edit-contacts.html" style="text-decoration: none;">
                <button class="btn btn-secondary" style="margin-top: 15px;">Edit Contacts</button>
            </a>
        </div>

        <!-- Contraction Timer -->
        <div class="timer-section">
            <h3>⏱️ Contraction Timer</h3>
            <div class="timer-display" id="timerDisplay">00:00</div>
            <div class="timer-controls">
                <button class="timer-btn start" onclick="startTimer()">Start</button>
                <button class="timer-btn stop" onclick="stopTimer()">Stop</button>
                <button class="timer-btn reset" onclick="resetTimer()">Reset</button>
            </div>
            <div class="contractions-count">
                Contractions: <span id="contractionCount">0</span>
            </div>
        </div>

        <!-- Medical Info -->
        <div class="medical-section">
            <h3>🏥 Medical Information</h3>
            <div class="medical-info">
                <div class="medical-item">
                    <label>Blood Type</label>
                    <span id="bloodType">Not set</span>
                </div>
                <div class="medical-item">
                    <label>Allergies</label>
                    <span id="allergies">None</span>
                </div>
                <div class="medical-item">
                    <label>Doctor's Name</label>
                    <span id="doctorName">Not set</span>
                </div>
                <div class="medical-item">
                    <label>Doctor's Phone</label>
                    <span id="doctorPhone">Not set</span>
                </div>
            </div>
            <a href="medical-info.html" style="text-decoration: none;">
                <button class="btn btn-secondary" style="margin-top: 15px;">Edit Medical Info</button>
            </a>
        </div>

        <!-- Location -->
        <div class="location-section">
            <h3>📍 Share Location</h3>
            <a href="share-location.html" style="text-decoration: none;">
                <button class="location-btn">📍 Share My Location</button>
            </a>
            <p class="location-text" id="locationText">Click to share via WhatsApp, SMS, or copy</p>
        </div>
    </div>

    <script>
        // User data storage
        let users = JSON.parse(localStorage.getItem('momcare_users')) || [];
        let currentUser = JSON.parse(localStorage.getItem('momcare_current')) || null;

        // Timer variables
        let timerInterval;
        let seconds = 0;
        let isTimerRunning = false;
        let contractionCount = 0;

        // Check if user is already logged in
        if (currentUser) {
            showDashboard();
        }

        // Login Form
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const username = document.getElementById('loginUsername').value;
            const password = document.getElementById('loginPassword').value;

            const user = users.find(u => u.username === username && u.password === password);
            
            if (user) {
                currentUser = user;
                localStorage.setItem('momcare_current', JSON.stringify(user));
                showDashboard();
            } else {
                alert('Invalid username or password!');
            }
        });

        // Register Form
        document.getElementById('registerForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('regName').value;
            const username = document.getElementById('regUsername').value;
            const password = document.getElementById('regPassword').value;
            const dueDate = document.getElementById('regDueDate').value;

            if (users.find(u => u.username === username)) {
                alert('Username already exists!');
                return;
            }

            const newUser = {
                name,
                username,
                password,
                dueDate,
                bloodType: 'Not set',
                allergies: 'None',
                doctorName: 'Not set',
                doctorPhone: 'Not set',
                husbandPhone: '',
                familyPhone: ''
            };

            users.push(newUser);
            localStorage.setItem('momcare_users', JSON.stringify(users));
            
            currentUser = newUser;
            localStorage.setItem('momcare_current', JSON.stringify(newUser));
            
            alert('Registration successful!');
            showDashboard();
        });

        function showRegister() {
            document.getElementById('loginForm').classList.add('hidden');
            document.getElementById('registerForm').classList.remove('hidden');
            document.getElementById('toggleToLogin').classList.remove('hidden');
            document.querySelector('.toggle-auth').classList.add('hidden');
        }

        function showLogin() {
            document.getElementById('loginForm').classList.remove('hidden');
            document.getElementById('registerForm').classList.add('hidden');
            document.getElementById('toggleToLogin').classList.add('hidden');
            document.querySelector('.toggle-auth').classList.remove('hidden');
        }

        function showDashboard() {
            document.getElementById('authSection').classList.add('hidden');
            document.getElementById('dashboard').style.display = 'block';
            
            // Load user data
            document.getElementById('userName').textContent = currentUser.name || 'Mom';
            
            if (currentUser.dueDate) {
                const dueDate = new Date(currentUser.dueDate);
                document.getElementById('dueDateDisplay').textContent = dueDate.toLocaleDateString();
                
                const today = new Date();
                const diffTime = dueDate - today;
                const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
                document.getElementById('daysLeft').textContent = diffDays + ' days left';
                
                // Calculate pregnancy week
                const conceived = new Date(dueDate);
                conceived.setDate(conceived.getDate() - 280); // 40 weeks
                const weeks = Math.floor((today - conceived) / (7 * 24 * 60 * 60 * 1000));
                document.getElementById('pregnancyWeek').textContent = weeks > 0 ? weeks : 0;
            }
            
            // Load medical info
            document.getElementById('bloodType').textContent = currentUser.bloodType || 'Not set';
            document.getElementById('allergies').textContent = currentUser.allergies || 'None';
            document.getElementById('doctorName').textContent = currentUser.doctorName || 'Not set';
            document.getElementById('doctorPhone').textContent = currentUser.doctorPhone || 'Not set';
        }

        function logout() {
            currentUser = null;
            localStorage.removeItem('momcare_current');
            document.getElementById('dashboard').style.display = 'none';
            document.getElementById('authSection').classList.remove('hidden');
            
            // Reset forms
            document.getElementById('loginForm').reset();
            document.getElementById('registerForm').reset();
            showLogin();
        }

        function triggerSOS() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(function(position) {
                    const lat = position.coords.latitude;
                    const lng = position.coords.longitude;
                    const message = `EMERGENCY! Pregnant woman needs help!\nLocation: https://maps.google.com/?q=${lat},${lng}`;
                    
                    alert('Emergency alert sent!\n\nLocation: ' + lat + ', ' + lng);
                    
                    // In a real app, this would send to emergency services
                    console.log('SOS triggered at:', lat, lng);
                }, function() {
                    alert('EMERGENCY! Unable to get location, but help is on the way!');
                });
            } else {
                alert('EMERGENCY! Unable to get location!');
            }
        }

        function callContact(type) {
            let phone = '';
            switch(type) {
                case 'husband':
                    phone = currentUser.husbandPhone || prompt('Enter husband phone number:');
                    break;
                case 'doctor':
                    phone = currentUser.doctorPhone || currentUser.doctorPhone;
                    break;
                case 'ambulance':
                    phone = '102'; // Ambulance number in India
                    break;
                case 'family':
                    phone = currentUser.familyPhone || prompt('Enter family phone number:');
                    break;
            }
            
            if (phone) {
                window.location.href = 'tel:' + phone;
            } else {
                alert('Phone number not set. Please edit your profile.');
            }
        }

        // Timer functions
        function startTimer() {
            if (!isTimerRunning) {
                isTimerRunning = true;
                timerInterval = setInterval(function() {
                    seconds++;
                    updateTimerDisplay();
                }, 1000);
            }
        }

        function stopTimer() {
            if (isTimerRunning) {
                isTimerRunning = false;
                clearInterval(timerInterval);
                contractionCount++;
                document.getElementById('contractionCount').textContent = contractionCount;
            }
        }

        function resetTimer() {
            isTimerRunning = false;
            clearInterval(timerInterval);
            seconds = 0;
            contractionCount = 0;
            updateTimerDisplay();
            document.getElementById('contractionCount').textContent = 0;
        }

        function updateTimerDisplay() {
            const mins = Math.floor(seconds / 60).toString().padStart(2, '0');
            const secs = (seconds % 60).toString().padStart(2, '0');
            document.getElementById('timerDisplay').textContent = mins + ':' + secs;
        }

        function editMedicalInfo() {
            const bloodType = prompt('Blood Type:', currentUser.bloodType);
            const allergies = prompt('Allergies:', currentUser.allergies);
            const doctorName = prompt('Doctor Name:', currentUser.doctorName);
            const doctorPhone = prompt('Doctor Phone:', currentUser.doctorPhone);
            const husbandPhone = prompt('Husband Phone:', currentUser.husbandPhone);
            const familyPhone = prompt('Family Phone:', currentUser.familyPhone);

            if (bloodType !== null) currentUser.bloodType = bloodType;
            if (allergies !== null) currentUser.allergies = allergies;
            if (doctorName !== null) currentUser.doctorName = doctorName;
            if (doctorPhone !== null) currentUser.doctorPhone = doctorPhone;
            if (husbandPhone !== null) currentUser.husbandPhone = husbandPhone;
            if (familyPhone !== null) currentUser.familyPhone = familyPhone;

            // Update in localStorage
            const userIndex = users.findIndex(u => u.username === currentUser.username);
            if (userIndex !== -1) {
                users[userIndex] = currentUser;
                localStorage.setItem('momcare_users', JSON.stringify(users));
                localStorage.setItem('momcare_current', JSON.stringify(currentUser));
            }

            showDashboard();
        }

        function shareLocation() {
            if (navigator.geolocation) {
                document.getElementById('locationText').textContent = 'Getting location...';
                navigator.geolocation.getCurrentPosition(function(position) {
                    const lat = position.coords.latitude;
                    const lng = position.coords.longitude;
                    document.getElementById('locationText').textContent = 
                        'Lat: ' + lat.toFixed(6) + ', Lng: ' + lng.toFixed(6);
                }, function() {
                    document.getElementById('locationText').textContent = 'Unable to get location';
                });
            } else {
                document.getElementById('locationText').textContent = 'Geolocation not supported';
            }
        }
    </script>
</body>
</html>
