---
title: "How to exit misbehaving full screen game?"
date: 2011-07-12
forum: General Help
---

### Post by apoorvumang on 2011-07-12
It happens often with me that I'm playing a game (fullscreen) and change some video settings, and the game hangs. I always have to power off the computer and restart.
 
Is there any way to just exit that program, like in windows, one can open the task manager and end the process?

---

### Post by Bucky Ball on 2011-07-12
I used to use 'Force Quit' applet in Gnome but you probably can't get to the toolbar in your predicament.

You could try 'Alt-F2' and type in 'killall 'name-of-game'', meaning, if the name of the game is lobsters then you would type 'killall lobsters'. 

You generally use whatever kicks the game off from a terminal. If typing 'lobsters' in a terminal starts the game, then that's what you'd use to kill it, too.

Hope that makes sense!

---

### Post by Wim Sturkenboom on 2011-07-12
That depends on ;)

If you still can open a console (e.g. <ctrl><alt><F1>), you can login and kill the game in it. Next switch back with <alt><F7> (sometimes <alt><F8>). Try this first while the game does not hang so you know what to expect.

If not, you can restart the X-server with the key combination <ctrl><alt><printscreen>K (if I remembered the combination correctly)

---

### Post by philinux on 2011-07-12
> **Bucky Ball said:**
> I used to use 'Force Quit' applet in Gnome but you probably can't get to the toolbar in your predicament.

You could try 'Alt-F2' and type in 'killall 'name-of-game'', meaning, if the name of the game is lobsters then you would type 'killall lobsters'. 

You generally use whatever kicks the game off from a terminal. If typing 'lobsters' in a terminal starts the game, then that's what you'd use to kill it, too.

Hope that makes sense!

If that doesn't work hold down Alt + PrtScr/Sysrq and hit k. That will kill x and take you to the login screen. Much better than a hard reboot. :P

---

### Post by Habitual on 2011-07-12
Alt+F2 > xkill and click on the screen area of the game.

---

