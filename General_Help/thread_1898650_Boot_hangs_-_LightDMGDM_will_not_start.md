---
title: "Boot hangs - LightDM/GDM will not start"
date: 2011-12-21
forum: General Help
---

### Post by -nat- on 2011-12-21
After removing a bunch of Gnome and Unity related files (I use XFCE) as well as updating the kernel and removing old kernel packages, Ubuntu hangs towards the end of booting - the DM/login screen doesn't start. However, I am still able to login via ctrl-alt-F(x) and then run startx from there to get into my normal desktop.

When trying to start LightDM or GDM they just hang while trying to launch (black screen with loading cursor). Other posts I've seen where similar problems are described suggest re-installing graphics drivers, however I'm on an integrated Intel chip, so am unsure of how to do this, or if that is even what is causing the issues.

Any suggestions would be appreciated.

[EDIT]
GDM seems to be starting fine now (I am yet to try LightDM, but I imagine it should also work). Not entirely sure what I did to solve the problem, although it may have been solved by following [these instructions]("http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html") to remove, reinstall and re configure xorg. To person from the future reading this with this same issue: I'm sorry if that's not what fixed it, and good luck ([http://xkcd.com/979/]("http://xkcd.com/979/")).

---

