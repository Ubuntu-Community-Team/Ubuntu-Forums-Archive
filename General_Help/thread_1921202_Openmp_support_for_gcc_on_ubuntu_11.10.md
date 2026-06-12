---
title: "Openmp support for gcc on ubuntu 11.10 ?"
date: 2012-02-06
forum: General Help
---

### Post by kamesh419 on 2012-02-06
Hi all, 

does any one know if the gcc version thats shipped with ubuntu 11.10 comes with openmp support? I am trying to compile a tool called monitor ([http://icl.cs.utk.edu/~mucci/monitor/](http://icl.cs.utk.edu/~mucci/monitor/)) and I get the following error (pastebin). 

[http://pastebin.com/NKw1uu5T](http://pastebin.com/NKw1uu5T)

gcc -v gives me the following.

> 
vadrao@MatriX:~/Tools/monitor$ gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6.1/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.1-9ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++,go --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 




Cheers,
Kam

---

