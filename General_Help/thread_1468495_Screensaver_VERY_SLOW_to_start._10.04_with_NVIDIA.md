---
title: "Screensaver VERY SLOW to start. 10.04 with NVIDIA"
date: 2010-05-01
forum: General Help
---

### Post by Mike_IronFist on 2010-05-01
Okay, this particular issue is driving me nuts. Now I've been using Ubuntu since 8.10 Intrepid, and every time I chose a more recent NVIDIA driver, performance only got better. Now, while performance is still good with the current NVIDIA driver on 10.04, after resuming from a suspend, everything seems to run fine.

But when the screensaver comes on, either on its own or by me locking the screen, the framerate appears to drop severely, and takes at least 30 seconds longer to fade to black and then run the screensaver. This ONLY occurs after suspend/resumes, and never occurs after a fresh boot.

Please help?

---

### Post by Mike_IronFist on 2010-05-01
Bump. Come on, someone has to have an idea!

---

### Post by alexyz on 2010-05-16
this is indeed very annoying.

It just started happening today for me.  After I installed emerald, but I'm not sure that's the problem since it happens whether or not I have emerald running.  The only other thing I did today was install 64-bit flash, and tweak some compiz settings.

I'm using the nvidia proprietary driver.

---

### Post by alexyz on 2010-05-17
In compiz settings, turn on:

General Options > Display Settings > Sync To VBlank



Some details I suspect are related:  I have dual displays.  When the super-slow fadeout happened you could see it happening in slow steps, slightly dim display 1, slightly dim display 2, 1, 2, 1, 2 ... very slow, like one second per step.  Also I could see cpu jump, which was Xorg - not 100% but still unusually high.

---

### Post by alexyz on 2010-05-19
problem has returned :(  very annoying waiting two minutes for the screensaver to fade so I can wake it back up.  

the last compiz tweak definitely appeared to make a difference, the screensaver has kicked in fine many many times in a row. ... will post again if I come up with anything.

----

edit: fixed by a recent update.  :)  most likely one of these:

gnome-screensaver (2.30.0-0ubuntu1) to 2.30.0-0ubuntu2
gtk2-engines-pixbuf (2.20.0-0ubuntu4) to 2.20.1-0ubuntu1

or other gtk-related packages.

---

