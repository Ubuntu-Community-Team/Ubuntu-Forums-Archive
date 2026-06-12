---
title: "I can't remove this folder. Please help."
date: 2010-01-07
forum: General Help
---

### Post by Khaous on 2010-01-07
I have is folder in my desktop dir and I can't get it to delete. Please help. It appears top be locked and not responding to commands to delete.

---

### Post by iponeverything on 2010-01-07
from the prompt:

gksu nautilus

---

### Post by maybeway36 on 2010-01-07
The output from
```
ls -l ~/Desktop
```
might also yield some clues. It'll tell you who owns it and whether it's read-only.

---

### Post by Khaous on 2010-01-07
ls -l ~/Desktop
output:
dr-xr-xr-x 3 robert robert 4096 2009-02-12 16:15 64BIT_x64

It is from a winxp 64bit install disk I ripped and burned and now I can't remove this folder.

---

### Post by daty on 2010-01-07
try chmod u+w ~/Desktop/64BIT_x64

After that, you have write permissions on the file, and thus should be able to delete it.

---

### Post by underquark on 2010-01-07
[Beaten to it by above post.  Open terminal and type man chmod for more info on this command].

---

### Post by Khaous on 2010-01-07
many thanks all.

---

