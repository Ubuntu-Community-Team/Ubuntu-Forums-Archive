---
title: "Xubuntu 10.10 desktop dissapearing."
date: 2011-09-12
forum: General Help
---

### Post by galacticaboy on 2011-09-12
I am running Xubuntu 10.10 with Xfce 8.x and my desktop keeps dissapearing after I log in sometimes. I will boot up and login, then my icons and my wallpaper are gone, it will be changed to the default 10.10 wallpaper, but everything else is the same, my themes and stuff. Then if I reboot, everything will be back to normal. What is going on?

---

### Post by Toz on 2011-09-12
Sounds like xfdesktop is crashing. Next time it happens, post back the contents of **~/.xsession-errors** before you logout (or **~/xsession-errors.old** if you have to log out and back in again). Perhaps there is something there that can help pinpoint the reason.

---

