---
title: "PATH question"
date: 2006-02-10
forum: General Help
---

### Post by hyperpsyched on 2006-02-10
Not sure if this is the right place to post but I need to find the file where the PATH is set up at start up. 

I need to add some directories (mpich stuff) to my PATH at startup and I cannot remember back to my UNIX days where this file might be. I would like these avilable to all users as well... even if the only user other than root happens to be me.

How about .xinitrc or .bashrc?

---

### Post by jrib on 2006-02-11
for all users, gnome doesn't source /etc/profile but uses /etc/login.defs to set the $PATH.  If you aren't using gnome and are instead logging into a terminal when you then you want /etc/profile.

/etc/bash.bashrc should work too...

[edit]Just noticed you posted in the kubuntu section.  I only know about gnome.  If you want it setup when people login to KDE, try /etc/login.defs and see if it works.  If it doesn't, then try /etc/profile.  I think kde will use /etc/login.defs as well, but I am just guessing.  Maybe someone who uses kde can give more info?

---

