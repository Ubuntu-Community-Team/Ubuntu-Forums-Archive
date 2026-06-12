---
title: "File Operation Errors - &quot;file too large&quot;"
date: 2009-11-19
forum: General Help
---

### Post by jim78 on 2009-11-19
Hi, I keep getting an error when trying to copy a dvd iso file from my home folder to another partition. It gets to 4gb of a 4.3gb file and then errors saying "file too large". What the??? The partition has 160gb of space left on it.

---

### Post by Cheesemill on 2009-11-19
Sounds like the partition your copying to is formatted as FAT32.
FAT32 has a file size limit of 4GB for a single file.

You'll need to change the filesystem to either NTFS (if you still want Windows compatiility) or EXT2/3/4 if your only using it with Ubuntu.

---

### Post by jim78 on 2009-11-19
Yep, that's it. Didn't think of that. I don't normally have files this big so it's never been a problem. O.K, so I've formatted it to ext3 but now I don't have write permissions
for it. How do I set them?

Thanks.

---

