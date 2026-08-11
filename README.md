# uprogramtech.github.io


<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Quantitative Computer Architecture — Lab 1</title>

<style>
    * {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        font-family: Arial, Helvetica, sans-serif;
        background: #f4f6f8;
        color: #1f2937;
        line-height: 1.5;
    }

    header {
        background: #17365d;
        color: white;
        padding: 28px 40px;
    }

    header h1 {
        margin: 0 0 6px;
        font-size: 30px;
    }

    header p {
        margin: 0;
        opacity: 0.9;
    }

    .container {
        max-width: 1200px;
        margin: 30px auto;
        padding: 0 20px;
    }

    .card {
        background: white;
        border-radius: 10px;
        padding: 25px;
        margin-bottom: 25px;
        box-shadow: 0 2px 8px rgba(0,0,0,0.08);
    }

    h2 {
        margin-top: 0;
        color: #17365d;
        border-bottom: 2px solid #e5e7eb;
        padding-bottom: 10px;
    }

    h3 {
        color: #274e75;
        margin-top: 25px;
    }

    .objective {
        background: #eef4fb;
        border-left: 5px solid #17365d;
        padding: 15px 20px;
        margin: 15px 0;
    }

    .formula {
        background: #f8fafc;
        border: 1px solid #dbe2ea;
        padding: 18px;
        border-radius: 8px;
        text-align: center;
        font-size: 20px;
        margin: 15px 0;
        font-family: Georgia, serif;
    }

    .controls {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
        gap: 18px;
        margin-top: 20px;
    }

    .control-group {
        display: flex;
        flex-direction: column;
    }

    label {
        font-weight: bold;
        margin-bottom: 7px;
    }

    input, select {
        padding: 11px;
        border: 1px solid #cbd5e1;
        border-radius: 6px;
        font-size: 16px;
    }

    input:focus, select:focus {
        outline: 2px solid #8db3d8;
    }

    .results {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
        gap: 15px;
        margin-top: 25px;
    }

    .result-box {
        background: #f1f5f9;
        border-radius: 8px;
        padding: 18px;
        text-align: center;
    }

    .result-label {
        font-size: 14px;
        color: #64748b;
    }

    .result-value {
        font-size: 24px;
        font-weight: bold;
        margin-top: 5px;
        color: #17365d;
    }

    button {
        background: #17365d;
        color: white;
        border: none;
        padding: 12px 20px;
        border-radius: 6px;
        cursor: pointer;
        font-size: 16px;
        font-weight: bold;
        margin-top: 15px;
    }

    button:hover {
        background: #0f2745;
    }

    .secondary {
        background: #64748b;
    }

    .secondary:hover {
        background: #475569;
    }

    table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 20px;
    }

    th, td {
        border: 1px solid #dbe2ea;
        padding: 12px;
        text-align: center;
    }

    th {
        background: #17365d;
        color: white;
    }

    tr:nth-child(even) {
        background: #f8fafc;
    }

    .question {
        background: #fafafa;
        border: 1px solid #e5e7eb;
        border-radius: 8px;
        padding: 18px;
        margin: 15px 0;
    }

    .question strong {
        display: block;
        margin-bottom: 8px;
    }

    .answer {
        width: 100%;
        min-height: 90px;
        resize: vertical;
        font-family: Arial, Helvetica, sans-serif;
    }

    .success {
        background: #ecfdf5;
        border-left: 5px solid #16a34a;
        padding: 15px;
        margin-top: 15px;
        display: none;
    }

    .warning {
        background: #fff7ed;
        border-left: 5px solid #ea580c;
        padding: 15px;
        margin-top: 15px;
    }

    .challenge-options {
        display: grid;
        gap: 12px;
        margin-top: 15px;
    }

    .challenge-option {
        border: 1px solid #cbd5e1;
        border-radius: 8px;
        padding: 15px;
        cursor: pointer;
        background: white;
    }

    .challenge-option:hover {
        background: #f8fafc;
    }

    .challenge-option input {
        margin-right: 10px;
    }

    .challenge-result {
        margin-top: 15px;
        padding: 15px;
        border-radius: 8px;
        display: none;
    }

    .correct {
        background: #ecfdf5;
        border: 1px solid #86efac;
    }

    .incorrect {
        background: #fef2f2;
        border: 1px solid #fca5a5;
    }

    canvas {
        width: 100%;
        max-height: 400px;
        margin-top: 20px;
    }

    footer {
        text-align: center;
        padding: 30px;
        color: #64748b;
        font-size: 14px;
    }

    @media (max-width: 700px) {
        header {
            padding: 25px 20px;
        }

        header h1 {
            font-size: 24px;
        }

        .card {
            padding: 18px;
        }
    }
</style>
</head>

<body>

<header>
    <h1>Quantitative Computer Architecture — Lab 1</h1>
    <p>Quantitative Performance Analysis and Amdahl's Law</p>
</header>

<div class="container">

    <!-- OBJECTIVES -->
    <section class="card">
        <h2>Lab Overview</h2>

        <div class="objective">
            <strong>Learning Objectives</strong>
            <ul>
                <li>Calculate CPU execution time using the CPU performance equation.</li>
                <li>Understand the relationship between CPI, IPC, clock rate, and performance.</li>
                <li>Compare processor performance quantitatively.</li>
                <li>Calculate speedup using Amdahl's Law.</li>
                <li>Evaluate architectural improvements and trade-offs.</li>
            </ul>
        </div>

        <h3>CPU Performance Equation</h3>

        <div class="formula">
            CPU Time =
            <strong>(Instruction Count × CPI) / Clock Rate</strong>
        </div>

        <h3>Amdahl's Law</h3>

        <div class="formula">
            Overall Speedup =
            <strong>1 / ((1 − F) + (F / S))</strong>
        </div>

        <p>
            Where <strong>F</strong> is the fraction of execution time improved
            and <strong>S</strong> is the speedup of the improved portion.
        </p>
    </section>


    <!-- PART 1 -->
    <section class="card">
        <h2>Part 1 — CPU Performance Equation</h2>

        <p>
            Modify the processor parameters below. The simulator will
            automatically calculate execution time, clock cycles, and IPC.
        </p>

        <div class="controls">

            <div class="control-group">
                <label for="instructionCount">
                    Instruction Count
                </label>

                <input
                    type="number"
                    id="instructionCount"
                    value="2000000000"
                    min="1"
                    step="100000000"
                >
            </div>

            <div class="control-group">
                <label for="clockRate">
                    Clock Rate (GHz)
                </label>

                <input
                    type="number"
                    id="clockRate"
                    value="3"
                    min="0.1"
                    step="0.1"
                >
            </div>

            <div class="control-group">
                <label for="cpi">
                    Average CPI
                </label>

                <input
                    type="number"
                    id="cpi"
                    value="1.5"
                    min="0.1"
                    step="0.1"
                >
            </div>

        </div>

        <div class="results">

            <div class="result-box">
                <div class="result-label">CPU Time</div>
                <div class="result-value" id="cpuTime">—</div>
            </div>

            <div class="result-box">
                <div class="result-label">Clock Cycles</div>
                <div class="result-value" id="clockCycles">—</div>
            </div>

            <div class="result-box">
                <div class="result-label">IPC</div>
                <div class="result-value" id="ipc">—</div>
            </div>

            <div class="result-box">
                <div class="result-label">Performance</div>
                <div class="result-value" id="performance">—</div>
            </div>

        </div>

        <h3>Experiment 1 — Change Clock Rate</h3>

        <p>
            Record the CPU time for clock rates of 2, 3, 4, and 5 GHz.
        </p>

        <table>
            <thead>
                <tr>
                    <th>Clock Rate</th>
                    <th>CPU Time</th>
                    <th>Relative Performance</th>
                </tr>
            </thead>

            <tbody id="clockTable"></tbody>
        </table>

        <button onclick="generateClockTable()">
            Generate Results
        </button>

    </section>


    <!-- PART 2 -->
    <section class="card">

        <h2>Part 2 — CPI and IPC</h2>

        <p>
            Keep the instruction count and clock rate fixed. Investigate how
            changing CPI affects execution time and IPC.
        </p>

        <table>

            <thead>
                <tr>
                    <th>CPI</th>
                    <th>CPU Time</th>
                    <th>IPC</th>
                </tr>
            </thead>

            <tbody id="cpiTable"></tbody>

        </table>

        <button onclick="generateCPITable()">
            Generate CPI Results
        </button>

        <div class="warning">
            <strong>Think:</strong>
            A processor with a higher clock rate is not automatically faster.
            Performance depends on both clock rate and CPI.
        </div>

    </section>


    <!-- PART 3 -->
    <section class="card">

        <h2>Part 3 — Compare Two Processors</h2>

        <p>
            Compare two processors running the same workload.
        </p>

        <div class="controls">

            <div class="control-group">

                <h3>Processor A</h3>

                <label>Clock Rate (GHz)</label>
                <input
                    type="number"
                    id="aClock"
                    value="3"
                    step="0.1"
                >

                <label>CPI</label>
                <input
                    type="number"
                    id="aCpi"
                    value="1.5"
                    step="0.1"
                >

            </div>


            <div class="control-group">

                <h3>Processor B</h3>

                <label>Clock Rate (GHz)</label>
                <input
                    type="number"
                    id="bClock"
                    value="4"
                    step="0.1"
                >

                <label>CPI</label>
                <input
                    type="number"
                    id="bCpi"
                    value="2"
                    step="0.1"
                >

            </div>

        </div>

        <button onclick="compareProcessors()">
            Compare Processors
        </button>

        <div id="processorComparison"></div>

    </section>


    <!-- PART 4 -->
    <section class="card">

        <h2>Part 4 — Amdahl's Law</h2>

        <p>
            Suppose a fraction of a program can be improved by a hardware
            or software optimization. Adjust the values below.
        </p>

        <div class="controls">

            <div class="control-group">

                <label>
                    Fraction Improved (%)
                </label>

                <input
                    type="number"
                    id="fractionImproved"
                    value="40"
                    min="0"
                    max="100"
                    step="1"
                >

            </div>

            <div class="control-group">

                <label>
                    Speedup of Improved Portion
                </label>

                <input
                    type="number"
                    id="componentSpeedup"
                    value="2"
                    min="1"
                    step="0.5"
                >

            </div>

        </div>

        <div class="results">

            <div class="result-box">
                <div class="result-label">Overall Speedup</div>
                <div class="result-value" id="overallSpeedup">
                    —
                </div>
            </div>

            <div class="result-box">
                <div class="result-label">Maximum Possible Speedup</div>
                <div class="result-value" id="maxSpeedup">
                    —
                </div>
            </div>

        </div>

        <button onclick="calculateAmdahl()">
            Calculate Speedup
        </button>

        <h3>Experiment — Increasing Component Speedup</h3>

        <table>

            <thead>
                <tr>
                    <th>Component Speedup</th>
                    <th>Overall Speedup</th>
                </tr>
            </thead>

            <tbody id="amdahlTable"></tbody>

        </table>

        <button onclick="generateAmdahlTable()">
            Generate Amdahl Results
        </button>

    </section>


    <!-- PART 5 -->
    <section class="card">

        <h2>Part 5 — The Architect's Challenge</h2>

        <p>
            You are the architect responsible for improving a processor.
            The baseline processor has the following characteristics:
        </p>

        <ul>
            <li>Clock Rate = 3 GHz</li>
            <li>CPI = 1.5</li>
            <li>Instruction Count = 2 billion</li>
        </ul>

        <p>
            You have three possible upgrades. Which one should you choose?
        </p>

        <div class="challenge-options">

            <label class="challenge-option">
                <input
                    type="radio"
                    name="challenge"
                    value="clock"
                >
                <strong>Option A:</strong>
                Increase clock rate from 3 GHz to 4 GHz.
            </label>

            <label class="challenge-option">
                <input
                    type="radio"
                    name="challenge"
                    value="cpi"
                >
                <strong>Option B:</strong>
                Reduce CPI from 1.5 to 1.1.
            </label>

            <label class="challenge-option">
                <input
                    type="radio"
                    name="challenge"
                    value="amdahl"
                >
                <strong>Option C:</strong>
                Optimize 50% of the workload by 5×.
            </label>

        </div>

        <button onclick="checkChallenge()">
            Check Answer
        </button>

        <div id="challengeResult" class="challenge-result"></div>

    </section>


    <!-- QUESTIONS -->
    <section class="card">

        <h2>Lab Analysis Questions</h2>

        <div class="question">

            <strong>1. Which parameter had the greatest effect on CPU performance?</strong>

            <textarea
                class="answer"
                placeholder="Explain your answer using quantitative evidence."
            ></textarea>

        </div>

        <div class="question">

            <strong>
                2. Why does increasing clock frequency not necessarily
                produce the same proportional increase in performance?
            </strong>

            <textarea
                class="answer"
                placeholder="Explain the relationship between clock rate and CPI."
            ></textarea>

        </div>

        <div class="question">

            <strong>
                3. Why can a processor with a lower clock rate outperform
                a processor with a higher clock rate?
            </strong>

            <textarea
                class="answer"
                placeholder="Use the CPU performance equation."
            ></textarea>

        </div>

        <div class="question">

            <strong>
                4. What does Amdahl's Law tell us about optimizing only
                part of a program?
            </strong>

            <textarea
                class="answer"
                placeholder="Discuss diminishing returns."
            ></textarea>

        </div>

        <div class="question">

            <strong>
                5. Which processor upgrade would you recommend and why?
            </strong>

            <textarea
                class="answer"
                placeholder="Support your recommendation with calculations."
            ></textarea>

        </div>

        <button onclick="window.print()">
            Print / Save Lab Report
        </button>

    </section>

</div>

<footer>
    Quantitative Computer Architecture — Lab 1<br>
    Quantitative Performance Analysis
</footer>


<script>

function getInputs() {

    const instructions =
        Number(document.getElementById("instructionCount").value);

    const clockGHz =
        Number(document.getElementById("clockRate").value);

    const cpi =
        Number(document.getElementById("cpi").value);

    return {
        instructions,
        clockGHz,
        cpi
    };
}


function calculateCPUTime(instructions, cpi, clockGHz) {

    const clockHz = clockGHz * 1e9;

    return (instructions * cpi) / clockHz;
}


function updateMainResults() {

    const {
        instructions,
        clockGHz,
        cpi
    } = getInputs();

    const cycles = instructions * cpi;

    const time =
        calculateCPUTime(
            instructions,
            cpi,
            clockGHz
        );

    const ipc = 1 / cpi;

    const performance = 1 / time;

    document.getElementById("cpuTime").textContent =
        time.toFixed(4) + " s";

    document.getElementById("clockCycles").textContent =
        cycles.toLocaleString();

    document.getElementById("ipc").textContent =
        ipc.toFixed(3);

    document.getElementById("performance").textContent =
        performance.toFixed(3) + " /s";
}


function generateClockTable() {

    const {
        instructions,
        cpi
    } = getInputs();

    const rates = [2, 3, 4, 5];

    const baselineTime =
        calculateCPUTime(
            instructions,
            cpi,
            3
        );

    let html = "";

    rates.forEach(rate => {

        const time =
            calculateCPUTime(
                instructions,
                cpi,
                rate
            );

        const performance =
            baselineTime / time;

        html += `
            <tr>
                <td>${rate} GHz</td>
                <td>${time.toFixed(4)} s</td>
                <td>${performance.toFixed(2)}×</td>
            </tr>
        `;
    });

    document.getElementById("clockTable").innerHTML =
        html;
}


function generateCPITable() {

    const {
        instructions,
        clockGHz
    } = getInputs();

    const cpis =
        [0.5, 1, 1.5, 2, 3];

    let html = "";

    cpis.forEach(cpi => {

        const time =
            calculateCPUTime(
                instructions,
                cpi,
                clockGHz
            );

        const ipc = 1 / cpi;

        html += `
            <tr>
                <td>${cpi.toFixed(1)}</td>
                <td>${time.toFixed(4)} s</td>
                <td>${ipc.toFixed(3)}</td>
            </tr>
        `;
    });

    document.getElementById("cpiTable").innerHTML =
        html;
}


function compareProcessors() {

    const instructions =
        Number(
            document.getElementById(
                "instructionCount"
            ).value
        );

    const aClock =
        Number(
            document.getElementById("aClock").value
        );

    const aCpi =
        Number(
            document.getElementById("aCpi").value
        );

    const bClock =
        Number(
            document.getElementById("bClock").value
        );

    const bCpi =
        Number(
            document.getElementById("bCpi").value
        );

    const timeA =
        calculateCPUTime(
            instructions,
            aCpi,
            aClock
        );

    const timeB =
        calculateCPUTime(
            instructions,
            bCpi,
            bClock
        );

    const speedup =
        Math.max(timeA, timeB) /
        Math.min(timeA, timeB);

    let faster;

    if (timeA < timeB) {

        faster = "Processor A is faster.";

    } else if (timeB < timeA) {

        faster = "Processor B is faster.";

    } else {

        faster = "Both processors have equal performance.";
    }

    document.getElementById(
        "processorComparison"
    ).innerHTML = `

        <table>

            <thead>
                <tr>
                    <th></th>
                    <th>Processor A</th>
                    <th>Processor B</th>
                </tr>
            </thead>

            <tbody>

                <tr>
                    <td>Clock Rate</td>
                    <td>${aClock} GHz</td>
                    <td>${bClock} GHz</td>
                </tr>

                <tr>
                    <td>CPI</td>
                    <td>${aCpi}</td>
                    <td>${bCpi}</td>
                </tr>

                <tr>
                    <td>CPU Time</td>
                    <td>${timeA.toFixed(4)} s</td>
                    <td>${timeB.toFixed(4)} s</td>
                </tr>

            </tbody>

        </table>

        <div class="success" style="display:block">
            <strong>${faster}</strong><br>
            Performance difference:
            ${speedup.toFixed(2)}×
        </div>
    `;
}


function calculateAmdahl() {

    const fraction =
        Number(
            document.getElementById(
                "fractionImproved"
            ).value
        ) / 100;

    const speedup =
        Number(
            document.getElementById(
                "componentSpeedup"
            ).value
        );

    const overall =
        1 /
        ((1 - fraction) +
        (fraction / speedup));

    const maximum =
        1 /
        (1 - fraction);

    document.getElementById(
        "overallSpeedup"
    ).textContent =
        overall.toFixed(3) + "×";

    document.getElementById(
        "maxSpeedup"
    ).textContent =
        maximum.toFixed(3) + "×";
}


function generateAmdahlTable() {

    const fraction =
        Number(
            document.getElementById(
                "fractionImproved"
            ).value
        ) / 100;

    const speeds =
        [1, 2, 4, 8, 16, 100];

    let html = "";

    speeds.forEach(speed => {

        const overall =
            1 /
            ((1 - fraction) +
            (fraction / speed));

        html += `
            <tr>
                <td>${speed}×</td>
                <td>${overall.toFixed(3)}×</td>
            </tr>
        `;
    });

    document.getElementById(
        "amdahlTable"
    ).innerHTML = html;
}


function checkChallenge() {

    const selected =
        document.querySelector(
            'input[name="challenge"]:checked'
        );

    const result =
        document.getElementById(
            "challengeResult"
        );

    if (!selected) {

        result.className =
            "challenge-result incorrect";

        result.style.display =
            "block";

        result.innerHTML =
            "Please select an option.";

        return;
    }

    /*
        Baseline:
        3 GHz, CPI 1.5

        Option A:
        3 GHz -> 4 GHz
        Speedup = 4/3 = 1.333×

        Option B:
        CPI 1.5 -> 1.1
        Speedup = 1.5/1.1 = 1.364×

        Option C:
        50% improved by 5×
        Amdahl = 1/(0.5 + 0.5/5)
        = 1.667×
    */

    if (selected.value === "amdahl") {

        result.className =
            "challenge-result correct";

        result.style.display =
            "block";

        result.innerHTML = `
            <strong>Correct.</strong><br><br>

            Option C provides the greatest theoretical
            speedup:

            <br><br>

            Amdahl's Law:
            <strong>1.667×</strong>

            <br><br>

            Option A provides approximately
            <strong>1.333×</strong> speedup.

            <br>

            Option B provides approximately
            <strong>1.364×</strong> speedup.

            <br><br>

            This demonstrates why architects must consider
            the fraction of execution time affected by an
            optimization, rather than simply making one
            component extremely fast.
        `;

    } else {

        result.className =
            "challenge-result incorrect";

        result.style.display =
            "block";

        result.innerHTML = `
            <strong>Not quite.</strong><br><br>

            Recalculate the speedup of each option using
            the CPU Performance Equation and Amdahl's Law.

            <br><br>

            Remember: the best architectural improvement
            is not necessarily the one with the largest
            improvement to a single component.
        `;
    }
}


// Automatically update the main simulator
document
    .getElementById("instructionCount")
    .addEventListener(
        "input",
        updateMainResults
    );

document
    .getElementById("clockRate")
    .addEventListener(
        "input",
        updateMainResults
    );

document
    .getElementById("cpi")
    .addEventListener(
        "input",
        updateMainResults
    );


// Initial calculations
updateMainResults();
generateClockTable();
generateCPITable();
calculateAmdahl();
generateAmdahlTable();

</script>

</body>
</html>
