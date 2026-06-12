---
title: "install to second drive only"
date: 2010-02-10
forum: General Help
---

### Post by examinator on 2010-02-10
urgent Help!

I am new at Ubuntu/Linux.  On a pc with two hard drives how do I install Ubuntu on the second drive totally for 39 gigs.

---

### Post by ubudog on 2010-02-10
There should be an option in the "Partioner" part of the install process.

---

### Post by lindsay7 on 2010-02-10
When you use the install disk, you will come to a point where you will be asked how and where to install Ubuntu. If you have two disk drives the will be named hd0 for the first one and hd1 for the second one.  They will or can also be called sda and sdb.  Chose the manual install option and pick the disk where the 39 gigs is located.  If this represents the whole disk just use the whole disk drive. If this is a partition just use that partition.

---

### Post by examinator on 2010-02-10
Thank you for your response.
when I choose "specify manually"
it scans the disks and reports the following

/dev/sda1   fat32   36 gigs -     drive c
/dev/sda5   fat32   43 gigs-      drive d
/dev/sda6              2311 mb     CD/DVD drive
/dev/sdb6                                empty stick dve/  floppy b drive
/dev/sdb5  NTFS    40 gigs        drive h   
reformat?

when I highlite drive h 
error message    no root file system defined 
rectify? 

Drive h is a slave on NT file system 

what do I do now?

---

### Post by lindsay7 on 2010-02-11
When you click on sdb5 there should be a little box towards the right of the screen, you want to click on that and make that the "/" or root  and  format that partition to ext3 leave all the other boxes unchecked or they will be formatted and you will lose everything on those partitions.

---

### Post by lindsay7 on 2010-02-11
Take a look at this, it should help,

[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

