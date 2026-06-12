---
title: "access ext4 with extents file systems and wubi disks from windows."
date: 2010-04-04
forum: General Help
---

### Post by mregmi on 2010-04-04
Hi all,
  we are pleased to announce a new version of our ext2read project
which we created 6 years ago.
we were motivated to redsign and rework the project after i installed
the new ubuntu karmic. By default it used Ext4
file system with Extent feature enabled. we could not find any tools
to read ext4 filesystems from windows . So we went

ahead and wrote this program.

FEATURES:
Simple UI designed using QT4.
View/Read Ext2/3/4 partitions.
Recursively Copy the entire folder or even /
Support for external USB disks.
Support for disk and filesystem  images. For eg. Wubi users can just
open their root.disk file through this program.
LRU based Block cache for faster access.


If you find any bugs, have any questions or comments. Please let us know.

The executables and sources can be downloaded from [http://ext2read.sf.net](http://ext2read.sf.net)

If any of you are interested in joing this project, you can join the
mailing list and discuss. Join from here
[https://lists.sourceforge.net/lists/listinfo/ext2read-devel](https://lists.sourceforge.net/lists/listinfo/ext2read-devel)

Enjoy reading your files.

NOTE: This program must be run as Administrator. right click the file
and select run as Administrator.
     This is not a transparent file system driver jusr a user space tool.

---

