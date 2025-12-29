<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>待辦清單 To-Do List</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f4f8;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      min-height: 100vh;
      padding: 50px 20px;
    }
    .container {
      background-color: #fff;
      padding: 20px 30px;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      width: 100%;
      max-width: 400px;
    }
    h1 {
      text-align: center;
      color: #333;
    }
    input[type="text"] {
      width: 100%;
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
      font-size: 16px;
    }
    button {
      padding: 10px 15px;
      border: none;
      border-radius: 5px;
      background-color: #4CAF50;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background-color: #45a049;
    }
    ul {
      list-style-type: none;
      padding-left: 0;
    }
    li {
      background-color: #f9f9f9;
      margin-bottom: 8px;
      padding: 10px;
      border-radius: 5px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    li.completed {
      text-decoration: line-through;
      color: #888;
    }
    .delete-btn {
      background-color: #f44336;
      padding: 5px 10px;
      border-radius: 5px;
      color: white;
      cursor: pointer;
      font-size: 14px;
    }
    .delete-btn:hover {
      background-color: #d32f2f;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>待辦清單</h1>
    <input type="text" id="taskInput" placeholder="輸入待辦事項">
    <button onclick="addTask()">新增</button>
    <ul id="taskList"></ul>
  </div>

  <script>
    const taskInput = document.getElementById('taskInput');
    const taskList = document.getElementById('taskList');

    function addTask() {
      const taskText = taskInput.value.trim();
      if (taskText === "") return;

      const li = document.createElement('li');
      li.textContent = taskText;

      li.addEventListener('click', () => {
        li.classList.toggle('completed');
      });

      const deleteBtn = document.createElement('span');
      deleteBtn.textContent = "刪除";
      deleteBtn.className = "delete-btn";
      deleteBtn.addEventListener('click', (e) => {
        e.stopPropagation();
        li.remove();
      });

      li.appendChild(deleteBtn);
      taskList.appendChild(li);

      taskInput.value = "";
    }

    // 支援按 Enter 新增
    taskInput.addEventListener('keypress', (e) => {
      if (e.key === 'Enter') {
        addTask();
      }
    });
  </script>
</body>
</html>
