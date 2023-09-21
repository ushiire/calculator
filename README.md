<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link rel="stylesheet" type="text/css"
        href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
</head>
<style>
    body {
        font-family: Arial, sans-serif;
        background-color: #f0f0f0;
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        margin: 0;
    }

    .container {
        background-color: #fff;
        border: 2px solid #ccc;
        border-radius: 8px;
        box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
        width: 300px;
    }

    .display {
        padding: 10px;
        text-align: right;
        font-size: 24px;
        border-bottom: 2px solid #ccc;
    }

    .btns {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
    }

    .btn {
        padding: 10px;
        font-size: 18px;
        border: 1px solid #ccc;
        border-radius: 5px;
        margin: 5px;
        cursor: pointer;
        transition: background-color 0.2s, color 0.2s;
    }

    .btn:hover {
        background-color: #eee;
    }

    /* Add styles for the new buttons here */
    #square,
    #cube,
    #abs,
    #ln,
    #exp {
        background: #ff9933;
        color: #fff;
    }

    #square:hover,
    #cube:hover,
    #abs:hover,
    #ln:hover,
    #exp:hover {
        box-shadow: inset 5px 5px 8px #cc8000, inset -5px -5px 8px #ff9933;
        background: #cc8000;
    }

    /* Number buttons */
    .number-btn {
        background-color: #f0f0f0;
        color: #000;
    }

    .number-btn:hover {
        background-color: #ccc;
    }

    /* Operator buttons */
    .operator {
        background-color: #f0f0f0;
        color: #ff9933;
    }

    .operator:hover {
        background-color: #ccc;
    }
</style>

<body>

    <div class="container">
        <div class="display">
            <input id="screen" type="text" placeholder="0" readonly>
        </div>

        <div class="btns">
            <!-- Add new buttons here -->
            <div class="row">
                <button id="ce" class="operator" onclick="backspc()">CE</button>
                <button onclick="fact()" class="operator">x!</button>
                <button class="btn operator">(</button>
                <button class="btn operator">)</button>
                <button class="btn operator">%</button>
                <button id="ac" class="operator" onclick="screen.value=''">AC</button>
            </div>

            <div class="row">
                <button onclick="sin()" class="operator">sin</button>
                <button onclick="pi()" class="operator">π</button>
                <button class="btn number-btn">7</button>
                <button class="btn number-btn">8</button>
                <button class="btn number-btn">9</button>
                <button class="btn operator">×</button>
            </div>

            <div class="row">
                <button onclick="cos()" class="operator">cos</button>
                <button onclick="log()" class="operator">log</button>
                <button class="btn number-btn">4</button>
                <button class="btn number-btn">5</button>
                <button class="btn number-btn">6</button>
                <button class="btn operator">×</button>
            </div>

            <div class="row">
                <button onclick="tan()" class="operator">tan</button>
                <button onclick="sqrt()" class="operator">√</button>
                <button class="btn number-btn">1</button>
                <button class="btn number-btn">2</button>
                <button class="btn number-btn">3</button>
                <button class="btn operator">-</button>
            </div>

            <div class="row">
                <button onclick="e()" class="operator">e</button>
                <button onclick="pow()" class="operator">x <span
                        style="position: relative; bottom: .4em; right: .1em;">y</span>
                </button>
                <button class="btn number-btn">0</button>
                <button class="btn operator">.</button>
                <button id="eval" class="operator" onclick="screen.value=eval(screen.value)">=</button>
                <button class="btn operator">+</button>
            </div>
            <!-- New buttons added here -->
            <div class="row">
                <button id="square" class="operator" onclick="square()">x²</button>
                <button id="cube" class="operator" onclick="cube()">x³</button>
                <button id="abs" class="operator" onclick="abs()">|x|</button>
                <button id="ln" class="operator" onclick="ln()">ln</button>
                <button id="exp" class="operator" onclick="exp()">e^x</button>
            </div>
        </div>
    </div>
</body>
<script>
    var screen = document.querySelector('#screen');
    var operatorBtns = document.querySelectorAll('.operator'); // Select operator buttons

    // Add event listeners for operator buttons
    for (item of operatorBtns) {
        item.addEventListener('click', (e) => {
            btntext = e.target.innerText;

            if (btntext == '×') {
                btntext = '*';
            }

            if (btntext == '÷') {
                btntext = '/';
            }

            screen.value += btntext;
        });
    }

    /* Your existing JavaScript code here */

    // New JavaScript functions for the added buttons
    function square() {
        screen.value = Math.pow(screen.value, 2);
    }

    function cube() {
        screen.value = Math.pow(screen.value, 3);
    }

    function abs() {
        screen.value = Math.abs(screen.value);
    }

    function ln() {
        screen.value = Math.log(screen.value);
    }

    function exp() {
        screen.value = Math.exp(screen.value);
    }

    // Add event listeners for number buttons
    var numBtns = document.querySelectorAll('.number-btn'); // Select number buttons
    for (item of numBtns) {
        item.addEventListener('click', (e) => {
            btntext = e.target.innerText;
            screen.value += btntext;
        });
    }

    // Existing JavaScript functions...
</script>

</html>
