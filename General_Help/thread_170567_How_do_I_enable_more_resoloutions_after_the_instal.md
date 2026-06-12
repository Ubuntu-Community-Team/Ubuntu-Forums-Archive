---
title: "How do I enable more resoloutions after the install?"
date: 2006-05-04
forum: General Help
---

### Post by dead7iest-weap0n on 2006-05-04
OK, I installed ubuntu, and it came up w/ a screen that listed many resoloutions. The problem is is that I accedentally presed enter, and it went forward. How do I enable other higher resoloutions? Because I need it to be 1280x1024

---

### Post by mscman on 2006-05-04
Open a terminal and run
```
sudo dpkg-reconfigure xserver-xorg
```
and go through the dialogue.  Then press CTRL+ALT+BACKSPACE to restart the xserver (or restart your computer).

---

### Post by jobezone on 2006-05-04
You can re-run that configuration, by running in a terminal: ```
sudo dpkg-reconfigure xserver-xorg
``` or by using the Synaptic Package Manage, under System->Administration: In this program, search for the package xserver-xorg. Select it, and go to  Package->Configure package(or similar wording).

---

