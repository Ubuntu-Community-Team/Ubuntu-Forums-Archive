---
title: "How to disable the default X power saving features ?"
date: 2010-04-02
forum: General Help
---

### Post by Zukero on 2010-04-02
Hi all,

I am using Xubuntu 9.10 on a nettop as a X11 terminal.
In order to do that, I created a custom session script that runs some commands instead of starting xfce4-session and the likes from GDM.
When I boot this nettop, GDM automatically logs a dummy user in (called "test"), and runs a script that does "xhost +", and opens a small X Terminal to keep the X session alive, while some other computer sets the DISPLAY environment variable to point to <nettop>:0 and runs gnome-session.

My trouble is that after 10 minutes of idle, the screen is blanked (power saving I presume).
I tried to add "xset -dpms" and "setterm -blank 0 -powersave off" to my startup script, in vain.

I want my power saving options to be configured on the remote computer, not the nettop.

How could I prevent X/GDM/Whoever from blanking the screen ?

---

### Post by sisco311 on 2010-04-03
Try to disable the screensaver as well:
```
xset s off
```

---

