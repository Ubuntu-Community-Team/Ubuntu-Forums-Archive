---
title: "mount --bind multiple folders into one?"
date: 2009-12-17
forum: General Help
---

### Post by yavoh on 2009-12-17
I have the same problem as the person in [this old thread]("http://ubuntuforums.org/showthread.php?t=702989"): I'd like to use ```
mount --bind
``` to bind several folders into one, kind of like the Win7 "libraries" feature.  For example, I'd like to include /media/drive2/folder1/ and /media/drive2/folder2 into ~/Desktop/bothfolders/.

The link provided in that thread, however, doesn't work.  There is no Google cache or Archive.org mirror of it.  Is there a way to achieve this in Karmic?

---

### Post by bodhi.zazen on 2009-12-17
No, mount --bind will not work that way.

You can copy the contents from one location to the second , but not combine them in the way you wish.

---

### Post by falconindy on 2009-12-17
The Win7 libraries feature is more easily simulated by creating a single directory with symlinks to other directories. There is no 'combining' of directories.

---

### Post by yavoh on 2009-12-17
I guess symlinks will work.  Thanks!

---

### Post by hazelnut on 2009-12-26
What you are looking for is Unionfs.

In karmic:

sudo apt-get install unionfs-fuse

To mount multiple folders into one use:

unionfs-fuse /path/to/folder1[=RO/RW][:/path/to/folder1[=RO/RW]...] /path/to/union/of/multiple/folders

or in fstab (here's mine):

unionfs-fuse#/drive/media/Movies=RW:/drive/workdrive/media/Movies=RW:/drive/media2/Movies=RW:/drive/xt/movies=RW /av/movies fuse cow,allow_other,uid=1000,gid=1000 0 0

All movies from multiple folders are now available in /av/movies. It's working pretty good for me.

---

### Post by falconindy on 2009-12-26
UnionFS is old and deprecated. If you want to go this route, use aufs2.

---

### Post by hazelnut on 2009-12-31
Who says Unionfs is deprecated?  Ubuntu only just now pulled it into the repositories.  Aufs2 is not in the repositories, hence a little more painful to install. 

Anyway, I abandoned unionfs in favor of mhddfs (also in repositories) mainly because it seems a little better at distributing the drive space.

---

