---
title: "Install Problem"
date: 2010-01-09
forum: General Help
---

### Post by MrATM on 2010-01-09
:(OK, this was my first time trying a new OS. I installed Ubuntustudio. The install went fine. It popped out the CD and then rebooted and when it came up it said,"error: no such device: 625B16F4-9473-4413-94E1-0769A4EAFEAD" Needless to say, I'm a bit bummed and confused. Any ideas? I would really appreciate it. My old HP was running soooo slow before this. It was this or bye-bye. Thanks.

---

### Post by michy99 on 2010-01-09
Boot from the install cd and 'Try without installing.' (I don't remember the exact wording.) Open a terminal (Applications->Accessories->Terminal) and enter these commands.```
sudo fdisk -l
sudo blkid
```Post the results here. Note: That is a lower-case L in the first command.

---

### Post by Jackzor on 2010-01-09
> **michy99 said:**
> Boot from the install cd and 'Try without installing.' (I don't remember the exact wording.) Open a terminal (Applications->Accessories->Terminal) and enter these commands.```
sudo fdisk -l
sudo blkid
```Post the results here. Note: That is a lower-case L in the first command.


Something about try without making changes to the harddrive or such...

---

### Post by MrATM on 2010-01-09
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000465ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60615   486889956   83  Linux
/dev/sda2           60616       60801     1494045    5  Extended
/dev/sda5           60616       60801     1494013+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="625b16f4-9473-4413-94e1-0769a4eafead" TYPE="ext4" 
/dev/sda5: UUID="fd1cebae-fa17-4ad0-9b74-e0f75f428e0a" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
ubuntu@ubuntu:~$

---

