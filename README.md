<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Ritika!</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(to bottom, #f0f8ff, #ffe4e1);
            text-align: center;
            padding: 20px;
            color: #333;
        }
        h1 {
            color: #ff69b4;
            animation: bounce 2s infinite;
        }
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }
        .countdown {
            font-size: 24px;
            margin: 20px;
            color: #ff4500;
        }
        .caption {
            margin: 20px;
            font-size: 18px;
            color: #333;
            background: #fff;
            padding: 10px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        .gallery {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            margin: 20px;
        }
        .gallery img {
            width: 150px;
            height: 150px;
            margin: 10px;
            border-radius: 10px;
            transition: transform 0.3s;
        }
        .gallery img:hover {
            transform: scale(1.1);
        }
        button {
            background: #ff69b4;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 18px;
            border-radius: 5px;
            cursor: pointer;
            margin: 20px;
        }
        button:hover {
            background: #ff1493;
        }
        #surprise {
            display: none;
            font-size: 20px;
            color: #32cd32;
            margin: 20px;
        }
        iframe {
            margin: 20px;
        }
        canvas {
            position: fixed;
            top: 0;
            left: 0;
            pointer-events: none;
        }
    </style>
</head>
<body>
    <h1>Happy Birthday, Ritika!</h1>
    <p>Dear Sister, on December 28, 2025, let's celebrate the amazing person you are. Wishing you a year filled with joy, love, and endless adventures!</p>
    
    <div class="countdown" id="countdown">Calculating time until your birthday...</div>
    
    <div class="caption">
        "From the day you were born, you've been my best friend, my confidant, and my biggest cheerleader. Happy Birthday, Ritika! Love you more than words can say. - Your Brother"
    </div>
    
    <div class="caption">
        "Sisters are like stars – you may not always see them, but you know they're always there. Shine bright on your special day! Happy Birthday!"
    </div>
    
    <div class="caption">
        "Through thick and thin, you've been my rock. Here's to more memories, more laughter, and more love. Happy Birthday, Ritika!"
    </div>
    
    <div class="caption">
        "Remember that time we [insert fun memory here]? Can't wait to make more! You're the best sister ever. Happy Birthday!"
    </div>
    
    <h2>Photo Gallery</h2>
    <div class="gallery">
        <img src="img1.jpeg" alt="Memory 1">
        <img src="img2.jpeg" alt="Memory 2">
        <img src="img3.jpeg" alt="Memory 3">
    </div>
    
    <button onclick="showSurprise()">Click for a Surprise!</button>
    <div id="surprise">🎉 You're the most awesome sister in the universe! 🎂</div>
    
    <!-- Embed a happy birthday song (replace VIDEO_ID with a YouTube video ID, e.g., for "Happy Birthday" song) -->
    <iframe width="560" height="315" src="song.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    
    <p>Enjoy your day! 🎉</p>
    
    <canvas id="confetti-canvas"></canvas>
    
    <script>
        // Countdown Timer
        function updateCountdown() {
            const birthday = new Date('December 28, 2025 00:00:00').getTime();
            const now = new Date().getTime();
            const distance = birthday - now;
            
            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);
            
            document.getElementById('countdown').innerHTML = days + "d " + hours + "h " + minutes + "m " + seconds + "s until your birthday!";
            
            if (distance < 0) {
                document.getElementById('countdown').innerHTML = "It's your birthday! 🎂";
            }
        }
        setInterval(updateCountdown, 1000);
        
        // Surprise Button
        function showSurprise() {
            document.getElementById('surprise').style.display = 'block';
            launchConfetti();
        }
        
        // Simple Confetti Effect
        function launchConfetti() {
            const canvas = document.getElementById('confetti-canvas');
            const ctx = canvas.getContext('2d');
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            
            const confetti = [];
            for (let i = 0; i < 100; i++) {
                confetti.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    r: Math.random() * 5 + 2,
                    d: Math.random() * 100,
                    color: `hsl(${Math.random() * 360}, 100%, 50%)`,
                    tilt: Math.random() * 10 - 10,
                    tiltAngleIncremental: Math.random() * 0.07 + 0.05,
                    tiltAngle: 0
                });
            }
            
            function draw() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                confetti.forEach((c, i) => {
                    ctx.beginPath();
                    ctx.arc(c.x, c.y, c.r, 0, Math.PI * 2);
                    ctx.fillStyle = c.color;
                    ctx.fill();
                    c.y += Math.cos(c.d) + 1 + c.r / 2;
                    c.tiltAngle += c.tiltAngleIncremental;
                    c.x += Math.sin(c.d);
                    if (c.y > canvas.height) confetti.splice(i, 1);
                });
                requestAnimationFrame(draw);
            }
            draw();
        }
    </script>
</body>
</html>
