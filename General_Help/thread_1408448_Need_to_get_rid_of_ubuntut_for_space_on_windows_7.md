---
title: "Need to get rid of ubuntut for space on windows 7"
date: 2010-02-16
forum: General Help
---

### Post by TheRevTastic on 2010-02-16
I didn't use wubi to install Ubuntu 9.10. And when I try to get rid of it by deleting the partition, it makes it free space, won't let me add that space back to my Windows 7 Partition, and doesn't uninstall grub.

Anyway to fix that?

---

### Post by audiomick on 2010-02-16
There are links to various methods to remove Ubuntu here:
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by woodmaster on 2010-02-16
boot from Live CD and use gparted to reformat your Ubuntu partition and merge it with Winows 7 partition.  They both need to be unmounted to change partition specs.

---

### Post by TheRevTastic on 2010-02-16
How would I go about getting to gparted after booting from the live cd?

---

### Post by Megaptera on 2010-02-16
Boot live CD, > System on menu bar > System tools > Gparted I think should do it?!

---

