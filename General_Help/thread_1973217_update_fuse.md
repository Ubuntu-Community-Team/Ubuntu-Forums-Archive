---
title: "update fuse"
date: 2012-05-04
forum: General Help
---

### Post by Xandaros on 2012-05-04
Hey there!
I'm currently trying to write a driver for a filesystem using fuse.
However, I noticed my FUSE is outdated and the API documentation is not valid for me.

Instead of trying to figure out what was different in my version, I thought about updating my fuse.

The only fuse-based filesystems I am knowingly using is SSHFS, but there might be some others I am not aware of.

Well, I could not find any info on how to update FUSE, so my question is: How to?
I really hope you can help me sort this out, using a file system with a hex editor is no fun, even if the files are small...

---

### Post by Cheesemill on 2012-05-04
As far as I can tell from the documentation the fuse API hasn't been updated since fuse version 2.6.
I'm running 12.04 which comes with fuse version 2.8.6, what version are you running?

---

### Post by Habitual on 2012-05-04
fuse-2.8.4.tar.gz here running over s3fs

[https://downloads.sourceforge.net/project/fuse/fuse-2.X/2.8.4/fuse-2.8.4.tar.gz?r=&ts=1299709935&use_mirror=cdnetworks-us-1](https://downloads.sourceforge.net/project/fuse/fuse-2.X/2.8.4/fuse-2.8.4.tar.gz?r=&ts=1299709935&use_mirror=cdnetworks-us-1)

But I don't run Ubuntu either.

YMMV

---

### Post by Xandaros on 2012-05-05
It seems the fuse library uses the old API by default.
defining "FUSE_USE_VERSION" to 26 prior to including the library seems to have fixed the problem.

(I only noticed when I saw I have a fairly new version of fuse)

Sorry for the trouble

---

