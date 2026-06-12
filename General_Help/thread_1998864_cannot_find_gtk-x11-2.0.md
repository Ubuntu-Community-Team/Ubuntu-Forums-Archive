---
title: "cannot find gtk-x11-2.0"
date: 2012-06-07
forum: General Help
---

### Post by rubxcubedude on 2012-06-07
I'm an running a Ubuntu 10.04 Vm on Oracles VirtualBox. I was able to download and set up my environment to run and compile a simple gtk example
```
gcc `pkg-config --cflags --libs gtk+-2.0` hello.c -o hello 
```This compiles successfully and runs. I then switch to using scratchbox's provided arm-linux-gcc under the arm-gcc-3.3.4-glibc-2.3.2 compiler and I get the error:

```
/scratchbox/compilers/arm-gcc-3.3.4-glibc-2.3.2/lib/gcc-lib/arm-linux/3.3.4/../../../../arm-linux/bin/ld: cannot find -lgtk-x11-2.0
collect2: ld returned 1 exit status

```since the normal gcc is working I suspect i need to add an additional link but performing a find on the file i don't find it on my system to link to which now has me confused as to why gcc is working correctly. Any one experience something like this and have an idea as to what i can do?

---

### Post by dino99 on 2012-06-07
[https://www.google.fr/search?hl=fr&output=search&sclient=psy-ab&q=%22gtk-x11-2.0%22&btnK=](https://www.google.fr/search?hl=fr&output=search&sclient=psy-ab&q=%22gtk-x11-2.0%22&btnK=)

---

### Post by rubxcubedude on 2012-06-07
I've already googled it and not found anything that helps me

---

