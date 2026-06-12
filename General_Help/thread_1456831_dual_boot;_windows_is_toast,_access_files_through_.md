---
title: "dual boot; windows is toast, access files through Ubuntu"
date: 2010-04-17
forum: General Help
---

### Post by designingpatrick on 2010-04-17
Windows is having fun with its blue screens, Ubuntu is fine. I'd like to access files stored on the Windows partition- how can I do this?

---

### Post by darolu on 2010-04-17
Mount you Windows partition and browser your files. You should see your Windows partition listed under Places, clicking it should mount your partition.

If it doesn't work, open a terminal (Applications - Accessories - Terminal) and run:
```
$ sudo fdisk -l
```
Paste your results.

---

