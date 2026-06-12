---
title: "xorg.conf"
date: 2010-08-27
forum: General Help
---

### Post by whitetimer on 2010-08-27
Hi All

Just done a stupid thing, i edited my xorg.conf file and when i reboot, my desktop freezes at the ubuntu splash screen and so i cant get to the gdm login prompt ...

How can resolve this ?

Many Thanks

---

### Post by smellyman on 2010-08-27
one easy way is to use a live cd and then edit your xorg file again.

---

### Post by whitetimer on 2010-08-27
Thanks ... sorted

---

### Post by TwoEars on 2010-08-27
What exactly did you do? To solve this, I suggest you run ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```, which should fix the problem, and post the output of ```
cat /etc/X11/xorg.conf.old
``` if you would like us to help you work on your xorg.conf

---

