---
title: "error mounting mount exited with exit code 13"
date: 2011-03-29
forum: General Help
---

### Post by RoaringMuffin on 2011-03-29
Hey guys my windows xp system has recently been messed up, everytime i boot, i see the windows logo and then it reboots so i decided to liveboot ubuntu in order to recover the important files on my hard drive and then reboot. Problem is when i try to click on my "500GB Filesystem" I get this message.
 
Unable to mount 500GB Filesystem
 
Error mounting: mount exited with code 13:ntfs_attr_pread_i:ntfs_pread failed:/input/output error Failed to read NTFS $Bitmap:Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk/f on Windows then reboot into Windows twice.The usage of the /f parameter is very important! If the device is SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/directory,(e.g./dev/mapper/nividia_eahaabcc1). Please see the 'dmraid' documentation
for more details
 
If anyone has any info plz help! Keep in mind I'm a total noob at ubuntu but I intent to stick with it after my files are recovered -Thanks

---

### Post by ibokozan on 2011-06-05
please help. i am getting the same message.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fbb04c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       16512   132526080    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           16512       19123    20970497    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           19123       38914   158968832    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           16512       16637      999424   82  Linux swap / Solaris
/dev/sda6           16637       19123    19970048   83  Linux


---

