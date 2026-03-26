<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Advanced Calculator</title>

<style>
body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
    font-family: Arial;
}

.calculator {
    backdrop-filter: blur(15px);
    background: rgba(255,255,255,0.05);
    padding: 20px;
    border-radius: 20px;
    box-shadow: 0 0 40px rgba(0,0,0,0.5);
}

#display {
    width: 100%;
    height: 70px;
    font-size: 28px;
    margin-bottom: 15px;
    text-align: right;
    padding: 10px;
    border: none;
    border-radius: 10px;
    background: black;
    color: #00ffcc;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(5, 65px);
    gap: 10px;
}

button {
    height: 60px;
    font-size: 18px;
    border: none;
    border-radius: 12px;
    background: rgba(255,255,255,0.1);
    color: white;
    cursor: pointer;
}

button:hover {
    background: rgba(255,255,255,0.3);
}

.operator { background: orange; }
.equal { background: green; }
.clear { background: red; }
.science { background: #6a5acd; }

</style>
</head>

<body>

<div class="calculator">
<input type="text" id="display" disabled>

<div class="buttons">
<button class="clear" onclick="clearDisplay()">C</button>
<button onclick="del()">DEL</button>
<button onclick="append('/')">/</button>
<button onclick="append('*')">*</button>
<button onclick="append('-')">-</button>

<button onclick="append('7')">7</button>
<button onclick="append('8')">8</button>
<button onclick="append('9')">9</button>
<button onclick="append('+')" class="operator">+</button>
<button onclick="calculate()" class="equal">=</button>

<button onclick="append('4')">4</button>
<button onclick="append('5')">5</button>
<button onclick="append('6')">6</button>
<button class="science" onclick="sqrt()">√</button>
<button class="science" onclick="power()">x²</button>

<button onclick="append('1')">1</button>
<button onclick="append('2')">2</button>
<button onclick="append('3')">3</button>
<button class="science" onclick="sin()">sin</button>
<button class="science" onclick="cos()">cos</button>

<button onclick="append('0')">0</button>
<button onclick="append('.')">.</button>
<button class="science" onclick="tan()">tan</button>
<button class="science" onclick="log()">log</button>
<button class="science" onclick="pi()">π</button>
</div>
</div>

<script>
const display = document.getElementById("display");

function append(val) {
    display.value += val;
}

function clearDisplay() {
    display.value = "";
}

function del() {
    display.value = display.value.slice(0, -1);
}

function calculate() {
    try {
        display.value = eval(display.value);
    } catch {
        alert("Error");
    }
}

// Scientific functions
function sqrt() {
    display.value = Math.sqrt(eval(display.value));
}

function power() {
    display.value = Math.pow(eval(display.value), 2);
}

function sin() {
    display.value = Math.sin(eval(display.value));
}

function cos() {
    display.value = Math.cos(eval(display.value));
}

function tan() {
    display.value = Math.tan(eval(display.value));
}

function log() {
    display.value = Math.log10(eval(display.value));
}

function pi() {
    display.value += Math.PI.toFixed(8);
}

// Keyboard support
document.addEventListener("keydown", function(e) {
    if (!isNaN(e.key) || "+-*/.".includes(e.key)) {
        append(e.key);
    } else if (e.key === "Enter") {
        calculate();
    } else if (e.key === "Backspace") {
        del();
    } else if (e.key === "Escape") {
        clearDisplay();
    }
});
</script>

</body>
</html>