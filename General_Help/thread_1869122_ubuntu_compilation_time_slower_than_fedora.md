---
title: "ubuntu compilation time slower than fedora"
date: 2011-10-25
forum: General Help
---

### Post by alpinito1 on 2011-10-25
Hello everyone,

I have a question about the compilation time using gcc.

I use ubuntu 11.04 64bits and gcc 4.5.2 (the detail of the ubuntu installation and the gcc version is in the botom  of this thread).

I have the c++ sources of a library I work on and it seams to compile slower in my ubuntu machine than in my collegue's one. He uses Fedora 15 and the same version of the gcc. 

The hardware in both machine is quite the same. However, the difference in the compilation time is like 3 times faster using Fedora,

Is this normal?? if so, is it possible to speed up the compilations on my computer?

Thank you in advance,

  Daniel


Details about ubuntu and gcc:

uname -a
Linux pc-pino-linux 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

and gcc:

gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=x86_64-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/x86_64-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/x86_64-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4)

---

