---
title: "Resize Ubuntu Partition"
date: 2012-08-08
forum: General Help
---

### Post by hgergo on 2012-08-08
It's there a way to resize ubuntu partition whitout using live CD/usb whit Gparted?

The 3 GB additional free space is ready (made whit acronis form windows but there i have a problem that acronis detects the ubuntu partition filesystem as ext3 but the file system is ext4 and i don't want to mess whit it).
Is there a way ti make it or i need live cd/usb to do that? (i have boardband connection whit data limit so i can't download the image :( )
Thx in advance

---

### Post by Cheesemill on 2012-08-08
You have to use a Live CD as you can't resize a partition while it's being used. I don't know of any Windows applications that I'd trust to resize Linux partitions.

Just to make sure though, can you post a gparted screenshot from your running system.

---

### Post by coffeecat on 2012-08-08
You cannot resize your Ubuntu root partition from the running system because you cannot resize a mounted filesystem. If you are limited to download bandwidth you could consider downloading the Gparted live CD ISO from here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

That is currently 128MB, much smaller than the nearly 700MB of an Ubuntu live CD. Would that be small enough?

If you do download and run the Gparted live CD, it will probably automount your swap partition, which may or may not hinder you from resizing your Ubuntu root partition depending on your partition layout. If this is a problem, right-click on the swap partition and choose "swapoff".

Acronis is a good product. However, some 3rd party Windows partitioning tools can create inconsistencies in the partition table which do not interfere with either Windows or Ubuntu booting up and running, but which do confuse Gparted. I don't know whether Acronis is prone to this, but if Gparted reports "unallocated" for your hard drive, this would be the problem. In such a situation Gparted is wrongly reporting the drive as unallocated because it has been confused by the partition table irregularity. The fix is fairly straightforward, and if you see this, post back and we can look into this.

Another cautionary note. Resizing partitions always carries the (small) risk of data loss and possibly loss of whole partitions. Make sure you have backed up all important data before you attempt to resize your Ubuntu partition.

I don't know about Acronis reporting ext4 as ext3. Is that an old version of Acronis?

---

### Post by hgergo on 2012-08-10
I will download it today and i will try it!

Acording now to acronis my partition is so

-C NTFS--D NTFS--3GB unallocated--Linux root--Swap-

If i want to put from unallocated tabel 2GB to ubuntu and 1 GB to swap it is ok or i wil have swap partition in the midle and on the end or Gparted will move the file how it should be?

---

### Post by coffeecat on 2012-08-10
It depends whether your Ubuntu root and swap partitions are logical partitions inside an extended partition, or are primary partitions, and whether the unallocated space is inside or outside any extended partition. Either way, you should be able to do that.

If you have Gparted already installed in Ubuntu, post a screenshot of a Gparted window (alt + PrintScreen). You won't be able to do anything else with Gparted in your running Ubuntu, but at least we'll see what your partition layout is like. Just knowing the order of the partitions as shown by Acronis is not sufficient information.

---

### Post by hgergo on 2012-08-10
So here is the screenshot

---

### Post by coffeecat on 2012-08-10
You can't move the swap partition from the end to the middle without deleting the old swap partition and creating a new one. This would mean that you would then have to edit /etc/fstab to ensure that the new swap is mounted. Instead I suggest you do this from the Gparted live CD:

1 - If there is a key symbol by the sda6 swap partition, right-click on it and choose swapoff. Without doing this you won't be able to resize sda3.

2 - Resize the extended partition (/dev/sda3) to include the 3GB unallocated.

3 - Move and resize the sda5 partition (your Ubuntu root partition) to include the currently unallocated space and to leave extra space for your swap partition to the right. You should be able to do this in one go from the Partition menu -> Resize/move. If not, simply move it into the unallocated space and then go to the next step. Note that this step will take a long time, perhaps an hour or more.

4 - Resize the swap partition to the left.

5 - You only need this step if you were only able to move sda5 in step 3. If so, simply resize it to include any space you've left between it and the swap partition.

As always, backup all valuable data before adjusting your partitions.

---

### Post by hgergo on 2012-08-10
Thx for the help all works fine

---

