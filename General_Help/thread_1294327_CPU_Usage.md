---
title: "CPU Usage"
date: 2009-10-18
forum: General Help
---

### Post by SkyDriver on 2009-10-18
I have installed Ubuntu 9.04 and when I opened System Monitor the CPU Usage was been more of 40% on the two processors... [Is this normal]("http://img8.imageshack.us/img8/813/screenshotar.png") or...?

P.S. I have open Opera (with 7-8 tabs), aMSN, Skype, Amarok and BlueFish editor.

And glxgears: 15021 frames in 5.0 seconds = 3004.148 FPS

Thanks...

---

### Post by lovinglinux on 2009-10-18
Go to "System >> Preferences >> Startup Applications" and disable Remote Desktop. That should help.

Also make sure you install the graphics card drivers from "System >> Administration >> Hardware Drivers".

BTW, is not normal if you computer is on idle. Keep in mind the System Monitor itself is a CPU hog. You can see which applications are eating CPU cycles from a terminal, with the command **top**.

---

### Post by Vaphell on 2009-10-18
also don't use GUI to measure cpu load, it adds some overhead
use **top** in terminal

---

### Post by pintooreddy on 2009-10-18
yeah really the GUI adds an overhead just use the **_top _**terminal.........****

---

