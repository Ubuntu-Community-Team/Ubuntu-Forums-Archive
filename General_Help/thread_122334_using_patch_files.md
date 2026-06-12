---
title: "using patch files"
date: 2006-01-27
forum: General Help
---

### Post by z3r0-c0d3r on 2006-01-27
I downloaded the patch for GIMP 2.2.10 but I don't know how to open the file,

does anybody know how to open this file??

---

### Post by hw-tph on 2006-01-27
You apply the patch to the source code using the **patch** command. **cd** to where you keep the source and type **patch -p0 < /path/ to/patch**. You may have to use the -p1 option instead. Then build the source as usual (according to the instructions).


Håkan

---

