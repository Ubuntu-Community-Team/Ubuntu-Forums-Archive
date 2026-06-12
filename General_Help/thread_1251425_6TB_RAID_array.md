---
title: "6TB RAID array"
date: 2009-08-27
forum: General Help
---

### Post by mattwallace on 2009-08-27
Hi Everyone, i'm looking to build a large 6TB RAID array to work within our macintosh network. We tried building a file server before with another flavour of linux, but we were stumped with having to keep the array to 2TB or under. Would we come across the same sort of thing with Ubuntu? 

Any help would be appreciated. Thanks very much,

Matt

---

### Post by blueridgedog on 2009-08-27
A hardware raid device should build the array and expose it to the OS as one or more physical devices.  Ubuntu should be able to handle a 6T device.

These links may describe why you hit a 2T limit:

[http://www.howtoadvice.com/Ext3Max/](http://www.howtoadvice.com/Ext3Max/)

and

[http://www.cyberciti.biz/tips/what-is-maximum-partition-size-supported-by-linux.html](http://www.cyberciti.biz/tips/what-is-maximum-partition-size-supported-by-linux.html)

---

### Post by fela on 2009-08-27
You just need to create the filesystem with a larger block size. To do this you have to make the filesystem with a tool such as mkfs.ext3. I recommend ext3 for a server as it's very reliable. If you need speed you could go for XFS. Have a look at the man pages for mkfs.xfs and mkfs.ext3.

Just curious to know but what kind of **** is going on all this 6TB? Is it a NAS or something? I run a NAS but with a 500GB disk only.

---

### Post by guneza on 2010-11-08
Here's how I solved a similar issue.

[http://ubuntuforums.org/showthread.php?p=10089106#post10089106](http://ubuntuforums.org/showthread.php?p=10089106#post10089106)

---

