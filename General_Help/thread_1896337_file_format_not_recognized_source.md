---
title: "file format not recognized source"
date: 2011-12-16
forum: General Help
---

### Post by stephanieg on 2011-12-16
Hi,

I've been trying to install a program using the command line (it's the only way this program allows) but encounter problems when I try to compile it. At the end of it all I get an error message*. (*See the quote)

```
oot@stephanie-Ubuntu:/gamit_globk# gfortran -v install_software
Driving: gfortran -v install_software -l gfortran -l m -shared-libgcc
Using built-in specs.
COLLECT_GCC=gfortran
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6.1/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.1-9ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++,go --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
Reading specs from /usr/lib/gcc/i686-linux-gnu/4.6.1/libgfortran.spec
rename spec lib to liborig
COLLECT_GCC_OPTIONS='-v' '-shared-libgcc' '-mtune=generic' '-march=i686'
COMPILER_PATH=/usr/lib/gcc/i686-linux-gnu/4.6.1/:/usr/lib/gcc/i686-linux-gnu/4.6.1/:/usr/lib/gcc/i686-linux-gnu/:/usr/lib/gcc/i686-linux-gnu/4.6.1/:/usr/lib/gcc/i686-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/i686-linux-gnu/4.6.1/:/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/:/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../../lib/:/lib/i386-linux-gnu/:/lib/../lib/:/usr/lib/i386-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-v' '-shared-libgcc' '-mtune=generic' '-march=i686'
 /usr/lib/gcc/i686-linux-gnu/4.6.1/collect2 --build-id --no-add-needed --as-needed --eh-frame-hdr -m elf_i386 --hash-style=gnu -dynamic-linker /lib/ld-linux.so.2 -z relro /usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crt1.o /usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crti.o /usr/lib/gcc/i686-linux-gnu/4.6.1/crtbegin.o -L/usr/lib/gcc/i686-linux-gnu/4.6.1 -L/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu -L/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../../lib -L/lib/i386-linux-gnu -L/lib/../lib -L/usr/lib/i386-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/i686-linux-gnu/4.6.1/../../.. install_software -lgfortran -lm -lgcc_s -lgcc -lquadmath -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc /usr/lib/gcc/i686-linux-gnu/4.6.1/crtend.o /usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crtn.o
install_software: file not recognized: File format not recognized
collect2: ld returned 1 exit status

```Help please! :(

Thanks

---

