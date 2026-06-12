---
title: "On Start Up Blocked By Terminal"
date: 2010-06-01
forum: General Help
---

### Post by sparcle_z on 2010-06-01
On Start Up I get a terminal which displays user@my-desktop:~$ on brown back-ground of ubuntu and then what to do after that, to log it? When I exit i pull me back to the login screen for user name and password.
Please help!!!!!

---

### Post by gsocker on 2010-06-01
Check the "session" setting before you login. I suspect it's set to something along the lines of "emergency" of "failsafe". These session types are designed to let you login and try to fix the problem if GNOME/KDE/XFCE/etc won't start correctly.

Usually all you see is a xterm screen. In most(all?) cases, depending on the settings, it won't even have window boders.

Change "Session Type" back to gnome, kde, or whatever desktop you use and you should be fine. 

It logs out when you run "exit" because that terminal is your "session" at this point; you are effectively "logging out" of your session.

---

