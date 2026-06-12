---
title: "Formatting Bootable USB"
date: 2011-12-29
forum: General Help
---

### Post by Kodeine on 2011-12-29
So I've got a 8GB verbatim USB device that I was intending to boot the Chrome OS from. But before that I needed to format it. I do so with disk utility and attempt to format it to 'FAT' (v32 I presume) but it gives me an error message.

**Error creating file system: helper exited with exit code 1: helper failed with: Total number of sectors (4005856) not a multiple of sectors per track (62)! Add mtools_skip_check=1 to your .mtoolsrc file to skip this test mkfs.vfat 3.0.9 (31 Jan 2010)**

It does however create a FAT partition of 2.1GB. Leaving the remaining 5.9 as empty space. I've tried locating this '.mtoolsrc' but I can't find it? Furthermore do I have to format it to FAT or could it be a Linux file system like ext*?

---

### Post by DanR01 on 2011-12-29
Could you install gparted

```
sudo apt-get install gparted
```and try using that?

FAT32 is compatible with Windows and Linux file systems so that would be your ideal choice.

---

