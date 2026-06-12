---
title: "Runnig apps at Start Up..."
date: 2006-02-02
forum: General Help
---

### Post by Tosa on 2006-02-02
... or rather not running them...

Well, yesterday I've noticed that when I turn on my PC Krusader is in the panel, and runnig! I have done nothing to make it happen (wel as far as I am aware).
How do I run apps on start up (sorry for Win terms, but I can't think of anything else right now), or in this case how I do not (remove) run apps at Start Up? I've tried System Settings, but couldn't find anything there...

Thanks !

---

### Post by aysiu on 2006-02-02
Somewhere in system settings there should be something about saving sessions on logout...

Choose that, kill all the apps you don't like, then log out.

---

### Post by Neo Ex on 2006-02-02
First, sorry if the terms may not be correct, but I'm not English.
To change the sessions policy, you have to go in KControl -> KDE Components -> Session management. I personally prefer to use a blank session every time i log in.
To make a program to launch at the startup, put his .desktop file (usually you can find it in /usr/share/applications) in ~/.kde/Autostart (I think also a link will work).

---

