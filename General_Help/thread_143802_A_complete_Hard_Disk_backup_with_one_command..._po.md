---
title: "A complete Hard Disk backup with one command... possible with a live CD??"
date: 2006-03-13
forum: General Help
---

### Post by simone.brunozzi on 2006-03-13
Hi there,
I have the necessity to abilitate a complete disc backup (I don't mean just the data, I mena THE ENTIRE DISK); maybe it's better to call it an "hard disk image".
I need it to be able to restore it in case of disk break.

This is the situation: there are some desktops at my university, with only one disk. On those desktops some students work for thesis and papers, and they save datas only once a week; I'd like to implement a system that boot a CD, makes a copy of the entire Hard Disk (sending it to a remote server in the internal LAN), or eventually restore a precedently saved hard disk image (including the operating system, etc).

Do you have any suggestions on how to do that, and which tools to use?

Thanks in advance for any help!!

---

### Post by hw-tph on 2006-03-13
Creating images of entire disks isn't too great of an idea I think. It could be hard to restore the image onto a disk with different geometry. However, it is certainly possible but I would go for imaging the partitions one by one instead.

The dd command is actually pretty much all you need. Boot from a livecd (just about anyone) and **dd if=/dev/hda1 of=/path/to/image/location.img**. You could easily write a script to perform the backup over the LAN with the images named after hostname, partition and date.


Håkan

---

### Post by cotcot on 2006-03-13
I do not know about 1 command for an entire disk. "dd" as above works fine. I use partimage to image partitions. It allows compression and splitting up the image in subimage files (is needed when you saved to FAT as this has a 4 GB file limit). Maybe this is worth a look at.
It is usefull to save the partition table too.

---

### Post by TLE on 2006-03-13
I agree that it is probably better to make images of the partitions, but i would definitely go for a program called partimage. It offers an easy to use terminal based user interface and allows for the possibility to not save the empty part of the partition. (As I understand it, if you use dd to back up a 10GB partition the backup file will be 10 GB no matter how much of it is used, that's not the case with partimage), plus it supports compression, making the backups even smaller. It should be evailable on most live cd's but I would recommend [System rescue cd]("http://www.sysresccd.org/Main_Page"). There are guides for partimage at their [homepage]("http://www.partimage.org/").

But no matter if you choose dd or partimage, you should definitely investigate if it will be possible to restore those images to a new HD, and what kind of demands that might pose.
Regards TLE

---

### Post by handy on 2006-03-13
I believe that you can also .tar a whole partition quite easily!

If you do a search of the forum this topic has been well covered before.

All the best...:KS
[B]
[Edit:][/B] *Here's a couple:*  

[http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+hard+drive](http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+hard+drive)

[http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/)

---

### Post by cotcot on 2006-03-13
There are restrictions with restoring images by mean of partimage. The partition on which the image will be restored must be at least equal or larger as the partition size from where the image was made. If you make an image from a hard disk partition to restore it to the same partition there is not problem. 
I tried saving and restoring successfully on my both computers (see signature) with all partitions before I adopted the system. I have the images on a external HDD and use Kanotix live CD because of its support to USB 2.0.
The images are some 80 % of the used part of the partitions used gz compression. 80 % look as low compression rate but this is because of an amount of jpeg files)

---

### Post by simone.brunozzi on 2006-03-13
Thanks a lot guys, good suggestions!

I need now to take a look at them and understand which one is better suitable for my needs.

Cheers,

---

### Post by OneSeventeen on 2006-03-13
Just out of curiosity, if I were to have used one of the above how-to's on making a .tar of my entire disk, then could it be safe to say that even if I changed the partition table, and mounted the various folders on separate drives, I could still restore the same .tar as long as each folder had enough space for the contents?

Sounds like a cool way to back up and restore, since it would be pretty hardware independent.  (meaning you could change from a single larg hard drive to 2 or 3 small but faster ones, and still use the same method to restore it.)

---

### Post by handy on 2006-03-13
I haven't done it yet, & it is only a little more complicated than you suggest.  

It has all been done on the forum before, just search it out.

All the best! :KS

---

