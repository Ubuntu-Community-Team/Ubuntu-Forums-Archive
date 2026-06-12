---
title: "understand fdisk output"
date: 2009-10-29
forum: General Help
---

### Post by alturion on 2009-10-29
Hi, I think i did a mess when I installed Ubuntu, I have one HD and I did some partitions (I don't remenber exactly how many 3 or 4 :(), now I would like set everything ok, but there is something strange in my fdisk -l output can anyone help me to read it?

$ sudo fdisk -l
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13b413b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11473    92156841    7  HPFS/NTFS
/dev/sda2           11474       38913   220411800    f  W95 Ext'd (LBA)
/dev/sda5           11474       26133   117756418+   7  HPFS/NTFS
/dev/sda6           32835       38913    48829536   83  Linux
```I have for sure a partition for WinXP, one for Ubuntu and one shared but:

[LIST=1]
[*]How can I recognize them from fdisk out?
[*]How is possible that partitions sda2 and sda5 have the same start block?
[/LIST]

---

### Post by akakingess on 2009-10-29
> **alturion said:**
> Hi, I think i did a mess when I installed Ubuntu, I have one HD and I did some partitions (I don't remenber exactly how many 3 or 4 :(), now I would like set everything ok, but there is something strange in my fdisk -l output can anyone help me to read it?

$ sudo fdisk -l
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13b413b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11473    92156841    7  HPFS/NTFS
/dev/sda2           11474       38913   220411800    f  W95 Ext'd (LBA)
/dev/sda5           11474       26133   117756418+   7  HPFS/NTFS
/dev/sda6           32835       38913    48829536   83  Linux
```I have for sure a partition for WinXP, one for Ubuntu and one shared but:

[LIST=1]
[*]How can I recognize them from fdisk out?
[*]How is possible that partitions sda2 and sda5 have the same start block?
[/LIST]


Also, where is your SWAP partition?

---

### Post by gareththegeek on 2009-10-29
1. How can I recognize them from fdisk out?

You can tell which disks are windows by the NTFS format so that's disks sda1 and sda5. sda6 is linux but you don't seem to have a swap drive set up.

   2. How is possible that partitions sda2 and sda5 have the same start block?

sda2 appears to be an extended partition with sda5 set up within it. You probably set this partition up without making it a primary partition. Also sda5 does not extend to fill the extended partition sda2 so you have some wasted space.

---

### Post by alturion on 2009-10-29
ok so there is another problem too...
I havent a swap partition!

[LIST=1]
[*]How can I make it?
[*]also, seems that sda2 and sda6 have the same end block?
[*]Is there any way to put everything okay without reformattig all? I would like for example do not touch the WinXp partion (sda1), do not touch the Linux partition (sda6?), about the residual space I'd like use it as shared space, only for data so at now I can without pain clean and reformatting it (about it which kind of partiotion is better to do it? NTFS or FAT32).
[/LIST]
Thank you

---

### Post by akakingess on 2009-10-29
> **alturion said:**
> ok so there is another problem too...
I havent a swap partition!

[LIST=1]
[*]How can I make it?
[*]also, seems that sda2 and sda6 have the same end block?
[*]Is there any way to put everything okay without reformattig all? I would like for example do not touch the WinXp partion (sda1), do not touch the Linux partition (sda6?), about the residual space I'd like use it as shared space, only for data so at now I can without pain clean and reformatting it (about it which kind of partiotion is better to do it? NTFS or FAT32).
[/LIST]
Thank you

I'm not really an expert when it comes to partitioning, etc. I just happened to notice that you didn't have a SWAP partition, but if it were me, I would start over from scratch as long as you have everything backed up. I would start over and give Windows more space as it can be mounted within Ubuntu with ntfs-config and therefore you could store stuff on your Windows partition from Ubuntu, I only say to do it that way to cut back on the # of partitions, because I would then create your SWAP partition, a seperate / (root) partition, and then another ext3 or ext4 partition (your preference) for your /home directories, that way when you later upgrade or reinstall Ubuntu, your documents, etc. should be safe as they are on their own partition. Just my humble opinion.  
Also, always go with NTFS on the Windows side of things.

---

### Post by PeggySue on 2009-10-29
Hi,
Just to get you started, I suggest:

Make sure you have backed up all your data before playing with partitions.  

Have a look at this disk partitioning thread
[http://ubuntuforums.org/showthread.php?t=282018]("http://ubuntuforums.org/showthread.php?t=282018")

You can't move a partition you are working in.  I always boot from a "System Rescue CD".  Google it to find it.  Go in to startx and run gparted.

For Linux you need a root partition to load into but also a swap partition, say twice the size of your RAM.

You can only have 4 primary partitions so make one of them an extended partion which holds additional partitions.

Your sda1 partition looks like a windows partition.  See if you can match the size with what your operating system reports.  sda2 looks like a windows extended partition.  Note it covers from 1174 to the end of the disk.  In this extended partition you have an NTFS partition (sda5) that you could write to with both Linux and windows and also a linux partition.  You don't have a swap partition.

I don't know what happened to the sda3 and sda4 assignments.  And don't forget if you just minimize the size of a partition you can make it bigger later! If you delete it, it is gone.

You might consider leaving the partitions as they are but shrinking sda6 to make room for another partition as swap.

I have to say I am unsure about the windows extended partition.  My guess is you did the repartitioning from inside windows.  If you can add another partition for swap then it is an extended partition.

Make sure you understand about marking the linux partition as '/' and finally consider which version of ubuntu to load.  8.10 comes out today but you might load 8.04 and format as ext3 which is stable for sure.  If all is well then load 8.10 over the top.  (8.10 will use ext4 and I assume it will format the disk accordingly.

I always go the safe route which is why my partitions aren't very tidy.  Don't copy this but for you information this is what my fdisk -l looks like.  I have 2 160 GB drives and an external USB drive.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa19fa19f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4857    39013821    7  HPFS/NTFS
/dev/sda2            4858       18890   112720072+  83  Linux
/dev/sda3           18891       19457     4554427+   5  Extended
/dev/sda5           18891       19457     4554396   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcaf7caf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4857    39013821    7  HPFS/NTFS
/dev/sdb2            4858       12152    58597087+  83  Linux
/dev/sdb3           12153       18236    48869730   83  Linux
/dev/sdb4           18237       19452     9767520    5  Extended
/dev/sdb5           18237       18803     4554396   82  Linux swap / Solaris
/dev/sdb6           18804       19452     5213061    b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    c  W95 FAT32 (LBA)

Good luck.

---

### Post by PeggySue on 2009-10-29
P.S.  Sorry I meant 9.10 comes out today!!  And I see you have lots of other helpful replies.  I'm too slow!

---

### Post by akakingess on 2009-10-29
> **PeggySue said:**
> Hi,
Just to get you started, I suggest:

Make sure you have backed up all your data before playing with partitions.  

Have a look at this disk partitioning thread
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

You can't move a partition you are working in.  I always boot from a "System Rescue CD".  Google it to find it.  Go in to startx and run gparted.

For Linux you need a root partition to load into but also a swap partition, say twice the size of your RAM.

You can only have 4 primary partitions so make one of them an extended partion which holds additional partitions.

Your sda1 partition looks like a windows partition.  See if you can match the size with what your operating system reports.  sda2 looks like a windows extended partition.  Note it covers from 1174 to the end of the disk.  In this extended partition you have an NTFS partition (sda5) that you could write to with both Linux and windows and also a linux partition.  You don't have a swap partition.

I don't know what happened to the sda3 and sda4 assignments.  And don't forget if you just minimize the size of a partition you can make it bigger later! If you delete it, it is gone.

You might consider leaving the partitions as they are but shrinking sda6 to make room for another partition as swap.

I have to say I am unsure about the windows extended partition.  My guess is you did the repartitioning from inside windows.  If you can add another partition for swap then it is an extended partition.

Make sure you understand about marking the linux partition as '/' and finally consider which version of ubuntu to load.  8.10 comes out today but you might load 8.04 and format as ext3 which is stable for sure.  If all is well then load 8.10 over the top.  (8.10 will use ext4 and I assume it will format the disk accordingly.

I always go the safe route which is why my partitions aren't very tidy.  Don't copy this but for you information this is what my fdisk -l looks like.  I have 2 160 GB drives and an external USB drive.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa19fa19f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4857    39013821    7  HPFS/NTFS
/dev/sda2            4858       18890   112720072+  83  Linux
/dev/sda3           18891       19457     4554427+   5  Extended
/dev/sda5           18891       19457     4554396   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcaf7caf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4857    39013821    7  HPFS/NTFS
/dev/sdb2            4858       12152    58597087+  83  Linux
/dev/sdb3           12153       18236    48869730   83  Linux
/dev/sdb4           18237       19452     9767520    5  Extended
/dev/sdb5           18237       18803     4554396   82  Linux swap / Solaris
/dev/sdb6           18804       19452     5213061    b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    c  W95 FAT32 (LBA)

Good luck.

I just wanted to note that the version numbers might be mixed up a little bit, 9.10 (Karmic Koala) comes out today 9.04 (Jaunty Jackalope) has been out about 6 months, and 8.04 is the current LTS, which means it will be supported for I think another year or year and a half. I just wanted to clarify the version #'s for Ubuntu.  BTW, LTS stands for Long Term Support (I think).

Edit: Sorry I was typing too slow, Peggy Sue beat me to the clarification!

---

### Post by alturion on 2009-10-29
Thank you guys!
I hope I have understand all... for now I will back-up my data and then start to play with partition, I will let you know...

for now my relase is 9.04.

---

### Post by akakingess on 2009-10-29
I would be sure and get everything stable with 9.04 before going up to 9.10, even if you want to risk going to 9.10 (if you have everything working, cuz 9.10 changes over to Grub2, which is the OS loader). But, if you want to go to 9.10 after you have everything up and running you can just do an update -d and I believe that will upgrade ya. I'm not 100% on that code cuz I just choose to do clean installs whenever I move up.

---

### Post by alturion on 2009-10-29
Is possible to make an image of linux as I can format my partitions and reinstall it as it is now?

---

### Post by alphaniner on 2009-10-29
If you are going to modify your partitions it would probably be rather difficult.  

However, most of your settings are saved in your home folder.  If you make a backup of it, install the same version of Ubuntu, and then restore it most things should be back as you had them.  But I've never tried this so don't quote me on it.

---

### Post by alturion on 2009-10-29
could I copy the whole file system on an USB HD and then restore it?

---

### Post by alphaniner on 2009-10-29
It wouldn't be a good idea for several reasons.

Foremost because certain system configuration files would have to be modified to deal with the new disk layout.  I can only think of a few off the top of my head, but I just think it would be more trouble that it's worth.  This isn't to say that it **can't** be done, though.

---

### Post by akakingess on 2009-10-30
Yeah, I agree with alphaniner, between the UIDs for users, and the UIDs for partitions, different config files would be looking at the wrong places for different items, drives, software, etc. It is best to make a backup of your "Home" folder though, as that has all of your settings in it, and the worst case scenario would be that you have to reinstall some software that doesn't reside in your Home directory. I know it's a pain, but you're probably looking at a bigger pain if you image the Linux OS and then repartition.

---

### Post by alturion on 2009-10-30
Okay
Now I think I can avoid to touch the WnXp partition and just delete the sda2, sda5 and sda6 and create from these the shared partition, the linux partition and the swap one. How can I do it without making other mess? 
from Windows before install Ubuntu or is better do it during the Ubuntu installation? 
Also, do you suggest me to install Ubuntu 9.04 from the CD or I can use without problems the Windows installer?

---

### Post by alturion on 2009-11-04
ok! I have done it!
I have created a  primary partition for ubuntu, and an extended with the swap, /home, /usr and a windows shared partition. Now I would like avoid to make other messes, which is the best place for install commercial applications as matlab?

---

### Post by PeggySue on 2009-11-04
Assuming you have the Unix/Linux DVD version of Matlab you should follow these instructions:
[http://www.mathworks.com/access/helpdesk/help/base/install/index.html?/access/helpdesk/help/base/install/install.html&http://www.google.co.uk/search?hl=en&safe=off&num=30&newwindow=1&q=matlab+install&btnG=Search&meta=&aq=f&oq=]("http://www.mathworks.com/access/helpdesk/help/base/install/index.html?/access/helpdesk/help/base/install/install.html&http://www.google.co.uk/search?hl=en&safe=off&num=30&newwindow=1&q=matlab+install&btnG=Search&meta=&aq=f&oq=")

Otherwise you will can trawl the Mathworks site for instructions.

Take a look at System | Administration | Synaptic Package Manager and search for matlab.  There are a couple of extras there.

---

