---
title: "wine directory tree"
date: 2010-10-09
forum: General Help
---

### Post by spin498 on 2010-10-09
I've got Photoshop Elements running under WINE. I downloaded an upgrade to Camera Raw. It requires copying the CameraRaw.8bi file into Element's plug in folder. Doing a file search doesn't turn up any directory tree for PSE and the folder I did find is 'empty'.
Where would such a directory tree reside on the harddrive and because it's actually MS is it invisible to Linux file searches?

---

### Post by roccivic on 2010-10-09
press ALT+F2 and type in
```
nautilus .wine
```
you should then see a folder containing an item called "drive_c". Have a look in there.

---

### Post by spin498 on 2010-10-09
Worked a charm, thanks.

---

