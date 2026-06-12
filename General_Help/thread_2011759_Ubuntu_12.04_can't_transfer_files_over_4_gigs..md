---
title: "Ubuntu 12.04 can't transfer files over 4 gigs."
date: 2012-06-27
forum: General Help
---

### Post by xd3rr1kx on 2012-06-27
A friend of mine cannot transfer a single file with a size over 4.3 gigs to external drives. 
We've tried splitting the file into pieces to transfer on it and re-combine the files and it still goes down to 4.3 gigs instead of the 5.9 file size. Any ideas?

---

### Post by rubylaser on 2012-06-27
Almost all external drives are formatted as [FAT32]("http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32").  The maximum file you can put on a FAT32 filesystem is 4GB.  If you want to put larger files on there, you'll need to use a different filesystem on the drive like NTFS (if you wan to maintain compatibility with Windows), or ext4.

---

