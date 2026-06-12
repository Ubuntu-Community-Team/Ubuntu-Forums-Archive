---
title: "Tint2 and Lucid"
date: 2010-06-17
forum: General Help
---

### Post by TheNessus on 2010-06-17
Ok, I installed Tint2, and the icons that normally appear in Gnome-panel's Indicator-applet do not appear in the system tray of Tint2. I mean volume control, battery, etc. Any ideas..? thank you

---

### Post by thil77 on 2010-06-17
The gnome panel's indicator is named "notification" or "systemtray".
It's not possible to have more than one "notification".

First test :
- open the config file of tint2 ~/.config/tint2/tint2rc
- and check if you have the option "systray = 1"

Second test :
- open a terminal and run "tint2"
- check if you have the message "another systemtray is running"
if you have this message, it's because gnome panel run a "notification" and so tint2 can't run another one.

[http://code.google.com/p/tint2/wiki/FAQ#tint2_doesn%27t_show_the_systray/notification](http://code.google.com/p/tint2/wiki/FAQ#tint2_doesn%27t_show_the_systray/notification)

---

### Post by TheNessus on 2010-06-17
Thank you

---

