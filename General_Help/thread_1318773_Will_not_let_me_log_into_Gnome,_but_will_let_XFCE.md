---
title: "Will not let me log into Gnome, but will let XFCE"
date: 2009-11-07
forum: General Help
---

### Post by Ryan8524 on 2009-11-07
Hey,

So after updating to ubuntu 9.10, it will not allow me to log into gnome. I spent about 30 minutes trying to log in, using my password and clicking on my username. I had no luck.

After that I decided to see if xfce would work and it did. I used the same exact password and i clicked the same username.

When I select gnome, i type in my password and its starts loading. then the screen goes black, comes back to loading, goes black again, then goes to the start-up menu where it has the different accounts.

Help please!


Thank you!

---

### Post by unamanic on 2009-11-07
I assume you are not getting any errors, if you are, please list them.   First thing to try is if another user can log into gnome.  

If other users can launch gnome, but you can't it's likely an error in your .gconf directories. :
- from the command line: 
  - "mv .gconf bak.gconf"
  - "mv .gconfd bak.gconfd"

---

### Post by Ryan8524 on 2009-11-09
I went to the terminal and put in those commands, nothing happened. I cannot log into gnome from other accounts.

---

### Post by julianb on 2009-11-09
one possibility:

remove gnome and then install it again. although it's possible that doing so will only help if you remove configuration files in the process.

It should be that you can remove gnome from the command line (you will want to Google for some info about doing so... use "apt-get remove" or "aptitude") or using a visual-interface tool in XFCE,  if you have one.

---

### Post by unamanic on 2009-11-09
These are the directories that the gnome configureation is stored, you have to restart gnome after you move them.  Although it's best to not be in gnome when you move them to prevent gnome from just re writing them.  Use the failsafe terminal lgon option or log off,  press [crtl] + [alt] + f1, login and perform the commands, then press [crtl] + [alt] + f7 and try to log into gnome again.

---

