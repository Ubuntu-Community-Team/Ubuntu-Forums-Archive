---
title: "monitor detection problem"
date: 2010-09-17
forum: General Help
---

### Post by 700 on 2010-09-17
I am using 2 identical monitors on 2 machines with 10.04.1 ubuntu release on both of them. 1 monitor is detected, 1 not. Missing "Applications bar" and "Desktop bar" - they are just hidden (don't fit into the resolution). 
Monitor detection from "monitor preferences" - doesn't work.
Monitor physical settings - doesn't work.
Different resolution settings - doesn't work.
"sudo dpkg-reconfigure xserver-xorg" + "sudo /etc/init.d/gdm restart" - doesn't work.

how to fix it, plz?

---

### Post by fragos on 2010-09-17
My system used to boot without applet bars on occasion. A reboot or restart of a Gnome session always fixed the problem. Are you aware that applet bars can be configured to hide? Try moving your cursor off the top or bottom of the screen to see if the bar appears. If you're using an Nvidia card, do System-> Administration-> NVIDIA X Server Settings-> X Server Display Configuration. That will tell you what has been discovered and allow configuration changes. I've Nvidia and a Viewsonic VA1912w series monitor. My monitor is recognized and configured correctly for 1440x900.

---

### Post by 700 on 2010-09-17
Applet bars don't appear while moving cursor. Bottom bar appears on different resolution settings (4:3 bar available - 5:4 bar not available). Top bar is available by pressing Alt+F1. Monitor preferences include information that monitor type is "Unknown".

---

### Post by fragos on 2010-09-17
Every monitor has an aspect ratio that it's designed for. What you're telling it to use may well be your problem. With the Nvidia I'm only offered resolution options which match the physical aspect ratio of my monitor. What brand and model of monitor are you using on both systems?

---

### Post by 700 on 2010-09-17
It's EIZO Nano 19" FlexScan L765 SlimEgdge - working very well on 1280x1024 (5:4), when detected.

---

### Post by 700 on 2010-09-18
Graphics card (using 'lspci | grep -i vga' command):
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphic Controller (rev 03)

---

### Post by fragos on 2010-09-18
"Top bar available by pressing Alt+F1" is exactly how the applet bar would work if you had it set to Autohide in that bar's preferences. Run the "Configuration Editor" apps-> panel-> toplevels-> top_panel_screen0 and uncheck auto_hide.

---

### Post by 700 on 2010-12-17
Problem fixed.
No problems at all with ubuntu 10.10!

---

