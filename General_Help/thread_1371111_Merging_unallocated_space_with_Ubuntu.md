---
title: "Merging unallocated space with Ubuntu"
date: 2010-01-03
forum: General Help
---

### Post by crowderd on 2010-01-03
Community,
  I am very confused on how to merge some unallocated space into my ubuntu partition of my hard drive. I dual boot Windows and Ubuntu and decided that since I use ubuntu more then I am going to need more space. I shrunk the Windows partition using Gparted and Im left with about 45gb of unallocated space. How would I get this 50gb into ubuntu partition with out doing a fresh install of ubuntu? 

I have enclosed screenshots of GParted if they help:confused:

---

### Post by john newbuntu on 2010-01-03
You do not seem to be running out of space as you still have 63 Gigs left on your sda6.  You also have a 4GB swap - a tad bit too big.

Since you also use windows, would you want to think about converting the unallocated partition to another NTFS or FAT32 partition?  This will allow you to share data between the 2 OSs'.

The other thing is to convert the unallocated partition to ext4 to house your /home filesystem.  This way, any future upgrades will happen on sda6 leaving /home and your settings undisturbed

If you still decide to merge it with your existing ubuntu partition, you will have to boot from an Ubuntu LiveCD and use gparted from there.  You can refer the manual on how exactly to do this.  But the overall method is to highlight your extended partition (/dev/sda2) on the list and then move this to the left till it occupies the empty space fully.

---

### Post by crowderd on 2010-01-03
I have toyed around with the idea of converting the partition to a fat32 partition but have come to the conclusion of merge it with the existing ubuntu partition. That 63gb will be filled up shortly as I plan to move all my media files from the external. I dont really need windows and the only reason its still there is only for the Zune support. I dont have a copy of the Ubuntu LiveCD but I do have gparted live CD. Will that suffice? Thank you for all your help

---

### Post by 3rdalbum on 2010-01-03
> **crowderd said:**
> I have toyed around with the idea of converting the partition to a fat32 partition but have come to the conclusion of merge it with the existing ubuntu partition. That 63gb will be filled up shortly as I plan to move all my media files from the external. I dont really need windows and the only reason its still there is only for the Zune support. I dont have a copy of the Ubuntu LiveCD but I do have gparted live CD. Will that suffice? Thank you for all your help

The Gparted live CD will work as well for partitioning as the Ubuntu live CD. Possibly better. But I'm not sure if you can resize an Extended partition (the light-blue bordered partition). In fact, I'm sure you can't do it.

The idea of converting the empty space into a new partition might be your only option.

---

### Post by plucky on 2010-01-03
> The Gparted live CD will work as well for partitioning as the Ubuntu live CD. Possibly better. But I'm not sure if you can resize an Extended partition (the light-blue bordered partition). In fact, I'm sure you can't do it.


Are you sure?

The problem is the Live CD will mount the swap partition and you have to turn swap off before it will allow you to increase the extended partition.

The start of the linux partition will have to be moved before you can increase the size of the partition and all the data with it,so it will take a long time,or you could create a separate ext3 partition and mount it as a storage partition for all your data and make it accessible to your user.

See [link](http://www.psychocats.net/ubuntu/mountlinux)

Good Luck

---

### Post by crowderd on 2010-01-03
Thank you for the very quick responses!!! I did use the GParted LiveCD and it allowed me to increase the extended partition after turning the swap off. And yes this took FOREVER. I had no idea the solution was so simple. I appreciate the forums and the fact that you can actually get help and not put down or made fun of because a newbie like myself doesn't quite know everything, yet. Thanks again

---

