---
title: "ISO mount question..."
date: 2010-07-18
forum: General Help
---

### Post by AndyCinDallas on 2010-07-18
I'm working through my Linux+ studies and I get the concept of mounting a device (or so I thought).

The instructor on the video shows a way to view the contents of an ISO-file (instead of having to burn it to CD first) by using the mount-command

He first mounts another Linux partition (/dev/sdb1) and calls it "test" from what I understand: **mount /dev/sdb1 /test/**

Then he mounts the ISO file into there: **mount -o loop xyz.iso /test/** 

and then reads the contents by doing: **ls /test/**

First question - is the name "test" simply a way of assigning a short, virtual name to /dev/sbd1 in this case?

Second - to mount an ISO, is it necessary for another drive/partition to be mounted? I don't have a second Linux drive, only Windows - so what do I have to create (via command-line, of course) into which an ISO-file can be mounted for viewing ?

Thanks for any help.

---

### Post by gmargo on 2010-07-18
> First question - is the name "test" simply a way of assigning a short, virtual name to /dev/sbd1 in this case?Effectively yes.  The correct term for the /test/ directory is "mount point".  After the "mount /dev/sdb1 /test/" command, the filesystem that resides on the physical device /dev/sdb1 partition will now be visible under the /test/ directory.

It is unnecessarily confusing that the instructor chose to perform the ISO mount onto the same /test/ directory without unmounting the first one.  After the "mount -o loop xyz.iso /test/" command, then the filesystem residing on the xyz.iso image is visible under the /test/ directory.  The confusing part is this: the /dev/sdb1 partition is **still** mounted on the /test/ directory, but the ISO image is mounted **over** it.  Under /test/ you will only see ISO content, but if you unmount the ISO, then the /dev/sdb1 content will be again visible under /test/. 

> Second - to mount an ISO, is it necessary for another drive/partition to  be mounted? I don't have a second Linux drive, only Windows - so what  do I have to create (via command-line, of course) into which an ISO-file  can be mounted for viewing ?To mount an ISO you only need a directory.  I typically do something like this:
```

mkdir /media/disk1
mount -t iso9660 -o ro,loop xyz.iso /media/disk1

```Then the read-only (ro) contents of the iso9660 filesystem on xyz.iso will be visible under /media/disk1.  (Then use disk2, disk3 etc to mount multiple ISOs at once.)

---

### Post by AndyCinDallas on 2010-07-18
Ahhhh... now that I understand! 

So you first create a directory using the mkdir command - and then mount the desired media into that so it can be read - gotcha!

Thanks a ton, gmargo! :D

---

