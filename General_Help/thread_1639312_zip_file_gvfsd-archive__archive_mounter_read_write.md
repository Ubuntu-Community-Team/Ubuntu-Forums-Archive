---
title: "zip file gvfsd-archive / archive mounter read write mode"
date: 2010-12-06
forum: General Help
---

### Post by yusuf81 on 2010-12-06
Hello Guys,
I'd like to ask about archive mounter feature, can I mount zip file with read write mode?
can gvfsd-archive do that?, or I must use fuse-zip to mount it?
If I must use fuse-zip, how I wrap it so I can use it via nautilus or via gvfs-fuse-daemon
Thank's

---

### Post by yusuf81 on 2010-12-08
BUMP
:popcorn:

---

### Post by kpoole on 2011-01-03
This was a question I was going to ask.  Mounting a .zip as if it were a drive is a great idea but being able to add files to the .zip in a drag-n-drop manner would complete this feature.

It's the sort of thing I've been waiting for from back in my old Atari ST days.

---

### Post by yusuf81 on 2011-02-10
let's bumping again
BUMP!
:popcorn:

---

### Post by Coder543 on 2011-06-26
its quite simple, and is helpful

```
fuse-zip -o rw /home/user/stuff.zip /home/user/Desktop/stuff
```

---

