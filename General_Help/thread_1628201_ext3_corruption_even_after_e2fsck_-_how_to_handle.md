---
title: "ext3 corruption even after e2fsck - how to handle?"
date: 2010-11-22
forum: General Help
---

### Post by josir on 2010-11-22
Hi folks,
I have a corrupted ext3 partition and I don't know to fix it.

I issue:

umount /dev/sdb1
e2fsck -vfy /dev/sdb1

and I got several lines like:

Error reading block 13074432 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  Ignore error? yes

Force rewrite? yes

If I try to issue the same command, the same blocks are reported again. 

How can I fix the filesystem ?

Thanks in advance,
Josir Gomes

---

### Post by dcstar on 2010-11-23
> **josir said:**
> Hi folks,
I have a corrupted ext3 partition and I don't know to fix it.

I issue:

umount /dev/sdb1
e2fsck -vfy /dev/sdb1

and I got several lines like:

Error reading block 13074432 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  Ignore error? yes

Force rewrite? yes

If I try to issue the same command, the same blocks are reported again. 

How can I fix the filesystem ?

Thanks in advance,
Josir Gomes

You cannot fix a filesystem if the hard drive is faulty and has bad blocks.

BTW, ignoring errors does **not** fix them.

---

