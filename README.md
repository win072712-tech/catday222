<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>喵喵節快樂！2.22 Nyan Day</title>
    <style>
        :root {
            --cat-pink: #ffb7c5;
            --cat-yellow: #fff9ae;
        }

        body {
            margin: 0;
            padding: 0;
            background-color: var(--cat-yellow);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            overflow: hidden;
            cursor: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="%23f08080" d="M12 2C10.9 2 10 2.9 10 4s.9 2 2 2s2-.9 2-2s-.9-2-2-2M7 4C5.9 4 5 4.9 5 6s.9 2 2 2s2-.9 2-2s-.9-2-2-2m10 0c-1.1 0-2 .9-2 2s.9 2 2 2s2-.9 2-2s-.9-2-2-2m-5 8c-2.8 0-5 2.2-5 5s2.2 5 5 5s5-2.2 5-5s-2.2-5-5-5Z"/></svg>'), auto;
        }

        h1 {
            color: #d63384;
            text-shadow: 2px 2px white;
            margin-bottom: 10px;
        }

        #cat-container {
            position: relative;
            font-size: 100px;
            cursor: pointer;
            transition: transform 0.2s;
            user-select: none;
        }

        #cat-container:active {
            transform: scale(0.9);
        }

        #speech-bubble {
            background: white;
            border-radius: 20px;
            padding: 10px 20px;
            position: absolute;
            top: -60px;
            left: 50%;
            transform: translateX(-50%);
            white-space: nowrap;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            font-weight: bold;
            display: none;
        }

        #speech-bubble::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            border-width: 10px 10px 0;
            border-style: solid;
            border-color: white transparent transparent;
            transform: translateX(-50%);
        }

        .heart {
            position: absolute;
            color: #ff6b6b;
            font-size: 24px;
            pointer-events: none;
            animation: floatUp 1s ease-out forwards;
        }

        @keyframes floatUp {
            0% { transform: translateY(0) scale(1); opacity: 1; }
            100% { transform: translateY(-100px) scale(1.5); opacity: 0; }
        }

        .btn {
            margin-top: 30px;
            padding: 10px 20px;
            background-color: #d63384;
            color: white;
            border: none;
            border-radius: 50px;
            font-size: 18px;
            cursor: pointer;
            box-shadow: 0 4px #a02663;
        }

        .btn:active {
            box-shadow: 0 2px #a02663;
            transform: translateY(2px);
        }

        #fact-display {
            margin-top: 20px;
            font-size: 16px;
            color: #555;
            max-width: 80%;
            text-align: center;
        }
    </style>
</head>
<body>

    <h1>🐾 貓之日快樂 🐾</h1>
    <p>點擊貓咪來摸摸牠吧！</p>

    <div id="cat-container">
        <div id="speech-bubble">喵～</div>
        🐱
    </div>

    <button class="btn" onclick="showFact()">獲得貓咪冷知識</button>
    <div id="fact-display"></div>

    <script>
        const cat = document.getElementById('cat-container');
        const bubble = document.getElementById('speech-bubble');
        const factDisplay = document.getElementById('fact-display');

        const catTalks = ["罐罐呢？", "再摸一下就咬你喔", "奴才表現不錯", "（呼嚕嚕...）", "喵嗚！", "要玩逗貓棒嗎？", "朕餓了。"];
        const catFacts = [
            "貓咪的肉球可以排汗唷！",
            "貓咪發出呼嚕聲不一定是開心，有時是在自我修復。",
            "貓咪一輩子有 70% 的時間在睡覺。",
            "每隻貓咪的鼻紋都是獨一無二的。",
            "貓咪跳躍的高度可以達到自己身高的 6 倍！"
        ];

        cat.addEventListener('click', (e) => {
            // 顯示對話框
            const randomTalk = catTalks[Math.floor(Math.random() * catTalks.length)];
            bubble.innerText = randomTalk;
            bubble.style.display = 'block';
            setTimeout(() => bubble.style.display = 'none', 1500);

            // 產生愛心
            createHeart(e.clientX, e.clientY);
        });

        function createHeart(x, y) {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = x - 10 + 'px';
            heart.style.top = y - 40 + 'px';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 1000);
        }

        function showFact() {
            const randomFact = catFacts[Math.floor(Math.random() * catFacts.length)];
            factDisplay.innerText = "💡 " + randomFact;
        }
    </script>
</body>
</html>
