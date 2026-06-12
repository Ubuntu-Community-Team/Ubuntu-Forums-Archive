---
title: "cannot mount/format drive"
date: 2011-01-14
forum: General Help
---

### Post by JohnnyC35 on 2011-01-14
hey, I am having issues with trying to load or format a drive, and in Disk Utitlity the 1tb drive shows up as a 2.2tb drive O.o
I can't mount the drive in Disk Utility, but when I tried to format it I got this error message:
> 
Error creating partition table: helper exited with exit code 1: cannot open /dev/sdf: No such device or address


I tried to mount the drive and got this:
sudo mount /dev/sdf /media/drive
> 
mount: /dev/sdf is not a valid block device


I tried to fsck it and got:
> 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such device or address while trying to open /dev/sdf
Possibly non-existent or swap device?


dmseg gave me this:
> 
[122562.613801] sd 14:0:0:0: rejecting I/O to offline device
[122562.613818] Dev sdf: unable to read RDB block 0
[122562.613835] sd 14:0:0:0: rejecting I/O to offline device
[122562.613862] sd 14:0:0:0: rejecting I/O to offline device
[122562.613901] sd 14:0:0:0: rejecting I/O to offline device
[122562.613927] sd 14:0:0:0: rejecting I/O to offline device
[122562.613954] sd 14:0:0:0: rejecting I/O to offline device
[122562.613981] sd 14:0:0:0: rejecting I/O to offline device
[122562.613996]  unable to read partition table
[122562.614261] sd 14:0:0:0: [sdf] Attached SCSI disk


any thoughts as to what to do now or is the drive toast? :-/
thanks :)

---

### Post by plucky on 2011-01-14
Try installing and using Gparted.

```
sudo apt-get install gparted
```

Then you will find it under **System > Administration > Gparted**

Good Luck

---

### Post by efflandt on 2011-01-14
What does **sudo fdisk -l** (small L or **-lu**) show for it?  If the drive worked before and fdisk does not show something about it (even if no partition data), something is probably electronically wrong with the drive.  In that case recovering data from it may be expensive or futile (disassembly in a clean room).

---

