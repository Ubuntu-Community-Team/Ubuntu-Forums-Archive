---
title: "kdesvn in kubuntu 5.10?"
date: 2006-03-05
forum: General Help
---

### Post by tomane on 2006-03-05
Hello.

Is it possible to install kdesvn in kubuntu 5.10?
I could only find rpms on the project site and the only debs I heard of were in the dapper repository.
The debs in the dapper repos need some packages with version numbers higher than I have installed. (synaptic tells me that I'm up to date)
I tried fetching the source from the project page, but the configure script fails.
I'm not sure if the compilation from source issue belongs here, so I'm not posting any details, but if you want it I can give them, just ask.

I tried rapidsvn and esvn, but kdesvn seems friendlier and is more kde-ish than the others.

Any help would be much apreciated.
Thanks.

---

### Post by ltmon on 2006-03-05
There are no prebuild packages for Breezy that I am aware of.

What configure errors do you get?  It is probably just a missing package, which will be fairly easy to install.

L.

---

### Post by tomane on 2006-03-05
Here is the part of config.log that I think is relevant.

```
configure:2274: checking for gcc
configure:2290: found /usr/bin/gcc
configure:2300: result: gcc
configure:2544: checking for C compiler version
configure:2547: gcc --version </dev/null >&5
gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2550: $? = 0
configure:2552: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with
-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=
mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/j
re --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
configure:2555: $? = 0
configure:2557: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2560: $? = 1
configure:2583: checking for C compiler default output file name
configure:2586: gcc     conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2589: $? = 1
configure: failed program was:
| /* confdefs.h.  */
|
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "kdesvn"
| #define VERSION "0.7.4"
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }

``` 
gcc is pointing to gcc-4.0.
I tried installing gcc-3.4 and make gcc point to it. Same result here, too.

Regards.

---

### Post by ltmon on 2006-03-05
Hmmm.... that is nasty.

Did you "apt get install build-essential" or just GCC?

It could be that you are missing some libc6-dev stuff. (Guessing btw).

Maybe try "apt-get install libc6-dev".

L.

---

### Post by GeneralZod on 2006-03-06
I have a checkinstall-created .deb of kdesvn 0.7.3 that I can post, although such debs do not contain any proper meta-data such as dependencies etc so aren't as good as "proper" debs.

---

### Post by tomane on 2006-03-06
[quote=ltmon]
Did you "apt get install build-essential" or just GCC?
Maybe try "apt-get install libc6-dev".
L.[/quote] THat's right, I only had installed gcc.
When I get home later I'll follow your tip. Thanks!

Zod, I'll try to install it from source, for now, but if It still fails, then I could use that package ;)

Regards.

---

