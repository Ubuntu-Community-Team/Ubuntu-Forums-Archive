---
title: "Severe lag for all 3-d video games (video driver issue?)"
date: 2011-08-06
forum: General Help
---

### Post by MetalMASK on 2011-08-06
Hi All,

I am running gnome 3 on ubuntu 11.04, a clean installation from the gNatty version, 32 bit. The machine is a Lenovo t420, with 6GB RAM and a integrated video card.

Everything is running smoothly but not for games. I tried urban terror, Tremulous, Nexuiz, all of the lags from the very beginning as if I was using a machine 5 years ago to run today's video games (ie, takes 10 seconds for a mouse move a show, audio lags, .etc). From my experience it should come from video card driver not installed, but the update manager shows all device works fine (indeed, the screen resolution is 1600X900).

Anyone has advice on how to solve this?

---

### Post by MetalMASK on 2011-08-06
I have installed the "better intel HD3000 driver" from this post: [http://ubuntuforums.org/showthread.php?t=1752993&highlight=lenovo+t420](http://ubuntuforums.org/showthread.php?t=1752993&highlight=lenovo+t420)

however the issue is still there. all 3d game are non-playable.

also "the board" will not load from the application.

I really do like gnome 3 (tried unity before, much much prefer gnome 3), it would be a bummer if this issue cannot be solved.....

---

### Post by pqwoerituytrueiwoq on 2011-08-06
```
glxinfo | grep OpenGL
```lets see if the card/chip has the opengl needed to play the game

---

### Post by MetalMASK on 2011-08-06
Thanks for the reply

the output is:

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.12-devel (git-0aed27e natty-oibaf-ppa+pp-branch)
OpenGL shading language version string: 1.20
OpenGL extensions:

---

### Post by maxar6 on 2011-08-06
3D is really tough on memory aka processor. How big is your memory that might be the problem for 3D you might want at lest 3gb.

---

### Post by pqwoerituytrueiwoq on 2011-08-06
super tux cart runs good here my gpu has 1gb memory but it has a little power :lolflag:

---

### Post by maxar6 on 2011-08-06
Open up the game and then go to System > Administration > Sytem Moniter and tell me how much memory it is using. If over 1 gb things really start to get ify.

---

### Post by MetalMASK on 2011-08-06
> **maxar6 said:**
> 3D is really tough on memory aka processor. How big is your memory that might be the problem for 3D you might want at lest 3gb.

as stated in OP, the machine has 6GB ram

---

### Post by MetalMASK on 2011-08-06
before start game: memory usage: 670MB
after start game: memory usage around 740 MB
CPU usage start to hike to 60%, sometimes even over 80%. normal usage was below 20%.

edit: shows Memory has 5.8 GiB, does that mean only 0.2 Gb was allocated to video? how to change this (to a larger size)?

---

### Post by pqwoerituytrueiwoq on 2011-08-06
he wants to know how much video ram you have but does not seem to realize (based on the wording used or it could be cause English is not his/her first language) that there is a difference in ram and video ram a chip only allows so much to be shared
if you look at how much ram you have under the system monitor and compare it to the 6gb you have installed the difference is going to video memory

---

### Post by MetalMASK on 2011-08-06
thanks for the clarification. from the System Monitor, under Resources, Memory and Swap history, it shows the memory has 5.8 GB.

---

### Post by MetalMASK on 2011-08-07
I should clarify that after installing the new driver, Nexuiz is playable (still lags for about a second once a minute or so) but not for urban terror and tremulous

---

