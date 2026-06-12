---
title: "GLXGears Question?"
date: 2010-09-10
forum: General Help
---

### Post by cottfcfan on 2010-09-10
I'm using a Radeon hd2400 G/C with the Radeon open source drivers.
Running Glxgears from a terminal in full screen, I get 300 fp/5seconds on Lucid & only 200 fp/5 seconds on Maverick.
I know Maverick is still in beta but I was hoping for an improvement.
Does this mean the open source drivers are regressing?
and how accurate is GLX Gears?


ps the readings were taken with compiz & effects on.

---

### Post by NoBugs! on 2010-09-10
GLXgears is not a benchmark, it shows that opengl is working though.
You can see if it's using the graphics acceleration by typing "glxinfo", and looking for the "direct rendering: Yes" line near the top.

---

### Post by cottfcfan on 2010-09-11
Nobugs..
Thanks for your reply.
Direct Rendering is being used. So you saying I shouldn't bother about the figure it gives me?

---

### Post by kelvin spratt on 2010-09-11
It only gives you a rough guide that all is workin this is mine windowed
17957 frames in 5.0 seconds = 3591.342 FPS
17266 frames in 5.0 seconds = 3452.035 FPS
this is mine full screen
1288 frames in 5.0 seconds = 257.343 FPS
1288 frames in 5.0 seconds = 257.452 FPS
1158 frames in 5.0 seconds = 231.586 FPS
1041 frames in 5.0 seconds = 208.153 FPS
Note this is using a Nvidia card with compiz 
and a few apps running

---

