---
title: "Need help resizing ext4"
date: 2011-08-14
forum: General Help
---

### Post by elys22 on 2011-08-14
I've had Windows and Lucid on dual boot for awhile, but I stopped using Ubuntu because I couldn't access my dorm's wireless on it. Now I've decided to scrap Windows altogether and just use the DSL at school. My problem is, back when I first installed Lucid on this machine I allocated it way too little space because I didn't anticipate using it very often. I also had a couple of misunderstandings while trying to get rid of Windows. I deleted its partitions and everything because what I read online indicated that the space would automatically be allocated to my root filesystem. Well, obviously that's not the case. I then tried to manually resize with gparted, but as you non-amateurs know, you can't resize a mounted partition that way. Instead of trying to guess my way through this by searching hundreds of threads, I'm appealing to you all directly for help. From what I understand, there are only two ways for me to resize ext4 at this point: I can boot from a Linux disc with gparted installed and do it that way, or use resize2fs to do it online. The latter seems to be the riskier method; if I understand correctly, I would have to delete ext4 and create a new one? How exactly would that work? I'd prefer to go with the former method, but I no longer have my Lucid disc, and irony of ironies, I don't think I have enough memory to download an ISO and burn another one. 

Can anyone see a way out of this?

---

### Post by spiky001 on 2011-08-14
So do you have a partition ex windows spare ( maybe post output of) ```
sudo fdisk -l
``` then maybe get gparted on your system then create ext4 on unallocated partition

---

### Post by elys22 on 2011-08-14
I might not be stating this correctly, but I believe the Windows partitions are gone, but the file systems are still there? They're just all marked as Unallocated. Would that make sense? This is what it looks like:

[http://tinypic.com/r/2qbzqmt/7](http://tinypic.com/r/2qbzqmt/7)
[IMG]http://tinypic.com/r/2qbzqmt/7[/IMG]

---

### Post by spiky001 on 2011-08-14
Is it possible to make the unallocated space ext4 down load the iso image to the new partition then make the disc then merge partitions, AS you mentioned they have to be unmounted 
[http://ubuntuforums.org/archive/index.php/t-941624.html](http://ubuntuforums.org/archive/index.php/t-941624.html) , Long way around but will get job done, or just download iso on another pc

---

### Post by spiky001 on 2011-08-14
It might be worth reinstalling as you only have 4 gig as linux and 259 swap, Maybe allocate 10 gig to root double ram as swap and the rest as home, there are also a couple of other unallocated spaces there as well.

---

### Post by elys22 on 2011-08-14
Let me see if I understand you correctly: I can download the ISO image to the unallocated file system and mount it, burn to DVD, then do a clean reinstall, allocating 10 gigs to swap and the rest to ext4? And if so, how do I specifically download the ISO to the unallocated space? And then, how do I access it? 

Sorry, I'm a bit slow on these things.

---

### Post by mikewhatever on 2011-08-14
Unallocated space is the disk space that has no file system. You should create a partition there and use it to download an iso.
10GB for swap is way too much, you'll probably never need more the 2GB.
When you click the iso download link, a a prompt will appear asking you to open or save the file. You should select the second option (to save the file). Now, if Firefox is set to ask where to save downloads, you'll get another window asking to select the location. Make sure that firefox doesn't autosect the Downloads folder.

---

### Post by elys22 on 2011-08-14
Can I do that (partition the unallocated space) in gparted by selecting that file system and Partition/New?

---

### Post by WyleECoyote on 2011-08-14
not sure if you have already wiped your existing Linux, if not here is how I resize my working partition.

1) I download and install live cd to usb thumb drive then boot into it, if not already installed I install Gparted then run it, resize my partition to include the deleted windblows partition.

2) I mount the Linux partition then use:
$ sudo blkid
to get the new uuid because the partition size changed then I open the /etc/fstab file in the linux partition and change the uuid

3) reboot, as long as you put the new uuid in the right place in fstab nothing else is needed

---

### Post by mikewhatever on 2011-08-14
> **elys22 said:**
> Can I do that (partition the unallocated space) in gparted by selecting that file system and Partition/New?

Yep. Gparted or the Disk Utility which is preinstalled.

---

### Post by elys22 on 2011-08-14
I see that it gives me the option of making it ext4. If I do that and make it the primary file system, can I unmount and delete the old one with the 4 GB? I don't really care if I lose any of my data, I already backed up everything I needed before deleting the Windows partition.

---

### Post by mikewhatever on 2011-08-14
ext4 is the default Linux file system - quite ok to use, you can make the partition primary or logical - doesn't matter because you are going to format the hdd when reinstalling, but you can't unmount the old 4GB partition - /dev/sda5, because the Ubuntu installation you currently use runs from there. It's the system partition for that installation.

---

