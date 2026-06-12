---
title: "I need Help restoring partition - Gparted mess :("
date: 2009-09-14
forum: General Help
---

### Post by b3rkl3y on 2009-09-14
Hello,

I tried to resize some partitions of my hard drive with gparted

My initial disk layout was:

|sda1   10gb | sda3 30gb   | sda5  36gb  | sda6 swap (512mb or 1024 dont remember) | sda7 36gb |


My sda7 was full and i needed some space from sda5, so my plan was, resize sda5 to a smaller partition, delete sda6, resize sda7 to a bigger size using the old space from the sda5 and from the swap, after that, resize the end of the sda7 to remove 1gb and use for swap.


After deleting the swap partition, when gparted tried to resize the sda7  that was renamed to sda6 it said:

```

check file system on /dev/sda6 for errors and (if possible) fix them  00:00:00    ( ERROR )
         
e2fsck -f -y -v /dev/sda6
         
e2fsck: Superblock invalid, trying backup blocks...

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Bad magic number in super-block while trying to open /dev/sda6

```The complete log is here: [http://pastebin.com/maa531ec](http://pastebin.com/maa531ec)

[[IMG]http://img9.imageshack.us/img9/793/gparteds.th.jpg[/IMG]]("http://img9.imageshack.us/i/gparteds.jpg/")[[IMG]http://img225.imageshack.us/img225/3995/screenshotinformationab.th.png[/IMG]]("http://img225.imageshack.us/i/screenshotinformationab.png/")

[http://img9.imageshack.us/img9/793/gparteds.jpg](http://img9.imageshack.us/img9/793/gparteds.jpg)
[http://img225.imageshack.us/img225/3995/screenshotinformationab.png](http://img225.imageshack.us/img225/3995/screenshotinformationab.png)

Is it possible to restore the information of this partition? I do have backups, but they are all online :(  and my internet link isn't very good.

Thanks in advance.
ps: all my partitions are in ext3

---

### Post by P4man on 2009-09-14
did you do that from a livecd?
If not, boot from a livecd, Im guessing its your fstab that tries to mount the wrong partition as the numbers have changed. If you boot from a live cd, it may well see your partitions correctly. if thats the case, we'll fix fstab.

---

