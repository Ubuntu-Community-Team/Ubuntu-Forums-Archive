---
title: "mdadm Raid 5 Question"
date: 2010-08-15
forum: General Help
---

### Post by doktarZues on 2010-08-15
I followed the instructions here: [https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid) to create a raid 5 array using three 1TB drives, looking for a 2TB volume at the end of the rainbow.  As far as I can tell, everything went well (no errors or instructions that I skipped).  Now that the array is created, it shows as a 2 TB capacity in Disk Utility but when I mount it it's showing that it's only 1.7 TB.  I understand from reading that there may be a superblock that goes on each drive that could measurably lower the overall array size, but ~300 GB? 

One nuance that I suspect may be relevant is the fact that of the 3  drives, 2 are using "Whole Disk" and the other  has an MBR partition on it (that I thought was the entire drive, not sure I know how to validate that).  Using fstab -l /dev/sda (the partitioned  disk) it looks like it's fine, but not entirely sure I know what I'm  looking at.  

So my real question is--is this normal and there's nothing I can do about it, or what can I do to get that 300GB back?  I'm tempted to just kill the disk with the partition on it (proof of concept--the array should work just fine with only 2 disks, right?) and let it rebuild as a WHOLE DISK like the others and either correct the problem or eliminate that variable. 

Any guidance or help is greatly appreciate..thanks for reading

Here is the fdisk output for the partitioned disk:

> $ sudo fdisk -l sda

Disk sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50a350a2

Device Boot      Start         End      Blocks   Id  System
  sda1               1      121601   976760001   fd  Linux raid autodetectHere is a screenshot of the array from disk utility

[IMG]http://i144.photobucket.com/albums/r189/doktarzues/Screenshot-1.png[/IMG]

---

### Post by doktarZues on 2010-08-17
bump

Has anyone ran into this before?  I may just be ignorant but ~300 GB sounds like a lot of overhead;  I'm 200GB away from being better of with mirroring the disks..

I already have 600gb of data on the array with no where to park it so I've so far been too chicken to kill the partitioned disk and see if that is the problem.

---

### Post by john newbuntu on 2010-08-17
The system reserves around 5% of your filesystem for administrative reasons.  You can check the reserved block count on the array.
sudo tune2fs -l /dev/md0

Divide the ""Reserved block count" by "Block Count". Multiply by 100.  You should find this to be close to 5%.  If true, you could reduce this to say 1% using the command:
sudo tune2fs -m1 /dev/md0
This way you can get over 200GB back.

As far as your statement:
> **doktarZues said:**
> ... of the 3   drives, 2 are using "Whole Disk" and the other  has an MBR partition on  it (that I thought was the entire drive, not sure I know how to validate  that).. 
Actually all 3 drives are used for RAID5 as the screenshot says or check with "cat /proc/mdstat". MBR is a teeny tiny portion on your drive - it does not take up your entire drive.  You may already know this: since you have used RAID5 the space equivalent to one disk gets allocated for parity.

---

### Post by doktarZues on 2010-08-17
Excellent.. thank you!

---

