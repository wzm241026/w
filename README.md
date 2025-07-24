# w
小游戏
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>🌿 森系英文名句打字游戏</title>
    <style>
      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
      }

      body {
        font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
        background: linear-gradient(135deg, #e8f5e9 0%, #c8e6c9 100%);
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 20px;
        color: #2e7d32;
      }

      .container {
        background-color: rgba(255, 255, 255, 0.92);
        border-radius: 20px;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        width: 100%;
        max-width: 800px;
        padding: 30px;
        text-align: center;
        position: relative;
        overflow: hidden;
        border: 1px solid #a5d6a7;
      }

      .container::before {
        content: "";
        position: absolute;
        top: -50px;
        left: -50px;
        width: 200px;
        height: 200px;
        background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="50" cy="50" r="40" fill="%23a5d6a7" opacity="0.3"/></svg>')
          no-repeat;
        background-size: contain;
        z-index: 0;
      }

      .container::after {
        content: "";
        position: absolute;
        bottom: -80px;
        right: -60px;
        width: 250px;
        height: 250px;
        background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><path d="M30,30 Q50,10 70,30 T90,70 Q70,90 50,70 T30,30" fill="%2381c784" opacity="0.2"/></svg>')
          no-repeat;
        background-size: contain;
        z-index: 0;
      }

      h1 {
        color: #2e7d32;
        margin-bottom: 10px;
        font-size: 2.2rem;
        position: relative;
        z-index: 1;
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
      }

      .subtitle {
        color: #4caf50;
        margin-bottom: 25px;
        font-size: 1.1rem;
        position: relative;
        z-index: 1;
      }

      .quote-container {
        background: linear-gradient(to right, #c8e6c9, #a5d6a7);
        border-radius: 15px;
        padding: 25px;
        margin: 20px 0;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        position: relative;
        z-index: 1;
        min-height: 150px;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px solid #81c784;
      }

      .quote {
        font-size: 1.6rem;
        font-style: italic;
        color: #1b5e20;
        line-height: 1.6;
        text-align: center;
        font-weight: 500;
        word-break: break-word;
      }

      .author {
        text-align: right;
        color: #388e3c;
        font-size: 1.1rem;
        margin-top: 15px;
        font-weight: 500;
      }

      .input-container {
        margin: 25px 0;
        position: relative;
        z-index: 1;
      }

      #user-input {
        width: 100%;
        padding: 15px 20px;
        font-size: 1.2rem;
        border: 2px solid #81c784;
        border-radius: 12px;
        outline: none;
        transition: all 0.3s ease;
        background-color: #e8f5e9;
        color: #1b5e20;
      }

      #user-input:focus {
        border-color: #4caf50;
        box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.2);
      }

      .stats {
        display: flex;
        justify-content: space-around;
        margin: 20px 0;
        flex-wrap: wrap;
        position: relative;
        z-index: 1;
      }

      .stat-box {
        background: linear-gradient(to bottom, #a5d6a7, #81c784);
        border-radius: 12px;
        padding: 15px 20px;
        min-width: 130px;
        margin: 8px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        border: 1px solid #66bb6a;
      }

      .stat-value {
        font-size: 1.8rem;
        font-weight: bold;
        color: #1b5e20;
      }

      .stat-label {
        color: #2e7d32;
        font-size: 0.9rem;
        margin-top: 5px;
      }

      .controls {
        margin: 20px 0;
        position: relative;
        z-index: 1;
      }

      button {
        background: linear-gradient(to right, #4caf50, #2e7d32);
        color: white;
        border: none;
        padding: 12px 25px;
        font-size: 1rem;
        border-radius: 50px;
        cursor: pointer;
        transition: all 0.3s ease;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        margin: 0 8px;
        font-weight: 500;
      }

      button:hover {
        transform: translateY(-3px);
        box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
      }

      button:active {
        transform: translateY(1px);
      }

      #next-quote {
        background: linear-gradient(to right, #81c784, #66bb6a);
      }

      #share-btn {
        background: linear-gradient(to right, #29b6f6, #0288d1);
      }

      .instructions {
        background-color: #e8f5e9;
        border-left: 4px solid #4caf50;
        padding: 15px;
        margin: 20px 0;
        text-align: left;
        border-radius: 0 10px 10px 0;
        position: relative;
        z-index: 1;
      }

      .instructions h3 {
        color: #2e7d32;
        margin-bottom: 10px;
      }

      .instructions ul {
        padding-left: 20px;
      }

      .instructions li {
        margin: 8px 0;
        color: #388e3c;
        font-size: 0.95rem;
      }

      .correct {
        color: #2e7d32;
        background-color: rgba(76, 175, 80, 0.2);
      }

      .incorrect {
        color: #d32f2f;
        background-color: rgba(211, 47, 47, 0.2);
      }

      .current {
        border-bottom: 2px solid #ff9800;
      }

      .result-message {
        font-size: 1.2rem;
        font-weight: bold;
        color: #1b5e20;
        margin: 15px 0;
        min-height: 30px;
      }

      .share-section {
        margin-top: 20px;
        padding: 15px;
        background-color: #f1f8e9;
        border-radius: 10px;
        border: 1px dashed #81c784;
      }

      .share-section h3 {
        color: #2e7d32;
        margin-bottom: 10px;
      }

      .share-buttons {
        display: flex;
        justify-content: center;
        gap: 10px;
        flex-wrap: wrap;
        margin-top: 15px;
      }

      .share-btn {
        padding: 8px 15px;
        font-size: 0.9rem;
      }

      .copy-section {
        margin-top: 15px;
        display: flex;
        gap: 10px;
      }

      #share-link {
        flex: 1;
        padding: 10px;
        border: 1px solid #81c784;
        border-radius: 8px;
        background: #e8f5e9;
        color: #2e7d32;
      }

      @media (max-width: 600px) {
        .container {
          padding: 20px 15px;
        }

        h1 {
          font-size: 1.8rem;
        }

        .quote {
          font-size: 1.3rem;
        }

        .stat-box {
          padding: 10px 15px;
          min-width: 110px;
        }

        .stat-value {
          font-size: 1.5rem;
        }

        button {
          padding: 10px 20px;
          font-size: 0.9rem;
          margin: 5px;
        }

        .copy-section {
          flex-direction: column;
        }
      }
    </style>
  </head>
  <body>
    <div class="container">
      <h1>🌿 森系英文名句打字游戏</h1>
      <p class="subtitle">在自然的氛围中提升您的英文打字速度</p>

      <div class="quote-container">
        <div>
          <p class="quote" id="quote">Loading...</p>
          <p class="author" id="author"></p>
        </div>
      </div>

      <div class="result-message" id="result-message"></div>

      <div class="input-container">
        <input
          type="text"
          id="user-input"
          placeholder="开始输入句子..."
          autocomplete="off"
        />
      </div>

      <div class="stats">
        <div class="stat-box">
          <div class="stat-value" id="wpm">0</div>
          <div class="stat-label">WPM</div>
        </div>
        <div class="stat-box">
          <div class="stat-value" id="accuracy">100%</div>
          <div class="stat-label">准确率</div>
        </div>
        <div class="stat-box">
          <div class="stat-value" id="time">0s</div>
          <div class="stat-label">用时</div>
        </div>
      </div>

      <div class="controls">
        <button id="start-btn">开始游戏</button>
        <button id="next-quote">下一句</button>
        <button id="reset-btn">重置</button>
      </div>

      <div class="instructions">
        <h3>游戏说明：</h3>
        <ul>
          <li>点击"开始游戏"按钮开始计时</li>
          <li>在输入框中输入显示的英文句子</li>
          <li>准确率和打字速度会实时显示</li>
          <li>完成一句后点击"下一句"继续挑战</li>
          <li>绿色表示正确输入，红色表示错误</li>
        </ul>
      </div>

      <div class="share-section">
        <h3>分享给朋友一起玩 🌟</h3>
        <p>邀请朋友一起来挑战打字速度吧！</p>

        <div class="copy-section">
          <input
            type="text"
            id="share-link"
            value="https://typing-game.example.com"
            readonly
          />
          <button id="copy-link">复制链接</button>
        </div>

        <div class="share-buttons">
          <button class="share-btn" id="share-weibo">分享到微博</button>
          <button class="share-btn" id="share-qq">分享到QQ</button>
          <button class="share-btn" id="share-wechat">分享到微信</button>
        </div>
      </div>
    </div>

    <script>
      // 英文名句数据库
      const quotes = [
        {
          text: "The best time to plant a tree was 20 years ago. The second best time is now.",
          author: "Chinese Proverb",
        },
        {
          text: "In the middle of difficulty lies opportunity.",
          author: "Albert Einstein",
        },
        {
          text: "The only way to do great work is to love what you do.",
          author: "Steve Jobs",
        },
        {
          text: "Life is what happens to you while you're busy making other plans.",
          author: "John Lennon",
        },
        {
          text: "The future belongs to those who believe in the beauty of their dreams.",
          author: "Eleanor Roosevelt",
        },
        {
          text: "It is during our darkest moments that we must focus to see the light.",
          author: "Aristotle",
        },
        {
          text: "The only impossible journey is the one you never begin.",
          author: "Tony Robbins",
        },
        {
          text: "Success is not final, failure is not fatal: it is the courage to continue that counts.",
          author: "Winston Churchill",
        },
        {
          text: "The way to get started is to quit talking and begin doing.",
          author: "Walt Disney",
        },
        {
          text: "The greatest glory in living lies not in never falling, but in rising every time we fall.",
          author: "Nelson Mandela",
        },
        {
          text: "The secret of getting ahead is getting started.",
          author: "Mark Twain",
        },
        {
          text: "It always seems impossible until it's done.",
          author: "Nelson Mandela",
        },
        {
          text: "The only limit to our realization of tomorrow is our doubts of today.",
          author: "Franklin D. Roosevelt",
        },
        {
          text: "Do not go where the path may lead, go instead where there is no path and leave a trail.",
          author: "Ralph Waldo Emerson",
        },
        {
          text: "The future belongs to those who prepare for it today.",
          author: "Malcolm X",
        },
      ];

      // DOM元素
      const quoteElement = document.getElementById("quote");
      const authorElement = document.getElementById("author");
      const userInput = document.getElementById("user-input");
      const wpmElement = document.getElementById("wpm");
      const accuracyElement = document.getElementById("accuracy");
      const timeElement = document.getElementById("time");
      const startBtn = document.getElementById("start-btn");
      const nextBtn = document.getElementById("next-quote");
      const resetBtn = document.getElementById("reset-btn");
      const resultMessage = document.getElementById("result-message");
      const shareWeiboBtn = document.getElementById("share-weibo");
      const shareQQBtn = document.getElementById("share-qq");
      const shareWechatBtn = document.getElementById("share-wechat");
      const copyLinkBtn = document.getElementById("copy-link");
      const shareLinkInput = document.getElementById("share-link");

      // 游戏状态变量
      let currentQuote = {};
      let startTime;
      let timer;
      let timeElapsed = 0;
      let gameActive = false;
      let totalCharacters = 0;
      let correctCharacters = 0;

      // 初始化游戏
      function initGame() {
        getRandomQuote();
        userInput.value = "";
        userInput.disabled = false;
        userInput.focus();
        resetStats();
        resultMessage.textContent = "";
      }

      // 获取随机名句
      function getRandomQuote() {
        const randomIndex = Math.floor(Math.random() * quotes.length);
        currentQuote = quotes[randomIndex];
        quoteElement.textContent = currentQuote.text;
        authorElement.textContent = `- ${currentQuote.author}`;
      }

      // 重置统计数据
      function resetStats() {
        wpmElement.textContent = "0";
        accuracyElement.textContent = "100%";
        timeElement.textContent = "0s";
        timeElapsed = 0;
        totalCharacters = 0;
        correctCharacters = 0;
        clearInterval(timer);
      }

      // 开始计时
      function startTimer() {
        if (gameActive) return;

        gameActive = true;
        startTime = new Date();
        timer = setInterval(() => {
          timeElapsed = Math.floor((new Date() - startTime) / 1000);
          timeElement.textContent = `${timeElapsed}s`;
          updateStats();
        }, 1000);
      }

      // 更新统计数据
      function updateStats() {
        // 计算WPM (每分钟单词数)
        const minutes = timeElapsed / 60;
        const words = totalCharacters / 5; // 英文标准：5个字符为一个单词
        const wpm = minutes > 0 ? Math.round(words / minutes) : 0;
        wpmElement.textContent = wpm;

        // 计算准确率
        const accuracy =
          totalCharacters > 0
            ? Math.round((correctCharacters / totalCharacters) * 100)
            : 100;
        accuracyElement.textContent = `${accuracy}%`;
      }

      // 检查输入
      function checkInput() {
        if (!gameActive) return;

        const currentInput = userInput.value;
        const quoteText = currentQuote.text;

        totalCharacters = currentInput.length;
        correctCharacters = 0;

        // 高亮显示正确和错误的字符
        let highlightedText = "";
        for (let i = 0; i < quoteText.length; i++) {
          const char = quoteText[i];
          const inputChar = currentInput[i];

          if (i < currentInput.length) {
            if (inputChar === char) {
              highlightedText += `<span class="correct">${char}</span>`;
              correctCharacters++;
            } else {
              highlightedText += `<span class="incorrect">${char}</span>`;
            }
          } else {
            if (i === currentInput.length) {
              highlightedText += `<span class="current">${char}</span>`;
            } else {
              highlightedText += char;
            }
          }
        }

        quoteElement.innerHTML = highlightedText;

        // 更新统计
        updateStats();

        // 检查是否完成
        if (currentInput === quoteText) {
          finishGame();
        }
      }

      // 完成游戏
      function finishGame() {
        clearInterval(timer);
        gameActive = false;
        userInput.disabled = true;

        // 计算最终成绩
        const finalWPM = wpmElement.textContent;
        const finalAccuracy = accuracyElement.textContent;

        // 显示完成信息
        resultMessage.textContent = `🎉 恭喜完成！用时${timeElapsed}秒，速度${finalWPM}WPM，准确率${finalAccuracy}`;

        // 自动滚动到结果
        resultMessage.scrollIntoView({ behavior: "smooth", block: "center" });
      }

      // 分享功能
      function shareToWeibo() {
        const url = window.location.href;
        const text = `我在玩森系英文名句打字游戏，挑战你的打字速度！`;
        const shareUrl = `https://service.weibo.com/share/share.php?url=${encodeURIComponent(
          url
        )}&title=${encodeURIComponent(text)}`;
        window.open(shareUrl, "_blank", "width=600,height=400");
      }

      function shareToQQ() {
        const url = window.location.href;
        const title = "森系英文名句打字游戏";
        const summary = "在自然的氛围中提升英文打字速度，快来挑战吧！";
        const shareUrl = `https://connect.qq.com/widget/shareqq/index.html?url=${encodeURIComponent(
          url
        )}&title=${encodeURIComponent(title)}&summary=${encodeURIComponent(
          summary
        )}`;
        window.open(shareUrl, "_blank", "width=700,height=500");
      }

      function shareToWechat() {
        alert("请在微信中打开此链接进行分享，或截图二维码分享给朋友");
      }

      function copyLink() {
        const url = window.location.href;
        navigator.clipboard
          .writeText(url)
          .then(() => {
            copyLinkBtn.textContent = "已复制!";
            setTimeout(() => {
              copyLinkBtn.textContent = "复制链接";
            }, 2000);
          })
          .catch((err) => {
            console.error("复制失败:", err);
            // 备用方法
            const textArea = document.createElement("textarea");
            textArea.value = url;
            document.body.appendChild(textArea);
            textArea.select();
            document.execCommand("copy");
            document.body.removeChild(textArea);
            copyLinkBtn.textContent = "已复制!";
            setTimeout(() => {
              copyLinkBtn.textContent = "复制链接";
            }, 2000);
          });
      }

      // 事件监听器
      startBtn.addEventListener("click", startTimer);

      nextBtn.addEventListener("click", () => {
        initGame();
        gameActive = false;
        clearInterval(timer);
      });

      resetBtn.addEventListener("click", () => {
        initGame();
        gameActive = false;
        clearInterval(timer);
      });

      userInput.addEventListener("input", checkInput);

      // 分享按钮事件
      shareWeiboBtn.addEventListener("click", shareToWeibo);
      shareQQBtn.addEventListener("click", shareToQQ);
      shareWechatBtn.addEventListener("click", shareToWechat);
      copyLinkBtn.addEventListener("click", copyLink);

      // 设置分享链接
      window.onload = function () {
        shareLinkInput.value = window.location.href;
        initGame();
      };
    </script>
  </body>
</html>
