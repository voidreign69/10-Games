<meta name='viewport' content='width=device-width, initial-scale=1'/><!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Buddy's 10 Mini Games</title>
<style>
  body { font-family: Arial; text-align: center; background: #f0f8ff; }
  h1 { color: #333; }
  button { margin: 5px; padding: 10px 20px; font-size: 16px; cursor: pointer; }
  #gameArea { margin-top: 20px; }
</style>
</head>
<body>

<h1>🎮 Buddy's 10 Mini Games</h1>
<div id="menu">
  <button onclick="showGame(1)">1. Coin Flip</button>
  <button onclick="showGame(2)">2. Dice Roll</button>
  <button onclick="showGame(3)">3. Guess Number</button>
  <button onclick="showGame(4)">4. Rock Paper Scissors</button>
  <button onclick="showGame(5)">5. Magic 8 Ball</button>
  <button onclick="showGame(6)">6. Number Adder</button>
  <button onclick="showGame(7)">7. Random Color</button>
  <button onclick="showGame(8)">8. Roll Two Dice</button>
  <button onclick="showGame(9)">9. Coin Guess</button>
  <button onclick="showGame(10)">10. Countdown Timer</button>
</div>

<div id="gameArea"></div>

<script>
function showGame(gameId) {
  let area = document.getElementById("gameArea");
  area.innerHTML = "";

  switch(gameId) {
    case 1: // Coin Flip
      area.innerHTML = `<h2>Coin Flip</h2>
        <button onclick="alert(Math.random() < 0.5 ? 'Heads' : 'Tails')">Flip Coin</button>`;
      break;
    case 2: // Dice Roll
      area.innerHTML = `<h2>Dice Roll</h2>
        <button onclick="alert('You rolled: ' + (Math.floor(Math.random()*6)+1))">Roll Dice</button>`;
      break;
    case 3: // Guess Number
      let number = Math.floor(Math.random()*10)+1;
      area.innerHTML = `<h2>Guess the Number (1-10)</h2>
        <input id="guessInput" type="number" min="1" max="10">
        <button onclick="checkGuess()">Guess</button>`;
      window.checkGuess = () => {
        let guess = document.getElementById("guessInput").value;
        alert(guess == number ? "🎉 Correct!" : "❌ Wrong, number was " + number);
      }
      break;
    case 4: // Rock Paper Scissors
      area.innerHTML = `<h2>Rock Paper Scissors</h2>
        <button onclick="rps('Rock')">Rock</button>
        <button onclick="rps('Paper')">Paper</button>
        <button onclick="rps('Scissors')">Scissors</button>`;
      window.rps = (player) => {
        let choices = ['Rock','Paper','Scissors'];
        let comp = choices[Math.floor(Math.random()*3)];
        let result = player === comp ? 'Draw' :
          (player==='Rock' && comp==='Scissors')||(player==='Paper' && comp==='Rock')||(player==='Scissors' && comp==='Paper') ? 'You Win!' : 'You Lose!';
        alert(`Computer chose: ${comp}\nResult: ${result}`);
      }
      break;
    case 5: // Magic 8 Ball
      area.innerHTML = `<h2>Magic 8 Ball</h2>
        <input id="magicQ" placeholder="Ask a question">
        <button onclick="magicAnswer()">Ask</button>`;
      window.magicAnswer = () => {
        let answers = ['Yes','No','Maybe','Definitely','Ask later','Absolutely not'];
        alert(answers[Math.floor(Math.random()*answers.length)]);
      }
      break;
    case 6: // Number Adder
      area.innerHTML = `<h2>Number Adder</h2>
        <input id="num1" type="number" placeholder="Number 1">
        <input id="num2" type="number" placeholder="Number 2">
        <button onclick="addNumbers()">Add</button>`;
      window.addNumbers = () => {
        let sum = Number(document.getElementById("num1").value) + Number(document.getElementById("num2").value);
        alert('Sum: ' + sum);
      }
      break;
    case 7: // Random Color
      area.innerHTML = `<h2>Random Color</h2>
        <button onclick="document.body.style.background = '#'+Math.floor(Math.random()*16777215).toString(16)">Change Color</button>`;
      break;
    case 8: // Roll Two Dice
      area.innerHTML = `<h2>Roll Two Dice</h2>
        <button onclick="alert('Dice 1: '+(Math.floor(Math.random()*6)+1)+'\nDice 2: '+(Math.floor(Math.random()*6)+1))">Roll</button>`;
      break;
    case 9: // Coin Guess
      area.innerHTML = `<h2>Coin Guess</h2>
        <button onclick="coinGuess('Heads')">Heads</button>
        <button onclick="coinGuess('Tails')">Tails</button>`;
      window.coinGuess = (choice) => {
        let result = Math.random() < 0.5 ? 'Heads' : 'Tails';
        alert(`Coin: ${result}\nYou ${choice===result ? 'Win! 🎉' : 'Lose! ❌'}`);
      }
      break;
    case 10: // Countdown Timer
      area.innerHTML = `<h2>Countdown Timer (5 seconds)</h2>
        <button onclick="startCountdown()">Start</button>
        <div id="timer"></div>`;
      window.startCountdown = () => {
        let sec = 5;
        let timerDiv = document.getElementById("timer");
        let interval = setInterval(() => {
          timerDiv.innerHTML = sec;
          sec--;
          if(sec<0){ clearInterval(interval); timerDiv.innerHTML='Time Up! ⏰'; }
        },1000);
      }
      break;
  }
}
</script>

</body>
</html> 
