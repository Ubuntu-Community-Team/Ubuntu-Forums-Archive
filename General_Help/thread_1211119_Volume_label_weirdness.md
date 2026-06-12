---
title: "Volume label weirdness"
date: 2009-07-12
forum: General Help
---

### Post by Piccy on 2009-07-12
I have just installed a new hard disk and have tried to give it a volume label. I have put it in gparted as "STORAGE" (without the quotes) and even tried to use sudo e2label /dev/sde1 STORAGE in the terminal.

Thing is it still keeps coming up as 1000.2GB MEDIA as the volume label, but when I run gksu nautilus the volume label is correct.

Is there some way of correcting this?

---

### Post by GCoffee on 2009-07-12
Have you rebooted your system?

Go back to GRUB and try to rename it again.

---

