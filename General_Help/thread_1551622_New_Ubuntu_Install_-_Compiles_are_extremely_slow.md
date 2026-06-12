---
title: "New Ubuntu Install - Compiles are extremely slow"
date: 2010-08-12
forum: General Help
---

### Post by mkukli on 2010-08-12
At work, we use Ubuntu to compile large numbers of C, C++, Java, and AIDL files.

My system is a Core i7 Quad-Core with 8GiB of RAM. Prior to this install, it ran Ubuntu 9.10, 32-bit. A basic compile took roughly 45 minutes.

I just did a clean install with (x)Ubuntu 10.04 64-bit. After setting up the build environment to allow 32-bit libraries (mobile development), a compile took roughly an hour:15. Any idea what might be causing such a slowdown?

---

### Post by earthpigg on 2010-08-12
gcc's make only uses one core to compile unless you specify otherwise.

monitor htop while compiling to see if that's what your problem is, and look here:

[http://stackoverflow.com/questions/414714/compiling-with-g-using-multiple-cores](http://stackoverflow.com/questions/414714/compiling-with-g-using-multiple-cores)

---

### Post by mkukli on 2010-08-12
> **earthpigg said:**
> gcc's make only uses one core to compile unless you specify otherwise.

monitor htop while compiling to see if that's what your problem is, and look here:

[http://stackoverflow.com/questions/414714/compiling-with-g-using-multiple-cores](http://stackoverflow.com/questions/414714/compiling-with-g-using-multiple-cores)

This is a corporate build, and it defaults to -j8.

---

