---
title: "Screen Resolution"
date: 2006-01-28
forum: General Help
---

### Post by benjfield on 2006-01-28
When i first installed ubuntu, the resolution was 2 small for my screen (1600x1280 i thnk). I changed it using kcontrol to a more viewable resolution, however everytime I reboot it resets to the original resolution. Can ne1 help me with rectifying this plz? Thanks

---

### Post by amohanty on 2006-01-28
Backup your /etc/X11/xorg.conf:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
Do a :
> sudo dpkg-reconfigure xserver-xorg
Use defaults for everything, just select the right color depth and resolution unchecking all others.
Restart X using Ctrl+Alt+Backspace

HTH
AM

---

### Post by benjfield on 2006-01-28
Thanks v much m8

---

