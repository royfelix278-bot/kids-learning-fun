<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Kids Learning Fun</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #fff5c7, #d9f7ff);
  text-align: center;
  color: #333;
}

.header {
  padding: 30px 15px 15px;
}

.header h1 {
  font-size: 36px;
  color: #ff6b6b;
  margin: 0;
}

.header p {
  font-size: 18px;
}

.games {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 15px;
  padding: 20px;
  max-width: 700px;
  margin: auto;
}

.card {
  border: none;
  border-radius: 25px;
  padding: 25px 10px;
  background: white;
  box-shadow: 0 6px 15px rgba(0,0,0,0.12);
  font-size: 19px;
  font-weight: bold;
}

.card span {
  display: block;
  font-size: 45px;
  margin-bottom: 10px;
}

.game-screen {
  display: none;
  padding: 25px 15px;
}

.question {
  font-size: 28px;
  font-weight: bold;
  margin: 25px 5px;
}

.score {
  font-size: 20px;
  font-weight: bold;
}

.answers {
  display: flex;
  justify-content: center;
  gap: 15px;
  flex-wrap: wrap;
}

.answer {
  font-size: 38px;
  background: white;
  border: none;
  border-radius: 22px;
  padding: 25px;
  min-width: 90px;
  box-shadow: 0 6px 15px rgba(0,0,0,0.15);
}

.answer:active {
  transform: scale(0.9);
}

.message {
  font-size: 26px;
  font-weight: bold;
  margin: 25px 5px;
  min-height: 65px;
}

.next {
  display: none;
  padding: 14px 28px;
  border: none;
  border-radius: 25px;
  background: #4caf50;
  color: white;
  font-size: 19px;
  font-weight: bold;
}

.back {
  margin-top: 20px;
  padding: 12px 25px;
  border: none;
  border-radius: 20px;
  background: #ff6b6b;
  color: white;
  font-size: 18px;
}

.pop {
  animation: pop 0.5s ease;
}

@keyframes pop {
  0% { transform: scale(1); }
  50% { transform: scale(1.25); }
  100% { transform: scale(1); }
}
</style>
</head>

<body>

<div id="home">

  <div class="header">
    <h1>🌈 Kids Learning Fun 🌈</h1>
    <p>Learn • Play • Enjoy!</p>
  </div>

  <div class="games">

    <button class="card" onclick="startNumbers()">
      <span>🔢</span>
      Numbers
    </button>

    <button class="card">
      <span>🔤</span>
      Alphabets
    </button>

    <button class="card">
      <span>🐶</span>
      Animals
    </button>

    <button class="card">
      <span>🎨</span>
      Colors
    </button>

    <button class="card">
      <span>🔺</span>
      Shapes
    </button>

    <button class="card">
      <span>🍎</span>
      Fruits
    </button>

    <button class="card">
      <span>🚗</span>
      Vehicles
    </button>

    <button class="card">
      <span>🐦</span>
      Birds
    </button>

    <button class="card">
      <span>🥕</span>
      Vegetables
    </button>

    <button class="card">
      <span>🐄</span>
      Farm Animals
    </button>

  </div>

</div>


<div id="numberGame" class="game-screen">

  <h1>🔢 Numbers Game</h1>

  <div class="score">
    ⭐ Score: <span id="score">0</span>
  </div>

  <div id="question" class="question">
    Which number is TWO?
  </div>

  <div id="answers" class="answers"></div>

  <div id="message" class="message"></div>

  <button id="nextButton" class="next" onclick="nextQuestion()">
    ➡️ Next Question
  </button>

  <br>

  <button class="back" onclick="goHome()">
    🏠 Home
  </button>

</div>


<script>

let correctNumber = 2;
let score = 0;

function startNumbers() {

  document.getElementById("home").style.display = "none";

  document.getElementById("numberGame").style.display = "block";

  score = 0;

  document.getElementById("score").innerText = score;

  nextQuestion();
}


function nextQuestion() {

  document.getElementById("message").innerHTML = "";

  document.getElementById("nextButton").style.display = "none";

  let numbers = [1, 2, 3];

  correctNumber = numbers[Math.floor(Math.random() * numbers.length)];

  let words = {
    1: "ONE",
    2: "TWO",
    3: "THREE"
  };

  document.getElementById("question").innerHTML =
    "Which number is " + words[correctNumber] + "?";

  let shuffled = [...numbers].sort(() => Math.random() - 0.5);

  let answerBox = document.getElementById("answers");

  answerBox.innerHTML = "";

  shuffled.forEach(function(number) {

    let button = document.createElement("button");

    button.className = "answer";

    button.innerText = number;

    button.onclick = function() {
      checkAnswer(number, button);
    };

    answerBox.appendChild(button);

  });

}


function checkAnswer(number, button) {

  if (number === correctNumber) {

    score += 10;

    document.getElementById("score").innerText = score;

    button.classList.add("pop");

    document.getElementById("message").innerHTML =
      "🎉 Congratulations! 🎉<br>⭐ Correct Answer! ⭐";

    document.getElementById("nextButton").style.display = "inline-block";

  } else {

    document.getElementById("message").innerHTML =
      "😊 Oops!<br>Try Again!";

  }

}


function goHome() {

  document.getElementById("numberGame").style.display = "none";

  document.getElementById("home").style.display = "block";

  document.getElementById("message").innerHTML = "";

}

</script>

</body>
</html>
