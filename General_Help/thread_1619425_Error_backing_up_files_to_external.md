---
title: "Error backing up files to external"
date: 2010-11-11
forum: General Help
---

### Post by FLCL on 2010-11-11
Hey all,
I just received a 1TB external(Western Digital) hard drive(NTFS) for backup purposes. I'm using an Ubuntu Live CD, and an external hard drive dock. I am transferring over esata and am receiving the error:
```
Connot open file: input/output error
```
Seems strange that it said "open". At any rate only about 60 of the 200+ GB were able to be transferred over...this won't do. I have tried to copy via CLI using ```
cp -r
``` and received the same issue. 

For clarification I am attempting to transfer from a mounted partition onto the mounted external.

Please help! I really need to back up this data.:confused:

---

### Post by FLCL on 2010-11-11
This seems to exclusively be effecting .mkv video files only. Any ideas? Thanks.

---

### Post by plucky on 2010-11-12
> **FLCL said:**
> This seems to exclusively be effecting .mkv video files only. Any ideas? Thanks.

What size are the files?

What filesystem are you using on the external drive?

If it is fat32 then there are file size limits that might be affecting you. 

From [Here](http://en.wikipedia.org/wiki/File_Allocation_Table)


> The maximum possible size for a file on a FAT32 volume is 4 GiB minus 1 byte (232&#8722;1 bytes). Video applications, large databases, and some other software easily exceed this limit. Larger files require another formatting type such as NTFS.



Good Luck

---

