---
title: "Ubuntu 10.04 freezes, boots to initramfs"
date: 2010-07-16
forum: General Help
---

### Post by bumgarb on 2010-07-16
I'm having trouble with my Ubuntu installation.
It will boot fine.  I'll use the system for a while (1-2 hours) then leave it running.  I'll return to find that the system has frozen.

On reboot, I get a bunch of mount errors and the system loads to initramfs.

To fix this, I can reboot from the thumbdrive I installed from. shutdown. reboot without the thumbdrive, and the system appears to have repaired itself. I use the system for a while and it works fine.  Then it will freeze again. Reboot and the cycle repeats.

I tried installing all the updates, rebooted, and the system went to initramfs.

Any ideas why the system keeps crashing?  The laptop worked fine with XP... just switched to Ubuntu for fun.

Thanks for any help.

---

### Post by cavalier911 on 2010-07-16
This seems to hit a lot of users.

[http://ubuntuforums.org/showthread.php?t=1478787&page=70](http://ubuntuforums.org/showthread.php?t=1478787&page=70)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)

---

### Post by bakegoodz on 2010-07-17
Try turning Suspend and Hibernate off in the Power Management 
settings.
 My guess suspend crashes the computer, then the root drive is too dirty to mount, so it goes into single user mode, which I think is useless mode to fix anything, then booting your install media makes the journal replay on the file-system (fixes unfinished writes on the file system). I thought the journal replay should be happening automatically when you reboot, so I'm not too sure about that one.

---

