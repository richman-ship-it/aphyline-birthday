# aphyline-birthday
a birthday gift
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Happy Birthday Aphyline</title>
<style>
  body {
    margin: 0;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background: linear-gradient(to top right, #ff9a9e, #fad0c4, #fad0c4);
    overflow: hidden;
    font-family: 'Comic Sans MS', cursive, sans-serif;
  }
  h1 {
    font-size: 3em;
    color: #fff;
    text-shadow: 0 0 10px #ff0080, 0 0 20px #ff0080, 0 0 30px #ff0080;
    animation: glow 2s ease-in-out infinite alternate;
    margin: 20px;
    z-index: 10;
  }
  @keyframes glow {
    from { text-shadow: 0 0 10px #ff0080, 0 0 20px #ff0080; }
    to   { text-shadow: 0 0 20px #ff80ff, 0 0 40px #ff80ff; }
  }
  p {
    font-size: 1.4em;
    color: #fff;
    text-align: center;
    z-index: 10;
  }
  .balloon {
    position: absolute;
    bottom: -150px;
    width: 60px;
    height: 80px;
    background: red;
    border-radius: 50% 50% 45% 55%;
    animation: float 10s linear infinite;
    z-index: 5;
  }
  @keyframes float {
    0% { transform: translateY(0) rotate(0deg); opacity: 1; }
    100% { transform: translateY(-120vh) rotate(360deg); opacity: 0; }
  }
  canvas {
    position: absolute;
    top: 0; left: 0;
    z-index: 1;
  }
  video {
    position: absolute;
    top: 0; left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 0;
    opacity: 0.25; /* makes it a soft background */
  }
</style>
</head>
<body>
  <!-- Background video -->
  <video autoplay loop muted>
    <source src="your-video.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>

  <!-- Birthday text -->
  <h1>🎂 Happy Birthday Aphyline 🎂</h1>
  <p>Wishing you joy, love, and endless happiness today 💖</p>

  <!-- Balloons (random colors) -->
  <div class="balloon" style="left:10%; background: pink; animation-duration: 8s;"></div>
  <div class="balloon" style="left:30%; background: purple; animation-duration: 12s;"></div>
  <div class="balloon" style="left:50%; background: yellow; animation-duration: 10s;"></div>
  <div class="balloon" style="left:70%; background: lightblue; animation-duration: 14s;"></div>
  <div class="balloon" style="left:90%; background: orange; animation-duration: 11s;"></div>

  <!-- Confetti canvas -->
  <canvas id="confetti"></canvas>

<script>
  // Confetti animation
  const canvas = document.getElementById('confetti');
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  const confetti = [];
  for (let i = 0; i < 150; i++) {
    confetti.push({
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height - canvas.height,
      r: Math.random() * 6 + 4,
      d: Math.random() * 10 + 10,
      color: `hsl(${Math.random() * 360}, 100%, 50%)`,
      tilt: Math.random() * 10 - 10
    });
  }

  function drawConfetti() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    confetti.forEach(c => {
      ctx.beginPath();
      ctx.fillStyle = c.color;
      ctx.ellipse(c.x, c.y, c.r, c.r / 2, c.tilt, 0, 2 * Math.PI);
      ctx.fill();
    });
    updateConfetti();
  }

  function updateConfetti() {
    confetti.forEach(c => {
      c.y += c.d * 0.2;
      if (c.y > canvas.height) {
        c.y = -10;
        c.x = Math.random() * canvas.width;
      }
    });
  }

  setInterval(drawConfetti, 30);
</script>
</body>
</html>
