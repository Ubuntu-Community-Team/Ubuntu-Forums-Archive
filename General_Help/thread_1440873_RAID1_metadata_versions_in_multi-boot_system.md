---
title: "RAID1 metadata versions in multi-boot system"
date: 2010-03-28
forum: General Help
---

### Post by rac9876 on 2010-03-28
I have used the "Disk Utility" in Ubuntu 10.04 (with a 64-bit 2.6.32.17 kernel) to create a RAID1 array (/dev/md2), and have successfully edited mdadm.conf and fstab to get the array to automatically start and mount. The array contains a single EXT3 partition.

I chose EXT3 rather than EXT4 because I wanted the new RAID1 array to be compatible with a version of 64 Studio 3.0 that I also use on the same machine for audio recording. That OS is based on a realtime 64-bit 2.6.29 kernel. Unfortunately, 64 Studio does not seem to recognize the new RAID1 array.

I suspect this may be because the new RAID1 array uses a version 1.2 superblock (metadata) while my two other RAID1 arrays (/dev/md0 and /dev/md1), which are both recognized fine by 64 Studio, use version 0.9 superblocks.

Is the version 1.2 superblock too new for the 2.6.29 kernel to understand? Is it possible to get this older version of Linux to recognize and automount the array with the 1.2 superblock, or do I have to rebuild the array from scratch with a 0.9 superblock to get it to work in both OSs?

---

### Post by rac9876 on 2010-03-29
Never mind - I figured it out.

In 64 Studio, "mdadm -Ds" did not show the new array. But then I found that "mdadm -Es" did, showing the details of all three arrays:

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=22ae6a2c:3e83592f:50ba6ed3:02cbdd17
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=1dc0f693:61c7a00e:40235ec8:3f2839b1
ARRAY /dev/md/LinuxData level=raid1 metadata=1.2 num-devices=2 UUID=a27fa202:c76780de:51069ca2:1411e618 name=:LinuxData

I just changed that "/dev/md/LinuxData" from the last line to "/dev/md2" and pasted the line into /etc/mdadm/mdadm.conf. This enabled 64 Studio to start the array.

---

