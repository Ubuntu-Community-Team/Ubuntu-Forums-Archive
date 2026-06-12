---
title: "Kernel problems"
date: 2006-01-22
forum: General Help
---

### Post by djpenguin on 2006-01-22
Okay, so I have a slightly older laptop (an ASUS S5Ne) based on a Banias processor.  The default ubuntu install was nice, but pretty sluggish.  In my quest to squeeze some more performance, I decided to compile a new, much more customized kernel.

Since this is my first ubuntu/debian machine, I decided to rigourously follow [this howto on the wiki](https://wiki.ubuntu.com/KernelHowto).  All went pretty well until I got to the rebooting and trying out part.  As soon as I booted the system with the new kernel, I got a kernel panic message.  Unfortunately, the howto just says to boot back to the old kernel, which is marvelously unhelpful, as I don't know how.

Now on a gentoo system, I would just pop in a live cd, chroot into the system, and edit the bootloader file to remove the offending kernel and boot normally with the known-good kernel.  What am I supposed to with a ubuntu system to get the same result?

---

### Post by cotcot on 2006-01-22
It should work.  Even without a live CD. The old kernel is normally still in the grub menu unless you removed it manually.

---

