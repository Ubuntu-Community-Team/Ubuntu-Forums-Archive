---
title: "Grub error 22 Help Needed!!!"
date: 2009-07-11
forum: General Help
---

### Post by Gusarich on 2009-07-11
Hi everyone,
Thanks to my noobish curiosity i messed up the grub.
I have 2 hard drives. One of them has Ubuntu and the other one has Windows on it.
My problem happened long ago but after hopelessly trying to resolve it i left it as it was for a few months.

While everything was working, i wanted to gain access to my ubuntu drive while using windows. 
I googled for some time and found some program that promised to do what i wanted. After foolishly playing around with it, i noticed that i can no longer boot from my ubuntu hdd because it threw some grub error 17 (im not sure though because this was long ago).
After following some instructions on the ubuntu forums, the error changed to GRUB Error 22 which i still can not fix.

Since then i couldnt anymore boot into my ubuntu hard drive and neither my windows and the ubuntu LiveCD could see the ubuntu hard drive.
None of the instructions seem to work for me.


All info i could get is here:

```

sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00057a21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           0           0           0    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sda2       614566575   625137344     5285385    5  Extended
/dev/sda5       614566638   625137344     5285353+  82  Linux swap / Solaris

```Please help me resolve my problem. I have tonns of extremely valuable info on the hard drive.

Thanks in advance!

---

### Post by lindsay7 on 2009-07-11
The partition sda1 is messed up. It is marked as the boot partition and it does not end on a cylinder.

And I am not sure there is a system installed here. Let me look at it again

---

### Post by lindsay7 on 2009-07-11
Can you post the results of sudo fdisk -l

---

### Post by Janeway on 2009-07-11
Hi,

seems that some boot sector or grub config files have been destroyed.
I would try to start an ubuntu LiveCD and mount the sda1/sda3/sda5 partitions and see if there's data on them.

If not, the file system is destroyed and there's no easy way to save data/repair the system. A new installation is easier then.

If you find the ubuntu partition, use chroot to change to it and do either grub-update or grub-install on it. 

That should restore the boot sector so that you can boot Linux and Windows again. If that doesn't work, you could also try to install lilo.

My own experience has shown that repairing grub often fails and that a new installation takes les time.

If the filesystem is still online, you could also try to boot linux with the super-grub-disk and then save your data. Especially it is better to have different partitions for data and system.

Best regards
Tuvok

---

### Post by usstitan on 2009-07-11
hi there, i recently put ubuntu on a laptop that is running on windows vista and have them dual booting, made a slight mistake though and only gave ubuntu 2gb to install too so when trying to alter this i accidently booted the pc using windows recovery instead of the normal option. and doing that gave the same grubb error 22 that you have even though i made no changes. so i couldn't boot up either windows or ubuntu. so because i had to alter my partition anyway and there was no personal data on the ubuntu partition i booted the computer with the ubuntu cd and reinstalled ubuntu making the partition larger. once this was complete i was able to boot the computer on ubuntu and windows and i didn't loose any of my data i keep on windows so a reinstall fixed my grubb error. there may be a better way to fix the error but a reinstall only took me 20 minutes and the computer was working fine, so as long as there is no data you need perhaps consider a reinstall. i only did it though cause i messed up.

---

### Post by Gusarich on 2009-07-11
Im a complete noob at this. Can you please be more specific with the instructions? 
I need to recover the data badly. I must to try whatever i possibly can... 

The error changed to 22 after a few commands in the terminal while using the ubuntu liveCD. With error 17 i still could see everything i had on the hdd. 
Hard to believe that a command in the terminal (which i can no longer remember) could damage ubuntu so badly. =(


```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf53af53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00057a21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdb2           38256       38913     5285385    5  Extended
/dev/sdb5           38256       38913     5285353+  82  Linux swap / Solaris

```

---

### Post by lindsay7 on 2009-07-11
Ok, this is what I see,

hard drive 1 or sda looks ok and that is where windows is located

hard dirve 2 or sdb has problems the boot partition sdb1 is empty and there is a problem with how it is set up since it says it does not end on a cylinder boundary.  There are two overlapping partitions at the end of the drive for the root partition and the swap partition. It looks like that that space is around 5 gigs and it could have data there or not, since the root partition and the swap partition overlap and nomally the swap partiton can not store data.

We can try to delete the partition sdb1 and then reinstall the grub menu, but first lets take a look at those partitions

go to the menu bar and under system/administration you will see Gparted or partition Editor open that and go to the drive sdb there is  button on the top right corner to change between drives. Find the screen shot application under appilcations/accesories and take a picture of the gparted screen. it can then be found on your desktop. open the reply screen to this post and click on the paper clip and browse to the desktop and picture and  click upload, then click on the paper clip again. post the results here.

---

### Post by Gusarich on 2009-07-11
Do you mean that there can be only 5gb of data left?... i had at least 60gb of raw video from my camcorder on the hdd and about 10gb of photos.

Here is the screenshot:
[ATTACH]120725[/ATTACH]

---

### Post by lindsay7 on 2009-07-11
Here is the screenshot:
Click image for larger version Name: Screenshot.png Views: 0 Size: 372.9 KB ID: 120725

As you can see there is an unallocated space that must have been your root directory and where your data was,  all that is left is the extended partition that contains the swap partition. As you can see on the gprated graphic this space is empty.  So, unless you can recover some data and files using something like the "Testdisk" appication, as far as I know this disk is empty.  
Sorry to have to tell you that, maybe someone on the forum knows something else or has an idea for recovery.  Sit tight for a while and see if you can some other advice on solving your situation.

PS:  You may want to start a new post and sak for help recovering your drive, right now this is not a grub problem, that way you can get some additional help!

---

### Post by Gusarich on 2009-07-11
Well... thanks a lot anyway. Ill wait here and post on some more forums.
If nothing helps ill have to give it away to professionals and pay a ******** of money for the recovery.

---

### Post by lindsay7 on 2009-07-11
Why not download "Testdisk" it is free, and try to recover what you can.  You can not harm the drive by running it.

---

### Post by unutbu on 2009-07-11
Gusarich, it is possible that your problem stems from a broken partition table. (No guarantees, but the following may help and at worst, it will not harm.)

Boot from your LiveCD.
Open a terminal (Applications>Accessories>Terminal), and type

```
cd ~/Desktop
wget http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2
tar xvjf testdisk*.tar.bz2
sudo testdisk-6.11.3/linux/testdisk_static /dev/sdb

```
This will run testdisk on your second hard drive, sdb.
testdisk can repair certain problems in partition tables.

Choose "Proceed","Intel","Analyze","Quick Search","Deeper Search".
This may take a while. 
When it is done you should see a list of partitions. 
Use the up/down arrows to select partitions.
Press "p" to see if you can list the files inside the partition.

Post back with the result of the Deeper Search, and indicate which lines correspond to partitions which have readable files in it.

---

### Post by Gusarich on 2009-07-11
Yay!!! The Testdisk Worked! :p
20 Seconds and done..... unbelievable.

Thanks a lot to everyone! You saved my life! :p

---

### Post by lindsay7 on 2009-07-11
I am happy for you. I know the feeling of losing a system. It is a good thing I do not keep anything sharp around my computer room.

Anyway, good for you! As a word of advise, BACKUP!!!1

---

