
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculatrice Programmable</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #e0e0e0; /* Fond gris clair */
            text-align: center;
            padding: 50px;
            color: black;
        }
        #calculator {
            display: inline-block;
            background-color: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
            border: 2px solid #007bff;
            width: 320px; /* Largeur de la calculatrice */
            transition: transform 0.3s;
        }
        #calculator:hover {
            transform: scale(1.02); /* Effet d'agrandissement au survol */
        }
        input[type="text"], textarea {
            width: 100%;
            height: 40px;
            font-size: 24px;
            text-align: right;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            padding: 5px;
        }
        textarea {
            height: 80px; /* Hauteur de l'éditeur de script */
            resize: none;
        }
        button {
            width: 60px;
            height: 60px;
            font-size: 20px;
            margin: 5px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            background-color: #007bff;
            color: white;
            transition: background-color 0.3s, transform 0.2s;
        }
        button:hover {
            background-color: #0056b3;
            transform: scale(1.05); /* Effet d'agrandissement au survol des boutons */
        }
        button:active {
            transform: scale(0.95); /* Effet de réduction au clic */
        }
    </style>
</head>
<body>

    <h1>Calculatrice Programmable</h1>
    <div id="calculator">
        <input type="text" id="display" disabled placeholder="Résultat">
        <textarea id="scriptInput" placeholder="Écrivez votre script ici..."></textarea>
        <br>
        <button onclick="executeScript()">Exécuter</button>
        <button onclick="clearDisplay()">C</button>
        <button onclick="appendToDisplay('7')">7</button>
        <button onclick="appendToDisplay('8')">8</button>
        <button onclick="appendToDisplay('9')">9</button>
        <button onclick="appendToDisplay('/')">/</button>
        <br>
        <button onclick="appendToDisplay('4')">4</button>
        <button onclick="appendToDisplay('5')">5</button>
        <button onclick="appendToDisplay('6')">6</button>
        <button onclick="appendToDisplay('*')">*</button>
        <br>
        <button onclick="appendToDisplay('1')">1</button>
        <button onclick="appendToDisplay('2')">2</button>
        <button onclick="appendToDisplay('3')">3</button>
        <button onclick="appendToDisplay('-')">-</button>
        <br>
        <button onclick="appendToDisplay('0')">0</button>
        <button onclick="calculate()">=</button>
        <button onclick="appendToDisplay('+')">+</button>
    </div>

    <script>
        function appendToDisplay(value) {
            document.getElementById('display').value += value;
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
            document.getElementById('scriptInput').value = '';
        }

        function calculate() {
            let display = document.getElementById('display');
            try {
                display.value = eval(display.value);
            } catch (error) {
                display.value = 'Erreur';
            }
        }

        function executeScript() {
            let script = document.getElementById('scriptInput').value;
            let display = document.getElementById('display');
            try {
                let result = eval(script);
                display.value = result;
            } catch (error) {
                display.value = 'Erreur dans le script';
            }
        }
    </script>

</body>
</html>
