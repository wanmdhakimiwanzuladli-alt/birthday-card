<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>💖 Happy Birthday, My Love!</title>
  <style>
    :root{
      --bg1:#ff8ad6;
      --bg2:#ffd1f2;
      --ink:#2b2341;
      --accent:#ff5fa2;
      --accent-2:#7f6bff;
      --paper:#fff9ff;
      --gold:#ffcc66;
    }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: "Inter", system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial;
      color:var(--ink);
      display:grid; place-items:center; overflow-x:hidden;
      background: linear-gradient(135deg,var(--bg1),var(--bg2));
      background-size: 200% 200%;
      animation:bgshift 12s ease-in-out infinite;
    }
    @keyframes bgshift{
      0%{background-position:0% 50%}
      50%{background-position:100% 50%}
      100%{background-position:0% 50%}
    }

    .wrap{width:min(900px,94vw); padding:24px;}

    .title{
      text-align:center; margin:0 0 14px; font-size:clamp(22px,3.5vw,36px);
      letter-spacing:.3px; text-shadow:0 2px 0 rgba(255,255,255,.45)
    }
    .subtitle{ text-align:center; margin:0 0 24px; opacity:.85 }

    .card-scene{ perspective:1200px; }
    .card{
      position:relative; margin:auto; height:480px; width:min(800px,92vw);
      transform-style:preserve-3d;
      transition: transform 900ms cubic-bezier(.2,.85,.12,1);
    }
    .card.open{ transform: rotateY(-180deg); }
    .side{ position:absolute; top:0; left:0; height:100%; width:100%;
      border-radius:22px; box-shadow:0 30px 70px rgba(0,0,0,.15);
      backface-visibility:hidden; overflow:hidden;
    }

    /* FRONT */
    .front{
      background: radial-gradient(1200px 600px at -5% -10%, #ffffffcc 0%, transparent 60%),
                  radial-gradient(1200px 800px at 120% 120%, #ffffffaa 0%, transparent 60%),
                  linear-gradient(145deg, #fff, var(--paper));
      display:grid; grid-template-rows:1fr auto; align-items:center; place-items:center; padding:28px;
      border: 2px solid #fff5; position:relative;
    }
    .front .badge{
      margin-top:36px; height:140px; width:140px; border-radius:50%; display:grid; place-items:center; font-size:54px;
      background:
        radial-gradient(circle at 30% 30%, #fff 0 30%, transparent 31%),
        radial-gradient(circle at 60% 60%, #fff 0 20%, transparent 21%),
        linear-gradient(135deg, var(--accent), var(--accent-2));
      color:white; box-shadow: inset 0 6px 18px #ffffff66, 0 12px 40px #00000022;
    }
    .front h2{ margin:16px 0 8px; font-size:clamp(26px,4vw,40px); }
    .front p{ margin:0; opacity:.9 }
    .ribbon{
      position:absolute; top:20px; right:-12px; background:linear-gradient(90deg,var(--accent),var(--accent-2));
      color:#fff; padding:10px 16px; font-weight:700; border-radius: 10px 10px 0 10px;
      box-shadow:0 10px 30px #0000002a;
    }
    .ribbon:after{
      content:""; position:absolute; right:0; bottom:-12px; border:12px solid transparent; border-top-color:var(--accent-2);
    }

    /* INSIDE */
    .inside{
      transform: rotateY(180deg);
      background: linear-gradient(180deg, #fff, var(--paper));
      padding: 26px min(3.2vw,26px);
      display:grid; grid-template-columns: 1.1fr 1fr; gap:22px;
    }

    .photo-frame {
      width: 100%; height: 100%; overflow: hidden;
      box-shadow: 0 8px 24px #00000025;
      display: flex; align-items: center; justify-content: center;
    }
    .photo { width: 100%; height: 100%; object-fit: cover; display: block; }

    @media (max-width: 720px){
      .inside{ grid-template-columns:1fr; height:auto; }
      .card{ height:auto; }
    }

    .message{ padding:18px; border-radius:18px; background: #ffffffcc;
      box-shadow: inset 0 2px 10px #0000000e;
    }
    .message h3{ margin:0 0 6px; font-size:clamp(20px,3vw,28px) }
    .message p{ line-height:1.6; margin:.5em 0 }

    .details{ display:grid; align-content:start; gap:16px; }
    .avatar{
      height:120px; width:120px; border-radius:50%; background: linear-gradient(135deg,var(--accent),var(--accent-2));
      display:grid; place-items:center; font-size:44px; color:#fff; box-shadow:0 8px 24px #00000025; margin-bottom:6px;
    }
    .list{ list-style:none; padding:0; margin:0; display:grid; gap:10px; }
    .list li{
      background:#fff; border-radius:14px; padding:12px 14px; box-shadow:0 4px 14px #00000012;
      display:flex; align-items:center; gap:10px;
    }
    .list .icon{ font-size:18px }

    .controls{ display:flex; justify-content:center; gap:12px; margin-top:18px }
    button{
      border:none; padding:12px 18px; border-radius:999px; font-weight:700; cursor:pointer;
      background:linear-gradient(135deg,var(--accent),var(--accent-2)); color:white;
      box-shadow:0 8px 30px #0000002a; transition: transform .1s ease, filter .2s ease;
    }
    button:hover{ transform: translateY(-1px); filter:brightness(1.05) }

    /* Floating hearts */
    .hearts{ position:fixed; inset:0; pointer-events:none; overflow:hidden }
    .heart{ position:absolute; font-size:18px; animation: floatUp 8s linear infinite; opacity:.8 }
    @keyframes floatUp{
      from{ transform: translateY(20vh) scale(.9); opacity:.0 }
      10%{opacity:.85}
      to{ transform: translateY(-110vh) scale(1.2); opacity:0 }
    }

    /* Confetti */
    #confetti{ position:fixed; inset:0; width:100%; height:100%; pointer-events:none; }

    @media print{
      body{ background:#fff; animation:none }
      .wrap{ padding:0 }
      .card{ transform:none !important }
      .front .ribbon, .controls, #confetti, .hearts{ display:none }
    }
  </style>
</head>
<body>
  <div class="wrap">
    <h1 class="title">💖 Happy Birthday, Babyyy Girlll!</h1>
    <p class="subtitle">A little interactive card made just for you. Click the button to open it 🎁</p>

    <!-- Spotify Player (hidden initially) -->
    <div style="margin: 24px 0; text-align: center;">
      <iframe id="spotifyPlayer" style="border-radius:12px; display:none;"
        width="320" height="80"
        frameBorder="0"
        allow="autoplay; clipboard-write; encrypted-media; picture-in-picture"
        loading="lazy">
      </iframe>
    </div>

    <div class="card-scene">
      <div class="card" id="card">
        <!-- FRONT COVER -->
        <section class="side front">
          <div class="badge">🎂</div>
          <div>
            <h2>To: <span id="toName">My Favorite Person</span></h2>
            <p>From: <span id="fromName">Your Biggest Fan</span></p>
          </div>
          <div class="ribbon">Birthday Girl ✨</div>
        </section>

        <!-- INSIDE -->
        <section class="side inside">
          <div class="message">
            <h3>Happy Birthday, <span id="dearName">Love</span>! 🎉</h3>
            <p>
              happy birthday to my most beautiful, loving, gorgeous and caring girlfriend!
              thank you for being a part of my life and for all the joy you bring.
              I pray that you win in life, achieve all your dreams, and get everything you want.
            </p>
            <p>
              I will always be here for you, please be healthy and always happy.
              Im sorry for hurting you , tbh im still loving you.
              I love and I miss you so much my treasure.I hope we can fix everything and be together again.
            </p>
            <p style="margin-top:14px; font-weight:700">
              With all my heart, <span id="signature">— Yours, Always</span> 💌
            </p>
          </div>
          <aside class="details">
            <div class="photo-frame">
              <img src="us.JPG" alt="Birthday Girl Photo" class="photo" />
            </div>
          </aside>
        </section>
      </div>
    </div>

    <div class="controls">
      <button id="toggle">Open Card</button>
      <button id="print">Print</button>
    </div>
  </div>

  <div class="hearts" id="hearts"></div>
  <canvas id="confetti"></canvas>

  <script>
    const NAMES = {
      to: "qilah",
      from: "kimi",
      dear: "qilah",
      sign: "— kimi"
    };
    for(const [key,val] of Object.entries(NAMES)){
      const el = document.getElementById(
        key === 'to' ? 'toName' : key === 'from' ? 'fromName' :
        key === 'dear' ? 'dearName' : 'signature'
      );
      if(el) el.textContent = val;
    }

    const card = document.getElementById('card');
    const btn = document.getElementById('toggle');
    const spotifyPlayer = document.getElementById('spotifyPlayer');
    let open = false;

    btn.addEventListener('click', () => {
      open = !open;
      card.classList.toggle('open', open);
      btn.textContent = open ? 'Close Card' : 'Open Card';

      if (open) {
        spotifyPlayer.style.display = "block";
        spotifyPlayer.src = "https://open.spotify.com/embed/track/51sJ2RHFHRu2tYPedg5MIq?utm_source=generator&autoplay=1";
        shootConfetti(850);
      } else {
        spotifyPlayer.src = "https://open.spotify.com/album/5gBzYaRS9oohVfSOlsW9EE?si=alPIu-u-Rc2KjUff2RqiXA";
        spotifyPlayer.style.display = "none";
      }
    });

    document.getElementById('print').addEventListener('click', () => window.print());

    const heartContainer = document.getElementById('hearts');
    const HEARTS = 18;
    for(let i=0;i<HEARTS;i++){
      const span = document.createElement('span');
      span.className = 'heart';
      span.textContent = ['💖','💞','💓','💗','💕'][Math.floor(Math.random()*5)];
      span.style.left = Math.random()*100+'vw';
      span.style.animationDelay = (Math.random()*8)+'s';
      span.style.fontSize = (16 + Math.random()*22)+'px';
      heartContainer.appendChild(span);
    }

    const canvas = document.getElementById('confetti');
    const ctx = canvas.getContext('2d');
    let confettiPieces = [];
    function resize(){ canvas.width = innerWidth; canvas.height = innerHeight }
    addEventListener('resize', resize); resize();

    function shootConfetti(duration=1000){
      const colors = ['#ffffff', '#ffe0f5', '#ffc2e8', '#ffd166', '#b5a8ff'];
      const count = Math.min(220, Math.floor(innerWidth/4));
      const start = performance.now();

      for(let i=0;i<count;i++){
        confettiPieces.push({
          x: Math.random()*canvas.width,
          y: -20 - Math.random()*40,
          w: 6 + Math.random()*8,
          h: 10 + Math.random()*10,
          vx: -2 + Math.random()*4,
          vy: 3 + Math.random()*3,
          rot: Math.random()*Math.PI,
          vr: (-0.1 + Math.random()*0.2),
          color: colors[Math.floor(Math.random()*colors.length)],
          life: 1
        });
      }
      function animate(now){
        const t = now - start;
        ctx.clearRect(0,0,canvas.width,canvas.height);
        confettiPieces.forEach(p=>{
          p.vy += 0.035;
          p.x += p.vx; p.y += p.vy; p.rot += p.vr;
          p.life *= 0.995;
          ctx.save();
          ctx.translate(p.x, p.y);
          ctx.rotate(p.rot);
          ctx.fillStyle = p.color;
          ctx.globalAlpha = Math.max(0, Math.min(1,p.life));
          ctx.fillRect(-p.w/2, -p.h/2, p.w, p.h);
          ctx.restore();
        });
        confettiPieces = confettiPieces.filter(p=> p.y < canvas.height + 40 && p.life > 0.05);
        if (t < duration || confettiPieces.length){ requestAnimationFrame(animate); }
      }
      requestAnimationFrame(animate);
    }
  </script>
</body>
</html>
