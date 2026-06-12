---
title: "Partitioning a USB Flash Drive, and more"
date: 2011-01-04
forum: General Help
---

### Post by Hatryst on 2011-01-04
Hello Everyone. I am sorry if this has been discussed before, or if I'm posting in a different forum. I have seen several forum posts on this topic, but none of them helped me in understanding the procedure. So please help me out

I want to partition my 4 GB USB Flash drive into 2 (almost equal) partitions...

So here are separate questions (for your answering convenience)


**Question 1:** If both partitions are set to FAT32, will both of them be readable by Windows?
(I've heard that it isn't possible, but just asking)

[B]
Question 2:[/B] How to carry out the partition? I attached my USB disk, opened GParted, and found that all the options for partitioning were dim (unavailable).

[IMG]http://i572.photobucket.com/albums/ss162/Hatryst/partition.png[/IMG]

Please guide me step-by-step. (detail required on this one)


**Question 3:** I want to install Ubuntu on the Ubuntu-reserved partition (after it is made). How would i be able to do that? PenDriveLinux ([http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)) allows installation of Ubuntu and other distros on a USB drive, but that is only possible from within Windows. Since the other partition would not be readable by Windows (most probably), how would I install Ubuntu on that partition?

Thanks in advance...

---

### Post by dino99 on 2011-01-04
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

---

### Post by TeoBigusGeekus on 2011-01-04
deleted.....

---

### Post by TeoBigusGeekus on 2011-01-04
1)Don't know about that.

2)You have to unmount the drive first. Gparted can't operate on disks that are already in use.

3)System>Administration>Create a usb startup disk

---

### Post by anystupidname1 on 2011-01-04
1) Yes, Windows natively supports FAT16, FAT32, FAT64, exFAT, and several versions of NTFS (fragment slightly less badly). You can also read/write several versions of EXT with an after market driver.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

2) Must be unmounted first. You may or may not need to install ntfs-3g and/or change a related configuration for NTFS to be an option if you choose to use that instead of FAT.

3) The answer to this question depends a lot on what will be in the other partition and what your intentions are for this flash drive. Here are some possibilities:

Built-in solution: System Menu>Administration>Startup Disk Creator
Crazy French guy solution: [http://liveusb.info/](http://liveusb.info/)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

PS, nicely formatted question :p

---

### Post by Hatryst on 2011-01-04
Wow those are some INSTANT replies :)
Thanks, keep it coming !

Well, after i unmount the disk, what to do next?

---

### Post by anystupidname1 on 2011-01-04
> **Hatryst said:**
> Wow those are some INSTANT replies :)
Thanks, keep it coming !

Well, after i unmount the disk, what to do next?

Give up and drink beer? You'll need to ask more precise questions.
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by Hatryst on 2011-01-04
I mean, once unmounted, what to do next?
(sorry for silly questions!)

---

### Post by Hatryst on 2011-01-04
> **anystupidname1 said:**
> Give up and drink beer? You'll need to ask more precise questions.
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

GParted documentation is TOO hard to understand...

I have unmounted the disk, now what?
Please, let me know...

---

### Post by TeoBigusGeekus on 2011-01-04
Right click the disk and select delete.
Once the partition table is deleted, you will have unallocated space.
Select it and click create. Give size, file system and create the first partition.
Create the second partition from the remaining unallocated space using the same procedure.

---

### Post by Hatryst on 2011-01-04
[IMG]http://i572.photobucket.com/albums/ss162/Hatryst/nowwhat.png[/IMG]


Here we are, after unmounting. What next?

---

