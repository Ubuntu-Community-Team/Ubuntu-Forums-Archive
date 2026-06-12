---
title: "rsync luckybackup ntfs file names"
date: 2011-02-07
forum: General Help
---

### Post by cscj01 on 2011-02-07
I have the following situation using luckybackup on Maverick and NTFS file systems.

Using NTFS under Ubuntu allows for all characters to be used in file names except / and ".  I have a luckybackup profile that backs up an NTFS file system to another NTFS file system on an external USB hard drive.  The hard disk file names of some files contain a colon ( : ).  These files cannot be backed up sucessfully because of the colon in the names.

Since both file systems are being managed by Ubuntu, where is the problem?

I am beginning to suspect it may have something to do with USB support.  If this is the case, is there a way to get the USB file system to allow the colons?

---

