---
title: "How do I completely remove Grub2 and go back to legacy?"
date: 2010-05-03
forum: General Help
---

### Post by asuastrophysics on 2010-05-03
Ever since I've updated from grub to grub2, I've had nothing but problems. 
From the Livecd, i chroot into my HDD and run
```
sudo apt-get remove grub2 grub-pc grub-common
```
It's telling me that grub2 and grub-pc aren't installed, but when I boot my computer up, the hateful grub2 happily greets me again, with more error 11's.

So how do I actually remove grub2 if apt-get remove --purge won't do the trick?

---

### Post by zvacet on 2010-05-03
[Here]("https://help.ubuntu.com/community/Grub2#Reverting to GRUB Legacy")

---

### Post by asuastrophysics on 2010-05-03
thanks for the link!
I followed all of the steps provided, using CHROOT. However, when I reboot, grub comes up as 1.98 still :(
Am I possibly missing a step? I'll gladly post the contents of my /boot folder if you wish

---

### Post by zvacet on 2010-05-04
As far I can see you don't have to use chroot.Just follow steps provided with link and you should be fine.

---

### Post by Leppie on 2010-05-04
did you install grub legacy afterwards?
if you do not clear the mbr, or overwrite it, grub2 will still be there.

---

