---
title: ".bin files"
date: 2005-02-12
forum: General Help
---

### Post by lao_V on 2005-02-12
Hi All,
  
  Does anyone know how to install a software using *.bin files or even is it possible?

---

### Post by GilGalad on 2005-02-12
There are packages which end in .bin and are shell scripts (e.g. the Sun Java packages). They are installed by issuing the command "sh <package>.bin". Type "head <package>.bin" and see if it contains a line similar to "#!/bin/sh".

Another issue is if you are talking about a binary disk image. Ask if this is the case.

---

### Post by cblack on 2005-02-12
Alternatively you can make the *.bin file executeable by running:

```
chmod +x <binfile>
``` 

and then doing:

```
./binfile
```

---

### Post by lao_V on 2005-02-14
Thanks guys, in this case the bin file I had was a program, so making it executible and doing "./" helped me install the program.

---

