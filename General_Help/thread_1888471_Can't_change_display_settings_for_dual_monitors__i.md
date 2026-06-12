---
title: "Can't change display settings for dual monitors  in 11.10"
date: 2011-11-29
forum: General Help
---

### Post by Miktor on 2011-11-29
I've had these problems before, but I'm not sure how I solved them back then. 

I simply tried to do mirrored display, but after doing that, I can't change it back.

I'm currently on a laptop (1366x768), and the second monitor is a 1920x1080 display.

I've tried following commands without luck:

```
rm .config/monitors.xml
unity --reset
sudo dpkg-reconfigure xserver-xorg
```


The funny part is that it runs without being mirrored in guest session, and before the login screen appears. I still can't figure out what the solution is though.

---

### Post by Miktor on 2011-11-29
I can change resolution etc. through xrandr it seems. Also I've managed to make them default as for the session, not the login, by making a .xprofile

Here's some documentation [https://wiki.ubuntu.com/X/Config/Resolution#By_Session_with_.xprofile](https://wiki.ubuntu.com/X/Config/Resolution#By_Session_with_.xprofile)

It's a bit annoying that it's still the mirrored setup in the login though.

---

