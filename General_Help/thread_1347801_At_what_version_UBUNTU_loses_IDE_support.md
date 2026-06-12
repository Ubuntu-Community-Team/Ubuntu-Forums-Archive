---
title: "At what version UBUNTU loses IDE support"
date: 2009-12-06
forum: General Help
---

### Post by phshirk on 2009-12-06
At what version of UBUNTU does the IDE support for CDROM's etc get dropped?
I went back from version 9.10 to 8.04. to get back to a version that supported the IDE devices and was wondering if I start having problems again at 8.10.

Thanks

---

### Post by coffeecat on 2009-12-06
IDE optical drives have worked just fine for me in every version of Ubuntu up to 9.10. Why do you think IDE support was dropped? What problem did you encounter?

---

### Post by Cheesemill on 2009-12-06
I can't imagine that IDE support will be dropped from the kernel for at least the next 10 years (and I think that's a conservative estimate).

---

### Post by falconindy on 2009-12-06
As long as the kernel supports the pata layer, Ubuntu will as well. There's been no signs of kernel devs looking to ditch it yet.

---

### Post by Jerry N on 2009-12-06
My test computer has _only_ IDE drives and Ubuntu 9.04 and 9.10 work fine on it, along with Mint 7, Mint 8, and Windows 7.

Jerry

---

### Post by phshirk on 2009-12-06
there are tons of post out there describing problems with UBUNTU 9.10 not recognizing perfectly good CDROMs. here is just one of them.

 title:**ubuntu 9.10 doesn't recognize my cdrom drive**

---

### Post by coffeecat on 2009-12-06
> **phshirk said:**
> 
 title:**ubuntu 9.10 doesn't recognize my cdrom drive**

Link?

---

### Post by phshirk on 2009-12-06
[http://ubuntuforums.org/showthread.php?t=1316796&highlight=ide+cdrom](http://ubuntuforums.org/showthread.php?t=1316796&highlight=ide+cdrom)
[http://ubuntuforums.org/showthread.php?t=1252521&highlight=ide+cdrom](http://ubuntuforums.org/showthread.php?t=1252521&highlight=ide+cdrom)

---

### Post by fredwong on 2009-12-08
Ubuntu has not lost the IDE support rather the IDE driver has been replaced by the new pata (Parallel ATA) driver. This new driver is really buggy. My IDE DVD writer only shows up every now and then when it feels like it. When it does show up, playing a DVD movie is really jerky. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307829]](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307829]). I really regretted buying an IDE drive in the first place when I built my media box a year ago. Should have bought an SATA drive instead. I don't know why they had to fiddle with the IDE support anyway in the first place and now things are broken. I am supprised that I don't see more threads regarding non working IDE drives on the forum.

---

### Post by gvlx on 2010-05-28
I have just started an installation on a old (1998) Toshiba Laptop which also worked until 6.06.

However, opening a secondary console and `modprobe pata_pnpisa` solved the problem.

G.

---

