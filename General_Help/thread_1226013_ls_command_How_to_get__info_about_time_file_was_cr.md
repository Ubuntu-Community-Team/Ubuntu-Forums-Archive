---
title: "ls command: How to get  info about time file was created?"
date: 2009-07-29
forum: General Help
---

### Post by abcuser on 2009-07-29
Hi,
on Ubuntu 9.04 I would like to get info about time file was created. How to write such a ls command in terminal?
Regards

---

### Post by lykeion on 2009-07-29
list files using long listing format:

ls -l

use man to get info on a command in linux:

man ls

---

### Post by abcuser on 2009-07-29
Hi,
ls -l displays last updated time of file, but I need time at which file was created. This two times can be the same if there was no update to the file.
Regards

---

### Post by Zorael on 2009-07-29
Do prove me wrong, but;
> Only FreeBSD and the UFS2 filesystem support file creation times (that they call "birth time")

More info (pdf): [http://linux.derkeiler.com/pdf/Mailing-Lists/SuSE/2005-08/1668.pdf](http://linux.derkeiler.com/pdf/Mailing-Lists/SuSE/2005-08/1668.pdf)

---

### Post by WilliamJenningsBryan on 2009-07-29
Unfortunately, Zorael is correct.

Only last modified date is stored. Some (primarily older editions) man pages even get this wrong and call it file creation date.

---

### Post by abcuser on 2009-07-29
Hi,
I see "creation time" is not available. Using 'stat myfile.txt' command I see:
```

  File: `myfile.txt'
  Size: 11        	Blocks: 8          IO Block: 4096   regular file
Device: 801h/2049d	Inode: 5666        Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/    me)   Gid: ( 1000/    me)
**Access:** 2009-07-29 12:55:29.996430208 +0200
**Modify:** 2009-07-29 12:55:29.996430208 +0200
**Change:** 2009-07-29 12:55:30.014550298 +0200

```
Regards

---

### Post by sisco311 on 2009-07-29
only, the ctime(ls -lc), atime(ls -lu) and mtime(ls -l) is stored.
[http://www.brandonhutchinson.com/ctime_atime_mtime.html]("http://www.brandonhutchinson.com/ctime_atime_mtime.html")

---

