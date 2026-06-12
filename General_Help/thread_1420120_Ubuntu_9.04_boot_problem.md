---
title: "Ubuntu 9.04 boot problem"
date: 2010-03-02
forum: General Help
---

### Post by LibraDragon on 2010-03-02
I tried to boot into ubuntu (**wubi** installation) and encountered the following message

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Booting 'Ubuntu 9.04, kernel 2.6.28-18-generic'

Filesystem type is ntfs, partition type 0x07
The current working directory  is /ubuntu/disks

Loading, please wait...
unknown or non-unique volume type (probe-all lists possibly conflicting types)
mount: mounting /dev/loop0 on /root failed: No such device
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init = bootary.

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)

(initramfs)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

How can I resolve this issue?
I tried to check the wubi partition for errors in windows vista and it was OK.

Pls help.

---

