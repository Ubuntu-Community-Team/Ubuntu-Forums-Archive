---
title: "Cannot mount 3T ntfs partition with GPT"
date: 2011-06-18
forum: General Help
---

### Post by gharris999 on 2011-06-18
I have a 3T hitachi hard disk partitioned by Windows 7 and formatted as NTFS that I'm unable to mount under Ubuntu 11.04.  The disk is in an external enclosure connected via USB2.  Windows 7 has no problems seeing the partition and mounting the drive.

gdisk reports:

```
# gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Warning! Secondary partition table overlaps the last partition by
4294966385 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sdb: 1565565872 sectors, 746.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): EC079B08-FF64-4964-819D-75656ABA67EA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1565565838
Partitions will be aligned on 8-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192      5860532223   2.7 TiB     0700  Basic data partition

```
All attempts to mount /dev/sdb2 under Ubuntu 11.04 fail with:
```
# mount -t ntfs-3g /dev/sdb2 /mnt/external
ntfs-3g: Failed to access volume '/dev/sdb2': No such file or directory


```
How do I go about mounting this drive?  Again, Windows 7 has no problem seeing this partition.

---

### Post by oldfred on 2011-06-18
Another thread with similar issues.

See posts by srs5694
[http://ubuntuforums.org/showthread.php?t=1490819](http://ubuntuforums.org/showthread.php?t=1490819)

---

### Post by srs5694 on 2011-06-18
It looks like there's a 32-bit assumption somewhere in the hardware or software chain for Linux, but presumably not for Windows. (I say this because gdisk is detecting the disk as being just 746.5GiB in size, which is what you'd expect if some critical driver is using a 32-bit value, rather than a 64-bit value, to store the disk's size.) I don't know of any configuration option that will fix this; it's a bug, wherever it is, and I'm afraid I don't know where that is, although my guess is it's in the USB disk handling code.

---

### Post by oldfred on 2011-06-18
Are you running 32bit Ubuntu or 64bit?
```

uname -a
```

i386 or i686 = 32-bit
x86_64 = 64-bit

---

### Post by srs5694 on 2011-06-19
My comment about 32- vs. 64-bits has nothing to do with the architecture you're running -- or at least it shouldn't! (There could be a bug that shows up only on 32-bit systems, though.) 32-bit systems are perfectly capable of using 64-bit sector values and, therefore, disks of over 2 TiB.

---

### Post by gharris999 on 2011-06-19
> **srs5694 said:**
> It looks like there's a 32-bit assumption somewhere in the hardware or software chain for Linux, but presumably not for Windows. (I say this because gdisk is detecting the disk as being just 746.5GiB in size, which is what you'd expect if some critical driver is using a 32-bit value, rather than a 64-bit value, to store the disk's size.) I don't know of any configuration option that will fix this; it's a bug, wherever it is, and I'm afraid I don't know where that is, although my guess is it's in the USB disk handling code.I'm using 11.04 desktop, 32bit on a ThinkPad T60.  You may be on to something, speculating about a 32bit limitation in the USB driver.  I believe that I've successfully mounted similarly partitioned and formatted drives when they've been connected via SATA.  I'll double check with this drive when I have a chance later next week.  If it does mount via SATA, I'll appreciate some help formulating a bug report.

---

