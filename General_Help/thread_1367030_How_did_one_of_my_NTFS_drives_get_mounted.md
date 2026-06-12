---
title: "How did one of my NTFS drives get mounted"
date: 2009-12-29
forum: General Help
---

### Post by vayu on 2009-12-29
In Dolphin one but not both of my NTFS drives shows up on the left pane.  It has a directory in /media.   There is no mention of it in /etc/fstab.  How come it's there and has a name, but the other one is not?

---

### Post by spigy11 on 2009-12-29
Hi

/etc/fstab contains static mounts, for example your HDD partition tables

If have you have hot-pluggable devices use command mount, to see all mounted devices, f.e. DVDs.

And the answer propably you have the package ntfs-config installed

[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

Hope that helps

Martin

---

