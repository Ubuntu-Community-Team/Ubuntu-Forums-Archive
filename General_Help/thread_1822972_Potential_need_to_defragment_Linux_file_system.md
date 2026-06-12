---
title: "Potential need to defragment Linux file system"
date: 2011-08-11
forum: General Help
---

### Post by MorrisseyJ on 2011-08-11
Hi,

I am wondering about the potential for needing to defragment my Linux system.

From this explanation of why you don't need to defragment a Linux file system ([http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)) i see that the caveat for fragmenting a linux file system is when it is more than 80% full. 

I have been using an old computer, with a relatively small (80GB), and thus full, hard drive - over 80%. 

Thankfully i am getting a new computer with a nice 320GB hard drive in the next couple of days. My question thus pertains to whether or not i need to defragment the disk before copying files across to my new machine. 

My logic is as follows:
If my linux hard drive is over 80% full, i have been fragmenting files when i have been amending them and saving them to the hard drive.
When i have backed up these files onto an external disk, they have stored in fragmented form - as a direct copy of my hard drive
In addition, work i have done to those files stored only on my external hard drive - which is FAT32 - would mean that they are also fragmented
Thus if i copy the files from my external hard drive onto my new machine, they will again copy in the format in which they sit on the external drive, and thus copy in fragmented form. 

So my solution would be to copy everything onto the external drive, defragment it, and then copy it to my new machine. Either that or, take everything onto my new machine and then defragment there. 

In this case i was wondering (i) is my thinking above correct and do i need to defragment? If so (ii) can anyone suggest a linux tool for defragementing, or do i need to do it via windows on the external drive?

Any ideas would be appreciated.

Thanks.

---

### Post by dino99 on 2011-08-11
you can force a fsck on next reboot: sudo shutdown -r now

but the system automatically take care every 35 loads (cronjob) so no one pay attention to such maintenance.

The most critical in your case is to make room: at least it need 10 % free space to be able to store tmp files and apply updates.

 So maybe you can remove ubuntu-desktop (metapackage) and software installed by it which you dont need. Or reduce the swap partition (2 GiB / 4 GiB if suspend/hibernate is used)

---

### Post by CatKiller on 2011-08-11
> **MorrisseyJ said:**
> My logic is as follows:
If my linux hard drive is over 80% full, i have been fragmenting files when i have been amending them and saving them to the hard drive.
When i have backed up these files onto an external disk, they have stored in fragmented form - as a direct copy of my hard drive
In addition, work i have done to those files stored only on my external hard drive - which is FAT32 - would mean that they are also fragmented
Thus if i copy the files from my external hard drive onto my new machine, they will again copy in the format in which they sit on the external drive, and thus copy in fragmented form. 

Only if you were using *dd*. If you were using anything that copies the files rather than the filesystem structure - *cp*, *tar*, *rsync* - then your files will not be fragmented.

The files that you've put on a FAT32 partition can't be fragmented, because you can't have used dd. Except for the fact that FAT is horrible, of course.

There's no reason why your files will have become fragmented just from normal use. The article you linked to explains why Windows filesystems are so rubbish and why Linux filesystems are better. Fragmentation only happens when you want to make the file bigger and there isn't room next to the existing file. In Windows this happens always. In Linux this happens rarely.

There is a command to see how much file fragmentation you have, but I can't recall what it is at the moment. Even so, file fragmentation doesn't come with a performance penalty in the same way that it does in Windows. You can defragment ext2 and ext3 filesystems, but that requires that you unmount those filesystems first. Ext4, AIUI is able to be defragmented whilst mounted, although I've never tried it.

In any case, moving the files to another filesystem in exactly the way you're planning to do anyway is perfectly sufficient to remove any fragmentation that might exist anyway.

EDIT: @dino99: fsck doesn't defragment, it just checks the filesystem for errors. The OP doesn't need to save space; he's getting a bigger hard drive.

---

### Post by Wim Sturkenboom on 2011-08-11
> **MorrisseyJ said:**
> When i have backed up these files onto an external disk, they have stored in fragmented form - as a direct copy of my hard drive
In addition, work i have done to those files stored only on my external hard drive - which is FAT32 - would mean that they are also fragmented
Thus if i copy the files from my external hard drive onto my new machine, they will again copy in the format in which they sit on the external drive, and thus copy in fragmented form. 

If you copy files (e.g. with nautilus or the cp command), the copies are (in principle) not fragmented. They will only be fragmented if the destination drive is already fragmented.
Copying those files back from the backup drive to the new system with a fresh HD, will take away any fragmentation.

---

### Post by MorrisseyJ on 2011-08-11
Great, 

Thanks for all the advice. Most informative and good to hear that i don't have to fiddle with defragging.

---

