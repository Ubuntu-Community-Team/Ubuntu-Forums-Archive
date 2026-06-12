---
title: "Why kubuntu is not booting instead is going into BusyBox"
date: 2011-01-13
forum: General Help
---

### Post by TroN-0074 on 2011-01-13
Hey everyone.

My system was hanging so I gave it a reboot.  After coming back up, the  system is booting into BusyBox.  I have tried booting into the Ubuntu  LiveCD and then mounting my / in /mnt and my /boot in /mnt/boot and then  doing a grub-install.  This doesn't seem to have fixed my issue.  I  have also tr 5a8 ied booting to the second drive in my raid 1 array.

Here is what I see on my screen:
```

mount: mounting /dev/disk/by-uuid/a4aad87c-c45b-4480-84fa-e0290f5a7853 on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Targeet filesystem doesn't have /sbin/init.
No init found.   Try passing init= bootarg

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```Any help will be highly appreciated. Thank you

---

