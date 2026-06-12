---
title: "cannot access windows files, correctly"
date: 2009-12-23
forum: General Help
---

### Post by jose1986 on 2009-12-23
So, I had just finished upgrading vista to windows 7 and what happened, ubuntu disappeared, as well as my dual boot screen. I reinstall ubuntu, check and put all the fixings on top, check. I also upgrade ubuntu to 9.1, check. Yet when I reinstalled ubuntu, the path to my windows files, just takes me to my ubuntu files, that doesnt make much sense why I would have to paths in my places menu to access my ubuntu files. I have tryed fixes but they don't stick. I know how to access my windows files via

sudo mount -t ntfs /dev/sda1 /mnt/windrive -o "umask=022"

this is only a temporary hold, it only keeps it for the session, so I cannot really save bookmarks. I was wondering if anyone knows how to change the path, so I can change my 21gb folder to the 260gb folder.....like a permanent fix.

...yes I know this is a repost but its pertinent for me!

---

### Post by lavinog on 2009-12-23
Try
```

sudo fdisk -l /dev/sda

```
Windows probably shuffled your partitions around.

---

### Post by jose1986 on 2009-12-23
How do I put them back in order?

---

### Post by unmole on 2009-12-23
Or you could try this [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by jose1986 on 2009-12-23
Ummm, this is interesting but I am brand new to this tool...so how would that help me to fix it?

---

### Post by lavinog on 2009-12-23
> **jose1986 said:**
> How do I put them back in order?

The order shouldn't matter...it is most likely that you are mounting the wrong partition...post the output of the fdisk command and we can see if we can figure out what drive you are trying to mount.

---

### Post by jose1986 on 2009-12-23
woops, i seem to have changed my windows partition from hpsf/ntfs to an extended partition...buttons are too much for me!
how can i revert it back to the normal, oh and that output you want is dependent on this...

---

### Post by jose1986 on 2009-12-23
well here is the output after i wrecked the partition types...now i have 2 problems, the revert that windows partition and access my windows files more conveniently on ubuntu


joey@ubuntu:~$ sudo fdisk -l /dev/sda
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Ignoring extra extended partition 3

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2081e8d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34870   280093243+   5  Extended
/dev/sda2           37487       38913    11454464    7  HPFS/NTFS
/dev/sda3           34871       37486    21013020    5  Extended
/dev/sda5   ?      120528      234814   918008208   4f  QNX4.x 3rd part

Partition table entries are not in disk order
joey@ubuntu:~$ sudo fdisk -l /dev/sda
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Ignoring extra extended partition 3

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2081e8d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34870   280093243+   5  Extended
/dev/sda2           37487       38913    11454464    7  HPFS/NTFS
/dev/sda3           34871       37486    21013020    5  Extended
/dev/sda5   ?      120528      234814   918008208   4f  QNX4.x 3rd part

Partition table entries are not in disk order

---

### Post by lavinog on 2009-12-23
> **jose1986 said:**
> woops, i seem to have changed my windows partition from hpsf/ntfs to an extended partition...buttons are too much for me!
how can i revert it back to the normal, oh and that output you want is dependent on this...
???...what button did you press?  What program are you using?
"Playing" with your partition table could erase **ALL OF YOUR DATA**.
Just a little warning for you because there are many things that cannot be undone when you change your partition table around.

```

Device Boot Start End Blocks Id System
/dev/sda1 * 1 34870 280093243+ 5 Extended
/dev/sda2 37487 38913 11454464 7 HPFS/NTFS
/dev/sda3 34871 37486 21013020 5 Extended
/dev/sda5 ? 120528 234814 918008208 4f QNX4.x 3rd part

```
Any idea what partition 5 is supposed to be?
Are you saying that partition 1 is for windows?...if so what partition is for ubuntu?
Partition 2 looks like a windows file system...try mounting that
```

sudo mount /dev/sda2 /mnt

```
then go to /mnt and see what files are in there.

---

