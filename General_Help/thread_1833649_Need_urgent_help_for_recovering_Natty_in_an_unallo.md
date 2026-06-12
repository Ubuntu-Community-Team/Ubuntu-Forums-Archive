---
title: "Need urgent help for recovering Natty in an unallocated space"
date: 2011-08-26
forum: General Help
---

### Post by harlequin_ on 2011-08-26
Hi everyone

A few hours ago I did a mistake that caused me a lot of trouble. I  wanted to merge my Windows data partition (which was around 30 gb)  with  my Windows OS partiton. Therefore I fist wanted to delete the data  partition and then merge. But instead of deleting the data partition, I  deleted my Linux partition (which was about 40 gb). I was using Disk Management utility of Computer Management/Storage under Windows 7.

I tried to install a few apps in Windows for recovering the partition but I failed. The bad thing is that during an analysis performed by one of these apps the computer froze and rebooted itself, and I was left with a black welcoming screen of *grub rescue*. Luckily I had my gf's pc with me so I prepared a LiveCd and now I used it to open a live session and here I am posting this.

What should I do? The data in the deleted Natty system is more important to me than the system itself. I have all my work-related data there and you know that stuff is pretty important. Is it possible that I somehow recover the whole partition with my Natty (considering that I have not written anything on that part of the disk after my mistake) or can I recover my files? I have read many threads and tried a few apps (including testdisk) but I honestly do not know how to entirely handle these apps and the tutorials I have been through did not really help, mostly because they were covering different scenerios. 

When I do [I]**sudo fdisk -l** I get 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd92e434e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       27944   224250801+   7  HPFS/NTFS
/dev/sda3           27944       36988    72643073    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4           36988       38914    15471448   12  Compaq diagnostics
/dev/sda5           32825       33039     1717248   82  Linux swap / Solaris

Disk /dev/sdb: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0056b003

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121516   976074752    7  HPFS/NTFS

[/I]Any suggestion is appreciated.
Cheers

---

### Post by bodhi.zazen on 2011-08-26
See if you can recover the partition with testdisk. I highly suggest yo do this from a live CD, testdisk is in the Ubuntu repos.

---

### Post by harlequin_ on 2011-08-26
> **bodhi.zazen said:**
> See if you can recover the partition with testdisk. I highly suggest yo do this from a live CD, testdisk is in the Ubuntu repos.

Thanks. Now I'll try and post the results asap.

---

### Post by harlequin_ on 2011-08-26
> **bodhi.zazen said:**
> See if you can recover the partition with testdisk. I highly suggest yo do this from a live CD, testdisk is in the Ubuntu repos.

I downloaded *testdisk*, ran it, and analyzed my partitions. I got the attached table when I did a quick search

When I go into the *Linux* partition I can see all my files and everything in the my Natty system! This applies to the second partition in the list (my windows 7 partition).

Now, as far as I understand I need to change something and recreate a new partition table and using Advanced Filesystem Utils need to do modifications. But I am not sure how because it is not as deeply expalined in the testdisk website and I'm a bit afraid to cause further damage so I don't want to do anything without being really sure. That's why a second step of recommendations would be really appreciated at this point. Anyone?

Cheers

---

### Post by bodhi.zazen on 2011-08-26
See this link :

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

you will need to be more specific with what step you do not understand, otherwise we would be re - typing the same set of instructions here.

---

### Post by harlequin_ on 2011-08-27
> **bodhi.zazen said:**
> See this link :

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

you will need to be more specific with what step you do not understand,  otherwise we would be re - typing the same set of instructions  here.

Thanks for the link. Yesterday I solved the situation and here is how for future users:

The action was: I mistakenly deleted my Ubuntu Natty Partition from within Windows 7 while trying to delete another partition of similar size.

Concequences were: I needed to save my files and I needed software for this. I downloaded a partition recovery software and during the analysis the computer froze. After the restart, I could not boot into neither of my systems, I guess because grub2 was deleted/damaged/unaccessible along with the ubuntu partition. 

What I did:

1- Using another pc downloaded and burned a bootmed cd from [here]("http://www.bootmed.com/")
The good thing about using such a cd was it contained testdisk and all sort of recovery utilities, which might not be present in a standard live ubuntu cd (then you have to install these utilities).

2- I first used testdisk to reidentify my partitions. I found the partition that I mistakenly deleted (its identifier was still *Linux*) from the list, turned it into a *primary partition*, and then saved my new partition table. 

3- I purged and reinstalled grub to my little (200mb) boot partition. And I know this was essential because without doing this it did not work. I do not know why deleting Linux partition would affect the files here. I think they were affected becuase otherwise after I reidentified my deleted partition with Testdisk I should've been able have a smooth boot (but no, without perging & reinstalling grub, I still got the grub rescue screen at booting). 

After these steps I could have a normal dualboot again. 
Cheers

---

