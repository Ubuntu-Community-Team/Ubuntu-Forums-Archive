---
title: "Azureus write error, disk full"
date: 2009-09-04
forum: General Help
---

### Post by Weidbrewer on 2009-09-04
First off, I'm using Azureus 3.x on an Ubuntu 64 installation.  I had some stuff DLing last night, and when I got up this morning, all of them had errored out.  It said that there was a write error, and the disk was full...hoever, the drive that they're DLing to still has 202GB free.  Any ideas?

---

### Post by Blackie_Chan on 2009-09-04
Are you downloading the files to a temporary area first. If so, is that disk full? Is any of your disks full? 

Empty your trash and check that drives still has space on them.

---

### Post by Weidbrewer on 2009-09-04
Trash = Emptied
Destination drive = 202 GB free
System drive = 14 GB free

So, it appears that there's space where ever it might be ending up.

---

### Post by sedawk on 2009-09-04
If you sit in front of the machine there are some things you can test:

* monitor disk usage with "df" to see if some disk is running full
* monitor disk I/O with "iostat", e.g. "iostat 60 120" to show
  the I/O every minute for 120 times (requires package sysstat).

* can you copy any other big file to the DL directory without 
  problems?
  (I wonder if your user is running into a quota limit, but quota
   is normally not installed on Ubuntu. Or is there a problem with
   big files, e.g. does your file system not allow files bigger than 4 GB).

---

### Post by Weidbrewer on 2009-09-04
> **sedawk said:**
> 
* can you copy any other big file to the DL directory without 
  problems?
  (I wonder if your user is running into a quota limit, but quota
   is normally not installed on Ubuntu. Or is there a problem with
   big files, e.g. does your file system not allow files bigger than 4 GB).

That's certainly easy enough for me to test when I get home.  As far as i know, there aren't any limits on the files, though this *is* a recent migration from a 32-bit install to a 64-bit install...so, if there was something extra slipped in with this version...

---

### Post by Nostalos on 2009-09-04
Checked if you have plenty of free inodes?  "df -i"

---

### Post by Weidbrewer on 2009-09-04
And what, exactly, is a "free inode"?

(Is this some strange limitation on 64-bit?  On 32, as soon as i got my ports forwaded correctly, I never had a problem with this software.)

---

### Post by Nostalos on 2009-09-04
[http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode)

Had nothing to do with 32bit or 64bit.  Inode is basically a pointer to a position on a disk.  Typically when formatted, it is 1 inode per every 4k.  Part if the way the filesystem works.  

You write a file to disk, the machine looks for it by inode.  Problem is that if you have alot of files smaller than 4k it will still use an inode even though its smaller than 4k.    Run out of inodes and your disk is technically full with being truely full.


Its not a likely scenario,  you don't see it very often but it does happen.   

"df -i"  will give you a ratio of used to free inodes just like it does for diskspace.

---

### Post by Weidbrewer on 2009-09-04
Okay...figured it out...The *torrents* were saving to the right place, but the *files* weren't.

---

