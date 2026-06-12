---
title: "Initramfs - Busy Box Error - Can Mount"
date: 2012-02-04
forum: General Help
---

### Post by leehamer on 2012-02-04
Evening all,

I have an issue a laptop I have been asked to look at that is running Ubuntu 10.10.

When booting it comes up with:

> mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) _[LEFT][COLOR=#000000]
[/COLOR][/LEFT]


I have tried the following: 

> Solution:

1. Boot from the Ubuntu Live CD;

2. Open/Run Terminal;

3. Type:* sudo fdisk -l* (to get the device name) then press ENTER;

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: **********

 Device Boot Start End Blocks Id System
/dev/sda1 * 1 30238 242886703+ 83 Linux
/dev/sda2 30239 30401 1309297+ 5 Extended
/dev/sda5 30239 30401 1309266 82 Linux swap / Solaris

 The device name for my friend's system based on the above: */dev/sda1*

4. Type: *sudo fsck /dev/sda1* then press ENTER;

5. Restart the system and boot normally.[LEFT][COLOR=#000000]
Read more: [http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html#ixzz1lRJEel71](http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html#ixzz1lRJEel71)
[/COLOR][/LEFT]


This didn't work, using the live cd I went into the disk utility and I cannot unmount the drive as it says that it is busy.

I had this problem a while back and found a blog somewhere where someone gave instructions. I remember one of the comments was something along the lines of " clearing the journal, why didn't I think of that ". This was the only thing that worked for me, but I cant find it again. Hopefully someone knows what to do!

Thanks in advance for any help

---

### Post by leehamer on 2012-02-04
sorry to add, the laptop is playing up after it froze and my partners mum just powered it down so it didn't shut down properly

---

### Post by leehamer on 2012-02-05
anyone??

---

