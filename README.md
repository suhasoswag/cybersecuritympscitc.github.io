<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cyber Security</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #000;
      color: #c8fff9;
      margin: 0;
      padding: 0;
      overflow-y: auto; 
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 0; 
    }

    header, nav, section, footer {
      position: relative;
      z-index: 1;
    }

 header {
  background-color: #004d4d;
  text-align: center;
  padding: 40px 20px;
  color: white;
  box-shadow: 0 4px 15px rgba(0, 255, 204, 0.3);
}

    nav {
      background-color: #002626;
      display: flex;
      justify-content: center;
      padding: 15px;
      border-top: 2px solid #00cccc;
      border-bottom: 2px solid #00cccc;
    }

    nav a {
      color: #66fff2;
      text-decoration: none;
      margin: 0 20px;
      font-weight: bold;
      transition: color 0.3s, text-shadow 0.3s;
      cursor: pointer;
    }

    nav a:hover {
      color: #ffffff;
      text-shadow: 0 0 10px #00ffff, 0 0 20px #00cccc;
    }

    section {
      display: none;
      padding: 50px;
      width: 80%;
      max-width: 1100px;
      margin: 60px auto;
      background-color: rgba(0, 51, 51, 0.85);
      border-radius: 15px;
      box-shadow: 0 0 25px rgba(0, 255, 204, 0.3);
    }

    section.active {
      display: block;
      animation: fadeIn 0.6s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(15px); }
      to { opacity: 1; transform: translateY(0); }
    }

    h1, h2 {
      color: #00ffff;
      text-shadow: 0 0 15px #00cccc;
    }

    .contact-info p {
      line-height: 1.8;
    }

    footer {
      background-color: #002626;
      text-align: center;
      padding: 20px;
      color: #66fff2;
      border-top: 2px solid #00cccc;
      box-shadow: 0 -4px 10px rgba(0, 255, 204, 0.2);
    }

    footer span {
      color: #00ffff;
      font-weight: bold;
    }

    img {
      display: block;
      margin: 25px auto;
      border-radius: 10px;
      max-width: 100%;
      box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
    }

    ul {
      text-align: left;
      max-width: 800px;
      margin: auto;
      font-size: 1.1em;
      line-height: 1.8;
    }

    li {
      margin-bottom: 10px;
    }
  </style>
</head>
<body>
  <canvas id="canvas"></canvas>

  <header>
    <h1>Cyber Security</h1>
    <p>Why being aware of every click matters</p>
  </header>

  <nav>
    <a onclick="showSection('home')">Home</a>
    <a onclick="showSection('contact')">Contact</a>
  </nav>

  <section id="home" class="active">
    <h2>What is Cyber Security?</h2>
    <p>Cybersecurity consists of all the technologies and practices that keep computer systems and electronic data safe.</p>
    <p>Everything is connected by computers and the internet — communication, entertainment, transportation, shopping, medicine, and more. A large amount of personal information is stored in these services, which is why cybersecurity is critical. Cyberattacks can disrupt, damage, or destroy systems and lead to identity theft, extortion, and data loss.</p>

    <img src="https://i.postimg.cc/501Yr3nf/cybersecurity.jpg" alt="Online Image">

    <h2>Why is it necessary?</h2>
    <p>Cybersecurity keeps people and organizations safe from hackers, fraud, and digital crimes. As cyberattacks become more frequent, cybersecurity professionals are in high demand to protect our personal and national security.</p>

    <h2>Ways to Implement Cybersecurity</h2>
    <ul>
      <li>Use strong, unique passwords and update them regularly.</li>
      <li>Enable two-factor authentication for extra protection.</li>
      <li>Keep your software and antivirus programs up to date.</li>
      <li>Do not click on suspicious links or attachments.</li>
      <li>Use firewalls and encryption to secure data.</li>
      <li>Backup important files regularly.</li>
    </ul>
  </section>

  <section id="contact">
    <h2>Contact Information</h2>
    <div class="contact-info">
      <p><strong>Name:</strong> Suha Binte Ibrahim</p>
      <p><strong>Class:</strong> XI</p>
      <p><strong>Section:</strong> M.Alam</p>
      <p><strong>ID:</strong> 2013FE051</p>
      <p><strong>Institution:</strong> Mohammadpur Preparatory School & College</p>
      <p><strong>Version:</strong> English</p>
      <p><strong>Wing:</strong> Girls'</p>
    </div>
  </section>



  <script>
    function showSection(id) {
      document.querySelectorAll('section').forEach(section => {
        section.classList.remove('active');
      });
      document.getElementById(id).classList.add('active');
    }

    // Matrix Background Script
    const state = {
      fps: 30,
      color: "#00ffcc",
      charset: "0123456789ABCDEF",
      size: 20
    };

    const canvas = document.getElementById("canvas");
    const ctx = canvas.getContext("2d");

    let w, h, p;
    const resize = () => {
      canvas.width = innerWidth;
      canvas.height = innerHeight;
      w = innerWidth;
      h = innerHeight;
      p = Array(Math.ceil(w / state.size)).fill(0);
    };

    window.addEventListener("resize", resize);
    resize();

    const draw = () => {
      ctx.fillStyle = "rgba(0, 0, 0, 0.08)";
      ctx.fillRect(0, 0, w, h);
      ctx.fillStyle = state.color;
      ctx.font = `${state.size}px monospace`;

      for (let i = 0; i < p.length; i++) {
        const char = state.charset[Math.floor(Math.random() * state.charset.length)];
        const x = i * state.size;
        const y = p[i] * state.size;
        ctx.fillText(char, x, y);
        if (y > h + Math.random() * 10000) p[i] = 0;
        else p[i]++;
      }
    };

    setInterval(draw, 1000 / state.fps);
  </script>
</body>
</html>
