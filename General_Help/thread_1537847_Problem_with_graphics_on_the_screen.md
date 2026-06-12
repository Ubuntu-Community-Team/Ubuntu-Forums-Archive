---
title: "Problem with graphics on the screen"
date: 2010-07-24
forum: General Help
---

### Post by saeidfarahi on 2010-07-24
Hi everybody,
I'm using karmic ( ubuntu 9.04 ). When I open a graphical program ( this has happened to me with crack-attack game and a program which is run form the terminal and has got a picture as background ) then seeing the things inside the window is really hard because the background is switching between its real graphical objects and the windows behind that window. I use the ATI graphic card and its driver is installed. can anyone give me any idea to how to solve this problem?!!!!!!!!:(

---

### Post by agnes on 2010-07-24
You likely have a problem with OpenGL, crack-attack uses OpenGL. Does the program 'glxgears' display ok? If not it's an OpenGL problem. There are various threads on the forums about OpenGL + ATI. Which is where I suggest to look.
Some classic solutions are, to install the proprietary driver if you have the opensource one, or a newer version (via envyng-qt is easiest); turning off Compiz; or reconfiguring the X server by typing "sudo dpkg-reconfigure -phigh xserver-xorg".

---

