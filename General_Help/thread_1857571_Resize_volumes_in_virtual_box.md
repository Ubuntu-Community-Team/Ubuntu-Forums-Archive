---
title: "Resize volumes in virtual box"
date: 2011-10-10
forum: General Help
---

### Post by Bradburts on 2011-10-10
I have create a virtual machine under Virtual Box and have /root & /swap partitions.
I would now like to create a /backup partition.
I don't have any virtual disk space left to create the new partition.
 
lvreduce -L2G /dev/Develop/root 
 
warns me that I may loose everything. I could clone but I am not sure if all data losses would be immediately noticed?
 
I am sure that VB told me that I could increase the physical volume latter, how do I do that?
I am guessing that its not safe to reduce the /root partition whilst mounted?
 
Also fdisk -l reports:
Device Boot Start End Blocks Id System
/dev/sda1 * 1 32 248832 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2 32 1045 8136705 5 Extended
/dev/sda5 32 1045 8136704 8e Linux LVM
 
Does that mean I have another 8Gb drive available?

---

### Post by haqking on 2011-10-10
> **Bradburts said:**
> I have create a virtual machine under Virtual Box and have /root & /swap partitions.
I would now like to create a /backup partition.
I don't have any virtual disk space left to create the new partition.
 
lvreduce -L2G /dev/Develop/root 
 
warns me that I may loose everything. I could clone but I am not sure if all data losses would be immediately noticed?
 
I am sure that VB told me that I could increase the physical volume latter, how do I do that?
I am guessing that its not safe to reduce the /root partition whilst mounted?
 
Also fdisk -l reports:
Device Boot Start End Blocks Id System
/dev/sda1 * 1 32 248832 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2 32 1045 8136705 5 Extended
/dev/sda5 32 1045 8136704 8e Linux LVM
 
Does that mean I have another 8Gb drive available?

you can resize a virtual hdd, but easier to create a new disk and attach it, just like having putting an extra HDD in the machine

---

### Post by Bradburts on 2011-10-11
Thanks.
I suppose I am asking;
Is it safe to resize the virtual hard disk whilst mounted? lvreduce warns me that the world may end.
Secondly why do I have sda2 & sda5 ?
 
EDIT:
I reduced the volume, the world did not end, not immediately!
 
sudo lvcreate &#8211;name backup &#8211;size 1G Develop
 
fails with:
Command failed with status code 5.
 
being an ex windows programmer:
 
sudo shutdown -r now
 
failed. So I now know that you cannot reduce a mounted disk.
 
Is the only way to increase physical storage to add another disk?

---

### Post by Bradburts on 2011-10-11
Have added a new virtual disk & that is easy enough.

---

### Post by haqking on 2011-10-11
> **Bradburts said:**
> Have added a new virtual disk & that is easy enough.

sorry didnt get back to it earlier.

Cool you got it sorted then, you can also in future boot your VM to a gparted or similar live CD to manipulate the disks without them being mounted etc.

anyways all sorted.

cheers

---

