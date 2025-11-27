<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>1337 Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0e27;
            color: #00ff41;
            font-family: 'Courier New', monospace;
            overflow-x: hidden;
            min-height: 100vh;
            position: relative;
        }

        .scanlines {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                to bottom,
                transparent 50%,
                rgba(0, 255, 65, 0.03) 51%
            );
            background-size: 100% 4px;
            pointer-events: none;
            z-index: 999;
            animation: scan 8s linear infinite;
        }

        @keyframes scan {
            0% { transform: translateY(0); }
            100% { transform: translateY(4px); }
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 40px 20px;
            position: relative;
            z-index: 1;
        }

        .terminal-header {
            border: 2px solid #00ff41;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 30px;
            background: rgba(0, 255, 65, 0.05);
            box-shadow: 0 0 20px rgba(0, 255, 65, 0.3);
            animation: glowPulse 3s ease-in-out infinite;
        }

        @keyframes glowPulse {
            0%, 100% { box-shadow: 0 0 20px rgba(0, 255, 65, 0.3); }
            50% { box-shadow: 0 0 30px rgba(0, 255, 65, 0.5); }
        }

        .prompt {
            color: #ff006e;
            text-shadow: 0 0 10px #ff006e;
        }

        .username {
            color: #00d9ff;
            text-shadow: 0 0 10px #00d9ff;
            font-size: 2em;
            margin: 10px 0;
            animation: flicker 4s infinite;
        }

        @keyframes flicker {
            0%, 100% { opacity: 1; }
            41%, 43% { opacity: 0.8; }
            45% { opacity: 1; }
        }

        .status {
            color: #00ff41;
            margin: 5px 0;
        }

        .section {
            border-left: 3px solid #00ff41;
            padding: 20px;
            margin: 20px 0;
            background: rgba(0, 0, 0, 0.4);
            position: relative;
            transition: all 0.3s ease;
        }

        .section:hover {
            background: rgba(0, 255, 65, 0.1);
            border-left-width: 5px;
            padding-left: 25px;
        }

        .section-title {
            color: #ff006e;
            font-size: 1.3em;
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 0 0 10px #ff006e;
        }

        .skill-bar {
            margin: 15px 0;
        }

        .skill-name {
            color: #00d9ff;
            margin-bottom: 5px;
        }

        .bar-container {
            width: 100%;
            height: 20px;
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid #00ff41;
            position: relative;
            overflow: hidden;
        }

        .bar-fill {
            height: 100%;
            background: linear-gradient(90deg, #00ff41, #00d9ff);
            box-shadow: 0 0 10px #00ff41;
            transition: width 2s ease;
            position: relative;
            animation: barGlow 2s ease-in-out infinite;
        }

        @keyframes barGlow {
            0%, 100% { box-shadow: 0 0 10px #00ff41; }
            50% { box-shadow: 0 0 20px #00ff41, 0 0 30px #00d9ff; }
        }

        .matrix-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            opacity: 0.1;
            z-index: 0;
        }

        .tag {
            display: inline-block;
            padding: 5px 12px;
            margin: 5px;
            background: rgba(0, 255, 65, 0.2);
            border: 1px solid #00ff41;
            border-radius: 3px;
            font-size: 0.9em;
            transition: all 0.3s ease;
        }

        .tag:hover {
            background: rgba(0, 255, 65, 0.4);
            box-shadow: 0 0 15px rgba(0, 255, 65, 0.5);
            transform: scale(1.05);
        }

        .blink {
            animation: blink 1s step-start infinite;
        }

        @keyframes blink {
            50% { opacity: 0; }
        }

        .ascii-art {
            color: #00ff41;
            font-size: 0.7em;
            line-height: 1.2;
            text-align: center;
            margin: 20px 0;
            text-shadow: 0 0 5px #00ff41;
        }

        .achievement {
            padding: 10px;
            margin: 10px 0;
            background: rgba(255, 0, 110, 0.1);
            border-left: 3px solid #ff006e;
            transition: all 0.3s ease;
        }

        .achievement:hover {
            background: rgba(255, 0, 110, 0.2);
            transform: translateX(10px);
        }
    </style>
</head>
<body>
    <div class="scanlines"></div>
    <canvas class="matrix-bg" id="matrix"></canvas>
    
    <div class="container">
        <div class="terminal-header">
            <div class="ascii-art">
    ██████╗██╗   ██╗██████╗ ███████╗██████╗ 
   ██╔════╝╚██╗ ██╔╝██╔══██╗██╔════╝██╔══██╗
   ██║      ╚████╔╝ ██████╔╝█████╗  ██████╔╝
   ██║       ╚██╔╝  ██╔══██╗██╔══╝  ██╔══██╗
   ╚██████╗   ██║   ██████╔╝███████╗██║  ██║
    ╚═════╝   ╚═╝   ╚═════╝ ╚══════╝╚═╝  ╚═╝
            </div>
            <div><span class="prompt">root@mainframe:~$</span> whoami</div>
            <div class="username">[YOUR_USERNAME_HERE]</div>
            <div class="status">> Status: <span style="color: #00ff41;">ONLINE</span> | Access Level: <span style="color: #ff006e;">1337</span> | Clearance: <span style="color: #00d9ff;">ROOT</span></div>
            <div class="status">> Location: <span style="color: #00d9ff;">The Matrix</span> | Uptime: <span id="uptime">Calculating...</span></div>
        </div>

        <div class="section">
            <div class="section-title">[+] About Me</div>
            <p><span class="prompt">></span> Cybersecurity specialist & elite coder</p>
            <p><span class="prompt">></span> Breaking systems, building defenses</p>
            <p><span class="prompt">></span> Living in the terminal, thinking in binary</p>
            <p><span class="prompt">></span> "In a world of 1s and 0s, I am the exception handler"</p>
        </div>

        <div class="section">
            <div class="section-title">[+] Skill Matrix</div>
            
            <div class="skill-bar">
                <div class="skill-name">Penetration Testing</div>
                <div class="bar-container">
                    <div class="bar-fill" style="width: 0%" data-width="90%"></div>
                </div>
            </div>

            <div class="skill-bar">
                <div class="skill-name">Network Security</div>
                <div class="bar-container">
                    <div class="bar-fill" style="width: 0%" data-width="85%"></div>
                </div>
            </div>

            <div class="skill-bar">
                <div class="skill-name">Exploit Development</div>
                <div class="bar-container">
                    <div class="bar-fill" style="width: 0%" data-width="80%"></div>
                </div>
            </div>

            <div class="skill-bar">
                <div class="skill-name">Reverse Engineering</div>
                <div class="bar-container">
                    <div class="bar-fill" style="width: 0%" data-width="75%"></div>
                </div>
            </div>

            <div class="skill-bar">
                <div class="skill-name">Python | C | Assembly</div>
                <div class="bar-container">
                    <div class="bar-fill" style="width: 0%" data-width="88%"></div>
                </div>
            </div>
        </div>

        <div class="section">
            <div class="section-title">[+] Tech Stack</div>
            <div>
                <span class="tag">Kali Linux</span>
                <span class="tag">Metasploit</span>
                <span class="tag">Burp Suite</span>
                <span class="tag">Wireshark</span>
                <span class="tag">Nmap</span>
                <span class="tag">Python</span>
                <span class="tag">C/C++</span>
                <span class="tag">Assembly</span>
                <span class="tag">SQL Injection</span>
                <span class="tag">XSS</span>
                <span class="tag">Buffer Overflow</span>
                <span class="tag">Cryptography</span>
                <span class="tag">OSINT</span>
                <span class="tag">Docker</span>
                <span class="tag">Git</span>
            </div>
        </div>

        <div class="section">
            <div class="section-title">[+] Achievements Unlocked</div>
            <div class="achievement">
                <span class="prompt">🏆</span> Root access obtained on [REDACTED]
            </div>
            <div class="achievement">
                <span class="prompt">🏆</span> 500+ CTF flags captured
            </div>
            <div class="achievement">
                <span class="prompt">🏆</span> 0-day vulnerability discovered and disclosed
            </div>
            <div class="achievement">
                <span class="prompt">🏆</span> Bug bounty hunter - $XX,XXX earned
            </div>
        </div>

        <div class="section">
            <div class="section-title">[+] Current Mission</div>
            <p><span class="prompt">></span> Studying advanced exploitation techniques</p>
            <p><span class="prompt">></span> Building custom security tools</p>
            <p><span class="prompt">></span> Contributing to open-source security projects</p>
            <p><span class="prompt">></span> Mastering the art of ethical hacking</p>
        </div>

        <div style="text-align: center; margin-top: 40px; color: #00ff41;">
            <p><span class="prompt">root@mainframe:~$</span> echo "H4CK TH3 PL4N3T"<span class="blink">_</span></p>
        </div>
    </div>

    <script>
        // Matrix rain effect
        const canvas = document.getElementById('matrix');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const chars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';
        const fontSize = 14;
        const columns = canvas.width / fontSize;
        const drops = Array(Math.floor(columns)).fill(1);

        function drawMatrix() {
            ctx.fillStyle = 'rgba(10, 14, 39, 0.05)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            ctx.fillStyle = '#00ff41';
            ctx.font = fontSize + 'px monospace';

            for (let i = 0; i < drops.length; i++) {
                const text = chars[Math.floor(Math.random() * chars.length)];
                ctx.fillText(text, i * fontSize, drops[i] * fontSize);

                if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                    drops[i] = 0;
                }
                drops[i]++;
            }
        }

        setInterval(drawMatrix, 50);

        // Animate skill bars
        window.addEventListener('load', () => {
            setTimeout(() => {
                document.querySelectorAll('.bar-fill').forEach(bar => {
                    bar.style.width = bar.dataset.width;
                });
            }, 500);
        });

        // Uptime counter
        const startTime = Date.now();
        function updateUptime() {
            const elapsed = Math.floor((Date.now() - startTime) / 1000);
            const hours = Math.floor(elapsed / 3600);
            const minutes = Math.floor((elapsed % 3600) / 60);
            const seconds = elapsed % 60;
            document.getElementById('uptime').textContent = 
                `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
        }
        setInterval(updateUptime, 1000);

        // Resize canvas on window resize
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>