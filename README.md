# Experiencial-learning-module-3-
<!DOCTYPE html>
<html lang="en">
<head>
<link rel="stylesheet" href="(exp. lea.)style.css">
<meta charset="UTF-8">
<title>Password Generator</title>
</head>

<body>

<!-- HEADER -->
<center>
<header>
    <h2>SecurePass</h2>

    <nav>
        <a href="#whysecurepass">Why SecurePass?</a> |
        <a href="#personal">Personal</a> |
        <a href="#business">Business</a> |
        <a href="#pricing">Pricing</a> |
        <a href="#partners">Partners</a>
    </nav>

    <br>

    <a href="#generator">
        <button>Get SecurePass Free</button>
    </a>
</header>
</center>

<hr>

<main>

<!-- HERO -->
<section id="home">
<center>
<h1>Instantly generate a secure, random password</h1>
<p>Use our online password generator tool to instantly create a secure password.</p>
</center>
</section>

<br><br>

<!-- GENERATOR -->
<section id="generator">
<center>

<h2>Password Generator Tool</h2>

<form>

<label for="password"><b>Password</b></label><br><br>

<input type="text" id="password">

<br><br>

<button type="button" id="refreshBtn">🔄 Refresh</button>
<button type="button" id="copyBtn">📋 Copy Password</button>

<br><br>

<label><b>Strength:</b></label><br>
<progress value="90" max="100"></progress>
<span>Strong</span>

<br><br><br>

<label for="length"><b>Password Length 12</b></label><br><br>
<input type="range" id="length" min="6" max="30" value="12">

<br><br>

<fieldset>
<legend><b>Password Options</b></legend>

<input type="checkbox" id="upper" checked>
<label for="upper">Uppercase Letters</label><br><br>

<input type="checkbox" id="lower" checked>
<label for="lower">Lowercase Letters</label><br><br>

<input type="checkbox" id="number" checked>
<label for="number">Numbers</label><br><br>

<input type="checkbox" id="symbol">
<label for="symbol">Symbols</label><br><br>

</fieldset>

<br>

<button type="submit" id="generateBtn">Generate Secure Password</button>

</form>

</center>
</section>

<br><br>

<!-- WHY SECUREPASS -->
<section id="whysecurepass">
<center>
<h2>Why Choose SecurePass?</h2>
<p>
SecurePass helps you generate, store, and manage your passwords securely.
It ensures that your digital identity remains protected at all times.
</p>

<p>🔒 Strong encryption for safety</p>
<p>⚠️ Alerts for weak passwords</p>
<p>🔑 Smart password suggestions</p>
<p>📱 Multi-device access</p>
</center>
</section>

<br>

<!-- PERSONAL -->
<section id="personal">
<center>
<h2>Personal Use</h2>

<p>Store unlimited passwords</p>
<p>Auto-fill login details</p>
<p>Generate strong passwords</p>
<p>Access from any device</p>

<p>Never worry about forgetting your passwords again.</p>
</center>
</section>

<br>

<!-- BUSINESS -->
<section id="business">
<center>
<h2>Business Solutions</h2>

<p>Team password sharing</p>
<p>Admin controls and monitoring</p>
<p>Secure employee access</p>
<p>Data breach protection</p>

<p>Ensure your business data stays safe and secure.</p>
</center>
</section>

<br>

<!-- PRICING -->
<section id="pricing">
<center>
<h2>Pricing Plans</h2>

<table border="1" cellpadding="10">
<tr>
<th>Plan</th>
<th>Features</th>
<th>Price</th>
</tr>

<tr>
<td>Free</td>
<td>Basic password storage</td>
<td>₹0/month</td>
</tr>

<tr>
<td>Premium</td>
<td>Advanced security + backup</td>
<td>₹300/month</td>
</tr>

<tr>
<td>Business</td>
<td>Team management + admin tools</td>
<td>₹800/month</td>
</tr>

</table>

</center>
</section>

<br>

<!-- PARTNERS -->
<section id="partners">
<center>
<h2>Our Partners</h2>

<p>Cloud service providers</p>
<p>Cybersecurity companies</p>
<p>Enterprise solution partners</p>
<p>Technology integrations</p>

<p>Together, we build a safer digital world.</p>
</center>
</section>

</main>

<hr>

<footer>
<center>
<p>© 2026 Password Generator</p>
</center>
</footer>

<!-- JAVASCRIPT -->
<script>

// Elements
const passwordField = document.getElementById("password");
const lengthSlider = document.getElementById("length");
const progressBar = document.querySelector("progress");
const strengthText = document.querySelector("progress + span");

const refreshBtn = document.getElementById("refreshBtn");
const copyBtn = document.getElementById("copyBtn");
const generateBtn = document.getElementById("generateBtn");

const upperCheck = document.getElementById("upper");
const lowerCheck = document.getElementById("lower");
const numberCheck = document.getElementById("number");
const symbolCheck = document.getElementById("symbol");

// Character sets
const upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
const lower = "abcdefghijklmnopqrstuvwxyz";
const numbers = "0123456789";
const symbols = "!@#$%^&*()_+~";

// Generate password
function generatePassword() {
    let length = lengthSlider.value;
    let chars = "";

    if (upperCheck.checked) chars += upper;
    if (lowerCheck.checked) chars += lower;
    if (numberCheck.checked) chars += numbers;
    if (symbolCheck.checked) chars += symbols;

    if (chars === "") {
        alert("Select at least one option!");
        return;
    }

    let password = "";
    for (let i = 0; i < length; i++) {
        password += chars.charAt(Math.floor(Math.random() * chars.length));
    }

    passwordField.value = password;
    updateStrength(password);
}

// Strength based on user choice
function updateStrength(password) {
    let strength = 0;

    if (password.length >= 6) strength += 10;
    if (password.length >= 10) strength += 15;
    if (password.length >= 14) strength += 15;

    if (upperCheck.checked) strength += 15;
    if (lowerCheck.checked) strength += 15;
    if (numberCheck.checked) strength += 15;
    if (symbolCheck.checked) strength += 15;

    if (strength > 100) strength = 100;

    progressBar.value = strength;

    if (strength <= 40) strengthText.textContent = "Weak";
    else if (strength <= 70) strengthText.textContent = "Medium";
    else strengthText.textContent = "Strong";
}

// Copy password
function copyPassword() {
    navigator.clipboard.writeText(passwordField.value);
    alert("Password Copied!");
}

// Events
refreshBtn.addEventListener("click", generatePassword);
copyBtn.addEventListener("click", copyPassword);

generateBtn.addEventListener("click", function(e) {
    e.preventDefault();
    generatePassword();
});

lengthSlider.addEventListener("input", function() {
    document.querySelector("label[for='length'] b").textContent =
        "Password Length " + lengthSlider.value;
    updateStrength(passwordField.value);
});

upperCheck.addEventListener("change", () => updateStrength(passwordField.value));
lowerCheck.addEventListener("change", () => updateStrength(passwordField.value));
numberCheck.addEventListener("change", () => updateStrength(passwordField.value));
symbolCheck.addEventListener("change", () => updateStrength(passwordField.value));

</script>

</body>
</html>
