---
title: "Really big mess. Need some help."
date: 2009-12-04
forum: General Help
---

### Post by ramidavis on 2009-12-04
I would love to have an explanation for this, and hopefully a fix. Now, lets see if i can try to explain what i think happened:
This laptop belonged to my father, and he had ubuntu and windows 7 on it. He was inside ubuntu, looking at partitions and i think he was trying to resize them. But, somehow, he ended up wiping out the 'system reserved' partition of 7. I think he used a program called test disk to try and restore the partition, but somehow, he has managed to delete all the partitions. At least, that is what gparted (live cd) is telling me. All unallocated space. Ready for the really strange part? I loaded up parted magic live cd, and fired up test disk, the same program which i believe caused this mess somehow, and it is showing all the partitions, even showing thier names/id. Using parted magic live cd, i was able to pull any data we needed off of the windows partition with its file browser, so we would not loose anything.
It gets better though people. Not only is gparted telling me that i have no partitions, and test disk is saying they are still there, but i can actually still get 7 to boot... even though it is not there according to gparted. How did i manage to get 7 booting from unallocated space? Well, i used super grub disk. There was an option that reads "WIN => MBR & !WIN! : (((((((((". After using this option, windows 7 is booting, and running like nothing ever happened. I can shut down, reboot, log out or what ever. And i am doing it from unallocated space. Now, who would like to help me fix this mess, anyone? Please? Has anyone ever had this, or something like this, happen to them before? Yes, i know i could just wipe the hard drive, but where is the fun in that? Anybody have ideas for a fun way of fixing this? You know, just play around with it and see what we can do, hopefully get linux up as well. I suppose when i mess up a machine, i really mess it up good.
Video [[IMG]http://i941.photobucket.com/albums/ad253/ramidavis/th_VIDEO0015.jpg[/IMG]](http://s941.photobucket.com/albums/ad253/ramidavis/?action=view&current=VIDEO0015.flv)

---

### Post by akashiraffee on 2009-12-04
This is not that strange.  It looks to me like your "super grub disk" replaced the MBR with the original windows MBR, meaning you now boot straight into windows without going through grub, right?

The Master Boot Record is a 512k block at the start of the hard drive containing the partition table information.  Nb, that this can be changed WITHOUT changing the actual contents of the drive.  So if "test disk" reads it's information by scanning the drive, it will represent the true state, whereas parted may only report the state of the partition table (which it is crucial for these to match, anyway).

If you use one of those linux disks again, you can view the partition table with fdisk:

fdisk /dev/sda

Choose an option: p

---

### Post by ramidavis on 2009-12-04
Windows 7 partition manager shows 4 partitions: c: , system reserved, unknown, and unknown. Those last 2 would be my linux and swap partition.

Is there any way to 'unhide' the partitions? Only gparted seems to be saying no partitions. Windows, "parted magic" live cd partitioning disc, "testdisk"(linux based partitioning program, available on the parted magic cd) can see them.

But how do i actually restore them? Or can i at all? Why would linux say there is no partitions, but windows can see them just fine?

---

### Post by rbc on 2009-12-04
It does, in fact, appear that your father nuked the mbr. See here for details about the mbr:
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
When you used Super Grub Disk, you restored a Windows bootloader, so it was not looking for anything other than Windows stuff, so it only installed information about those two the the partition table. TestDisk is a partition recovery application. I believe it is finding partitions that are available to restore. Pick the ones that are Linux related, then use Super Grub Disk to restore Grub to the mbr. After that, you should be back in order. If you are really paranoid, clone the drive first (PartMagic includes Clonzilla) and use that clone to test my and akashiraffee's theory

---

