---
title: "how to convert and add ntfs to ext4"
date: 2012-01-06
forum: General Help
---

### Post by malikge on 2012-01-06
Hi,
I have both window7 and ubuntu 10.04 installed on my pc.
I have a 19GB NTFS partition that I want to convert into ext4 and then add it the ubuntu ext4 partition.

In System >> Adminstration >> Disk Utility

there are option of deleting, edit file system , format volume,
I am confused to what to do to convert and then add this NTFS partition to ext4

---

### Post by ajgreeny on 2012-01-06
You need the two partitions you want to amalgamate side by side to do what you want;  if not you will have to move a partition from between them to the end of the disk.  That is possible but can be very long winded to do, possibly taking hours.  To do either you should boot to a live ubuntu CD/USB and use gparted from that, as you can not act on any linux partition while it is mounted.

If you are not sure about any of this, copy a screenshot of the gparted window back here, and it should be possible to give you more recommendations.

---

### Post by malikge on 2012-01-06
Any more recommendations...
I am still kinda confused.

Thanks

---

### Post by dcstar on 2012-01-07
> **malikge said:**
> Hi,
I have both window7 and ubuntu 10.04 installed on my pc.
I have a 19GB NTFS partition that I want to convert into ext4 and then add it the ubuntu ext4 partition.

In System >> Adminstration >> Disk Utility

there are option of deleting, edit file system , format volume,
I am confused to what to do to convert and then add this NTFS partition to ext4

You cannot "convert" any existing partition. You must delete it and then expand the existing EXT4 partition into any adjacent free space using the instructions in the other post.

There are already hundreds of threads in the forum addressing this topic.

---

### Post by Paqman on 2012-01-07
Obviously you'll need to back up any data on that NTFS partition first.

Then boot up into a LiveCD or USB, right click on your swap and "swapoff", delete the NTFS partition and expand your extended partitionto the left, and move or expand the partitions within.

This will take ages to complete, especially if you've got a spinny magnetic disk.

---

### Post by malikge on 2012-01-08
I have deleted the NTFS partation and now want to add this unallocated space into the /dev/sda5 partition.
But sda5 does not give any option of extending. 
sda2 gives the option to extend to right.

I want to add unallocated partition to sda5( which is ubuntu partition)

---

### Post by Paqman on 2012-01-08
> **malikge said:**
> But sda5 does not give any option of extending. 


That's because it's contained inside the extended partition (sda4). If you expand sda4 you'll be able to move or expand sda5.

---

### Post by raja.genupula on 2012-01-08
` Actually sda1, sda2 are primary and all other are sub partitions of extended partition .

so i think you directly not able to do it . First try to add that free unallocated space to extended partition i mean to sda4 and then try to add it to sda5 .

This is what i actually thinking , give a try . 

all the best. :):)

---

### Post by raja.genupula on 2012-01-08
> **Paqman said:**
> That's because it's contained inside the extended partition (sda4). If you expand sda4 you'll be able to move or expand sda5.
oops same submission time man .
@op,let us know what you got .

---

### Post by malikge on 2012-01-08
Thanks guys...
After adding unallocated space to sda4, I am able to add it to sda5.

Thanks again.

---

