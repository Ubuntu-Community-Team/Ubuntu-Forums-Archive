---
title: "Ubuntu 10.10 won't boot!"
date: 2010-12-21
forum: General Help
---

### Post by delcera on 2010-12-21
So I have a major problem here.

The laptop I use to take notes in my classes, a Compaq Presario CQ62, won't boot in either regular or recovery mode.

When I run the memory check, everything says it's fine, but when I go to boot it gives the following message:

"Begin: Running /scripts/local-bottom ... done.
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands."

When I then do what it says and pass it bootarg, it gives me the following:

"/bin/sh: bootarg: not found"

This is my laptop for college, and has some fairly important stuff on it. Nothing I couldn't replace, but it'd be a pain in the *** to do so. Strange thing is, I was using it twelve hours ago without a problem, and haven't done anything that should've nuked the important directories.

Halp plz?

---

### Post by sikander3786 on 2010-12-21
Welcome to the forums :-)

Boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

---

### Post by hal8000 on 2010-12-21
Boot with the Ubuntu 10.10 CD in live mode, this way your hard drive will not be touched.
once the live CD has reached the Gnome desktop, open the terminal
and post output of:

sudo fdisk -l

If the above command generates an error post also output of

dmesg | tail

---

### Post by Hippytaff on 2010-12-21
+1 boot info script

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by delcera on 2010-12-21
Well, the boot script failed utterly. I followed the instructions Sourceforge has to the letter, it hung on "searching sdal for information".

The fdisk command gives the following output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000654c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29637   238053376   83  Linux
/dev/sda2           29637       30402     6142977    5  Extended
/dev/sda5           29637       30402     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders
Units = cylinders of 320 * 512 = 163840 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48948     7831512    b  W95 FAT32

```

---

### Post by sikander3786 on 2010-12-21
Run filesystem check on sda1 from the Live CD.

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

Run bootinfoscript again and see if it can read sda1. If yes, reboot and you might be able to boot Ubuntu successfully. If not, post the boot scirpt output here to let us take a look.

---

### Post by delcera on 2010-12-21
No dice. Filesystem check gave me the following:

```

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```

And then when I run the info script, it just hangs at the same point it did before.

---

### Post by sikander3786 on 2010-12-21
> **delcera said:**
> No dice. Filesystem check gave me the following:

```

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```

And then when I run the info script, it just hangs at the same point it did before.
Then check you HDD for bad sectors. I just hope it is not failing....

There are some good instructions in this thread to follow.

[http://ubuntuforums.org/showthread.php?t=1601810](http://ubuntuforums.org/showthread.php?t=1601810)

---

### Post by delcera on 2010-12-21
So that thread you linked talks about Slax. I haven't the slightest clue what that is; mind helping out a poor newbie?

---

### Post by sikander3786 on 2010-12-21
[http://www.slax.org/](http://www.slax.org/)

Another Linux distro better at some administrative tasks ;-)

---

### Post by delcera on 2010-12-21
Aha. Awesome.

There wouldn't happen to be just an easy way of ripping the important files from my drive, would there? Because the last time this happened to me, I just reinstalled Ubuntu and it worked fine.

---

