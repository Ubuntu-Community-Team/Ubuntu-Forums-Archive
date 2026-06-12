---
title: "kernel headers too old error in configure command"
date: 2010-02-11
forum: General Help
---

### Post by Primepixel on 2010-02-11
Hello all

I am building a toolchain and configure command I am using is
 
BUILD_CC=gcc CFLAGS="-O1" CC="$TARGET-gcc \
-mcpu=ep9312 -mfix-crunch-d1" \
AR=$TARGET-ar RANLIB=${TARGET}-ranlib \
../glibc-2.3.5/configure \
--host=$TARGET \
--build=i686-pc-linux-gnu \
--prefix=${PREFIX} \
--enable-add-ons=linuxthreads \
--disable-debug \
--disable-profile \
--without-tls \
--without-gd \
--without-cvs \
--with-headers=${PREFIX}/include \
--with-__thread \
--with-binutils=${PREFIX}/bin 
 
make -j4
make install
===============

During configure command I get following error message,

checking for memory.h... no
checking for strings.h... no
checking for inttypes.h... no
checking for stdint.h... no
checking for unistd.h... no
checking for long double... no
checking size of long double... 0
running configure fragment for sysdeps/pthread
running configure fragment for sysdeps/unix/sysv/linux
checking for egrep... (cached) grep -E
checking installed Linux kernel header files... TOO OLD!
configure: error: GNU libc requires kernel header files from
Linux 2.0.10 or later to be installed before configuring.
The kernel header files are found usually in /usr/include/asm and
/usr/include/linux; make sure these directories use files from
Linux 2.0.10 or later. This check uses <linux/version.h>, so
make sure that file was built correctly when installing the kernel header
files. To use kernel headers not from /usr/include/linux, use the
configure option --with-headers.

====================

I am running ubunto 9.1, gcc-4.1.3 and Linux 2.6.31-19 on x86.

I am using using linux kernel headers given to me which is newer than what the
error says. They are properly installed at $PREFIX/include/linux and ../linux/asm. So, I dont think configure command sees my dot h files.

====================
This is what I have tried.

In the configure command above, it uses header option pointing to
$PREFIX/include. But I see directories in include directory but no dot h files. So,
I add /linux to header option,

--with-headers=${PREFIX}/include/linux \

but does not work. I tried include/asm directory too but does not work. (The
path PREFIX is working)

=====================
I looked at include/linux/version.h file to see if I can set the date. The error
message says it checks date in version.h. There are two commented out linux
version statemensts. I uncommented one but does not work. I don't know date
statement command to put in there.

=====================
I deleted header command in configure command but still get same error. So, command does not even detect header option.
 
=====================
Regards

---

