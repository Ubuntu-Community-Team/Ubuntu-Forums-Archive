---
title: "gvfs should it take half the HDD?"
date: 2009-08-11
forum: General Help
---

### Post by ookooboontoo on 2009-08-11
Hi All,

I have a laptop with an 80Gb HDD but I can only use half of it as it appears GVFS is duplicating my machine. Am I right in thinking this, is it a bug, do I need gvfs and can I get all the 80 GB into use?

I am using Hardy.

Thanks in advance

A

---

### Post by michy99 on 2009-08-11
Gvfs is a virtual file system. It is probably not actually taking up any space. What is the output of these commands?```
sudo fdisk -l
df -h
```

---

### Post by ookooboontoo on 2009-08-11
Thanks Michy for the reply

I get ```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

```
Is this right?

I did see there was a bug posted
[http://ubuntuforums.org/showthread.php?p=4902571#post4902571](http://ubuntuforums.org/showthread.php?p=4902571#post4902571)

what would you recommend?

Thanks

---

### Post by ookooboontoo on 2009-08-11
I know it says ```
Disk /dev/sda: 40.0 GB, 40007761920 bytes

```but running Disk usage analyser it says
Total file system 70Gb used 56Gb!

It does not add up

A

---

### Post by ookooboontoo on 2009-08-11
A quick thought, When I orignally reformatted the drive, could I have made it into a 40Gb by  changing sector capacities?

---

### Post by ookooboontoo on 2009-08-11
On system monitor I see this

---

### Post by michy99 on 2009-08-11
I think you have a 40 GB drive, and a bug in Hardy causes Disk Analyzer to report the size as double. This has been reported here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789)

It seems it was fixed in Intreped, but not in Hardy. To see that your disk is actually 40 GB, look at it in Gparted, or go into your bios menu at start-up and see what it reports.

---

### Post by ookooboontoo on 2009-08-11
DANG!

It appears from the BIOS that I do indeed have a 40Gb drive. Thank you for sparing the time to help, Ireally appreciate it. I am now off to do some serious pruning!

A

---

