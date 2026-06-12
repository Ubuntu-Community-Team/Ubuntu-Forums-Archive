---
title: "problem installing gcc"
date: 2006-04-07
forum: General Help
---

### Post by gondilon on 2006-04-07
I downloaded the newest version of gcc and I successfully created a make file.  When I execute 'make install' it starts to install and then gives me the following error :\
WARNING: `makeinfo' is missing on your system.  You should only need it if
         you modified a `.texi' or `.texinfo' file, or any other file
         indirectly affecting the aspect of the manual.  The spurious
         call might also be the consequence of using a buggy `make' (AIX,
         DU, IRIX).  You might want to install the `Texinfo' package or
         the `GNU make' package.  Grab either from any GNU archive site.
make[2]: *** [fastjar.info] Error 1
make[2]: Leaving directory `/home/carl/gcc-4.1.0/host-i686-pc-linux-gnu/fastjar'make[1]: *** [install-fastjar] Error 2
make[1]: Leaving directory `/home/carl/gcc-4.1.0'
make: *** [install] Error 2
I installed GNU make and it did not help
this has been work around by using synaptic.

---

### Post by MartinG on 2006-04-07
If you run```
sudo apt-get install build-essential
```this will install not only gcc (which you now have) but various other essential (geddit :) ) packages you need, which should sort this out.

---

### Post by MartinG on 2006-04-07
Sorry!  Double post.

---

### Post by Aireana on 2006-09-10
hi, this is my first post here:) 

im having the same problem as gondilon... so can anyone tell me where should i run the code "sudo apt-get install build-essential"? i have tried running it in the gcc-build directory, but all i get is "sudo: apt-get: command not found"

if possible, could ye include a step-by-step guide? im quite new to linux.. thanks in advance:)

---

