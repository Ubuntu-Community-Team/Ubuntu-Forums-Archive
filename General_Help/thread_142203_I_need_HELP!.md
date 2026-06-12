---
title: "I need HELP!"
date: 2006-03-09
forum: General Help
---

### Post by pearlgdatingaling on 2006-03-09
Greetings!

I have decided to install ubuntu.

I have partitioned my HDD (80 gb) into two (40 each)
The primary drive has Win XP
The other one, I installed Ubuntu
The installation is successful 
I tried to configure the mouse setup from PS2 to COM1, and I successfully edited it, 
The problem is, when I restarted Ubuntu, I can no longer get into the main window of the program. Instead, and error message appears that says something about error in setup of graphics in the X server.
Win XP on the other hand, is not affected at all.

Please help!

thank you so much!

Pearl

---

### Post by gerbman on 2006-03-10
[QUOTE=pearlgdatingaling]Greetings!

I have decided to install ubuntu.

I have partitioned my HDD (80 gb) into two (40 each)
The primary drive has Win XP
The other one, I installed Ubuntu
The installation is successful 
I tried to configure the mouse setup from PS2 to COM1, and I successfully edited it, 
The problem is, when I restarted Ubuntu, I can no longer get into the main window of the program. Instead, and error message appears that says something about error in setup of graphics in the X server.
Win XP on the other hand, is not affected at all.

Please help!

thank you so much!

Pearl[/QUOTE]

Did you edit the Xorg file, the one at /etc/X11/xorg.conf? Chances are you messed something up in there. Try changing it back to the original (it is usually a good practice to back xorg.conf up before making changes). I'm not sure how to configure a COM mouse, but at least you'll have your desktop back.

---

