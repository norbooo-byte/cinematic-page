# cinematic-page
this is for beginer only
# Cinematic Motivational Webpage (Single File)

Create a folder and place:

1. `index.html` (copy the code below)
2. Your photo as `mountain.jpg` (use the image you uploaded)
3. Your own audio file as `song.mp3` *(optional — browser autoplay may require user interaction, but the Enter button solves this)*

Then open `index.html` in browser.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>I Am The Best of Beasts</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@500;700&family=Poppins:wght@300;400&display=swap" rel="stylesheet">

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      overflow: hidden;
      font-family: 'Poppins', sans-serif;
      background: black;
      color: white;
    }

    .background {
      position: fixed;
      width: 100%;
      height: 100vh;
      background: linear-gradient(rgba(0,0,0,0.45), rgba(0,0,0,0.65)), url('mountain.jpg');
      background-size: cover;
      background-position: center;
      transform: scale(1);
      animation: cinematicZoom 20s ease-in-out infinite alternate;
      z-index: -2;
    }

    .light {
      position: fixed;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, rgba(255,255,255,0.08), transparent 55%);
      animation: moveLight 12s infinite alternate ease-in-out;
      z-index: -1;
    }

    @keyframes cinematicZoom {
      from { transform: scale(1); }
      to { transform: scale(1.12); }
    }

    @keyframes moveLight {
      from { transform: translate(-10%, -10%); }
      to { transform: translate(10%, 10%); }
    }

    .enter-screen {
      position: fixed;
      width: 100%;
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      background: rgba(0,0,0,0.88);
      z-index: 10;
      transition: opacity 1.2s ease;
    }

    .enter-screen h1 {
      font-family: 'Cinzel', serif;
      letter-spacing: 4px;
      margin-bottom: 25px;
      font-size: 2rem;
      text-align: center;
    }

    .enter-btn {
      padding: 14px 35px;
      border: 1px solid rgba(255,255,255,0.5);
      border-radius: 40px;
      background: rgba(255,255,255,0.08);
      color: white;
      font-size: 1rem;
      cursor: pointer;
      backdrop-filter: blur(6px);
      transition: 0.3s;
    }

    .enter-btn:hover {
      transform: scale(1.08);
      background: rgba(255,255,255,0.15);
    }

    .content {
      display: none;
      height: 100vh;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 30px;
      animation: fadeIn 2s ease;
    }

    .card {
      background: rgba(0,0,0,0.38);
      padding: 35px;
      border-radius: 28px;
      backdrop-filter: blur(10px);
      max-width: 850px;
      box-shadow: 0 0 30px rgba(0,0,0,0.4);
    }

    .title {
      font-family: 'Cinzel', serif;
      font-size: clamp(2rem, 4vw, 4rem);
      margin-bottom: 25px;
      text-transform: uppercase;
      letter-spacing: 3px;
    }

    .message {
      white-space: pre-line;
      font-size: clamp(1rem, 2vw, 1.4rem);
      line-height: 1.9;
      font-weight: 300;
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(25px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @media (max-width: 768px) {
      .card {
        width: 95%;
        padding: 25px;
      }
    }
  </style>
</head>
<body>

  <div class="background"></div>
  <div class="light"></div>

  <div class="enter-screen" id="enterScreen">
    <h1>I AM THE BEST OF BEASTS</h1>
    <button class="enter-btn" onclick="enterExperience()">Enter</button>
  </div>

  <div class="content" id="content">
    <div class="card">
      <div class="title">I AM THE BEST OF BEASTS</div>

      <div class="message">
Dekho yeh zindagi
Kitni hasi...

Har pal khushi hai yaha
Maine itna kabhi nahi chhaha

Zindagi ne hai
Itna kuch diya
Arz ada karta hu
Mai har pal

Nahi hai mere paas
Khone ke liya kuch yaha
Par fir bhi rehta hoon
Mast magaan har jaha
      </div>
    </div>
  </div>

  <audio id="bgMusic" loop>
    <source src="song.mp3" type="audio/mp3">
  </audio>

  <script>
    function enterExperience() {
      const screen = document.getElementById('enterScreen');
      const content = document.getElementById('content');
      const music = document.getElementById('bgMusic');

      screen.style.opacity = '0';

      setTimeout(() => {
        screen.style.display = 'none';
        content.style.display = 'flex';

        // Music starts after click (browser friendly)
        music.play().catch(() => {
          console.log('Autoplay blocked');
        });
      }, 1000);
    }
  </script>

</body>
</html>
```
