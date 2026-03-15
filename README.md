class attendance 
<!DOCTYPE html>
<html>
<head>
<title>Student Attendance</title>
</head>

<body>

<h2>Class Attendance</h2>

<input id="name" placeholder="Student Name"><br><br>

<input id="roll" placeholder="Roll Number"><br><br>

<input id="topic" placeholder="Topic taught today"><br><br>

<button onclick="mark()">Mark Present</button>

<p id="msg"></p>

<script>

let todayTopic = localStorage.getItem("todayTopic");

let today = new Date().toDateString();

let data = JSON.parse(localStorage.getItem("attendance")) || {};

function mark(){

let name = document.getElementById("name").value;
let roll = document.getElementById("roll").value;
let topic = document.getElementById("topic").value.toLowerCase();

let key = roll + "_" + today;

if(topic !== todayTopic){
document.getElementById("msg").innerText = "Wrong topic!";
return;
}

if(data[key]){
document.getElementById("msg").innerText = "Attendance already marked today!";
return;
}

data[key] = {
name:name,
roll:roll
};

localStorage.setItem("attendance", JSON.stringify(data));

document.getElementById("msg").innerText = "Attendance recorded";

}

</script>

</body>
</html>
