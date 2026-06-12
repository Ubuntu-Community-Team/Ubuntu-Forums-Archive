---
title: "How to only copy newer files from one location to another location"
date: 2012-09-28
forum: General Help
---

### Post by mike_kzc on 2012-09-28
Hi all,

I'd like to back up the important programs. say, all my programs are in a folder named MAT1 (which is about 20GB), I copied this folder to another disk every time, also named MAT1.

The problem is that: most of the files in these two folders are the same, is there any simple way to only copy newer files to the backup folder?

Thanks.

Mike

---

### Post by cortman on 2012-09-28
IIRC Nautilus can discern file age and will prompt you accordingly when copying. You can also use

```
cp -u
```

Which, from the cp man page "copies only when the SOURCE file is newer than the destination file or when the destination file is missing"

---

### Post by zombifier25 on 2012-09-28
There's rsync, a very powerful command line tool used to backup files. Usage:
```
rsync -av --delete /source/folder /source/folder/no/2 /source/folder/no/blabla /destination/folder
```
With this command, all files from /source/folder, /source/folder/no/2, and /source/folder/no/blabla will be copied to /destination/folder, but **only the newly modified files**. Also, the --delete flag will delete files in the destination that are no longer in the source.

(If you want graphical, use grsync)

---

### Post by agillator on 2012-09-28
rsync will do the job for you. It should already be installed. Check the man page (man rsync). If you want a full backup system take a look at rsnapshot which is based on rsync.

---

### Post by jerrrys on 2012-09-28
Rsync is part of the default install and there are several GUI's available for it.

Two that I like:

[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)

Both are in the software center

---

### Post by mike_kzc on 2012-10-05
thank you all guys. learning new stuff, hahah.

---

