<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Expense Tracker</title>
  <style>
    body {
      font-family: Arial, sans-serif;
    }

    #expense-list {
      list-style-type: none;
      padding: 0;
    }

    li {
      margin-bottom: 10px;
    }

    button {
      margin-top: 10px;
    }
  </style>
</head>
<body>

  <ul id="expense-list">
    <!-- Expenses will be dynamically added here -->
  </ul>

  <button id="add-expense-btn">Add Expense</button>
  <button id="delete-expense-btn">Delete Expense</button>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      var expenseList = document.getElementById('expense-list');
      var addExpenseBtn = document.getElementById('add-expense-btn');
      var deleteExpenseBtn = document.getElementById('delete-expense-btn');

      function addExpense() {
        var expenseName = prompt('Enter expense name:');
        var expenseAmount = parseFloat(prompt('Enter expense amount: $'));

        if (!isNaN(expenseAmount)) {
          var li = document.createElement('li');
          li.textContent = `${expenseName} - $${expenseAmount.toFixed(2)}`;
          expenseList.appendChild(li);
        } else {
          alert('Invalid amount. Please enter a valid number.');
        }
      }

      function deleteExpense() {
        var expenseIdToDelete = prompt('Enter expense ID to delete:');
        var expenseElement = document.querySelector(`[data-expense-id="${expenseIdToDelete}"]`);

        if (expenseElement) {
          expenseElement.remove();
        } else {
          alert('Expense not found. Please enter a valid ID.');
        }
      }

      addExpenseBtn.addEventListener('click', addExpense);
      deleteExpenseBtn.addEventListener('click', deleteExpense);
    });
  </script>
</body>
</html>
