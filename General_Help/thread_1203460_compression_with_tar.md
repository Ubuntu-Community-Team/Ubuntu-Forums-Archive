---
title: "compression with tar"
date: 2009-07-03
forum: General Help
---

### Post by zackpete on 2009-07-03
Anyone know how to find out the size of a file after it is compressed with tar+bz2, without actually creating the file?

---

### Post by ajgreeny on 2009-07-03
I'm not sure you can, as it will depend on the degree of compression in the files already in the tar, eg jpg files will not compress as much as bmp, etc etc.

Unless, of course, anyone else knows differently.

---

### Post by spibou on 2009-07-03
> **zackpete said:**
> Anyone know how to find out the size of a file after it is compressed with tar+bz2, without actually creating the file?
I'm not sure what you mean by "a file" since people use tar for more than one files. Perhaps you're looking for ```
bzip2 -dc compressed-file | wc -c
```

---

