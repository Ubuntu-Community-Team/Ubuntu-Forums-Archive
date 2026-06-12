---
title: "nvidia driver/resolution"
date: 2011-01-05
forum: General Help
---

### Post by MrJuanBond on 2011-01-05
Hey I'm no guro at Linux or Ubuntu.  So with that said here is my issue: I recently downloaded/enabled the nVidia drivers for my PC.  Now i'm stuck in a 640 res with a panning res of 1024.  I'm wondering what I need to do to change the res.  I've tried using the nVidia panel but it max out at 640.  I know the card and monitor can atleast handle 1024.  So with that being said let me know any more information I need to include.


Thanks for any help,
Mr Juan Bond

---

### Post by Dans564 on 2011-01-05
Do u know what GPU you have?

---

### Post by Krytarik on 2011-01-05
Judging from some recent threads I followed, the reason for this might be incorrect specs set for your monitor in "/etc/X11/xorg.conf".

Enter in a terminal:
```
sudo apt-get install hwinfo
sudo hwinfo --monitor
```and check the values for HorizSync and VertRefresh. If they differ, update the xorg.conf accordingly. Then log out and in again.

---

### Post by gmargo on 2011-01-06
Probably you need to run **nvidia-xconfig(1)** and have it write out an xorg.conf file, then restart X or reboot.

---

