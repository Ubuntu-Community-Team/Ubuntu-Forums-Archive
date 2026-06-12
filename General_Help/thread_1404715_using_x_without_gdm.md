---
title: "using x without gdm"
date: 2010-02-11
forum: General Help
---

### Post by powerplayground on 2010-02-11
I uninstalled gdm because the crappy gui login takes too long to load. I uninstalled it and once I restarted, the gui booted, it displayed a distorted gnome error message, and I can't access any virtual terminals. It works fine when I boot into safe mode in a root terminal su into my account and run startx.

All I want to do is startup normally into a virtual terminal, login and then just type startx. I'm using xorg and fluxbox, so I don't need gdm.

---

### Post by spiderbatdad on 2010-02-11
I believe you can just add the word text to the grub kernel line and accomplish what you want.

---

### Post by Satoru-san on 2010-02-11
```
update-rc.d remove -f gdm
nano ~/.xinitrc

----put this in-----

  [s]export XDG_MENU_PREFIX=gnome-
 exec /usr/bin/gnome-session[/s]


```Now you can login to a framebuffered tty and startx


cheers.


EDIT: THAT IS FOR GNOME, I am not sure how to start flux or whatever wm you are using

---

### Post by powerplayground on 2010-02-18
> **Satoru-san said:**
> ```
update-rc.d remove -f gdm
nano ~/.xinitrc

----put this in-----

  [s]export XDG_MENU_PREFIX=gnome-
 exec /usr/bin/gnome-session[/s]


```Now you can login to a framebuffered tty and startx


cheers.


EDIT: THAT IS FOR GNOME, I am not sure how to start flux or whatever wm you are using

gdm is gone, dead, DELETED. Is there any way to force ubuntu to start in runlevel 3 or do I need to reinstall gdm? (Which BTW is 100% retarded.)

---

