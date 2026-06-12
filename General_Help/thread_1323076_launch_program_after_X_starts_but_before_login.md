---
title: "launch program after X starts but before login"
date: 2009-11-11
forum: General Help
---

### Post by tramir on 2009-11-11
I have a notebook that I dock when at the office. I have a script that checks if the notebook is docked and if so enables the external monitor and disables the notebook screen. I added the script to the list of start-up applications and it works perfectly fine if I start the computer after a shutdown, but not if I wake it up after hibernation -- in that case, the script never gets run, since I'm restoring an already-started session (not to mention that I have to open the display in order to login).

So what I'm wondering is: is there any way to run this script when X starts, but before the login screen (gdm?)? Especially when waking up from hibernation. I tried putting it in /etc/X11/xinitrc or in /etc/X11/Xsession, but neither worked (actually, nothing I put in those two was run at all). Any suggestions are welcome and warmly appreciated :)

---

### Post by Sin@Sin-Sacrifice on 2009-11-11
[http://ubuntuforums.org/showthread.php?t=345614](http://ubuntuforums.org/showthread.php?t=345614) hope this helps

---

