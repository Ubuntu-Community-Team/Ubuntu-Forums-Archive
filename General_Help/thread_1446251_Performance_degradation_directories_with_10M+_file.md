---
title: "Performance degradation: directories with 10M+ files"
date: 2010-04-03
forum: General Help
---

### Post by likebucks on 2010-04-03
Hello,

I have directories storing a large number of files, and performance severely degrades when running a command like ls.

e.g. if I run ls -l, it would take several minutes before the results start showing.

Even doing an *ls -l | head* takes several minutes. 
One of these directories has over 13 million files in it.

I want to know, is there any recommended ceiling for the number of  files in a directory, and if there's a recommended subdirectory structure or way to handle large number of files in a directory.

Thank you!
Saket

---

### Post by new_tolinux on 2010-04-03
> **likebucks said:**
> I want to know, is there any recommended ceiling for the number of  files in a directory, and if there's a recommended subdirectory structure or way to handle large number of files in a directory.
I googled around somewhat today, and I can't find the "source" of it again yet, but 10-15K seems to be a good ceiling.
There also is a hard limit of 31998 subdirectories per folder.

That ls is taking long doesn't really seem odd, since I noticed that ls sorts the directory before listing it.

---

### Post by srs5694 on 2010-04-03
> **new_tolinux said:**
> I googled around somewhat today, and I can't find the "source" of it again yet, but 10-15K seems to be a good ceiling.
There also is a hard limit of 31998 subdirectories per folder.

The 31,998 subdirectories limit is true of ext2fs and ext3fs, but not of most other Linux filesystems. I *think* it's been lifted in ext4fs, but I've never tested that. I recently tested ReiserFS, XFS, and JFS, and found that none of them has this limit. (It's conceivable they've got higher limits, but all four supported at least 100,000 subdirectories in a test directory.)

> That ls is taking long doesn't really seem odd, since I noticed that ls sorts the directory before listing it.

The -f option to ls disables sorting. I haven't tested if it speeds up listings in crowded directories, but it's worth a try.

---

