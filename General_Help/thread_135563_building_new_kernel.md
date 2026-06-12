---
title: "building new kernel"
date: 2006-02-24
forum: General Help
---

### Post by cerenbudak on 2006-02-24
Hi 
I am trying to build a new kernel. I downloaded the source code (but I could not find the exact match to my system which is 2.6.12-10.386, so I downloaded 2.6.12.tar) I compiled the source code and wrote make modules and then make modules_install. But when I boot the system from the new kernel it gives bunch of errors saying it could not open files /lib/modules/linux2.6.12/...  Does this mean the source code I downloaded was incomplete. What should I do?

---

### Post by lamego on 2006-02-24
You should use the source already packed for Ubuntu (and which matches your current kernel), it is much easier to rebuild.
Read this [howto]("https://wiki.ubuntu.com/KernelHowto") .

---

### Post by hw-tph on 2006-02-24
The [wiki](https://wiki.ubuntu.com) has [detailed descriptions](https://wiki.ubuntu.com/KernelBuildpackageDetailedHowto) on how to properly install a new kernel in Debian/Ubuntu.


Håkan

---

### Post by cerenbudak on 2006-03-01
thanks a lot : )

---

