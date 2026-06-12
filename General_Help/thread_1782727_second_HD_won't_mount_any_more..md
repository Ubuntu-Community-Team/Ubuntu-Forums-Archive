---
title: "second HD won't mount any more."
date: 2011-06-15
forum: General Help
---

### Post by rhythmiccycle on 2011-06-15
It was working fine, then all of a sudden, When I try to open my second HD i get the message

> 
Unable to mount 250 GB Filesystem

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



is there any way I get access the files?

I did this:

```

$ sudo fsck /dev/sdb
 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?

```

and when I look at the drive in Disk utility, it just says "unknown"

this makes me think the that partition table was corrupted. idk

is this fixable?

---

### Post by nomko on 2011-06-15
What's the output of:
```
cat /etc/fstab
``` 
(do this in a terminal)
Post the output here.

---

### Post by rhythmiccycle on 2011-06-15
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=2e40d1e2-01d6-4a5d-84ed-21006128c93c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ffb0bdbd-9796-4dea-8dd2-30c4874feaa2 none            swap    sw              0       0

---

### Post by tredegar on 2011-06-15
> I did this:

Code:

$ sudo fsck **/dev/sdb**

**/dev/sdb** is the *device*. You (maybe) need to **fsck** the *partition* eg /dev/sdb1

> In some cases useful info is found in syslog - try
dmesg | tail 
So, does dmesg have any useful information?
With the disk plugged in, what is the output of ```
sudo fdisk -l
```?

What did you recently do that might have caused this to happen?

---

### Post by rhythmiccycle on 2011-06-20
It started working again. I didn't do any thing, but reboot a few times. I'm glad its working, but I wish I understood Why the problem happened. 

I see it is as, rebooting is the novice way to solve a problem.  A part of me wants to know the deeper inter-workings of the computer, even if things can work just fine with out the knowledge.

```


$ sudo fdisk -l


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb5bd2b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1852    14872576   1b  Hidden W95 FAT32
/dev/sda2   *        1852       38998   298375784+   7  HPFS/NTFS
/dev/sda3           38998      121602   663512065    5  Extended
/dev/sda5           38998      121112   659581952   83  Linux
/dev/sda6          121113      121602     3929088   82  Linux swap / Solaris

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7688443

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24792   199141708+   7  HPFS/NTFS


```

---

### Post by vanadium on 2011-06-20
Your second drive contains one partition with an ntfs file system, the file system used by MS Windows. Even though it works again, you may need to check the file system using the MS Windows disk checking tools.

---

