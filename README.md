<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VITRCARE AI Welcome - 3D Elegant Design</title>
    <link href="index (1).html" rel="stylesheet">
    <!-- Load Three.js Library -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        /* --- CSS Styles --- */
        
        /* 1. Reset and Base Styles */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        /* Application Header Styling */
        .app-header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            /* Changed header background to be darker and less transparent for readability over the new dark body */
            background-color: rgba(45, 10, 85, 0.95); /* Deep Purple, near opaque */
            backdrop-filter: blur(5px);
            color: white;
            padding: 10px 20px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.5);
            z-index: 1000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: bold;
            font-size: 1.1em;
        }
        
        /* 2. Background and Layout - Now driven by Three.js Canvas */
        body {
            /* Changed background to a deep indigo/blue for better contrast with particles */
            background-color: #1a237e; /* Deep Indigo */
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding-top: 60px; 
            padding-left: 20px;
            padding-right: 20px;
            overflow: hidden;
            position: relative;
        }

        /* NEW: Styles for the Three.js Canvas Background */
        #three-scene {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2; /* Ensure it's behind everything */
        }
        
        /* 3. The Card Container - Positioned over the 3D scene */
        .login-card { 
            background-color: rgba(255, 255, 255, 0.9); /* Card remains light */
            backdrop-filter: blur(8px); /* Increased blur for elegance */
            padding: 40px;
            border-radius: 16px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.4); 
            text-align: center;
            max-width: 450px; 
            width: 100%;
            transition: transform 0.4s ease, box-shadow 0.4s ease, border-color 0.4s ease;
            border: 1px solid rgba(255, 255, 255, 0.5); 
            position: relative; 
            z-index: 10; /* Ensure card is above canvas */
        }

        .login-card:hover {
            transform: translateY(-8px) scale(1.01);
            /* Glow adjusted to fit the dark background */
            box-shadow: 0 20px 50px rgba(0,0,0,0.5), 0 0 40px rgba(102, 126, 234, 1); 
            border-color: rgba(102, 126, 234, 1);
        }

        /* Icon Styling and Animation */
        .icon {
            font-size: 3.5em;
            margin-bottom: 20px;
            display: inline-block;
            color: #764ba2;
            text-shadow: 0 2px 5px rgba(0,0,0,0.1);
            animation: elegantBounce 1.5s ease-in-out infinite alternate;
        }
        
        @keyframes elegantBounce {
            0% { transform: translateY(0); }
            50% { transform: translateY(-7px); }
            100% { transform: translateY(0); }
        }

        /* 4. Typography */
        h1 {
            color: #333;
            margin-bottom: 12px;
            font-size: 2.2em;
            font-weight: 700;
            letter-spacing: -0.5px;
        }

        .subtitle {
            color: #555;
            margin-bottom: 35px;
            font-size: 1.1em;
            line-height: 1.7;
        }

        /* 6. Button Styling */
        .btn {
            background-image: linear-gradient(45deg, #764ba2 0%, #667eea 100%); 
            background-size: 200% auto; /* For gradient shift effect */
            color: white;
            border: none;
            padding: 15px 35px;
            font-size: 1.1em;
            font-weight: bold;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.5s ease;
            width: 80%;
            max-width: 300px;
            margin-top: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .btn:hover {
            background-position: right center; /* Shift gradient on hover */
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 8px 20px rgba(0,0,0,0.3), 0 0 10px #667eea;
        }

        .btn:active {
            transform: translateY(0) scale(0.98);
            box-shadow: 0 3px 10px rgba(0,0,0,0.15);
        }

        /* 7. Message Box for Status Updates */
        .message-box {
            padding: 15px;
            border-radius: 8px;
            margin-top: 30px;
            font-weight: bold;
            display: none;
            animation: fadeIn 0.5s;
            border: 1px solid;
            font-size: 0.95em;
            z-index: 10;
        }

        .message-error {
            background-color: #fce4e4;
            color: #c70000;
            border-color: #ef9a9a;
        }
        
        .message-success {
            background-color: #e8f5e9;
            color: #2e7d32;
            border-color: #a5d6a7;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>
    
    <!-- Three.js Scene Container -->
    <div id="three-scene"></div>

    <!-- Application Header -->
    <div class="app-header">
        <span>VITRCARE AI</span>
        <span style="font-size: 0.8em; opacity: 0.8;">| Health & Wellness Platform</span>
    </div>

    <!-- Main Content Card (Now an Elegant Welcome Card) -->
    <div class="login-card" id="welcome-card">
        <div class="icon">💚</div> 
        <h1>Welcome to VITRCARE AI</h1>
        <p class="subtitle">Your personalized companion for health and wellness project management. Begin your journey to a healthier, more organized future.</p>
        
        <a href="index (1).html" class="btn" id="get-started-btn">Get Started</a>
        

        <div id="message-container" class="message-box"></div>
    </div>

    <!-- Simple JavaScript for interaction and Three.js initialization -->
    <script>
        // --- UI/Interaction Logic ---
        const messageContainer = document.getElementById('message-container');
        const getStartedBtn = document.getElementById('get-started-btn');

        function displayMessage(message, isError = false) {
            messageContainer.textContent = message;
            messageContainer.className = 'message-box';
            messageContainer.style.display = 'block';
            
            if (isError) {
                messageContainer.classList.add('message-error');
            } else {
                messageContainer.classList.add('message-success');
            }
            setTimeout(() => {
                messageContainer.style.display = 'none';
            }, 5000);
        }

        getStartedBtn.addEventListener('click', function(event) {
            getStartedBtn.textContent = 'Loading Dashboard...';
            getStartedBtn.disabled = true;

            setTimeout(() => {
                displayMessage('Accessing your VITRCARE AI Dashboard...', false);
                
                setTimeout(() => {
                    getStartedBtn.textContent = 'Dashboard Access Granted';
                    
                    setTimeout(() => {
                        getStartedBtn.textContent = 'Get Started';
                        getStartedBtn.disabled = false;
                        displayMessage('Simulated Dashboard Load Complete. Click "Get Started" again to restart the simulation.', false);
                    }, 1500);

                }, 2000); 
            }, 500);
        });

        // --- Three.js 3D Background Logic ---
        let scene, camera, renderer, particles, particleCount, particleGeometry, particleMaterial;

        function initThreeScene() {
            const container = document.getElementById('three-scene');
            const width = window.innerWidth;
            const height = window.innerHeight;

            // 1. Scene
            scene = new THREE.Scene();

            // 2. Camera
            camera = new THREE.PerspectiveCamera(75, width / height, 1, 1000);
            camera.position.z = 100;

            // 3. Renderer
            renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
            renderer.setSize(width, height);
            renderer.setPixelRatio(window.devicePixelRatio);
            // setClearColor is set to transparent (alpha: 0) to allow the CSS body background color to show through
            renderer.setClearColor(0x1a237e, 0); 
            container.appendChild(renderer.domElement);

            // 4. Particles (Subtle Network/Grid)
            particleCount = 100;
            particleGeometry = new THREE.BufferGeometry();
            const positions = [];
            const colors = [];
            const color1 = new THREE.Color(0x764ba2); // Purple
            const color2 = new THREE.Color(0x667eea); // Blue
            
            for (let i = 0; i < particleCount; i++) {
                // Position randomly in a box
                positions.push(
                    (Math.random() - 0.5) * 400, // x
                    (Math.random() - 0.5) * 400, // y
                    (Math.random() - 0.5) * 400  // z
                );
                // Assign a color based on interpolation between the two theme colors
                colors.push(color1.r + (color2.r - color1.r) * Math.random(),
                            color1.g + (color2.g - color1.g) * Math.random(),
                            color1.b + (color2.b - color1.b) * Math.random());
            }

            particleGeometry.setAttribute('position', new THREE.Float32BufferAttribute(positions, 3));
            particleGeometry.setAttribute('color', new THREE.Float32BufferAttribute(colors, 3));

            particleMaterial = new THREE.PointsMaterial({ 
                size: 2.5, /* Slightly larger size for better visibility */
                vertexColors: true, 
                blending: THREE.AdditiveBlending,
                transparent: true,
                opacity: 0.8
            });
            
            particles = new THREE.Points(particleGeometry, particleMaterial);
            scene.add(particles);

            // 5. Ambient Light (for subtle shading if we add solid objects)
            const ambientLight = new THREE.AmbientLight(0x404040, 1); 
            scene.add(ambientLight);
            
            // 6. Handle resizing
            window.addEventListener('resize', onWindowResize, false);
        }

        function onWindowResize() {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        }

        function animate() {
            requestAnimationFrame(animate);

            // Increased subtle rotation for a more noticeable 3D effect
            particles.rotation.x += 0.0005;
            particles.rotation.y += 0.001;

            renderer.render(scene, camera);
        }

        // Start the Three.js initialization and animation loop
        window.onload = function () {
            initThreeScene();
            animate();
        }
    </script>

</body>
</html>
