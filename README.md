<!doctype html>
<html lang="de">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Countdown bis giggand — 16:00</title>

<style>
  body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #4b0082, #7a00cc);
    color: white;
  }

  .container {
    text-align: center;
    background: rgba(255, 255, 255, 0.08);
    padding: 30px 40px;
    border-radius: 14px;
    box-shadow: 0 8px 25px rgba(0,0,0,0.4);
  }

  h1 {
    font-size: 1.6rem;
    margin-bottom: 10px;
  }

  .countdown {
    display: flex;
    gap: 15px;
    justify-content: center;
    margin-top: 20px;
  }

  .unit {
    background: rgba(255,255,255,0.1);
    padding: 15px 18px;
    border-radius: 10px;
    min-width: 80px;
  }

  .value {
    font-size: 2.8rem;
    font-weight: bold;
  }

  .label {
    margin-top: 5px;
    font-size: 0.8rem;
    opacity: 0.8;
  }

  .message {
    margin-top: 25px;
    font-size: 1.2rem;
    font-weight: bold;
    display: none;
  }
</style>
</head>

<body>
<div class="container">
  <h1>Countdown – giggand streamt heute um 16:00</h1>

  <div id="countdown" class="countdown">
    <div class="unit">
      <div id="days" class="value">0</div>
      <div class="label">Tage</div>
    </div>
    <div class="unit">
      <div id="hours" class="value">00</div>
      <div class="label">Stunden</div>
    </div>
    <div class="unit">
      <div id="minutes" class="value">00</div>
      <div class="label">Minuten</div>
    </div>
    <div class="unit">
      <div id="seconds" class="value">00</div>
      <div class="label">Sekunden</div>
    </div>
  </div>

  <div id="message" class="message"></div>
</div>

<script>
  function getTargetTime() {
    const now = new Date();
    return new Date(now.getFullYear(), now.getMonth(), now.getDate(), 16, 0, 0);
  }

  const daysEl = document.getElementById("days");
  const hoursEl = document.getElementById("hours");
  const minutesEl = document.getElementById("minutes");
  const secondsEl = document.getElementById("seconds");
  const messageEl = document.getElementById("message");
  const countdownEl = document.getElementById("countdown");

  function updateCountdown() {
    const now = new Date();
    const target = getTargetTime();
    const diff = target - now;

    if (diff <= 0) {
      countdownEl.style.display = "none";
      messageEl.style.display = "block";
      messageEl.textContent = "giggand streamt jetzt! 🎉";
      return;
    }

    const totalSeconds = Math.floor(diff / 1000);
    const days = Math.floor(totalSeconds / 86400);
    const hours = Math.floor((totalSeconds % 86400) / 3600);
    const minutes = Math.floor((totalSeconds % 3600) / 60);
    const seconds = totalSeconds % 60;

    daysEl.textContent = days;
    hoursEl.textContent = String(hours).padStart(2, "0");
    minutesEl.textContent = String(minutes).padStart(2, "0");
    secondsEl.textContent = String(seconds).padStart(2, "0");
  }

  updateCountdown();
  setInterval(updateCountdown, 250);
</script>
</body>
</html>
