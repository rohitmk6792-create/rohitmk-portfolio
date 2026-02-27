Skip to content
rohitmk6792-create
rohitmk-portfolio
Repository navigation
Code
Issues
Pull requests
Actions
Projects
Wiki
Security
Insights
Settings
Commit 7c7b2ef
rohitmk6792-create
rohitmk6792-create
authored
14 minutes ago
·
·
Verified
Update index.html
main
1 parent 
2a40e8d
 commit 
7c7b2ef
File tree
Filter files…
index.html
1 file changed
+9
-122
lines changed
Search within code
 
‎index.html‎
+9
-122
Lines changed: 9 additions & 122 deletions
Original file line number	Diff line number	Diff line change
@@ -88,11 +88,6 @@
color:#38bdf8;
}

.hero p{
margin-top:20px;
max-width:600px;
}
.btn{
margin-top:25px;
display:inline-block;
@@ -111,40 +106,6 @@
transform:scale(1.05);
}

.skills-container{
display:flex;
flex-wrap:wrap;
justify-content:center;
gap:15px;
}
.skill{
padding:10px 20px;
background:rgba(255,255,255,0.1);
border-radius:20px;
backdrop-filter:blur(5px);
}
.projects{
display:flex;
flex-wrap:wrap;
gap:20px;
justify-content:center;
}
.project{
width:280px;
padding:20px;
border-radius:15px;
background:rgba(255,255,255,0.05);
backdrop-filter:blur(8px);
transition:0.3s;
}
.project:hover{
transform:translateY(-10px);
}
form{
max-width:500px;
margin:auto;
@@ -164,17 +125,6 @@
padding:20px;
background:rgba(255,255,255,0.05);
}
.hidden{
opacity:0;
transform:translateY(30px);
transition:all 0.6s;
}
.show{
opacity:1;
transform:translateY(0);
}
</style>
</head>

@@ -184,60 +134,17 @@
<div><strong>Rohit MK</strong></div>
<nav>
<a href="#home">Home</a>
<a href="#about">About</a>
<a href="#skills">Skills</a>
<a href="#projects">Projects</a>
<a href="#contact">Contact</a>
<button class="toggle-btn" onclick="toggleMode()">Toggle</button>
</nav>
</header>

<section class="hero" id="home">
<h1>Hello, I'm <span>Rohit MK</span></h1>
<h2><span id="typing"></span></h2>
<p>Cloud Computing student passionate about AWS, DevOps and scalable cloud architecture.</p>
<a href="resume.pdf" class="btn" download>Download Resume</a>
</section>
<section id="about" class="hidden">
<h2>About Me</h2>
<p style="text-align:center;max-width:700px;margin:auto;">
I specialize in cloud infrastructure, containerization, networking and DevOps practices.
</p>
</section>
<section id="skills" class="hidden">
<h2>Technical Skills</h2>
<div class="skills-container">
<div class="skill">AWS</div>
<div class="skill">Azure</div>
<div class="skill">Docker</div>
<div class="skill">Linux</div>
<div class="skill">Kubernetes</div>
<div class="skill">Networking</div>
<div class="skill">DevOps</div>
</div>
</section>
<section id="projects" class="hidden">
<h2>Projects</h2>
<div class="projects">
<div class="project">
<h3>Cloud Deployment</h3>
<p>Deployed scalable application using AWS EC2 & S3.</p>
</div>
<div class="project">
<h3>Dockerized App</h3>
<p>Containerized full stack app using Docker.</p>
</div>
<div class="project">
<h3>CI/CD Pipeline</h3>
<p>Implemented CI/CD using GitHub Actions.</p>
</div>
</div>
</section>

<section id="contact" class="hidden">
<section id="contact">
<h2>Contact Me</h2>
<form id="contact-form">
<input type="text" id="name" placeholder="Your Name" required>
@@ -249,61 +156,41 @@ <h2>Contact Me</h2>
</section>

<footer>
© 2026 Rohit MK | Cloud Computing Student
© 2026 Rohit MK
</footer>

<script>
const text = "Cloud Computing Student";
let i = 0;
function typing(){
if(i < text.length){
document.getElementById("typing").innerHTML += text.charAt(i);
i++;
setTimeout(typing,100);
}
}
typing();

function toggleMode(){
document.body.classList.toggle("light");
}

const observer = new IntersectionObserver(entries=>{
entries.forEach(entry=>{
if(entry.isIntersecting){
entry.target.classList.add("show");
}
});
});
document.querySelectorAll(".hidden").forEach(el=>{
observer.observe(el);
});
/* SUPABASE CONFIG */
const supabaseUrl = "YOUR_SUPABASE_URL";
const supabaseKey = "YOUR_SUPABASE_ANON_KEY";
const supabase = window.supabase.createClient(supabaseUrl, supabaseKey);

/* FORM SUBMIT */
document.getElementById("contact-form").addEventListener("submit", async function(e){
e.preventDefault();

const name = document.getElementById("name").value;
const email = document.getElementById("email").value;
const message = document.getElementById("message").value;

const { error } = await supabase
const { data, error } = await supabase
.from("contact_messages")
.insert([{ name, email, message }]);

if(error){
document.getElementById("msg").innerHTML="Error sending message.";
console.log(error);
}else{
document.getElementById("msg").innerHTML="Message stored successfully!";
document.getElementById("msg").innerHTML = "❌ Failed to send message.";
console.error("Supabase Error:", error.message);
} else {
document.getElementById("msg").innerHTML = "✅ Message sent successfully!";
document.getElementById("contact-form").reset();
}
});
</script>

</body>
0 commit comments
Comments
0
 (0)
Comment
You're not receiving notifications from this thread.


