
let score = 0;
let cross = true;
let gameStarted = false;
let gamePaused = false;
let gameEnded = false;
let audio = new Audio("music.mp3");
let audiogo = new Audio("gameover.mp3");
audio.loop = true;
const menuScreen = document.getElementById("menuScreen");

const menuTitle = document.getElementById("menuTitle");

const menuMessage = document.getElementById("menuMessage");

const startBtn = document.getElementById("startBtn");

const resumeBtn = document.getElementById("resumeBtn");

const playAgainBtn = document.getElementById("playAgainBtn");

const pauseBtn = document.getElementById("pauseBtn");

const dino = document.querySelector(".dino");

const obstacle = document.querySelector(".obstacle");

const gameOverText = document.querySelector(".gameOver");



resumeBtn.style.display = "none";

playAgainBtn.style.display = "none";

pauseBtn.style.display = "none";


startBtn.addEventListener("click", function () {
  startGame();
});

function startGame() {
  gameStarted = true;

  gamePaused = false;

  gameEnded = false;

  /* Reset score */

  score = 0;

  cross = true;

  updateScore();

  /* Reset player */

  dino.style.left = "52px";

  /* Reset obstacle */

  obstacle.style.left = "100vw";

  obstacle.style.animationDuration = "5s";

  /* Start obstacle */

  obstacle.classList.add("obstacleAni");

  obstacle.style.animationPlayState = "running";

  /* Hide menu */

  menuScreen.style.display = "none";

  /* Show pause button */

  pauseBtn.style.display = "block";

  /* Reset title */

  gameOverText.innerHTML = "Welcome to iRun Adventures";

  /* Start music */

  audio.currentTime = 0;

  audio.play().catch(function () {
    console.log("Music could not start.");
  });
}


pauseBtn.addEventListener("click", function () {
  if (!gameStarted || gameEnded) {
    return;
  }

  pauseGame();
});

function pauseGame() {
  gamePaused = true;

  /* Pause obstacle */

  obstacle.style.animationPlayState = "paused";

  /* Pause music */

  audio.pause();

  /* Change menu */

  menuTitle.innerHTML = "⏸ Game Paused";

  menuMessage.innerHTML = "Your game is paused. Click RESUME to continue.";

  /* Button visibility */

  startBtn.style.display = "none";

  resumeBtn.style.display = "block";

  playAgainBtn.style.display = "none";

  /* Show menu */

  menuScreen.style.display = "flex";
}



resumeBtn.addEventListener("click", function () {
  resumeGame();
});

function resumeGame() {
  gamePaused = false;

  /* Hide menu */

  menuScreen.style.display = "none";

  /* Continue obstacle */

  obstacle.style.animationPlayState = "running";

  /* Show pause button */

  pauseBtn.style.display = "block";

  /* Continue music */

  audio.play().catch(function () {
    console.log("Music could not resume.");
  });
}


document.onkeydown = function (e) {
  /* Don't allow movement when game is not running */

  if (!gameStarted || gamePaused || gameEnded) {
    return;
  }

  /* ================================= */
  /* UP - JUMP */
  /* ================================= */

  if (e.keyCode == 38) {
    dino.classList.remove("animateDino");

    /* Restart jump animation */

    void dino.offsetWidth;

    dino.classList.add("animateDino");

    setTimeout(function () {
      dino.classList.remove("animateDino");
    }, 700);
  }

 
  if (e.keyCode == 39) {
    let dinoX = parseInt(
      window.getComputedStyle(dino, null).getPropertyValue("left"),
    );

    dino.style.left = dinoX + 112 + "px";
  }

  /* ================================= */
  /* LEFT */
  /* ================================= */

  if (e.keyCode == 37) {
    let dinoX = parseInt(
      window.getComputedStyle(dino, null).getPropertyValue("left"),
    );

    dino.style.left = dinoX - 112 + "px";
  }
};


setInterval(function () {
  /* Don't check while game isn't running */

  if (!gameStarted || gamePaused || gameEnded) {
    return;
  }

  let dx = parseInt(
    window.getComputedStyle(dino, null).getPropertyValue("left"),
  );

  let dy = parseInt(
    window.getComputedStyle(dino, null).getPropertyValue("top"),
  );

  let ox = parseInt(
    window.getComputedStyle(obstacle, null).getPropertyValue("left"),
  );

  let oy = parseInt(
    window.getComputedStyle(obstacle, null).getPropertyValue("top"),
  );

  let offsetX = Math.abs(dx - ox);

  let offsetY = Math.abs(dy - oy);



  if (offsetX < 73 && offsetY < 52) {
    endGame();
  } else if (offsetX < 145 && cross) {


    score++;

    updateScore();

    cross = false;

    setTimeout(function () {
      cross = true;
    }, 1000);

    /* Increase difficulty */

    setTimeout(function () {
      if (gameEnded || gamePaused) {
        return;
      }

      let aniDur = parseFloat(
        window
          .getComputedStyle(obstacle, null)
          .getPropertyValue("animation-duration"),
      );

      let newDur = Math.max(1.5, aniDur - 0.1);

      obstacle.style.animationDuration = newDur + "s";
    }, 500);
  }
}, 10);



function endGame() {
  gameEnded = true;

  gameStarted = false;

  /* Stop obstacle */

  obstacle.classList.remove("obstacleAni");

  /* Stop music */

  audio.pause();

  /* Game over sound */

  audiogo.currentTime = 0;

  audiogo.play().catch(function () {
    console.log("Game over sound could not play.");
  });

  /* Change menu */

  menuTitle.innerHTML = "💥 Game Over!";

  menuMessage.innerHTML = "Your final score: " + score;

  /* Hide Start */

  startBtn.style.display = "none";

  /* Hide Resume */

  resumeBtn.style.display = "none";

  /* Show Play Again */

  playAgainBtn.style.display = "block";

  /* Show menu */

  menuScreen.style.display = "flex";

  /* Hide pause */

  pauseBtn.style.display = "none";

  /* Change game title */

  gameOverText.innerHTML = "Game Over";
}



playAgainBtn.addEventListener("click", function () {
  startGame();
});


function updateScore() {
  document.getElementById("scoreCont").innerHTML = "Your Score: " + score;
}
