---
title: "A big problem"
date: 2010-11-26
forum: General Help
---

### Post by meloade on 2010-11-26
I've run into a little problem... 
Here's how it started. Lately I"ve  been pretty fed up with the iPod incompatibility, wine problems, ect.  ect. ect. So i decided to dual-boot. I ran a live CD of Kubuntu and used  gparted to shrink my main partition, then installed xp....
Yet now.... whenever I boot up, it automatically loads windows... no option for ubunutu.
I have no idea why this is happening...any help?

---

### Post by igotsanevo4g on 2010-11-26
Try going into BIOS (usually the del key when booting but every pc is different) and mess with the boot order.

---

### Post by Sazhen86 on 2010-11-26
Hi

When you installed windows, it probably replace GRUB with its own bootloader which only loads windows.  This post may help you to restore GRUB and allow you to dual boot:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Cheers

---

### Post by meloade on 2010-11-26
> **Sazhen86 said:**
> Hi

When you installed windows, it probably replace GRUB with its own bootloader which only loads windows.  This post may help you to restore GRUB and allow you to dual boot:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Cheers
 Thanks for the help! I can't try it now though, too tired. ;)
but i'll make sure to post back with the results!

---

