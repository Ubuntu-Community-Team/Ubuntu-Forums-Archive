---
title: "patching linux kernel source code"
date: 2011-11-11
forum: General Help
---

### Post by hotshot247 on 2011-11-11
hey all, i just downloaded the source code for the kernel 3.0.0 and i'm trying to patch it to upgrade it to version 3.0.8 but i get this:
>  can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/virtual/lguest/lguest.c b/Documentation/virtual/lguest/lguest.c
|index cd9d6af..aec80e5 100644
|--- a/Documentation/virtual/lguest/lguest.c
|+++ b/Documentation/virtual/lguest/lguest.c
--------------------------

also, just to let you know, the command i typed it was:
> patch -p0 < patch-3.0.8
any help would be appreciated, thanks! also, if you can find a good site on kernel patching and compiling that explains it really good, can you let me know? thanks!

---

