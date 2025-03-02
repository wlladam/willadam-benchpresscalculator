<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Bench Press PR Calculator</title>
    
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 20px;
        }

        .container {
            max-width: 400px;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        h1 {
            color: #333;
        }

        input {
            width: 80%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }

        button {
            background-color: #28a745;
            color: white;
            padding: 10px 15px;
            border: none;
            cursor: pointer;
            font-size: 18px;
            border-radius: 5px;
        }

        button:hover {
            background-color: #218838;
        }

        #result, #ratioResult {
            font-size: 20px;
            font-weight: bold;
            margin-top: 15px;
        }

        hr {
            margin: 20px 0;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Bench Press PR Calculator</h1>
    <p>Enter the weight lifted and the number of reps to estimate your 1-rep max.</p>

    <label for="weight">Weight Lifted (lbs/kg):</label>
    <input type="number" id="weight" placeholder="Enter weight lifted" required>

    <label for="reps">Reps Performed:</label>
    <input type="number" id="reps" placeholder="Enter reps" required>

    <button onclick="calculatePR()">Calculate 1RM</button>

    <p id="result"></p>

    <hr>

    <h2>Weight-to-Strength Ratio</h2>
    <p>Enter your body weight and bench press max to calculate your weight-to-strength ratio.</p>

    <label for="bodyWeight">Your Body Weight (lbs/kg):</label>
    <input type="number" id="bodyWeight" placeholder="Enter your body weight" required>

    <label for="benchMax">Your Bench Press Max (lbs/kg):</label>
    <input type="number" id="benchMax" placeholder="Enter your bench press max" required>

    <button onclick="calculateWeightStrengthRatio()">Calculate Ratio</button>

    <p id="ratioResult"></p>
</div>

<script>
    // Function to calculate the 1-Rep Max (1RM)
    function calculatePR() {
        let weight = parseFloat(document.getElementById("weight").value);
        let reps = parseInt(document.getElementById("reps").value);

        if (isNaN(weight) || isNaN(reps) || weight <= 0 || reps <= 0) {
            document.getElementById("result").innerHTML = "Please enter valid numbers!";
            return;
        }

        let oneRepMax = weight * (1 + reps / 30);
        document.getElementById("result").innerHTML = 
            `Estimated 1-Rep Max: <strong>${oneRepMax.toFixed(2)}</strong> lbs/kg`;
    }

    // Function to calculate the Weight-to-Strength Ratio
    function calculateWeightStrengthRatio() {
        let bodyWeight = parseFloat(document.getElementById("bodyWeight").value);
        let benchMax = parseFloat(document.getElementById("benchMax").value);

        if (isNaN(bodyWeight) || isNaN(benchMax) || bodyWeight <= 0 || benchMax <= 0) {
            document.getElementById("ratioResult").innerHTML = "Please enter valid numbers!";
            return;
        }

        let ratio = benchMax / bodyWeight;
        document.getElementById("ratioResult").innerHTML = 
            `Your Weight-to-Strength Ratio: <strong>${ratio.toFixed(2)}</strong>`;
    }
</script>

</body>
</html>
