---
title: "Commands help"
date: 2010-03-11
forum: General Help
---

### Post by yomnym on 2010-03-11
Hello, im having some trouble with adding some startup applications and shortcut keys due to my lack of command knowledge.  I was trying to make cairo dock auto start but i by using ```
cairo-dock
``` but the i get a dialog box asking me whether to run or not Open GL.  I wanted to avoid this, just run the dock.
The other issue is, i was trying to create a keyboard shortcut to reboot the pc, i added the shortcut with the command ```
sudo reboot
```, this worked for a while but now it has no effect what so ever, if i run Terminal and enter the command, i get asked for the root password?  What am i doing wrong, thanks a lot for any advise you could offer.

---

### Post by undecim on 2010-03-11
use "cairo-dock -c" to use the cairo backend and "cairo-dock -o" to use the opengl backend

for shutdown, go to a terminal and run "sudo visudo" then add this line to the end of the file:
```
%admin ALL=NOPASSWD: /sbin/poweroff, /sbin/reboot, /sbin/shutdown
```
that will let anyone with admin privileges shut down or reboot the computer without a password.

---

### Post by yomnym on 2010-03-11
Thanks for your help
So to run cairo then i just add to the startup apps both of those commands cairo-dock -c and then another startup with the command cairo-dock -o?
 
Does the code to remove password authentication work for reboot, shutdown?

---

### Post by undecim on 2010-03-11
For cairo, you just need to use one command, depending on wether you want opengl or cairo to do all the graphic work. -c means cairo and -o means opengl.

The line I gave you for visudo will let youuse the poweroff, reboot, and shutdown commands without a password.

---

### Post by yomnym on 2010-03-11
Thanks for the clarification, what i want to achive with the cairo command is to open the Dock when i start the pc, which one would i have to add to the application starup to accomplish this?  The problem that i had before was that i entere the cairo-dock command to the app startup and that opened the Dock fine, but then i get a pop up asking me if i wanted to run Open GL, i wanted to avoid this and just run the Dock on startup.  I appreciate your support.

---

### Post by m_duck on 2010-03-11
As undecim mentioned, which command you use just depends on which backend you want to do the graphical legwork - using the ***-o*** switch tells cairo-dock to use OpenGL which the ***-c*** switch tells cairo to do it itself. Basically, use whichever one works. [This link]("https://help.ubuntu.com/community/CairoDock") on the wiki suggests that if you are using an ATI or Intel graphics card on Karmic, it may be better to use ***cairo-dock -c*** and presumably ***cairo-dock -o*** otherwise.

Short version: it seems to me that ***cairo-dock -o*** is probably better as it will utilise your graphics card more rather than all on the CPU, and if that doesn't work, use ***cairo-dock -c***.

---

### Post by yomnym on 2010-03-11
thanks guys, i'll try this later on.  I just hope it opens and i dont get that dialog box asking me to run GL.

---

### Post by yomnym on 2010-03-11
Ok the command that enabled me to reboot or shutdown using a shortcut key seems to work just fine.  Just had to find out how to safe my changes once in the sudo visudo file.
The Cairo dock opening that still isn't working with the startup application that i created.  Maybe im doing this wrong but i simply went to System>Preferences>Startup Applications then added a new startup app using the commands either ```
cairo-dock -o
```  or ```
cairo-dock -c
```.  Neither of these allow me to auto start the dock without clicking yes on this annoying little pop up at the beginning of my session.

Well guys i just realized that by right clicking on the dock then >Cairo-Dock>start dock on startup, does what I've been asking for.  Funny enough it adds the same start application with the same cairo-dock -o command you guys were telling me.  Oh well thanks a lot for your help.

---

