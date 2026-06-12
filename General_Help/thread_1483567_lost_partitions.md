---
title: "lost partitions"
date: 2010-05-14
forum: General Help
---

### Post by pavel989 on 2010-05-14
ok so heres my issue

i had a partition table that looked something like this

[ntfs][ntfs][extended]
the extended had something like:
[bt4 /] [bt4 /home] [lucid /] [lucid /home] [swap]


so i installed windows 7 today, and in doing so, deleted the second ntfs. i noticed immedietly that something wasnt right because the installer saw the extended partition but nothign within it.

to be clearer, prior to deleting the second ntfs, win 7 DID see the extended and partitions within, just knew nothing about them.

well i deleted the first ntfs anyway, and used the new unallocated space to install win 7. finally got home where i made a ubuntu live usb (ftw)

and uh yeah, so im in my live cd, and it sees the extended partition and the swap, but none of the ext4 bt's or lucids.

now i found a tool: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) to restore files.

all i really care to restore is a few scripts, the rest of the crap was just customization and... crap. 

so using that tool, would i be able to at least restore the scripts if not restore the partitions?

---

### Post by cariboo on 2010-05-14
You can use testdisk, which is in the repositories to restore your missing partitions. The System Rescue CD may include testdisk.

---

### Post by pavel989 on 2010-05-17
Thank you! this worked perfect. i wish i new about this tool long ago.

---

