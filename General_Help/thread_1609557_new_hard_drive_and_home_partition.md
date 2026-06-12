---
title: "new hard drive and home partition"
date: 2010-10-30
forum: General Help
---

### Post by goatroper on 2010-10-30
I have an existing install of 10.4 on a 320 GB hard drive without home in it's own partition.  I have a new 500GB hard drive that I want to install 10.10 on.  After installing 10.10 and making /Home on it's own partition can I copy the entire old home folder including the hidden files to the new home partition on the new hard drive so that all of my programs and files are saved. I don't have enough room left on the old hard drive to create and copy home to a new partition.  Am I going about this the right way or do I need to rethink and do some kind of backup restore on the new hard drive or some other way.  I am trying to accomplish this so that in the future I can install a clean copy of Ubuntu when they are released without losing my current settings and files.  I started out with 7.10 but my learning curve is slow so any help will be appreciated.

---

### Post by papibe on 2010-10-30
> **goatroper said:**
> ...can I copy the entire old home folder including the hidden files to the new home partition on the new hard drive ...
Yes, you can  :) . Just use:
```
$ cd /home
$ cp -rp /path_to_old_home/youruser youruser
```
-r works recursively, and -p is for preserving owner and permissions.

> **goatroper said:**
> ...so that all of my programs and files are saved...
Not exactly. First of all, programs are not installed in /home. Also they are packaged for a different version of Ubuntu. You'd have to install them all again. This is not too hard at all, but I would recommend making a list of what you have installed before changing the disks. Nevertheless, note that by copying the whole /home/youruser dir, at least the programs settings will be saved.

In order to accomplish want you want, you will need, at some point, to have both disks mounted. If you have an extra free sata port, and a 3.5" free bay, you are all set. If not, you may use a USB enclosure to mount the old disk.

This is what I would do:
[LIST=1]
[*]Take out your old disk.
[*]Install the new one.
[*]Insert the Ubuntu installation CD and turn on the machine.
[*]Install Ubuntu 10.10. For / use 10-20Gb. For swap match your RAM. The rest use it for /home.
[*]Check your installation went OK.
[*]Now you'll need to mount the old disk. If you can do install it internally you could reuse the space after you get your files. If not, get a USB enclosure and install the old disk there.
[/LIST]

**Disk installed internally**
It may be possible that next time you boot, you'll boot from your old disk. In that case, go to the BIOS and change to boot order. Since the old disk was not available at installation time, it won't get mounted automatically. Use this command to find it:
```
$ sudo fdisk -l
```
Let's say it is named /dev/sdb1. Mount it where you want, for example:
```
$ sudo mkdir /OldDisk
$ sudo mount /dev/sdb1 /OldDisk
```

**USB enclosure**
This one is more easy. Just connect the disk and it will be auto mounted (probably on /media). If not, use the same method described above.

There's some enclosure that don't get recognized when plugged. In that case restart the machine with the disk connected and turn on.


I hope this helps.
Regards.

---

### Post by goatroper on 2010-10-30
Thank you very much for your thorough and easy to follow directions.  I am using a HP laptop so usb mounting of the old hard drive is the only way as this one has no esata plug.  Thanks again and I'll let you know if all is successful.

---

