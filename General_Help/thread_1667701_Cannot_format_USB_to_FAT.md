---
title: "Cannot format USB to FAT"
date: 2011-01-15
forum: General Help
---

### Post by Kranix on 2011-01-15
I don't know which section this should be in, so I just placed it here.

I'm currently on my Ubuntu 10.10 laptop, and I wish to install Linux Mint 10 on my desktop using a 4 GB Verbatim STORE N GO, so I want to format it to FAT, as that's the only format option I see that is compatible with Windows; I can format to ext2 just fine, but when I try to format it to FAT, I get this message:

```
Error formatting volume

Error creating file system: helper exited with exit code 1: helper failed with:
Total number of sectors (7892040) not a multiple of sectors per track (62)!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test

mkfs.vfat 3.0.9 (31 Jan 2010)
```

---

### Post by ajgreeny on 2011-01-15
Have you tried gparted?  It may be worth deleting the current partition(s) on the flash drive first, then making a new one with fat32 as the format type, again using gparted.

---

