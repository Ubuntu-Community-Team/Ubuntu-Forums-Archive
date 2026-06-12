---
title: "Disk recovery software to recover files from ext3fs partition?"
date: 2009-12-12
forum: General Help
---

### Post by kernelhaxor on 2009-12-12
One of my ext3fs partitions shows up as a blank partition.  There were a lot of files.  The last time I used it was a long time back and I might have accidentally deleted all the files. 

Is there some software through which I can partially/fully recover all the files from that partition?

---

### Post by jbrown96 on 2009-12-12
If the files were deleted, then no. ExtX partitions write over the inode entries when files are deleted. There is no way to recover them.

---

### Post by Mister.Vash on 2009-12-12
Check out Photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

and ext3grep
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

### Post by kernelhaxor on 2009-12-13
Thanks .. I'll try those two.

---

### Post by bumanie on 2009-12-13
There is the choice of photorec, scalpel, foremost and magicrescue - the first 3 read off the raw hard drive, and are filesystem independent - not sure about the fourth one, but it for deleted file recovery too.

---

