---
title: "Auto boot?"
date: 2009-11-01
forum: General Help
---

### Post by Myke. on 2009-11-01
Hi, Didnt know where to post this.
Im running ubuntu 9.04 (updating later this week..) I used to dual boot ubuntu and xp. xp broke, I was wondering if there was a way to keep xp, But auto boot ubuntu on start up.
(getting xp fixed.. sooner or later)


If this is in the wrong thread sorry, im new ;x

---

### Post by andrewabc on 2009-11-01
Ubuntu 9.04 should be starting first instead of XP.

Read [HOWTO: StartUp Manager & Kernel Display Options](http://ubuntuforums.org/showthread.php?t=818177)

From that page short version:
backup menu.lst as howto states.
gksu gedit /boot/grub/menu.lst

Change 'default 0'
to another number wherever the ubuntu is listed (you'll have to manually count when GRUB appears when you start computer). 0 is first in list.

---

