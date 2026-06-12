---
title: "Installation on two hard drives help"
date: 2006-04-23
forum: General Help
---

### Post by Olaniyan Ibn Yusuf on 2006-04-23
Okay this is what i have going on. I have two hard drives both 80 GBs. I want to be able to mount the /home directory so that it takes up PART of hda and then the rest of hdb

I figured I would use raid0 as this would be the most efficient way of writing data across to physical disks or so I have always been taught. While reading through a LVM guide supplied I found on the net it seems you can do similiar things with just using LVM which would mean I don't really need RAID0.

However I am still a little lost on the entire process and here is why.

1. I know that /boot and / can not be a part of a LVM group if I read properly so they will be created first on hda. /boot will get 100M and / will get 45 GB (do you guys think that is enough?)

2. Once /boot and / are assigned how do I go about assigning the rest of the space on hda as a logical volume so that I can created a volume group and add it to the group? Also how do i get it to span /home from part of of hda to part of hdb?

3. how do I leave a little space at the end of hdb so that I can maybe either create a /tmp folder which I heard was good to do or a /opt folder which I also heard was good to do.

Long story short, I am not sure given my situation which is better to go with, a software raid or a LVM, and how do i go about setting up a /home partition with in the LVM system which will allow me to write data across to physical drivers.

---

### Post by sitedesign on 2006-05-22
For this example I will go by my experience: I tend to find that 5GB for / is plenty, I don't bother with a seperate /boot partition unless it's a server, swap  of 512MB seems good for most machines and home as big as you like. Remember you can always just add more disks and mount them to directories under you home folder later such as /home/downloads could be on a different disk to /home all simple but very useful.

It is quite simple. nRun the install CD/DVD then when on the partitioning screen select manually edit.

If the drives are clean then no problems, if you have windows on the machine then be careful not to delete or change that partition.
1) create a new partition on HDA with a size of say 5GB and use it as root with ext3
2)create another partition of say 512MB on HDA and use it as swap.
3) create another partition on HDA of the rest of the disk and use it as phisical partition for LVA
4) do the same again for HDB but don't use all the disk say 90%
5) no select the LVA group and create your home partition in it with ext3

Done.

---

