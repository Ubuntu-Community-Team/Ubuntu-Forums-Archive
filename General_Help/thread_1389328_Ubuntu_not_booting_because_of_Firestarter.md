---
title: "Ubuntu not booting because of Firestarter?"
date: 2010-01-24
forum: General Help
---

### Post by alexjohnc3 on 2010-01-24
For some reason when I try to boot Ubuntu up I get the following error messages:

[LIST=1]
[*]udevd[470]: NAME="%k" is superfluous and breaks kernel supplied names, please remove it from /etc/udev/rules.d/48-ldusb.rules:2
[*]One or more of the mounts listed in /etc/fstab cannot yet be mounted
[/LIST]

After the second error message, it says, "Stopping Firestarter..." and it stops there. :\

Edit: Mounting seems to be the problem. No idea how to fix it though.

---

### Post by alexjohnc3 on 2010-01-24
*bump*

---

### Post by n0dix on 2010-01-24
1. The only thing i find is this: [http://sidux.com/PNphpBB2-viewtopic-t-18679.html](http://sidux.com/PNphpBB2-viewtopic-t-18679.html)

I hope help you!!

---

### Post by Sef on 2010-01-24
> bump

Please wait for 24 hours with no posts before bumping your thread.  Thank you.

---

### Post by alexjohnc3 on 2010-01-25
> **n0dix said:**
> 1. The only thing i find is this: [http://sidux.com/PNphpBB2-viewtopic-t-18679.html](http://sidux.com/PNphpBB2-viewtopic-t-18679.html)

I hope help you!!
Well, I removed that line. Now the only message I'm getting is "swap:waiting for UUID:*a bunch of numbers/letters*", and the option to use a recovery shell.

---

### Post by n0dix on 2010-01-25
> **alexjohnc3 said:**
> Well, I removed that line. Now the only message I'm getting is "swap:waiting for UUID:*a bunch of numbers/letters*", and the option to use a recovery shell.

Post your /etc/fstab file. And your ```
sudo blkid
```

---

### Post by alexjohnc3 on 2010-01-25
fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=UUID1 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=UUID2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```


sudo blkid
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="UUID1" TYPE="ext3" 
/dev/sda5: UUID="UUID2" TYPE="swap"
```

(Changed UUIDs to UUID1 and UUID2 for no real reason. Actual output was a bunch of numbers and letters.)

---

### Post by n0dix on 2010-01-25
Post your: ```
sudo fdisk -l
```
And try:```
sudo swapon -a
```
Then ```
free -m
```
You have to see the swap partition.

---

### Post by alexjohnc3 on 2010-01-25
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30041   241304301   83  Linux
/dev/sda2           30042       30394     2835472+   5  Extended
/dev/sda5           30042       30394     2835441   82  Linux swap / Solaris

```

```
ubuntu@ubuntu:~$ sudo swapon -a
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           938        806        131          0         45        467
-/+ buffers/cache:        293        644
Swap:         2768          3       2765
```

(I'm using terminal in the Live CD to do this, not the command line in the recovery shell.)

---

### Post by n0dix on 2010-01-25
Enter to the recovery shell.
If you get something similar a /etc/fstab cannot yet be mounted

Do this:

Press Esc to enter the recovery shell
Remount the / filesystem as read-write: mount -o remount,rw /
Continue the upgrade: dpkg --configure -a

---

### Post by alexjohnc3 on 2010-01-25
> **n0dix said:**
> Enter to the recovery shell.
If you get something similar a /etc/fstab cannot yet be mounted

Do this:

Press Esc to enter the recovery shell
Remount the / filesystem as read-write: mount -o remount,rw /
Continue the upgrade: dpkg --configure -a
That didn't do anything for me. :(

Another possible reason for this problem is that I uninstalled LAMP using something like "sudo tasksel uinstall lamp-server" in the terminal, I think (which isn't how [this page]("https://help.ubuntu.com/community/ApacheMySQLPHP") says to do it).

---

### Post by n0dix on 2010-01-25
> **alexjohnc3 said:**
> That didn't do anything for me. :(

Another possible reason for this problem is that I uninstalled LAMP using something like "sudo tasksel uinstall lamp-server" in the terminal, I think (which isn't how [this page]("https://help.ubuntu.com/community/ApacheMySQLPHP") says to do it).

The tasksel thing don't has nothing to do with that.

What version of ubuntu have? It is a fresh install?

Modified your fstab in this way (do a backup before ;)):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
/dev/sda1 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
/dev/sda5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```


Give a complete error. 
Good luck!

---

### Post by alexjohnc3 on 2010-01-25
After I did that it just stopped booting with this:

```
fsck from util-linux-ng 2.16
/dev/sda1:clean, (some large number)/(some larger number) files (some large number)/(some larger number) blocks

```

After that, I can't type in any commands or do anything.

---

### Post by n0dix on 2010-01-25
If you don't have a critical information i recommend you do a fres install. This problem is very strange :(

---

