---
title: "Two HDD one computer, XP drive dont see Ubuntu drive files"
date: 2009-10-06
forum: General Help
---

### Post by Elecmn on 2009-10-06
I have two HDD's on one Compaq PRESARIO machine. One HDD has Ubuntu OS and the other, XP. I normally boot to Ubuntu and I can then mount the PRESARIO disk (with XP) and use/copy/edit those files. But when running the XP OS, I dont see the Ubuntu drive files. How do I change this? Is there something I need to do to the Ubuntu OS to make its files visible while running XP? Any help? :confused:

---

### Post by peculiar penguin on 2009-10-06
You'd need to install an ext3 file system driver in Windows... IIRC the Wikipedia article for ext3 links to some examples.

---

### Post by sedawk on 2009-10-06
Ubuntu can read FAT file systems and NTFS file systems, but
M$ doesn't deliver any drivers to read the file systems
of Ubuntu (ext2/ext3).

You need an additional driver like the free one you can find here:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

(There was an issue in the past because Ubuntu used
 a bigger value for a file system parameter that the
 driver couldn't handle. I haven't checked if this
 is still true. Give it a try ...).

---

### Post by Elecmn on 2009-10-07
Thanks to Pecular Penquin and Sedawk for their help. adding the driver worked. now I can backup my drives by sending them to the other disks.

---

