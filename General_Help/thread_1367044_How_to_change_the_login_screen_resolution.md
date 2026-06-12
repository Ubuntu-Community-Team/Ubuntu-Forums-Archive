---
title: "How to change the login screen resolution?"
date: 2009-12-29
forum: General Help
---

### Post by Ugluk on 2009-12-29
How can I change the login screen resolution in Xubuntu? My selection as user is not affect it.

---

### Post by Ugluk on 2010-01-11
Up

---

### Post by SecretCode on 2010-01-11
See my thread here: [[SOLVED] Screen resolution for ttys (text mode, not X) - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=1365744)

---

### Post by Capitolman on 2010-01-11
You don`t say what graphics card, but if it`s sis try the following site. sis graphics on linux, and look under downloads.

---

### Post by Ugluk on 2010-01-13
I don't need to change a boot screen resolution, it's a gdm screen resolution which is too large. How to change it?

---

### Post by SecretCode on 2010-01-14
Sorry - so your gdm screen is the wrong resolution, but after you've logged in you get the correct resolution (as set by system > prefs > display)?

You might need to try...
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 
or running **xrandr** as described in [X/Config/Resolution - Ubuntu Wiki](https://wiki.ubuntu.com/X/Config/Resolution)
or editing **xorg.conf** as described in [GDM (Login Screen) Resolution Too Big to Fit Screen? Try this… « Linux FUD](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)

---

