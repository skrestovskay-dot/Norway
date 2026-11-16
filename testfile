<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Паспорт гражданина Норвегии</title>
<style>
  :root{
    --bg: #0f172a; 
    --passport-cover: #8b1c24; 
    --passport-pages: #fdfbf7; 
    --accent: #0284c7; 
    --gold: #d4af37; 
    --ok: #10b981; 
    --bad: #ef4444; 
    --text: #1e293b; 
    --muted: #64748b; 
  }
  *{box-sizing:border-box; font-family:'Georgia', serif; user-select:none;}
  body{margin:0; min-height:100vh; background:radial-gradient(circle at center, #1e293b, var(--bg));
       color:var(--text); display:flex; align-items:center; justify-content:center; padding:16px; overflow:hidden;}

  .passport{width:100%; max-width:1000px; height:700px; background:var(--passport-cover);
        border-radius:12px; box-shadow:0 20px 80px rgba(0,0,0,0.8), inset 0 0 20px rgba(0,0,0,0.5);
        display:flex; padding:20px; position:relative; transition: transform 0.6s;}

  .cover-screen{position:absolute; inset:20px; background:var(--passport-cover); z-index:100; 
        display:flex; flex-direction:column; align-items:center; justify-content:center;
        border-radius:8px; border: 2px solid rgba(212, 175, 55, 0.3); transition: 0.5s;}
  .cover-screen.hidden{opacity:0; pointer-events:none; transform: scale(0.95);}
  
  .cover-emblem{width:120px; height:140px; border: 4px solid var(--gold); border-radius: 50% 50% 10% 10%; 
        display:flex; align-items:center; justify-content:center; margin-bottom:30px; box-shadow:0 0 30px rgba(212,175,55,0.3);}
  .cover-emblem span{font-size: 4rem;}
  .cover-screen h1{color:var(--gold); font-size:2.5rem; letter-spacing:4px; text-transform:uppercase; margin:0 0 10px; text-shadow:0 4px 10px rgba(0,0,0,0.5);}
  .cover-screen p{color: rgba(255,255,255,0.7); font-size:1rem; font-family:system-ui; margin-bottom: 40px;}
  .cover-screen button{background:var(--gold); color:#000; padding:16px 40px; font-size:1.1rem; border:none; border-radius:8px; font-weight:bold; cursor:pointer; box-shadow:0 10px 20px rgba(0,0,0,0.5); transition:0.2s;}
  .cover-screen button:hover{transform:scale(1.05);}

  .page{flex:1; background:var(--passport-pages); border-radius:4px; display:flex; flex-direction:column; position:relative; overflow:hidden;}
  
  .page::before{content:''; position:absolute; inset:0; pointer-events:none; opacity:0.04;
    background-image: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M50 50c-10 0-20-10-20-20s10-20 20-20 20 10 20 20-10 20-20 20zm0 40c-10 0-20-10-20-20s10-20 20-20 20 10 20 20-10 20-20 20z' fill='%23000' fill-rule='evenodd'/%3E%3C/svg%3E");
    background-size: 200px; z-index: 0;}

  .page-header{display:flex; justify-content:space-between; align-items:center; padding:16px 24px;
        border-bottom:2px solid #e2e8f0; position:relative; z-index:2;}
  .page-header .flag-box{width:50px; height:35px; border:1px solid #ccc; box-shadow:0 2px 5px rgba(0,0,0,0.1); position:relative; overflow:hidden; background:#ba0c2f;}
  .page-header .flag-box .flag{position:absolute; inset:0; background:linear-gradient(to bottom, transparent 40%, #fff 40%, #fff 46%, #00205b 46%, #00205b 54%, #fff 54%, #fff 60%, transparent 60%),linear-gradient(to right, transparent 28%, #fff 28%, #fff 35%, #00205b 35%, #00205b 42%, #fff 42%, #fff 49%, transparent 49%);}
  
  .page-header .progress{font-family:system-ui; font-weight:bold; font-size:0.9rem; color:var(--muted);}
  .page-header .progress b{color:var(--accent);}

  .page-body{flex:1; display:flex; padding:24px; gap:30px; position:relative; z-index:2;}

  .profile{width:200px; display:flex; flex-direction:column; align-items:center; gap:16px; border-right: 2px dashed #cbd5e1; padding-right:24px;}
  .photo-frame{width:140px; height:180px; background:#e2e8f0; border:4px solid #cbd5e1; border-radius:6px; display:flex; align-items:center; justify-content:center; font-size:5rem; box-shadow:0 5px 15px rgba(0,0,0,0.05);}
  
  .stamps-box{width:100%; margin-top:auto;}
  .stamps-box h4{margin:0 0 8px; font-family:system-ui; font-size:0.75rem; text-transform:uppercase; letter-spacing:1px; color:var(--muted);}
  
  .stamps{display:grid; grid-template-columns: repeat(4, 1fr); gap:8px; justify-items: center;}
  
  .stamp-slot{width:36px; height:36px; border-radius:50%; border:2px dashed #cbd5e1; display:flex; align-items:center; justify-content:center; position:relative;}
  
  .stamp-arrived{width:36px; height:36px; border-radius:50%; border:2px solid var(--ok); background:#f0fdf4; display:flex; align-items:center; justify-content:center; font-size:1.1rem; animation: land 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards; box-shadow: 0 2px 5px rgba(0,0,0,0.1);}
  
  @keyframes land {
    0% { transform: scale(1.5); opacity: 0; }
    50% { transform: scale(0.9); opacity: 1; }
    100% { transform: scale(1); opacity: 1; }
  }

  .quest{flex:1; display:flex; flex-direction:column;}
  .char-msg{background:#f1f5f9; border-radius:12px; padding:16px; border-left:4px solid var(--accent); margin-bottom:20px; position:relative;}
  .char-msg .name{font-family:system-ui; font-weight:800; font-size:0.8rem; color:var(--accent); text-transform:uppercase; letter-spacing:1px; margin-bottom:4px; display:block;}
  .char-msg p{margin:0; font-size:1rem; line-height:1.5; color:var(--text);}
  
  .quest h2{margin:0 0 12px; font-size:1.4rem; color:var(--text);}
  
  input{width:100%; padding:16px; border-radius:8px; border:2px solid #cbd5e1; background:#fff; color:var(--text); margin-bottom:12px; font-size:1.1rem; font-family:system-ui; font-weight:600;}
  input:focus{outline:none; border-color:var(--accent); box-shadow:0 0 0 4px rgba(2, 132, 199, 0.1);}

  button.btn{padding:16px 24px; border:none; border-radius:8px; background:var(--accent); color:#fff; font-weight:bold; font-family:system-ui; cursor:pointer; font-size:1rem; width:100%; margin-bottom:10px; transition:0.2s;}
  button.btn:hover{background:#026aa3;}
  
  button.opt{background:#fff; color:var(--text); border:2px solid #cbd5e1; text-align:left; font-family:system-ui;}
  button.opt:hover{border-color:var(--accent); background:#f8fafc;}
  button.opt.correct{border-color:var(--ok); background:#ecfdf5; color:#047857;}
  button.opt.wrong{border-color:var(--bad); background:#fef2f2; color:#b91c1c; animation:shake 0.3s;}
  
  button.hint{background:transparent; color:var(--gold); border:2px solid var(--gold); font-size:0.9rem;}
  button.hint:hover{background:rgba(212,175,55,0.1);}

  @keyframes shake{25%{transform:translateX(-6px);} 75%{transform:translateX(6px);}}
  .msg{font-family:system-ui; font-size:0.9rem; font-weight:600; margin-top:10px; min-height:20px;}
  .msg.ok{color:var(--ok);} .msg.bad{color:var(--bad);}

  /* Анимация полета штампа */
  .flying-stamp {
    position: fixed; z-index: 9999; font-size: 2.5rem; 
    display: flex; align-items: center; justify-content: center;
    width: 70px; height: 70px; border-radius: 50%; background: #fff; border: 3px solid var(--ok);
    pointer-events: none; box-shadow: 0 10px 30px rgba(0,0,0,0.4);
  }

  @keyframes fly {
    0% { transform: translate(0, 0) scale(2.5) rotate(-30deg); opacity: 0; }
    15% { transform: translate(0, -50px) scale(1.8) rotate(0deg); opacity: 1; }
    60% { transform: translate(var(--tx), var(--ty)) scale(1.2) rotate(10deg); opacity: 1; }
    80% { transform: translate(var(--tx), var(--ty)) scale(1.1) rotate(-5deg); opacity: 1; }
    100% { transform: translate(var(--tx), var(--ty)) scale(1) rotate(0deg); opacity: 0; }
  }

  /* Финальный замок */
  .lock-screen{position:absolute; inset:0; background:var(--passport-pages); z-index:50; display:none; flex-direction:column; align-items:center; justify-content:center; padding:40px; text-align:center;}
  .lock-screen.show{display:flex; animation: fadeIn 0.5s;}
  .lock-screen h2{font-size:2rem; color:var(--passport-cover); margin:0 0 10px;}
  .lock-screen p{font-family:system-ui; color:var(--muted); max-width:400px; margin-bottom:24px;}
  
  .code-inputs{display:flex; gap:16px; margin-bottom:24px;}
  .code-inputs input{width:80px; height:60px; text-align:center; font-size:1.5rem; border-radius:8px; margin:0; padding:0; border:2px solid #cbd5e1;}
  .code-inputs input:focus{border-color:var(--accent); outline:none;}
  
  /* Важно: стили для кликабельности кнопки */
  .lock-screen button { position: relative; z-index: 10; cursor: pointer; }

  .stamp-final { border: 4px solid var(--ok); color: var(--ok); border-radius: 12px; padding: 20px; transform: rotate(-5deg); display: inline-block; margin-top:20px; opacity: 0.8;}
  .stamp-final h3 { margin:0; font-family: system-ui; text-transform: uppercase; letter-spacing: 2px;}

  @keyframes fadeIn {from{opacity:0;} to{opacity:1;}}

  /* Мобильная версия */
  @media (max-width: 768px) {
    body { padding: 0; background: var(--passport-pages); }
    .passport { height: 100dvh; border-radius: 0; padding: 0; box-shadow: none; border:none; }
    .page { border-radius: 0; }
    .page-body { flex-direction: column; padding: 16px; gap: 16px; overflow-y: auto; }
    .profile { width: 100%; border-right: none; border-bottom: 2px dashed #cbd5e1; padding-right: 0; padding-bottom: 16px; flex-direction: row; justify-content: space-between; align-items: center;}
    .photo-frame { width: 80px; height: 100px; font-size: 3rem; border-width: 2px; border-radius: 4px;}
    .stamps-box { margin-top: 0; width: auto; }
    .stamps { grid-template-columns: repeat(4, 1fr); max-width: 180px; gap: 4px;}
    .stamp-slot, .stamp-arrived { width: 30px; height: 30px; font-size: 0.9rem; border-width: 2px;}
    .cover-screen { inset: 0; border-radius: 0; }
    .quest h2 { font-size: 1.2rem; }
    .lock-screen { padding: 16px; }
    .code-inputs { gap: 8px; flex-wrap: wrap; justify-content: center; }
    .code-inputs input { width: 60px; height: 50px; font-size: 1.2rem;}
  }
</style>
</head>
<body>

<div class="passport">
  
  <div class="cover-screen" id="coverScreen">
    <div class="cover-emblem"><span>🇳🇴</span></div>
    <h1>NORGE</h1>
    <p>Kongeriket Norge • Королевство Норвегия</p>
    <button onclick="openPassport()">Открыть паспорт</button>
  </div>

  <div class="page">
    <div class="page-header">
      <div class="flag-box"><div class="flag"></div></div>
      <div class="progress">Страница <b id="progress">1</b> из 12</div>
    </div>

    <div class="page-body">
      <div class="profile">
        <div class="photo-frame" id="avatar">👑</div>
        <div class="stamps-box">
          <h4>Визы и штампы</h4>
          <div class="stamps" id="stampsContainer"></div>
        </div>
      </div>

      <div class="quest" id="questArea"></div>
    </div>

    <div class="lock-screen" id="lockScreen">
      <h2>Пограничный контроль</h2>
      <p>Введите код, чтобы получить финальную печать.</p>
      <div class="code-inputs">
        <input id="l1" maxlength="4" inputmode="numeric" placeholder="____">
        <input id="l2" maxlength="2" inputmode="numeric" placeholder="__">
        <input id="l3" maxlength="3" inputmode="numeric" placeholder="___">
      </div>
      <div style="font-family:system-ui; font-size:0.85rem; color:#64748b; margin-bottom:20px;">
        Подсказка: Дата Конституции (4) • Возраст голосования (2) • Депутаты (3)
      </div>
      <button class="btn" style="width:200px;" onclick="checkFinal()">Поставить печать</button>
      <div class="msg" id="lockMsg"></div>
    </div>

  </div>
</div>

<script>
const CHARACTERS = {
  king:  { name:'Король Харальд V', avatar:'👑' },
  queen: { name:'Королева Соня',    avatar:'👸' },
  guide: { name:'Эйрик',            avatar:'🧔‍♂️' }
};

const LOCATIONS = [
  { id:'eidsvoll', char:'queen', title:'Рождение Конституции', desc:'Здесь в 1814 году была принята Конституция. Введи день и месяц её принятия (4 цифры).', type:'input', answer:'1705', hint:'Это день национального праздника Норвегии — 17 мая.', artifact:'📜' },
  { id:'storting1', char:'king', title:'Стортинг: Число депутатов', desc:'Здесь заседает парламент. Сколько депутатов в Стортинге?', type:'input', answer:'169', hint:'Число между 150 и 180.', artifact:'🏛' },
  { id:'storting2', char:'king', title:'Три задачи Стортинга', desc:'Какая из перечисленных задач НЕ относится к Стортингу?', type:'options', options:['Законодательная','Бюджетная','Командование армией','Контрольная'], answer:'Командование армией', hint:'Армией командует исполнительная власть.', artifact:'⚖️' },
  { id:'komitety', char:'queen', title:'Постоянные комитеты', desc:'Сколько постоянных комитетов работает в Стортинге?', type:'input', answer:'12', hint:'Больше десяти, но меньше пятнадцати.', artifact:'📋' },
  { id:'palace1', char:'king', title:'Контрассигнация', desc:'Король подписал указ. Что нужно, чтобы он вступил в силу?', type:'options', options:['Достаточно подписи короля','Нужна подпись премьер-министра','Нужно голосование Стортинга'], answer:'Нужна подпись премьер-министра', hint:'Это называется контрассигнация.', artifact:'✍️' },
  { id:'palace2', char:'king', title:'Парламентаризм', desc:'Правительство должно пользоваться доверием ...', type:'options', options:['Короля','Стортинга','Верховного суда'], answer:'Стортинга', hint:'Кто может отправить правительство в отставку?', artifact:'🤝' },
  { id:'gov', char:'queen', title:'Сколько министров?', desc:'Сколько примерно министров входит в правительство Норвегии?', type:'input', answer:'20', hint:'Число около двадцати.', artifact:'👥' },
  { id:'court1', char:'king', title:'Особый суд', desc:'Министр нарушил закон. Какой суд рассматривает дело?', type:'options', options:['Окружной суд','Верховный суд','Суд импичмента'], answer:'Суд импичмента', hint:'Это особый суд для членов правительства.', artifact:'⚖️' },
  { id:'court2', char:'queen', title:'Судебный контроль', desc:'Может ли суд Норвегии признать закон неконституционным?', type:'options', options:['Да, это судебный контроль','Нет, только Стортинг решает','Только король может отменить'], answer:'Да, это судебный контроль', hint:'Суды могут отменять неконституционные законы.', artifact:'🔍' },
  { id:'vote', char:'king', title:'Возраст голосования', desc:'С какого возраста в Норвегии можно голосовать?', type:'input', answer:'18', hint:'Совершеннолетие в Европе.', artifact:'🗳' },
  { id:'ref', char:'king', title:'Референдумы', desc:'Каков статус референдумов в Норвегии?', type:'options', options:['Обязательные','Консультативные','Референдумов не существует'], answer:'Консультативные', hint:'Результат не обязывает парламент.', artifact:'📊' },
  { id:'media', char:'queen', title:'Четвёртая власть', desc:'Что в Норвегии неофициально называют «четвёртой властью»?', type:'options', options:['СМИ','Короля','Саамский парламент'], answer:'СМИ', hint:'Они формируют общественное мнение.', artifact:'📰' }
];

const state = { current: 0, hintsLeft: 3 };
const $ = id => document.getElementById(id);

function openPassport() {
  $('coverScreen').classList.add('hidden');
  render();
}

function renderStamps() {
  const container = $('stampsContainer');
  container.innerHTML = '';
  for(let i=0; i<12; i++) {
    if(i < state.current) {
      container.innerHTML += `<div class="stamp-arrived">${LOCATIONS[i].artifact}</div>`;
    } else {
      container.innerHTML += `<div class="stamp-slot" id="slot-${i}"></div>`;
    }
  }
}

function setCharacter(charKey, text) {
  const c = CHARACTERS[charKey];
  $('avatar').textContent = c.avatar;
  return `
    <div class="char-msg">
      <span class="name">${c.name}</span>
      <p>${text}</p>
    </div>
  `;
}

function render() {
  if (state.current >= LOCATIONS.length) {
    $('questArea').innerHTML = `<h2>Все проверки пройдены</h2><p style="font-family:system-ui">Нажмите кнопку ниже, чтобы пройти таможню.</p><button class="btn" style="background:var(--gold); color:#000; margin-top:20px;" onclick="showLock()">На таможню</button>`;
    return;
  }

  const loc = LOCATIONS[state.current];
  $('progress').textContent = state.current + 1;
  renderStamps();

  let content = setCharacter(loc.char, loc.desc);
  content += `<h2>${loc.title}</h2>`;

  if (loc.type === 'input') {
    content += `
      <input id="ans" placeholder="Твой ответ..." autocomplete="off">
      <button class="btn" onclick="checkInput()">Проверить</button>
      <button class="btn hint" onclick="useHint()">💡 Подсказка (${state.hintsLeft})</button>
      <div class="msg" id="msg"></div>
    `;
  } else {
    content += loc.options.map(o => `<button class="btn opt" onclick="checkOption(this, '${o.replace(/'/g,'&#39;')}')">${o}</button>`).join('');
    content += `<button class="btn hint" onclick="useHint()" style="margin-top:10px;">💡 Подсказка (${state.hintsLeft})</button><div class="msg" id="msg"></div>`;
  }

  $('questArea').innerHTML = content;
  
  const inp = $('ans');
  if(inp) {
    inp.focus();
    inp.addEventListener('keydown', e => { if(e.key==='Enter') checkInput(); });
  }
}

function checkInput(){
  const loc = LOCATIONS[state.current];
  if($('ans').value.trim().toLowerCase() === loc.answer.toLowerCase()) correct(); else wrong();
}

function checkOption(btn, val){
  const loc = LOCATIONS[state.current];
  if(val === loc.answer){ btn.classList.add('correct'); setTimeout(correct, 300); }
  else { btn.classList.add('wrong'); wrong(); }
}

function wrong(){
  const m = $('msg');
  if(m){ m.className='msg bad'; m.textContent='Неверно. Штамп не поставлен.'; }
  const page = document.querySelector('.page');
  page.style.animation = 'none'; page.offsetHeight; page.style.animation = 'shake .4s';
}

function correct() {
  const m = $('msg'); 
  if(m){ m.className='msg ok'; m.textContent='Верно! Летит печать...'; }
  
  // Блокируем кнопки только на время анимации текущего вопроса
  const allBtns = document.querySelectorAll('button');
  allBtns.forEach(b => b.disabled = true);

  const loc = LOCATIONS[state.current];
  const targetSlot = $(`slot-${state.current}`);
  
  if (targetSlot) {
    const rect = targetSlot.getBoundingClientRect();
    
    const flyer = document.createElement('div');
    flyer.className = 'flying-stamp';
    flyer.textContent = loc.artifact;
    
    flyer.style.left = '50%';
    flyer.style.top = '50%';
    flyer.style.transform = 'translate(-50%, -50%)';
    
    const startX = window.innerWidth / 2;
    const startY = window.innerHeight / 2;
    
    const targetX = rect.left + rect.width / 2;
    const targetY = rect.top + rect.height / 2;
    
    flyer.style.setProperty('--tx', (targetX - startX) + 'px');
    flyer.style.setProperty('--ty', (targetY - startY) + 'px');
    
    flyer.style.animation = 'fly 1.5s cubic-bezier(0.25, 1, 0.5, 1) forwards';
    
    document.body.appendChild(flyer);
    
    playStampSound();

    setTimeout(() => {
      flyer.remove();
      state.current++;
      render();
    }, 1500);
  } else {
    state.current++;
    render();
  }
}

function playStampSound() {
  try {
    const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    const osc = audioCtx.createOscillator();
    const gain = audioCtx.createGain();
    
    osc.type = 'sine';
    osc.frequency.setValueAtTime(150, audioCtx.currentTime);
    osc.frequency.exponentialRampToValueAtTime(40, audioCtx.currentTime + 0.2);
    
    gain.gain.setValueAtTime(0.5, audioCtx.currentTime);
    gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.2);
    
    osc.connect(gain);
    gain.connect(audioCtx.destination);
    
    osc.start();
    osc.stop(audioCtx.currentTime + 0.2);
  } catch (e) {}
}

function useHint(){
  if(state.hintsLeft <= 0){ alert('Подсказки закончились.'); return; }
  state.hintsLeft--;
  const loc = LOCATIONS[state.current];
  alert(`Подсказка: ${loc.hint}`);
  const btn = document.querySelector('.hint'); if(btn) btn.textContent = `💡 Подсказка (${state.hintsLeft})`;
}

// ВАЖНО: эта функция снимает блокировку с кнопок перед показом финала
function showLock(){ 
  document.querySelectorAll('button').forEach(b => b.disabled = false);
  $('lockScreen').classList.add('show'); 
}

function checkFinal(){
  const code = ['l1','l2','l3'].map(id => $(id).value.trim()).join('');
  const m = $('lockMsg');
  if(code === '170518169'){ 
    try {
      const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
      const osc = audioCtx.createOscillator();
      const gain = audioCtx.createGain();
      osc.type = 'triangle';
      osc.frequency.setValueAtTime(440, audioCtx.currentTime);
      osc.frequency.setValueAtTime(554, audioCtx.currentTime + 0.1);
      osc.frequency.setValueAtTime(659, audioCtx.currentTime + 0.2);
      gain.gain.setValueAtTime(0.3, audioCtx.currentTime);
      gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.6);
      osc.connect(gain);
      gain.connect(audioCtx.destination);
      osc.start();
      osc.stop(audioCtx.currentTime + 0.6);
    } catch(e) {}

    $('lockScreen').innerHTML = `
      <div class="stamp-final">
        <h3>APPROVED</h3>
        <p style="font-family:system-ui; margin:5px 0 0; font-size:0.8rem;">Velkommen til Norge!</p>
      </div>
      <h2 style="margin-top:30px; color:var(--ok);">Добро пожаловать!</h2>
      <p>Паспорт заполнен. Вы успешно разобрались в устройстве Норвегии и пересекли границу.</p>
      <button class="btn" style="background:var(--text); margin-top:20px;" onclick="location.reload()">Оформить новый паспорт</button>
    `;
  } else { 
    m.className = 'msg bad'; m.textContent = 'Код неверен. Проверьте цифры.'; 
  }
}

render();
</script>
</body>
</html>
