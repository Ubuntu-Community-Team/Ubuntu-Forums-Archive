---
title: "dual boot with windows 7: cannot resize win7 partition"
date: 2010-08-08
forum: General Help
---

### Post by darklord06 on 2010-08-08
hello,

I am writing this post because i would need some help regarding the installation of ubuntu 10.0.4 on my HP pavilion DV5000 laptop.
I previously installed windows 7 in my laptop and i would like to have ubuntu and windows 7 in dual boot. in order to do that i need to free up some space to be able to install to create partitions for ubuntu and the swap even if I have 30GB of unused space.

when i launch the live cD and i reach the step 4 ubuntu is actually recognising three operating systems installed:

- windows 7 (loader) under dev/sda1 (92,86GB)  NTFS
- windows NT/2000/XP (which is corresponding to my "HP recovery" partition) under dev/sda2 en FAT32 (6,2GB)
- windows XP embedded (I don't unerstand what it is) under dev/sda3 NTFS (1,1GB)

when I go to the step 6 to modify the size of sda1 to free up some space, i don't have the possibility to change it, i can read "unknown" under the used space collumn.
I also tried to resize this partition using gparted but unfortunately i had the same problem, when i select it all the options to modify it are greyed out and i can notice a key near the hard drive logo (is it locked ?).

anybody knows what is going on or what I should do ?

thank you

---

### Post by pania on 2010-08-08
This might help you

[http://pcsplace.com/tutorial/how-to-dual-boot-windows-7-ubuntu-linux-install-run-ubuntu-on-windows/](http://pcsplace.com/tutorial/how-to-dual-boot-windows-7-ubuntu-linux-install-run-ubuntu-on-windows/)

it is recommended to use Windows to shrink the Win 7 partition.

---

### Post by BigCityCat on 2010-08-08
You should shrink windows seven with windows sevens shrink utility. Then when you install ubuntu just select use largest continuous free space.

In win seven click start button, right click computer, select manage, select disk management, right click on win7 partition, select shrink, and then decide the size to shrink.

---

### Post by colin.p on 2010-08-08
Just an addendum, I found that 7 will only let you shrink by only so much. I could only shrink a 305GB partition by 126GB or so, leaving the rest for 7.
The windows partition only has 40GB on it, but I couldn't shrink it any more. However, 126GB is plenty for linux, especially if you use external drives for storage.

---

### Post by BigCityCat on 2010-08-08
Two other things. If you ever decide to delete your ubuntu partition from disk management you need to re write the mbr or you won't be able to boot into windows cause grub gets removed. There is a free program that does this in a couple of clicks. It's called Easy BCD.

Also I have run into problems resizing partitions because of the location of the MBR at the end of the partition. There is a program that has a free month trial that defrags the hard drive and moves the MBR so you can resize. Let me look for it.

This is the one I used. It had a free trial. I;m pretty sure it still does.

[http://perfectdisk.raxco.com/](http://perfectdisk.raxco.com/)

---

### Post by Mark Phelps on 2010-08-08
Few points to consider ...

BEFORE you start messing around with Win7 partitions, do yourself a favor and use the Backup feature to create and burn a Win7 Repair CD.  That will prove invaluable later should you need to repair the Win7 boot loader.

If the Win7 Disk Management utility won't let you shrink it, do not resort to using GParted to do that.  That runs the risk of corrupting your Win7 OS and rendering it unbootable.

EASEUS Partition Master is an MS Windows based partitioning tool and can be downloaded for free from their website, but I don't think the free version is bootable.

And, finally, NO, the MBR is NOT part of any partition. And, it is certainly NOT at the end of any partition.  It is the first 512 bytes of the hard drive.

---

### Post by BigCityCat on 2010-08-08
Yeh well I don't remember exactly what it was but in the past a couple of times I tried to use win7 disk management to shrink the hard drive and it would not give me any shrink space on an unpartitioned disk. I searched around and I read some things for why this was happening. I was told it had something to do with the MBR. It was suggested that I use perfect disk to fix this problem. I used perfect disk to defragment and after I was able to shrink.

Here is an article on what it was.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

> The reason why Windows won&#8217;t let you shrink the volume is because there are immovable system files at the very end of the volume, as this screenshot from Auslogics defragment utility shows us. In this case, the immovable file is actually the MFT, or Master File Table for the volume.

So what I forgot was not the MBR but the MFT.

---

### Post by darklord06 on 2010-08-08
wow thank you for your feedbacks !!! i will try to shink the windows 7 partition from the windows 7 tool and tell you what happened. And mark phelps that's a good idea i'll burn a win7 repair CD first

thank you !

---

### Post by colin.p on 2010-08-08
and another thing, read [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) first as it shows how to fix your bootrec, should 7 decide to "frig" it up.

---

### Post by wilee-nilee on 2010-08-08
As suggested get your backup or have a install disc, that your activation key works with in case needed.

This defragger will, using a boot offline defragging to move everything to the front of the disc, allowing the MS disk management to shrink further.

This has a 30 day free trial, personally that's all I have used it for, I had a shrink stuck at 76 gigs after the defrag I got to 38 gigs
[http://perfectdisk.raxco.com/](http://perfectdisk.raxco.com/)

Gparted can be used if you tick off the round to cylinders, in the resize gui, but this will probably trigger a chkdsk or need one possibly if you shrink a great amount, I suspect.

This W7 forums link post #6 is the origin of the perfectdisk reference.
[http://www.sevenforums.com/general-discussion/68287-cant-shrink-windows-7-partition-anymore.html](http://www.sevenforums.com/general-discussion/68287-cant-shrink-windows-7-partition-anymore.html)

---

### Post by darklord06 on 2010-08-09
thank you !!! 

i followed all the instructions on BigCityCat's link and I finally managed to install ubuntu !!

for now I am a little disapointed by the performance, it is a bit slower than i expected on my hp pavilion DV5000 an the video playback quality isn't the best (i have an ati mobility radeon xpress 200 series video card) i guess i'll have to fine tune all that

thanx again for your help !

---

