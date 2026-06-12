---
title: "cannot compile anything with gcc"
date: 2011-09-30
forum: General Help
---

### Post by avenpace on 2011-09-30
I have simple hello world c as follow

> 
#include <stdio.h>

int main()
{
      printf( "Hello World!\n" );

        return 0;
}

and when I tried to compile it with gcc, it gave me error

> In file included from /usr/include/stdio.h:75,
                 from simple.c:1:
/usr/include/libio.h:53: fatal error: stdarg.h: No such file or directory

I ran "gcc -v" with result below 
> Using built-in specs.
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.4.4-14ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.4 --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5)

My guess that my gcc are somehow misconfigure because I had ext4 failure and made me lost some amount of file
I did tried compile with command "gcc --sysroot=/usr/ simple.c" but the error become
> simple.c:1: error: no include path in which to search for stdio.h
simple.c: In function ‘main’:
simple.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

Please let me know how to fix this because I can't barely compile anything

---

### Post by wannabegeek on 2011-09-30
Hi,
I'm not qualified to trouble shoot this, but just for fun, try g++  .

wbg

---

### Post by avenpace on 2011-09-30
> **wannabegeek said:**
> Hi,
I'm not qualified to trouble shoot this, but just for fun, try g++  .

wbg
g++ come with different error 
> g++: error trying to exec 'cc1plus': execvp: No such file or directory

---

### Post by pjd99 on 2011-10-03
Looks like a problem with paths or missing files. Install (purge and reinstall) build-essential and try again.

---

### Post by sum1nil on 2011-10-03
Check out [http://manpages.ubuntu.com/manpages/jaunty/man8/dpkg-reconfigure.8.html]("http://manpages.ubuntu.com/manpages/jaunty/man8/dpkg-reconfigure.8.html") 
gcc may not be configured correctly and I hope this helps.

---

### Post by gordintoronto on 2011-10-04
CD to where you have saved your C program before you run gcc.

---

