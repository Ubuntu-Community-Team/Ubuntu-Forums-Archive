---
title: "GRUB/Vista Loader"
date: 2009-07-27
forum: General Help
---

### Post by DanSchnell on 2009-07-27
So i boot up my computer and it goes into GRUB, giving me the option to boot Ubuntu (in various modes) or go to the Vista/Windows Loader.  I would like the Vista loader to come first and give the option of going into the Ubuntu/GRUB loader.

How do i edit menu.lst to change that?

[http://paste-bin.com/view/c51c42bb](http://paste-bin.com/view/c51c42bb)

Thats my menu.lst

Thanks for any help.

edit: I'm using Ubuntu 9.04 right now.

---

### Post by philcamlin on 2009-07-27
when dual booting with Vista, download the program EasyBCD (in Windows), and use it to make an entry for Ubuntu in Vista's bootloader.

:popcorn:

---

### Post by DanSchnell on 2009-07-27
> **philcamlin said:**
> when dual booting with Vista, download the program EasyBCD (in Windows), and use it to make an entry for Ubuntu in Vista's bootloader.

:popcorn:

Does it matter that I have 3 OS installed?

Hard Drive 1, Only partition, Windows XP
Hard Drive 2, partition 1, Windows 7 RC (Loader)
Hard Drive 2, Partition 2, Ubuntu 9.04

---

### Post by philcamlin on 2009-07-27
nope :)
you just add the option in easy bcd :)

---

