---
title: "dd'd the front of my storage drive"
date: 2009-07-11
forum: General Help
---

### Post by Sjeti on 2009-07-11
-----:~$ sudo dd if=/dev/urandom of=/dev/sdb
^@^C440972+0 records in
440971+0 records out
225777152 bytes (226 MB) copied, 50.5128 s, 4.5 MB/s

------:~$
------:~$
------:~$
------:~$ sudo gparted
======================
libparted : 1.8.8
======================
/dev/sdb: unrecognised disk label
------:~$ 


So, I was going to clean my external hard drive. However, I was a letter off.  Luckily I realized my mistake before I left and managed to cancel the operation, but as I'm sure you guys know At the very least 226MB of my data is completely irrecoverable.  My big question is, instead of using something like photorec, is there anything I can use write a MBR and restore the data in place?

I'm sure its not that common of an occurrence that someone dd's the front of their storage drive, but I'm pretty sure I'm not the first person to do it.

---

### Post by Sjeti on 2009-07-11
No one?

---

### Post by Sjeti on 2009-07-12
I'm trying to recover my directory structure.  Is there any way to do this?

---

### Post by louieb on 2009-07-12
Try** testdisk** what it does is try to restore the partition structure. In the repositories. and on a variety of rescue CDs. [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk") 
[SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by jerome1232 on 2009-07-12
+1 for testdisk you probably just destroyed your partition table and a little bit of data at the front of the first partition. Test disk should be able to recreate the partition table for you, then fsck your partition and hopefully no valuable data was lost at the front of that partition.

---

### Post by Sjeti on 2009-07-13
Yea, I had tried getting testdisk to detect the partition, but I'm pretty sure I trashed the file allocation table and everything else important on the disk.

I managed to salvage all my music, etc via photorec, but my year's worth of wine installs are all gone. -_-


So, let me echo what I've been told, and even told to people before I did this.  Pay attention with dd.

---

### Post by Sjeti on 2009-07-13
I still have the image on my 1TB drive if anyone has any ideas.  I attempted to detect the partition via testdisk, as well as an attempt to grab the file structure via sleuthkit.  Neither worked.

---

