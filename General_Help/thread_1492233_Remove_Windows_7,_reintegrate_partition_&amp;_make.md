---
title: "Remove Windows 7, reintegrate partition &amp; make the world a better place"
date: 2010-05-24
forum: General Help
---

### Post by thedrklion on 2010-05-24
I am rather new to the linux scene. Currently have a dual boot HTPC running windows 7  & ubuntu 9.10 ,  windows pulled "no longer a valid"on me after an update an i was left with a limited machine. 

I figure now is as good time as any to go full with a fully linux system.
However, i am having some problems.

1) Windows 7 needs purged from my system.. like a cancer.
I need to get rid of my sda1 windows partition. I gathered i will need gparted and grub2..  
But will i need a Gpart liveCD?
I need someone to take my though it.

I got and ran Gparted.
My system seems to have 3 partitions with 2 unallocated spaces.

Any help would be greatly appreciated.

2) I will need to remount the windows partition after i  reformate it and get rid of windows.
    I will likely need help with this as well.

I believe it is also worth noting that i believe wubi was used to put Ubuntu on this machine. 
    
Again, any help would be greatly appreciated.
P.S.
My ubuntu 9.10 CD seems to give me an error when i try to boot from it and select "try Ubuntu without changing you system"
I figured id mention this because some threads mention the use of a live cd.

---

### Post by ali999 on 2010-05-24
Couple of things. First off you can install gparted through package manager or simply go ```
sudo apt-get install gparted
``` in terminal so you don't have to load it off the live CD everytime. The CD could be giving errors perhaps due to a bad burn or something so you should try downloading a new image file and burn that. 
Now when you look at the partitions, the windows is the one that is in NTFS format and Ubuntu will be in the ext format with another smaller  partition used for swap space.
But the problem is that you used wubi to install which to my understanding does not create a seperate physical partition for ubuntu but rather put it within the windows ntfs partition. This could be a problem since deleting the windows ntfs partition will most likely delete the ubuntu filesystem as well. 
If I were you, I would burn another CD and then reinstall ubuntu on a seperate partition  by loading the disk at startup. Of course you will loose all your data in this process so backup all your important files first

---

### Post by thedrklion on 2010-05-24
I am unsure if WUBI was or was not used.
It is my belief that it was.

Is there a way to check if WUBI was used to install Ubuntu?

Currently, termal command:         sudo fdisk -l
results in

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4fe03cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       47281   379679740    7  HPFS/NTFS
/dev/sda3           47282       91201   352787400    5  Extended
/dev/sda5           47282       89977   342955588+  83  Linux
/dev/sda6           89978       91201     9831748+  82  Linux swap / Solaris

Disk /dev/sdd: 8067 MB, 8067743744 bytes
217 heads, 4 sectors/track, 18153 cylinders
Units = cylinders of 868 * 512 = 444416 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              10       18154     7874560    b  W95 FAT32

does this help in any way?

[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by ali999 on 2010-05-24
hmm...looking at that it seems like you have a separate linux partition. so if i were you, i'd jsut use gparted to delete the windows ntfs one, then run ```
sudo update-grub
``` in terminal. however, i have never used wubi personally so i am not 100% sure so i would backup all my files first just in case

---

### Post by simich on 2012-12-14
> **ali999 said:**
> hmm...looking at that it seems like you have a separate linux partition. so if i were you, i'd jsut use gparted to delete the windows ntfs one, then run ```
sudo update-grub
``` in terminal. however, i have never used wubi personally so i am not 100% sure so i would backup all my files first just in case

(First, hi, I am a brand new member of the forums but have been reading them for quite some time.)

[@ali999]("http://ubuntuforums.org/member.php?u=504122") Is this the way to go? 

I installed Ubuntu after/alongside Windows 7 (with a 'live USB', not wubi) and now I want to get rid of the latter. I've been searching the Web for any info but unfortunately my 'replace windows 7 bootloader with grub 2' search in Google returns results for the opposite - 'replace grub 2 with windows 7 bootloader', which doesn't help me at all.

Having in mind my (still) negligible understanding of Ubuntu (and Linux in general) I figured that the way to do what I want is to first replace the Windows bootloader with grub2, then format my Windows partition and finally remove the Windows boot entry. Assuming my plan is valid, I am stuck at the beginning because I don't know how to do step 1.

So, I'd like to ask, is my plan OK? (Ubuntu is installed on the extended partition; is this an obstacle?) If so, how would I complete step 1?

If not, could you point me to some readings that would hopefully get me on the right track after improving my understanding of how things work in the Linux world?

regards,
simich

---

### Post by lisati on 2012-12-14
A lot can change in the space of two years. If a thread hasn't had a response in over a year, it's often a best to start a new thread, with a link back to the original thread if required.

Old thread closed.

---

