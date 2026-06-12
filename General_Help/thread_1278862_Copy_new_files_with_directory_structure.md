---
title: "Copy new files with directory structure"
date: 2009-09-30
forum: General Help
---

### Post by Zalbor on 2009-09-30
Hello, let me try to explain what I'm looking for (skip to the bottom for the one-line question if you want).

There is a directory with many subdirectories and files. I want to manually backup files from it once a month, but **only the files that were modified since the last time I did it**, and burn those files on a DVD.
To do that, I need a way to select all files and subdirectories from that directory that were modified since a specific date (which I'll want to set).
The "find" utility can do this already, but I also need to keep the directory structure of the source directory. For example, if the directory is /home/blah/Documents and the files modified since 1 Sep 2009 are Documents/dir1/file4 and Documents/dir3/subdir8/file1, I want to create a directory that's to be burned which have this structure:
```
TO-BE-BURNED/
|
|
#--dir1/
|  |
|  |
|  #--file4
|
|
#--dir3/
   |
   |
   #--subdir8/
      |
      |
      #--file1
```

Basically, **I want to only copy files newer than a specific date and retain the directory structire of the source dir**.

I hope I've explained it well.
Does anyone know a way to do this easily?

---

### Post by geirha on 2009-09-30
GNU cp has a --parents option which keeps the directory structure, so you probably want something like:
```
cd /home/blah/Documents && find ... -exec cp --parents -t /dest/ {} +
```

---

### Post by Zalbor on 2009-09-30
I think that should work... Thanks a lot!

---

