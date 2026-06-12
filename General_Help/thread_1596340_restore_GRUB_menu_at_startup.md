---
title: "restore GRUB menu at startup"
date: 2010-10-14
forum: General Help
---

### Post by Circlethesky on 2010-10-14
hi
for about a month iv been dual booting with windows 7 and ubuntu, which was all working fine up until i tried to edit the GRUB screen.
when i stuffed that up i had to use the windows disc to run a repair, which removed the grub screen where i choose which operating system to use on start up, and when i turned my computer on it just booted into windows.
could someone tell me how i can get that screen back up so i can access ubuntu as well as windows? everything iv tried has just stuffed it up and iv had to use the repair again, im hoping the solution is quick and easy, it seems like ill be trying to sort this issue out for years...

---

### Post by VMC on 2010-10-14
Try this [_**method**_]("https://wiki.ubuntu.com/Grub2#Restore GRUB2 - Recovering from a Windows XP / Vista / 7 Reinstallation") using Chroot.

---

### Post by Mark Phelps on 2010-10-14
Unless they've radically changed the way Wubi works, it does not use GRUB or GRUB2; instead, is uses GRUB4DOS -- a GRUB variant that installs and runs in MS Windows NTFS partitions.

So, trying to reinstall GRUB or GRUB2 using the standard approaches is not only unlikely to work, it runs the risk of hosing up your machine further.

---

### Post by bcbc on 2010-10-14
When you first installed burg, did it uninstall grub-pc? If so, did you reinstall grub-pc after playing with burg? You may have to do this in a chroot if you can't boot the wubi install.

Do you still get Ubuntu in the windows boot manager screen?

IMO, unless you have strong reasons to try and repair your wubi, it will be easier to loopmount the root.disk and copy off your important data (or use ext2read v2.2 from windows), and then reinstall.

---

