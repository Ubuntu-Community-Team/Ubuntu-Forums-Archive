---
title: "Add Programs to Ubuntu System Settings?"
date: 2012-04-04
forum: General Help
---

### Post by tcmct on 2012-04-04
Specifically I would like to add Computer Janitor and Alacarte to it. Here is my code for Alacarte.
```

[Desktop Entry]
Name=Main Menu
Comment=Change Unity Menu Settings
Icon=/usr/share/icons/Meopardicons/apps/scalable/alacarte.png
Exec=alacarte
Terminal=false
Type=Application
Categories=GNOME;GTK;Settings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings
OnlyShowIn=GNOME;Unity;
X-GNOME-Settings-Panel=background
X-GNOME-Settings-Panel=/usr/share/icons/Meopardicons/apps/scalable/alacarte.png -64
X-Ubuntu-Gettext-Domain=gnome-control-center-2.0
```

It's pretty much a copy of the Appearance script, which does appear in my System Settings. I placed this script in /usr/share/applications.

Is the something I need to change in my script, possibly being Appilcation specific? Or maybe I have my script in the wrong place? Any help is greatly appreciated! Thank you!

---

### Post by JKyleOKC on 2012-04-04
Have you logged out and back in, or alternatively restarted the system, since adding the new desktop files? And did you put them in the same place as the existing file that do show in your menu?

I've found that sometimes the logout/login is necessary to make things show up, and at other times a full restart is required. Your file itself looks okay to me; the "categories" line, if copied from one that does show in the menu, is the critical one.

---

### Post by tcmct on 2012-04-04
I have tried logging in/out and also restarting my system. Tried playing with the script as well as copying code from some of the other applications from the menu. Also tried the full Exec path /usr/bin/alacarte. No success. I'm using ubuntu 11.10 and 12.04b1 if that helps. Neither work. I'm going to try my (now multiple) scripts in a few different places. I was thinking possibly putting them in ~/.local/share/applications? Not sure, I'll keep looking and post my results. Once again Thank you any help is appreciated!

---

### Post by JKyleOKC on 2012-04-04
Well, ~/.local/share/applications is the right place on my system, but I'm using Xubuntu which has XFCE as its window manager and consequently the location might not be the same for you... However I believe that it should be, since many of the desktop specifications are standardized across most of the different window manager programs.

---

### Post by tcmct on 2012-04-05
Still no success after placing my scripts in /.local/share/applications.  After typing locate applications in terminal I found some an  interesting thing in ~/.config/menus that makes me wonder if I need to  add my script to a larger menu script? I'm a little clueless at this  point. I may just end up doing the same thing I did for a simple custom  launcher before I discover I could edit my menus with Alacarte. Which  was just making a directory with my scripts in it, and adding that  directory to my dock. 

Also as a side note I tried installing  xfce4 through ubuntu software center on ubuntu 12.04b1, and it doesn't  install. That'll probably be fixed in a month though. I hope.

---

