---
title: "change ntfs file system type"
date: 2012-07-01
forum: General Help
---

### Post by malikge on 2012-07-01
Hi,
I have a dual boot system.
I have a ntfs file system, on which my window7 is installed.
I am not been able to access it either through live ubuntu or installed ubuntu system, and I also cannot boot into windows.

I want to know,
if I run the live ubuntu, and from gParted, if I change the file system to ntfs or any other type, is it going to delete all my data on that partition or not?
I just want to access my data from my windows.

plz help.

---

### Post by mikewhatever on 2012-07-01
Yes, changing the file system will delete everything, don't do it.

---

### Post by malikge on 2012-07-01
Can you please tell me any other way of accessing my ntfs windows partition?
output of **sudo fdisk -l** is:
> 
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07f907f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    71682047    35737600    7  HPFS/NTFS/exFAT
/dev/sda3        71684094   156248063    42281985    5  Extended
/dev/sda5        71684096    75587583     1951744   82  Linux swap / Solaris
/dev/sda6        75589632   104884223    14647296   83  Linux
/dev/sda7       104886272   156248063    25680896   83  Linux

Disk /dev/sdb: 16.0 GB, 16047407104 bytes
255 heads, 63 sectors/track, 1950 cylinders, total 31342592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060d3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    31342591    15670272    c  W95 FAT32 (LBA)


/dev/sda2 is the C drive, that I want to access.

---

### Post by mikewhatever on 2012-07-01
What happens exactly when you try accessing that partition? Any errors? What's the output of **dmesg | grep sda2**?

---

### Post by malikge on 2012-07-01
When I try to access that partition, it gives error message:
> **Unable to mount 37 GB Filesystem**
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details. The output of **dmesg | grep sda2 **is:
> [    8.610089]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[   21.748412] Buffer I/O error on device sda2, logical block 6289327
[   21.748416] Buffer I/O error on device sda2, logical block 6289328
[   21.748420] Buffer I/O error on device sda2, logical block 6289329
[   21.748424] Buffer I/O error on device sda2, logical block 6289330
[   21.748428] Buffer I/O error on device sda2, logical block 6289331
[   21.748432] Buffer I/O error on device sda2, logical block 6289332
[   21.748435] Buffer I/O error on device sda2, logical block 6289333
[   21.748439] Buffer I/O error on device sda2, logical block 6289334
[   21.748443] Buffer I/O error on device sda2, logical block 6289335
[   21.748447] Buffer I/O error on device sda2, logical block 6289336
[   33.084363] Buffer I/O error on device sda2, logical block 6289327
[   44.496369] Buffer I/O error on device sda2, logical block 6289327
[   56.040325] Buffer I/O error on device sda2, logical block 6289327



---

### Post by mikewhatever on 2012-07-01
You'll need to find a working windows computer, and use it to check the file system. I know of no other way to fix it.

---

