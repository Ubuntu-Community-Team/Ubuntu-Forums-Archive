---
title: "Merge Directories"
date: 2010-05-04
forum: General Help
---

### Post by lakerssuperman on 2010-05-04
I recently had to rescue files from a dying hard drive using Photorec.  However, it dumped the files randomly in many different directories.  Is there a way I can transfer the contents of these directories into one master directory without the file structure.  For example, I have folders 1 through 10 as subdirectories in folder X.  How can I transfer the contents of all those folders into folder Y while getting rid of the subdirectories 1 - 10?

---

### Post by StuartN on 2010-05-04
> **lakerssuperman said:**
> For example, I have folders 1 through 10 as subdirectories in folder X.  How can I transfer the contents of all those folders into folder Y while getting rid of the subdirectories 1 - 10?

```
mkdir y
mv x/*/* y
rmdir x/*
```

This will move all the contents of subdirectories of x into y, then remove all the subdirectories of x. Only empty subdirectories will be deleted.

---

### Post by lakerssuperman on 2010-05-04
Works great.  Much appreciated.

---

### Post by tomillares on 2011-03-27
Thanks. Very useful

---

