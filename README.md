<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>Riddler Challenge</title>
    <style>
        body {
            background-color: black;
            color: #00ff00;
            font-family: monospace;
            text-align: center;
            padding: 30px;
        }
        .box {
            border: 1px solid #00ff00;
            padding: 20px;
            margin-top: 20px;
        }
        input {
            background: black;
            color: #00ff00;
            border: 1px solid #00ff00;
            padding: 5px;
        }
        button {
            background: black;
            color: #00ff00;
            border: 1px solid #00ff00;
            padding: 5px 10px;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <h1>🧩 Riddler Challenge</h1>
    <p>Jawab semua teka-teki untuk mendapatkan hadiah...</p>

    <div class="box">
        <p id="question"></p>
        <input type="text" id="answer" placeholder="Jawabanmu...">
        <br><br>
        <button onclick="checkAnswer()">Submit</button>
        <p id="result"></p>
    </div>

    <script>
        const riddles = [
            {
                q: "Aku punya kunci tapi tak punya pintu, aku punya ruang tapi tak ada isi. Apa aku?",
                a: "keyboard"
            },
            {
                q: "Aku selalu di depanmu tapi tak bisa kamu lihat. Apa aku?",
                a: "masa depan"
            },
            {
                q: "Semakin banyak kamu ambil dariku, semakin besar aku. Apa aku?",
                a: "lubang"
            },
            {
                q: "Aku punya kota tanpa rumah, sungai tanpa air, dan hutan tanpa pohon. Apa aku?",
                a: "peta"
            }
        ];

        let current = 0;

        function loadQuestion() {
            document.getElementById("question").innerText = riddles[current].q;
            document.getElementById("answer").value = "";
            document.getElementById("result").innerText = "";
        }

        function checkAnswer() {
            let userAnswer = document.getElementById("answer").value.toLowerCase().trim();

            if (userAnswer === riddles[current].a) {
                current++;
                if (current < riddles.length) {
                    loadQuestion();
                } else {
                    document.querySelector(".box").innerHTML = `
                        <p>😈 Selamat... kamu berhasil.</p>
                        <p>Hadiahmu:</p>
                        <h2>-6.143026,106.739128</h2>
                    `;
                }
            } else {
                document.getElementById("result").innerText = "❌ Salah... coba lagi.";
            }
        }

        loadQuestion();
    </script>

</body>
</html>
