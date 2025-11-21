# Build-a-Portfolio-Website-with-Flask
from flask import Flask, render_template, request, redirect, url_for
app = Flask(__name__)
@app.route('/')
def home():
    return render_template('index.html')
@app.route('/about')
def about():
    return render_template('about.html')
@app.route('/projects')
def projects():
    # Example projects list (you can replace with real data)
    projects = 
    return render_template('projects.html', projects=projects)
@app.route('/contact', methods=['GET', 'POST'])
def contact():
    if request.method == 'POST':
        # In a real site you'd handle/store/send the message.
        name = request.form.get('name')
        email = request.form.get('email')
        message = request.form.get('message')
        # For now just redirect to thank you page (or back to contact)
        return render_template('contact_thanks.html', name=name)
    return render_template('contact.html')
if __name__ == '__main__':
    app.run(debug=True)
=== portfolio_website/requirements.txt ===
Flask==3.0.0
=== portfolio_website/static/style.css ===
{
    box-sizing: border-box;
}
body {
    font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    margin: 0;
    background: #f7f7fa;
    color: #1f2937;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
header {
    background: linear-gradient(90deg, #0f172a, #0b1220);
    color: #fff;
    padding: 28px 16px;
    text-align: center;
}
header h1 {
    margin: 0;
    font-size: 28px;
    letter-spacing: 0.4px;
}
nav {
    margin-top: 10px;
}
nav a {
    color: rgba(255,255,255,0.95);
    margin: 0 12px;
    text-decoration: none;
    font-weight: 600;
}
.container {
    max-width: 960px;
    margin: 28px auto;
    padding: 0 16px;
}
.hero {
    display: flex;
    gap: 24px;
    align-items: center;
    margin-bottom: 20px;
}
.hero .intro {
    flex: 1;
}
.profile {
    width: 140px;
    height: 140px;
    border-radius: 12px;
    object-fit: cover;
    border: 6px solid #fff;
    box-shadow: 0 8px 30px rgba(2,6,23,0.12);
}
.card {
    background: #fff;
    padding: 20px;
    margin: 18px 0;
    border-radius: 12px;
    box-shadow: 0 6px 18px rgba(15,23,42,0.06);
}
.projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill,minmax(240px,1fr));
    gap: 16px;
}
.project-item h3 {
    margin: 0 0 8px;
}
.btn {
    display: inline-block;
    padding: 10px 14px;
    border-radius: 8px;
    background: #111827;
    color: #fff;
    text-decoration: none;
    font-weight: 600;
}
.contact-form input[type="text"],
.contact-form input[type="email"],
.contact-form textarea {
    width: 100%;
    padding: 10px;
    margin-top: 8px;
    border-radius: 8px;
    border: 1px solid #e6e9ef;
    font-size: 14px;
}
.contact-form label {
    display: block;
    margin-top: 12px;
    font-weight: 600;
}
footer {
    text-align: center;
    color: #6b7280;
    padding: 20px 16px;
    margin-top: 24px;
}
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Home — My Portfolio</title>
  <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
  <header>
    <h1>My Portfolio</h1>
    <nav>
      <a href="{{ url_for('home') }}">Home</a>
      <a href="{{ url_for('about') }}">About</a>
      <a href="{{ url_for('projects') }}">Projects</a>
      <a href="{{ url_for('contact') }}">Contact</a>
    </nav>
  </header>
  <div class="container">
    <section class="hero card">
      <div class="intro">
        <h2>Hello — I'm [Your Name]</h2>
        <p>I’m a developer who builds web apps with Python and Flask. I love building clean, useful interfaces and solving real problems.</p>
        <p><a class="btn" href="{{ url_for('projects') }}">See my projects</a></p>
      </div>
      <div>
        <img class="profile" src="{{ url_for('static', filename='profile.jpg') }}" alt="Profile image" onerror="this.style.display='none'">
      </div>
    </section>
    <section class="card">
      <h3>Skills</h3>
      <p>Python · Flask · HTML · CSS · JavaScript · SQL</p>
    </section>
    <section class="card">
      <h3>Recent Work</h3>
      <div class="projects-grid">
        <div class="project-item">
          <h4>Mini CRM</h4>
          <p>Small customer management app built with Flask and SQLite.</p>
        </div>
        <div class="project-item">
          <h4>Blog Platform</h4>
          <p>Static and dynamic blog using Flask templates and Markdown content.</p>
        </div>
      </div>
    </section>
  </div>

  <footer>
    © {{ (2025) }} • Built with Flask
  </footer>
</body>
</html>

=== portfolio_website/templates/about.html ===
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>About — My Portfolio</title>
  <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
  <header>
    <h1>About Me</h1>
    <nav>
      <a href="{{ url_for('home') }}">Home</a>
      <a href="{{ url_for('about') }}">About</a>
      <a href="{{ url_for('projects') }}">Projects</a>
      <a href="{{ url_for('contact') }}">Contact</a>
    </nav>
  </header>

  <div class="container">
    <section class="card">
      <h2>Who I Am</h2>
      <p>I'm a web developer focused on building accessible, performant websites and applications. My stack typically includes Python, Flask, and standard front-end technologies.</p>
  <h3>Education</h3>
      <p>Degree or coursework here — replace with your details.</p>
   <h3>Interests</h3>
      <p>Open-source, learning new languages, hiking and photography.</p>
    </section>
  </div>

  <footer>
    © {{ (2025) }}
  </footer>
</body>
</html>

=== portfolio_website/templates/projects.html ===
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Projects — My Portfolio</title>
  <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
  <header>
    <h1>Projects</h1>
    <nav>
      <a href="{{ url_for('home') }}">Home</a>
      <a href="{{ url_for('about') }}">About</a>
      <a href="{{ url_for('projects') }}">Projects</a>
      <a href="{{ url_for('contact') }}">Contact</a>
    </nav>
  </header>
  <div class="container">
    <div class="card">
      <h2>My Projects</h2>
      <div class="projects-grid">
        {% for p in projects %}
        <div class="project-item card">
          <h3>{{ p.title }}</h3>
          <p>{{ p.desc }}</p>
          <p><a href="{{ p.link }}" class="btn">View</a></p>
        </div>
        {% endfor %}
      </div>
    </div>
  </div>

  <footer>
    © {{ (2025) }}
  </footer>
</body>
</html>
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Contact — My Portfolio</title>
  <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
  <header>
    <h1>Contact</h1>
    <nav>
      <a href="{{ url_for('home') }}">Home</a>
      <a href="{{ url_for('about') }}">About</a>
      <a href="{{ url_for('projects') }}">Projects</a>
      <a href="{{ url_for('contact') }}">Contact</a>
    </nav>
  </header>
  <div class="container">
    <div class="card">
      <h2>Get in touch</h2>
      <form class="contact-form" method="post" action="{{ url_for('contact') }}">
        <label for="name">Name</label>
        <input id="name" name="name" type="text" placeholder="Your name" required>
  <label for="email">Email</label>
        <input id="email" name="email" type="email" placeholder="you@example.com" required>
    <label for="message">Message</label>
        <textarea id="message" name="message" rows="6" placeholder="Write a quick message..." required></textarea>
   <div style="margin-top:12px;">
          <button class="btn" type="submit">Send</button>
        </div>
      </form>
    </div>
  </div>

  <footer>
    © {{ (2025) }}
  </footer>
</body>
</html>

=== portfolio_website/templates/contact_thanks.html ===
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Thanks — My Portfolio</title>
  <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
  <header>
    <h1>Thank you!</h1>
    <nav>
      <a href="{{ url_for('home') }}">Home</a>
      <a href="{{ url_for('about') }}">About</a>
      <a href="{{ url_for('projects') }}">Projects</a>
      <a href="{{ url_for('contact') }}">Contact</a>
    </nav>
  </header>

  <div class="container">
    <div class="card">
      <h2>Thanks, {{ name }}!</h2>
      <p>Your message has been received. I'll get back to you soon.</p>
      <p><a href="{{ url_for('home') }}" class="btn">Return home</a></p>
    </div>
  </div>

  <footer>
    © {{ (2025) }}
  </footer>
</body>
</html>
