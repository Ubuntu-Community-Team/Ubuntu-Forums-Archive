---
title: "Keyboard settings won't stay after reboot"
date: 2010-03-19
forum: General Help
---

### Post by - Mikko - on 2010-03-19
I'm using Ubuntu Netbook Remix 9.04 in Acer Aspire One together with Windows XP (both on different partitions). The trouble since installing Ubuntu has been that my keyboard has scandinavic layout which includes "ä" and "ö" keys. When I assign the layout in Ubuntu's as "FI" instead of "USA" everything is fine. After reboot for some reason the changes made won't stay and I have to change the keyboard layout manually. If I remove "USA" from the list after reboot it'll appear to the list again!

I've tried to create /etc/X11/xorg.conf file with the keyboard configuration code, but it has no effect for the situation. I've tried also command:
```
sudo dpkg-reconfigure console-setup
```This has no effect also.

I'm starting to be frustrated for the situation. I really enjoy using Ubuntu instead of XP but this just doesn't make sense that the keyboard layout won't stay on.

Does anyone have any help for the situation?

---

### Post by - Mikko - on 2010-03-20
Anybody got ideas? It feels like as long as "USA" keeps coming back to the list it over runs the "FI" choise.

---

### Post by ghmanek on 2010-03-20
looks real...

---

