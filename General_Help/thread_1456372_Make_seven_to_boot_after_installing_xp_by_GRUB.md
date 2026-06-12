---
title: "Make seven to boot after installing xp by GRUB"
date: 2010-04-17
forum: General Help
---

### Post by MortezaJS on 2010-04-17
Hi
At first I apologize if my question isn't so Ubuntu-related.
I had Win7 installed on my first partition. Before installing xp (on second partition), I toke a backup of MBR (actually first 63 sectors) by dd utility.
Later i installed xp. You may know, it doesn't know seven and makes it un-bootable. Then I restored MBR. But I surprised because xp still boots up. whats the problem?
BTW what I want to do now is to multi boot xp and seven. Is there any work around, something like a hack using GRUB boot loader to be able boot the both?

---

### Post by chris.jericho on 2010-04-17
do you want both xp and 7 in your PC or only 7?

---

### Post by MortezaJS on 2010-04-17
I mean to have the both in boot menu, but if you know a way to boot 7 only, I appreciate if tell me.

---

### Post by chris.jericho on 2010-04-17
when you restart your computer at first... what screen do you see? And in which drive have you install 7?

---

### Post by wilee-nilee on 2010-04-17
[http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html](http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html)

This should give you the answers you need read carefully.

---

### Post by oldfred on 2010-04-17
Windows only knows how to boot from the active (boot) partition. It is easier to do before you install the second windows. You may be able to move the boot flag and run repairs on the second install to make it separately bootable.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

