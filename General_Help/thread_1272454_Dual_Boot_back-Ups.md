---
title: "Dual Boot back-Ups"
date: 2009-09-22
forum: General Help
---

### Post by mikeody on 2009-09-22
Hello All,
I have a lot of exposure to various Windows OSs and am just starting out with Ubuntu Jaunty. I am really impressed with Jaunty and things are going well so far.
I have a 160GB SATA hard drive partioned roughly equally between XP and Ubuntu. I am dual booting with GRUB and all works well.
My immediate concern now though is how to guard against a 'nasty accident' to either of the partitions - a lot of work has gone into all this and I want to be able to restore either or both partitions if necessary.
What is the best way to go ? What back up/ imaging software seems to work best with a Windows/Ubuntu dual boot ?
Should I be looking to back up each partition separately ? But if so what about GRUB ? Or should I be looking to completely copy the whole 160GB drive onto say an external hard drive ?
How do you guys approach this issue ?
Any help and advice would really be great. Thanks.
Mike

---

### Post by Sir Jasper on 2009-09-22
Hi,

If affordable, I would go for a 500 GB drive (or at least 320 GB so you can have two complete clones). An internal drive, set to slave, would likely be faster and more convenient but an external drive would be more secure in that it could be stored in a separate location.

I would then clone the whole of the original drive to the new drive.

Then I would consider if it might be of advantage to have a shared partition on the original drive. Music, pictures, pdfs and many documents could doubtless be read by either system.

I would then boot from the original ´buntu CD and use gparted to adjust my old drive partition sizes and add any new partitions.

Personally, I like HDClone 3.8 standard version for cloning operations. It has SmartCopy for NTFS, FAT32 and EXT 2, EXT 3 which is fast. However, EXT 4 or absolutely any File System/files can be cloned using the Physical 1 to 1 cloning option (ie all free space is cloned but it usually takes significantly longer than SmartCopy). The standard version costs about £35 but in some 30 months it has never let me down and I have long since ceased using the verify option.

Certainly, if you go for a larger internal hard drive you can use the free version of HDClone to see what you think of it.

Once everything was to my liking I would repartition my new hard drive with partition sizes identical to my newly adjusted original drive (with everything in duplicate - except I would not copy any Swap partitions).

HDClone will copy everthing including MBR/Grub but others will have free alternatives and if they do not post here then google or search here.

Personally I would clone each system regularly twice a month say 15th and 30th of each month and before any major update or system change.

If you go for a 500 GB you could use the extra space to clone an image of your original drive (as opposed to a copy) whenever you wish to.

My regards

PS Some users set up a separate ´buntu Home partition but if you have clones this does not appeal to me. Also keep taking Windows and ´buntu  backups.   

Finally, I am not an expert but a similar method to that described above has worked extremely well for me.

---

### Post by mikeody on 2009-09-22
Thanks for all that information.
I am particularly interested in HDClone as I have had some 'strange' experiences with other 'Copy Entire Disk' software whilst running just Windows. Drive Image 7 [now Symantec] was a famous example in that whilst it worked well backing up [and restoring] just a single Windows partition, when you wanted to 'Copy entire Disk' it seemed to clone the disk OK but when the time came to write it back it never worked. Others seem to have had similar experiences with that software.
Thanks again,
Mike

---

### Post by Sir Jasper on 2009-09-23
Hi again,

Restoration from partition to partition is hugely quicker than restoration of partition to drive. So, personally, I would favour cloning from partition to partition not only for speed but also because in the case of any hard drive failure it  seems to me to have a greater chance of simpler successful recovery.

My regards

PS Partition>Image>Partition would work just as well.

---

