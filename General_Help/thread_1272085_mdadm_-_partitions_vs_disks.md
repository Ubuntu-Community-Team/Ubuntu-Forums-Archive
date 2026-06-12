---
title: "mdadm - partitions vs disks"
date: 2009-09-21
forum: General Help
---

### Post by pingtoft on 2009-09-21
I recently set up my first RAID5 with mdadm using this [howto]("http://ubuntuforums.org/showthread.php?p=3420959") I found in the howto-section.
One thing is confusing me: In the howto (and other howtos I've found elsewhere) partitions were created first and used to build the arrays.
I just added the raw disks to the array and that seems to work just fine.
Is there something I'm missing or is the initial creation of partitions redundant?

---

### Post by bblis001 on 2009-09-21
When I was reading about creating Raid5 setups myself with mdadm, I saw it posted both ways.  When I finally set mine up, I did the same as you, whole disks.  So far no problems, and I have installed several versions on Ubuntu as well as Debian and Fedora (all clean installs) and was able to rebuild the array each time with no problems without using the mdadm.conf file.

If I remember correctly, you can setup the raid so it only uses certain partitions on the disk, leaving the rest of the space for whatever.
I am pretty sure this is correct, but have not done it myself.  Sure someone will chime in if I am wrong though.

---

### Post by ian dobson on 2009-09-22
Hi,

You can do it either way (Raw disk or Partition) mdadm supports both. 

I usually create a partition on each disk (Thats abit smaller that the size of the drive) and then create the RAID device using the partition. I do this so that when the harddisk dies I can install a new harddisk thats atleast the same size, create a partition and add to array. With a raw device your stuck with the device size.

Regards
Ian Dobson

---

### Post by pingtoft on 2009-09-22
That's a good point. If I had realised that before I built the array I would have created partitions first.

Thx for the answer :)

---

