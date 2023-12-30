<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Hello Animation</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .container {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100%;
    }

    .box {
      width: 900px;
      height: 200px;
      background-image: linear-gradient(
        -45deg,
        #90ee90 25%, /* Light green */
        #add8e6 25%, /* Light blue */
        #add8e6 50%, /* Light blue */
        #90ee90 50%, /* Light green */
        #90ee90 75%, /* Light green */
        #add8e6 75%, /* Light blue */
        #add8e6 100% /* Light blue */
      );
      color: #eee; /* Lighter text color for contrast */
      font-size: 60px;
      border-radius: 20px;
      overflow: hidden;
      box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
      display: flex;
      justify-content: center;
      align-items: center;
      transition: transform 0.7s ease-in-out, opacity 0.7s ease-in-out; /* Adjusted transition timing */
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
      font-family: 'Tenorite', sans-serif;
      mix-blend-mode: overlay; /* Blending mode */
    }

    .text {
      opacity: 1;
      transform: scale(1);
      transition: transform 0.7s ease-in-out, opacity 0.7s ease-in-out; /* Adjusted transition timing */
      text-align: center;
    }

    .text.hidden {
      opacity: 0;
      transform: scale(0);
    }
  </style>
  <!-- Link to Tenorite font -->
  <link href="https://fonts.googleapis.com/css2?family=Tenorite&display=swap" rel="stylesheet">
</head>
<body>
  <div class="container">
    <div class="box">
      <div class="text" id="hello" lang="en"></div>
    </div>
  </div>

  <script>
    const greetings = [
      { text: 'Hello', lang: 'en' },
      { text: 'Bonjour', lang: 'fr' },
      { text: 'Hola', lang: 'es' },
      { text: 'Ciao', lang: 'it' },
      { text: 'Konnichiwa', lang: 'ja' },
      { text: 'नमस्ते', lang: 'hi' }, // "Namaste" in Hindi
      { text: 'Hallo', lang: 'de' },
      { text: 'Olá', lang: 'pt' },
      { text: 'سلام', lang: 'ur' },
      { text: 'Merhaba', lang: 'tr' }
    ];

    const textElement = document.getElementById('hello');
    let index = 0;

    function displayNextGreeting() {
      const { text, lang } = greetings[index];
      textElement.classList.add('hidden');
      setTimeout(() => {
        textElement.textContent = text;
        textElement.lang = lang;
        textElement.classList.remove('hidden');
        index++;
        if (index === greetings.length) {
          clearInterval(interval);
        }
      }, index === 0 ? 0 : 1000); // Initial display immediately, then change every 1 second
    }

    const interval = setInterval(displayNextGreeting, 1000); // Changing interval set to 1 second
  </script>
</body>
</html>
