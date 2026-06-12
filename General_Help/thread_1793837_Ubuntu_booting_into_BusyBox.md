---
title: "Ubuntu booting into BusyBox"
date: 2011-06-30
forum: General Help
---

### Post by Happehwalrus on 2011-06-30
As far as I know the power went out once and my computer might have been on- now Ubuntu won't boot correctly. It boots into 'BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)'.

```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
(initramfs)
```

---

### Post by Ozymandias_117 on 2011-06-30
You'll need to boot into a liveCD.  Since it certainly looks like something was messed up, I would start by running fsck on the partition that you have Ubuntu installed on. ```
fsck /dev/sd??
``` Then follow this boot info guide and post the results. [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Happehwalrus on 2011-06-30
I've done fsck and that script- here are the results.
```
sudo fsck /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?

```
```
sudo bash ~/Downloads/boot_info_script*.sh

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "/usr/lib/initramfs-tools/bin/busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdf...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 


```
It just won't work with my partition that I installed Ubuntu on for some reason. I don't know why it can't do that- it's not mounted or in use. I'm using an elementaryOS liveUSB (unetbootin <3) right now.

---

