---
title: "Logging to ram disk"
date: 2009-10-29
forum: General Help
---

### Post by Xamiga on 2009-10-29
For testing I've installed 64bit 9.10 on a bootable USB drive.  To minimize disk writes I would like to direct all logging to a ram disk.  Step by step, how do I do this?

---

### Post by Lars Noodén on 2009-10-30
Look up tmpfs or ramfs.  
For a HowTo on that, see the tail end of this one for tmpfs:
[http://www.howtoforge.com/storing-files-directories-in-memory-with-tmpfs](http://www.howtoforge.com/storing-files-directories-in-memory-with-tmpfs)

When you can mount/unmount a tmpfs partition on a mount point.  Then you might risk mounting /var/log as a tmpfs partition.   Remember that /var/log/ must be populated with directories and files and that they must have the correct permissions...

For a brief comparison, see:
[http://www.thegeekstuff.com/2008/11/overview-of-ramfs-and-tmpfs-on-linux/](http://www.thegeekstuff.com/2008/11/overview-of-ramfs-and-tmpfs-on-linux/)

---

### Post by Xamiga on 2009-10-30
Thanks, playing with it now.

---

