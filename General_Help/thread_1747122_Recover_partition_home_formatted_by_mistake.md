---
title: "Recover partition /home formatted by mistake"
date: 2011-05-02
forum: General Help
---

### Post by jlotero on 2011-05-02
My hard drive has the following partitions:
/dev/sda1 ntfs (reserved for system)
/dev/sda2 ntfs (win7)
/dev/sda3 extended partition with the following:
  /dev/sda5 (swap)
  /dev/sda6 (64bit Ubuntu 10.10)
  /dev/sda7 (32 bits kubuntu 10.10)
  /dev/sda8 (32-bit Ubuntu 10.10)
  /dev/sda9 (/home shared by sda 6, 7 and 8)
When trying to upgrade from version 10.10 to 11.04,  accidentally I marked the partition /home to be formatted. (I realized this when the process already were at about 15% of implementation)
At this point, both gparted and testdisk identified /dev/sda9 in the partition list, but I could not access to its contents.
Is there any way to recover this partition and / or content?
As can be expected, /home is probably the most important part (using data from various years). I appreciate your help.
jlotero

---

### Post by Megaptera on 2011-05-02
Not used it myself, but have seen Test Disk suggested here for this type of situation:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Hope this helps.

---

### Post by oldfred on 2011-05-02
I have used photorec (part of testdisk) to recover folders I accidentally deleted. It just scans drive for any data that looks like a file and copies to another drive. It does not recover file names. I had saved a text file many times and it found many copies. Between backups & many copies (grepping for similar info in all text files found) I recovered most of that file, but never was sure I found last saved version. And the more files you have, it becomes a huge task.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by jlotero on 2011-05-02
Thanks for the replies. I'll try with Photorec. I guess it will take to me quite a long time, so I'll have a tough job ahead. I'll let you know the results, whether or not successful. Thank you again.

---

