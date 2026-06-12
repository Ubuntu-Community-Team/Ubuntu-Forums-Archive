---
title: "Hard Drive Went Missing in Windows"
date: 2009-12-07
forum: General Help
---

### Post by rknopf on 2009-12-07
Hey, sorry if this is a stupid problem.  I have a 3 TB raid 5 that I wanted to mount automatically in ubuntu on start up.  I was advised an easy way to do this is to set the flag for this hard drive to "boot" in gparted.  After doing this the hard drive does indeed auto mount as ntfs and I just have to enter a password to access it.  The problem is now this hard drive is entirely missing in windows.  How do I get it back in windows?  And, ideally, how do I get it back and still have it automount in ubuntu?  Thanks for any help.

---

### Post by pqwoerituytrueiwoq on 2009-12-07
windows ignores linux systems does not recognize the format you can try the disk management utility in windows no idea if it will work but worth a look
control panel-> administrative tools

---

### Post by Toast2120 on 2009-12-07
Depending on the filesystem you can probably see it in Disk Management and do a format (useless for you) but mounting a Linux partition in Windows may be a pipe dram for many.

If you have the extra hardware I advise building a server, as Windows 7 has better experiences with filesharing between another computer.

---

### Post by rknopf on 2009-12-07
It does't actually show up in disk manager anyone either.  It's very strange.  And guys, I'm not trying to set up filesharing, primarily I just want to know if I can get the partition back in WINDOWS without having to copy all the files to another drive and completely reformatting.  I don't see why I wouldn't be able to do this without reformatting the drive.  There must be some way or some utility that will do it.

---

### Post by rknopf on 2009-12-08
Sorry, bump...

---

