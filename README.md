# Inde.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Student Attendance</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f9f9f9;
      padding: 20px;
    }
    h2 {
      text-align: center;
      margin-bottom: 20px;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      background: white;
      box-shadow: 0 2px 6px rgba(0,0,0,0.2);
    }
    th, td {
      padding: 10px;
      border: 1px solid #ddd;
      text-align: left;
    }
    th {
      background: #007bff;
      color: white;
    }
    tr:nth-child(even) {
      background: #f2f2f2;
    }
    .submit-btn {
      margin-top: 20px;
      display: block;
      padding: 10px 20px;
      background: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    .submit-btn:hover {
      background: #0056b3;
    }
    #result {
      margin-top: 20px;
      padding: 15px;
      background: #e9ffe9;
      border: 1px solid #a6d8a6;
      border-radius: 5px;
    }
  </style>
</head>
<body>

  <h2>Student Attendance Sheet</h2>

  <form id="attendanceForm">
    <table>
      <tr>
        <th>Sl. No.</th>
        <th>Registration No.</th>
        <th>Student Name</th>
        <th>Present</th>
      </tr>

      <!-- Rows will be injected here by JavaScript -->
    </table>

    <button type="submit" class="submit-btn">Submit Attendance</button>
  </form>

  <div id="result"></div>

  <script>
    const students = [
      "KRUTIDEEPA PANI","KUMAR SABYASACHI","KUMKUM MANDAL","LAXMIDHAR BIRUA","LOPAMUDRA MOHANTY",
      "M. CHANDRASEKHAR RAO","MADHABANANDA PATRA","MADHUSMITA ROUT","MAMATA SAHOO","MANJIT SAHOO",
      "MANMATH SAHOO","MANYAJEET BEHERA","MRUTYUNJAYA BEHERA","NIGAMANANDA SAHU","NITEESH BEHERA",
      "OM PRAKASH BEHERA","OM SAI RUDRAPRATAP PRUSTY","OMM NARAYAN DAS","OMM PRAKASH PATTANAIK",
      "OMM SIBANANDA DIXIT","PIYUSH KUMAR","PRAJUKTA BEHERA","PRAKASH NAYAK","PRATAP KUMAR PARIDA",
      "PRATYUSH SAHOO","PRATYUSHA SAHOO","PRIYAMBADA MALLICK","PRIYANKA DAS","PRIYANKA MAHALI",
      "PRIYANKA SAHANI","PRIYA RANJAN DAS","PULLAKITA MOHARANA","QAUSEEN AHMAD","RAKESH KUMAR SAHOO",
      "RATI RANJAN PANDA","REHENUMA PARWEEN","RUDRA PRASAD ROUT","SAGARIKA PATTANAIK","SAI KRISHNA DAS",
      "SAILESH MOHANTY","SALIN MOHAPATRA","SAMARJIT BADU","SANKALPA PUHAN","SANTOSH KUMAR BHAL",
      "SANTRUPTA JENA","SARADA PRASAD ROUT","SATYAJIT BEHERA","SATYAM MOHAPATRA","SAYED MAQSOOD ALI",
      "SAYED UMAIR ALI","SHAGUN SHREE MULIA","SHASWAT BEHERA","SHREYA KARMAKAR","SIPUN KUMAR MOHANTA"
    ];

    const table = document.querySelector("table");

    // Generate rows dynamically
    students.forEach((name, index) => {
      const row = document.createElement("tr");
      const regNo = 2401206074 + index;

      row.innerHTML = `
        <td>${index + 1}</td>
        <td>${regNo}</td>
        <td>${name}</td>
        <td><input type="checkbox" name="attendance" value="${name}"></td>
      `;

      table.appendChild(row);
    });

    // Handle form submission
    document.getElementById("attendanceForm").addEventListener("submit", function(event) {
      event.preventDefault();

      const checked = document.querySelectorAll('input[name="attendance"]:checked');
      const presentCount = checked.length;
      const presentNames = Array.from(checked).map(cb => cb.value);

      document.getElementById("result").innerHTML = `
        <h3>Total Present: ${presentCount}</h3>
        <p><strong>Present Students:</strong><br>${presentNames.join(", ")}</p>
      `;
    });
  </script>

</body>
</html>
