---
title: "Steam desktop icon help"
date: 2010-08-17
forum: General Help
---

### Post by pYrO1v1aniac on 2010-08-17
Wine linux gamer here, I'm having some trouble with the desktop icons created by the new steam. The old client worked perfectly, made the right icons, and they were clickable, and could be added to the 'quick launch bar' in gnome to launch games. The new kind don't work at all, and have no icon.

I've got a custom icon, but now I'm trying to find a launch command that works.

For TF2 what I've been trying is-
env WINEPREFIX="/home/carl/.wine" wine "~/.wine/drive_c/Program\ Files\Steam\steam.exe -applaunch 440"

But it doesn't even attempt to launch. What am I doing wrong?

---

### Post by pYrO1v1aniac on 2010-08-17
Figured it out.

env WINEPREFIX="/home/carl/.wine" wine C:\\Program\ Files\\Steam\\Steam.exe applaunch-440

(Applaunch number is the steam game you want to launch)

---

