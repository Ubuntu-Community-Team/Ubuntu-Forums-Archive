---
title: "How to reinstall windows 7 on a ubuntu/windows dual boot drive?"
date: 2012-08-03
forum: General Help
---

### Post by xioSlayer on 2012-08-03
Can anyone walk me through the steps of reformatting windows 7 on the same drive you have ubuntu installed on?

Firstly, I already had this setup and tried to reinstall windows 7 and chose the correct partition for it (the one windows was previously on).

This destroyed my /home partition and testdisk says its not recoverable.  I thought it would be that simple but I guess I was wrong (I knew I'd have to reinstall GRUB but i thought that would be it).

Now I'm going to reformat the whole drive, reinstall windows 7 again, then install ubuntu from scratch.  However I'd like to know the process of reinstalling windows in a dual boot drive in case I ever need to reformat again so I dont destroy my ubuntu a second time.


Thank you.

---

### Post by Ubun2to on 2012-08-03
Well, you need to do Ubuntu AFTER Windows. Doing it before Windows has caused problems with the Grub bootloader, in my experience.
1. Boot into a GParted live CD. Format the drive. You need to do this because Ubuntu uses ext2, 3, and 4, which Windows can't even recognize (it only works with NTFS and FAT32).
2. Boot into the Windows install disk.
3. Setup the partitions so that you have 1 partition, and lots of free space. Adjust the Windows partition to whatever size you want. Leave the rest as free space. Select the partition you just created to be where Windows lives.
4. Then, let Windows do it's thing. You might have to install some drivers afterwards, specifically video card drivers, which are the most troublesome for Windows to install in my experience.
5. After you are comfy with your Windows partition, install Ubuntu. Boot to a USB or CD, then install it in the free space you left when you partitioned Windows. If you messed up and made it smaller than you wanted it, you can easily resize your Windows partition.
6. If you want a swap partition, you will most likely need to do that manually after the install. When you are comfy with your Ubuntu setup, you can do whatever you feel like.

---

### Post by oldfred on 2012-08-04
I do not know how Windows could have deleted your /home. It does not see Linux partitions. It has overwritten partition table info to remove extended partitions, but testdisk or other tools can usually recover that. 

Of course, before any system change you should have good backups. Sometimes unexpected things happen.

Install Windows either before Ubuntu or after:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)
 [https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)

---

