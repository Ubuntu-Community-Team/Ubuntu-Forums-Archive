---
title: "copy ALL files in a directory"
date: 2010-12-11
forum: General Help
---

### Post by yc2 on 2010-12-11
Hello,

I need to make a complete backup of the files in my Drupal installation (including hidden (.) files and what have you?). I have checked around and finally settled for this command (first cd to source-dir)

tar cvf - . | (cd /dest/dir; tar xvf -)

Is this the simplest and safest way to copy _ALL_ the files of a directory?

Thanks

---

### Post by TiBaal89 on 2010-12-11
No need to do anything funny at all.  tar automatically is recursive and automatically includes hidden files.  

To confirm, I just made the following directory:

```
$ ls -al temp/
total 16
drwxr-xr-x  4 mccambrm mccambrm 4096 2010-12-10 22:44 .
drwxr-xr-x. 3 mccambrm mccambrm 4096 2010-12-10 22:46 ..
drwxr-xr-x  2 mccambrm mccambrm 4096 2010-12-10 22:43 .hidden
-rw-r--r--  1 mccambrm mccambrm    0 2010-12-10 22:43 .hidden.txt
drwxr-xr-x  2 mccambrm mccambrm 4096 2010-12-10 22:43 visible
-rw-r--r--  1 mccambrm mccambrm    0 2010-12-10 22:43 visible.txt
```

and tar'd it up:

```

$ tar cvzf test.tar.gz temp/
temp/
temp/visible.txt
temp/.hidden.txt
temp/visible/
temp/.hidden/
```

Just run tar on your drupal folder itself, it will take care of everything.

---

### Post by yc2 on 2010-12-11
Thanks,

_tar_ seems to be the simplest way to make complete copies of directories including all subdirectories, hidden files and whatever there is in them.

---

### Post by kanishkdudeja on 2010-12-11
please mark the thread as solved.

---

### Post by StephenDavison on 2010-12-11
You might also try the following from the parent directory of the one you want to backup:

cp -a source-dir /dest/

Much easier than tar'ing through a pipe.

---

### Post by TiBaal89 on 2010-12-11
Yea, if your purpose is backing up - also look into rsync.

---

### Post by yc2 on 2010-12-11
Thanks for replies.

My purpose is rather simply to be able to make a COMPLETE copy of a directory with a simple command.

cp -a src dest (or cp -ar src dest ?) would be perfect but I am not sure f.ex. hidden files will be copied? (maybe depends on system settings?)

I remember this "fancy" command from when I copied my home directory to a separate partition.
```
cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```
Maybe this is the most complete? (including files with "strange" characters)

But so far, I still think tarring the directory seems to be the simplest.

---

