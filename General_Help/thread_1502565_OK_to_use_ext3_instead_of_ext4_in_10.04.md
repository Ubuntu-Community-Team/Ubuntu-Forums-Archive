---
title: "OK to use ext3 instead of ext4 in 10.04?"
date: 2010-06-05
forum: General Help
---

### Post by Ernesto RD on 2010-06-05
Im about to install Ubuntu 10.04 NRE on my dell mini10v, along with windowsXP (dual boot), but i want to keep all my stuff ont he linux partition, and be able to access them from windows, so i read about a few programs that enable me to do this, but they are all designed for ext2 or ext3 NOT ext4.
So, i know i can select ext3 instead of ext4 during the ubuntu installation process (using manual partitioning option), but is there a disadvantage to using ext3 instead of ext4?
is there any particular reason why i SHOULD use ext4 instead of ext3 in 10.04?

thanks

---

### Post by VCoolio on 2010-06-05
No problem to use ext3 in 10.04. Remember that when you install the ext3 stuff on windows it will ask you to format the newly found partition! Of course, don't do that. Maybe it's better to have a ntfs data partition and access that from linux, but that's your call.

---

### Post by John Bean on 2010-06-05
> **VCoolio said:**
> Maybe it's better to have a ntfs data partition and access that from linux, but that's your call.

Yes. Linux can reliably read and write to native Windows filesystems, the reverse is not true (and not even close to being true).

---

### Post by Ernesto RD on 2010-06-05
Thanks guys, i have tought of the idea of keeping my data on an ntfs partition, but i would prefeer to keep them on an ext3/4 one for 2 reasons:

1.- I want then under the protection of linux, safe from viruses, etc. :)

2.- i like things to work as they are supposed to, so i want "my music" "my documents", shortcuts in linux to work (because they really are under my home dir) so i want to keep my songs, my docs, etc on those folders, so i can access them quickly under linux.

as (hopefully) linux will the primary OS, i only need read support fot the linux partitions under windows.
And ibe found this program called Ext2Read
[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)
It sais:
"Ext2Read is an explorer like utility to explore ext2/ext3/ext4 files. It  now supports LVM2 _**and EXT4**_ extents. It can be used to view and copy  files and folders. It can recursively copy entire folders. It can also  be used to view and copy disk and file     "

anyone used it? does it work ok?

---

### Post by John Bean on 2010-06-05
Yes, it works. But it's not integrated with Windows and it's read-only. You can look at files and copy them but you can't for example "run" them in situ. I use it to look at the contents of ext4-formatted USB drives and copy files to my XP netbook.

If you just want a one-way file copy it's great, but it's not a very comprehensive solution. Mounting NTFS in Linux is routine, safe, and standard. Far better option IMO.

---

