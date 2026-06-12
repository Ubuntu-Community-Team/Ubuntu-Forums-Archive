---
title: "Couple Partition Questions"
date: 2010-03-08
forum: General Help
---

### Post by FinalShot on 2010-03-08
I currently have Windows XP Pro SP3 on a 320GB hard, totaling 1 partition. I plan to Live Boot Ubuntu 9.10, use gparted to make a 30GB or so partition from the 320GB partition.

Now if I was to want to increase the 30GB, is that possible?

---

### Post by FinalShot on 2010-03-08
?

---

### Post by bbzjdhs on 2010-03-08
If the one partion don't occupy the total 320GB, for example, the partion occupy 120GB, then you can use the remain space for ubuntu directly.
If not, then you can use the partion magic to decrease the size of the partion to remain space for ubuntu.

---

### Post by marcopolo1981 on 2010-03-08
Firstly, you will need to boot into XP and do a serious defrag! I mean do it. Then do it again. And even another time. Failure to do this may corrupt your XP Data.

Once you are satisfied, boot the live cd. Use GParted, like you say, to SHRINK your XP NTFS partition to the LEFT. If you want the Ubuntu install to use 30 Gig, take it off the NTFS partition. If you think you may need to have a larger Ubuntu Partition at some point, take that off the NTFS partition as well. 

Then create a new EXT4 partition in the start of the new free space. It is also advisable to have a swap partition. Use your own discretion as to what size you make this, and whether you allow this to eat into your EXT4 partition. But make this at the END of the free space 

Now install Ubuntu in the new EXT4 partition as normal. If you opted to leave some empty space should you need to make the EXT4 partition larger, you can use the free space between the existing EXT4 partition and the SWAP partition. You will need to boot into the Live CD in order to do this though.

Whilst you are using Ubuntu and XP, that free space will be inaccessable. You can create a FAT32 partition so that you can use it safely from both XP and Ubuntu. Then when you need to make EXT4 larger, copy the existing data from the FAT32 to somewhere safe, then delete the FAT32 Partition. Go into a live CD, and use Gparted to make the EXT4 fill the available space.

Job done. But please be safe and back up everything you can. I will not be held responsible for any data loss/corruption.

The first time you boot into XP again, it will want to run a CheckDisk. Let it and all should be ok.

---

### Post by 3rdalbum on 2010-03-08
> **bbzjdhs said:**
> If the one partion don't occupy the total 320GB, for example, the partion occupy 120GB, then you can use the remain space for ubuntu directly.
If not, then you can use the partion magic to decrease the size of the partion to remain space for ubuntu.

Why would you use Partition Magic when the Ubuntu installer can resize partitions?

Yes, you can use the Ubuntu installer to make 30 gigabytes of space available. I'd recommend defragmenting your disk first from within Windows, so there's as much contiguous space as possible toward the end of the disk. Ubuntu can do it too, but very slowly.

If you want more than 30 gigs at a later date, you should be able to resize the partition again using Gparted.

---

### Post by bbzjdhs on 2010-03-08
So far, i only know gedit, gcc, insmod and rmmod and so on, i do the related development on windows platform before, thus i hope i can become a super user as you guys in the future :)

---

### Post by Barriehie on 2010-03-08
I'ld recommend a seperate partition for /home, it can help make your computing worry free when you start 'optimizing' your install! :)

---

