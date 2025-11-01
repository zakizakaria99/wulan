<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>Ajak Nonton untuk Wulan 💕</title>
<style>
  :root {
    --pink1: #ffc4da;
    --pink2: #ffd6e8;
    --btn1: #ff5ca8;
    --btn2: #ff7bbd;
    --no1: #ff9fb5;
    --no2: #ff6f91;
    --text: #752e4a;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }

  html, body {
    height: 100%;
    background: linear-gradient(180deg, var(--pink1), var(--pink2));
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: "Poppins", sans-serif;
    color: var(--text);
    overflow: hidden;
    -webkit-tap-highlight-color: transparent;
    touch-action: manipulation;
  }

  .card {
    background: linear-gradient(180deg,#fff5fa,#ffe3f2);
    border: 2px solid #ffb6d1;
    border-radius: 20px;
    box-shadow: 0 8px 20px rgba(255,80,150,0.25);
    padding: 24px 20px;
    width: 90vw;
    max-width: 380px;
    text-align: center;
    position: relative;
    z-index: 2;
  }

  h1 {
    font-size: 1.4rem;
    margin-bottom: 8px;
    color: #ff3c87;
  }

  p.lead {
    font-size: 0.95rem;
    margin-bottom: 20px;
    color: #a84f72;
  }

  .buttons {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
    margin-bottom: 15px;
    position: relative;
    z-index: 3;
  }

  button.btn {
    min-width: 120px;
    max-width: 130px;
    border: none;
    border-radius: 12px;
    font-weight: 700;
    font-size: 1rem;
    padding: 12px;
    color: white;
    cursor: pointer;
    transition: transform 0.25s ease, box-shadow 0.25s ease;
    box-shadow: 0 4px 10px rgba(255,60,135,0.3);
    position: relative;
    z-index: 5;
    touch-action: manipulation;
    -webkit-user-select: none;
    user-select: none;
  }

  #yes {
    background: linear-gradient(90deg, var(--btn1), var(--btn2));
  }

  #no {
    background: linear-gradient(90deg, var(--no1), var(--no2));
  }

  .note {
    font-size: 0.85rem;
    color: #a84f72;
  }

  /* Love animation */
  .heart {
    position: fixed;
    font-size: 20px;
    animation: floatUp 2s linear forwards;
    pointer-events: none;
    z-index: 999;
  }

  @keyframes floatUp {
    0% { transform: translateY(0) scale(1); opacity: 1; }
    100% { transform: translateY(-180px) scale(1.6); opacity: 0; }
  }

  /* Popup modal */
  .overlay {
    position: fixed;
    inset: 0;
    display: none;
    align-items: center;
    justify-content: center;
    background: rgba(0,0,0,0.3);
    z-index: 1000;
    padding: 20px;
    -webkit-backdrop-filter: blur(2px);
            backdrop-filter: blur(2px);
  }

  .modal {
    background: linear-gradient(180deg,#fff0f6,#ffe0ec);
    border: 2px solid #ffb6d1;
    border-radius: 18px;
    box-shadow: 0 6px 25px rgba(255,80,150,0.3);
    width: 85%;
    max-width: 320px;
    text-align: center;
    padding: 22px 18px;
    color: #ff2e88;
    z-index: 2000;
  }

  .modal h2 {
    font-size: 1.3rem;
    margin-bottom: 6px;
  }

  .modal p {
    font-size: 0.95rem;
    color: #a84f72;
    margin-bottom: 14px;
  }

  .close {
    background: #ff7ab8;
    color: #fff;
    border: none;
    border-radius: 10px;
    padding: 10px 18px;
    font-weight: 600;
    cursor: pointer;
    touch-action: manipulation;
  }

  @media screen and (max-width: 480px) {
    button.btn {
      min-width: 100px;
      max-width: 110px;
      font-size: 0.95rem;
      padding: 10px;
    }
    .buttons { gap: 14px; }
  }
</style>
</head>
<body>
  <div class="card">
    <h1>Wulan 💖</h1>
    <p class="lead">Mau nonton bareng aku? Pilih salah satu tombol di bawah ya 😚</p>

    <div class="buttons" id="btnContainer">
      <button id="yes" class="btn">Iya</button>
      <button id="no" class="btn">Tidak</button>
    </div>

    <p class="note">(Klik salah satu ya... tapi aku yakin kamu pilih yang pink 💞)</p>
  </div>

  <!-- Popup -->
  <div id="overlay" class="overlay">
    <div class="modal">
      <h2>Yay! 🎬💕</h2>
      <p>Mau nemenin aku nonton? Gak usah mikir dulu, yang penting bareng kamu ❤</p>
      <button id="closeModal" class="close">Tutup</button>
    </div>
  </div>

  <script>
    const yesBtn = document.getElementById('yes');
    const noBtn = document.getElementById('no');
    const overlay = document.getElementById('overlay');
    const closeModal = document.getElementById('closeModal');
    const container = document.getElementById('btnContainer');
    let noScale = 1;
    const NO_MIN = 0.35;

    function createHearts(){
      for(let i=0;i<20;i++){
        const heart=document.createElement("div");
        heart.classList.add("heart");
        heart.textContent="💖";
        document.body.appendChild(heart);
        heart.style.left=Math.random()*window.innerWidth+"px";
        heart.style.top=(window.innerHeight-50)+"px";
        heart.style.fontSize=(14+Math.random()*18)+"px";
        heart.style.animationDuration=(1.5+Math.random())+"s";
        heart.style.opacity=Math.random();
        setTimeout(()=>heart.remove(),2000);
      }
    }

    // Tombol Iya
    yesBtn.addEventListener('touchstart',()=>{ yesBtn.click(); });
    yesBtn.addEventListener('click',()=>{
      createHearts();
      setTimeout(()=>{ overlay.style.display='flex'; },400);
    });

    // Tombol Tidak
    noBtn.addEventListener('touchstart',()=>{ noBtn.click(); });
    noBtn.addEventListener('click',()=>{
      const maxX=container.offsetWidth-noBtn.offsetWidth;
      const maxY=container.offsetHeight-noBtn.offsetHeight;
      const randomX=(Math.random()*maxX)-maxX/2;
      const randomY=(Math.random()*maxY)-maxY/2;
      noBtn.style.transform=`translate(${randomX}px,${randomY}px) scale(${noScale})`;
      noScale=Math.max(NO_MIN, noScale-0.1);
      if(noScale<=0.45) noBtn.textContent="Hehe...";
      else noBtn.textContent="Tidak";
    });

    // Tutup popup
    closeModal.addEventListener('click',()=>overlay.style.display='none');
    overlay.addEventListener('click',e=>{if(e.target===overlay)overlay.style.display='none';});
  </script>
</body>
</html>
