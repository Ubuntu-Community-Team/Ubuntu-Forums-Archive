---
title: "Why Windows can't read Ubuntu hard disk?"
date: 2009-09-06
forum: General Help
---

### Post by carlosgs91 on 2009-09-06
.

---

### Post by Whiffle on 2009-09-06
Yep.  Windows doesn't have a driver for ext3 or ext4 out of the box.  

This might support it eventually, but not yet:
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by scragar on 2009-09-06
Windows doesn't support the EXT4 file system.
I know it's possible to read EXT3 file systems on windows using a work around, but I have no idea about support for EXT4.

[http://en.wikipedia.org/wiki/Comparison_of_file_systems#OS_support](http://en.wikipedia.org/wiki/Comparison_of_file_systems#OS_support)
Scroll down to EXT4.

---

### Post by gmjs on 2009-09-06
Yes.  Windows can't read the extX file system.

Personally, I use the following program if I ever want to transfer something from my Linux ext3 partitions to Windows:

[http://www.chrysocome.net/explore2fs]("http://www.chrysocome.net/explore2fs")

I don't know if it reads ext4 though.  Still, it may be worth a try.

You can always copy files to the Windows disk from Ubuntu.  An alternative would be to set some disk space aside for data and format as NTFS or FAT32 that's accessible by both systems.

Hope this helps.

---

### Post by Bartender on 2009-09-06
Your external drive must be FAT or NTFS?

---

### Post by carlosgs91 on 2009-09-06
.

---

