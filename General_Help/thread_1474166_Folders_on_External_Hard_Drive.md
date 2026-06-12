---
title: "Folders on External Hard Drive"
date: 2010-05-05
forum: General Help
---

### Post by arabicamadmen on 2010-05-05
Hi, I have an external hard drive on which many of the folders are showing up as plain text files. Has anyone else had this problem? Do you know how to fix it?

---

### Post by darolu on 2010-05-05
Open a terminal and type:
```
$ ls -l /media/<yourharddrive>
```
Maybe they're missing the right permissions/mode.

---

### Post by arabicamadmen on 2010-05-08
The hard drive is plugged in and showing up on the desktop in the GUI but it says it can't be accessed, no such file or directory.

---

