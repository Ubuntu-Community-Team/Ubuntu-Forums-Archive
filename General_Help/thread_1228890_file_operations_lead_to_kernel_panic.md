---
title: "file operations lead to kernel panic"
date: 2009-08-01
forum: General Help
---

### Post by lazka on 2009-08-01
hard disk: 2 partitions, both ext3.

the first works flawlessly

the second one can be mounted, browsed with nautilus (as long as there is no thumbnail generation involved)

If I try to open a file or copy one: kernel crash (and the drive makes a parking noise)
If I try to fsck the partition: crash.
If I start from a CD, fsck: crash.
Old kernel (2.6.24): same as above: crash.

I've ran out of ideas... First I thought the drive is going to die, but the first partition is working and SMART says everything is okey.

any ideas? :(

---

### Post by lazka on 2009-08-01
mounting it in windows fixed it :)

now that's something new.. fixing linux with windows.

---

