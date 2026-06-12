---
title: "Compile/make errors ... missing zlib.h and rand.h"
date: 2006-05-17
forum: General Help
---

### Post by Joshatdot on 2006-05-17
I am trying to compile sleuthkit-2.04 and I can't get to **make**.  At first I was getting errors of missing **stdio.h** and other header files, but I fixed that with **aptitude install build-essential**.

But now I am missing zlib.h and rand.h :

```
poweruser@f205-19:~/Desktop/sleuthkit-2.04$ sudo make
Password:
cd src/auxtools; make "CC=gcc" MAKELEVEL=
gcc -DLINUX2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DVER=\"2.04\" -O -Wall -g   -c -o mymalloc.o mymalloc.c
gcc -DLINUX2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DVER=\"2.04\" -O -Wall -g   -c -o strerror.o strerror.c
gcc -DLINUX2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DVER=\"2.04\" -O -Wall -g   -c -o split_at.o split_at.c
gcc -DLINUX2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DVER=\"2.04\" -O -Wall -g   -c -o tsk_endian.o tsk_endian.c
gcc -DLINUX2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DVER=\"2.04\" -O -Wall -g   -c -o unicode.o unicode.c
gcc -DLINUX2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DVER=\"2.04\" -O -Wall -g   -c -o data_buf.o data_buf.c
gcc -DLINUX2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DVER=\"2.04\" -O -Wall -g   -c -o tsk_version.o tsk_version.c
gcc -DLINUX2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DVER=\"2.04\" -O -Wall -g   -c -o tsk_error.o tsk_error.c
gcc -DLINUX2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DVER=\"2.04\" -O -Wall -g   -c -o tsk_parse.o tsk_parse.c
ar rv ../../lib/libauxtools.a mymalloc.o strerror.o split_at.o tsk_endian.o unicode.o data_buf.o tsk_version.o tsk_error.o tsk_parse.o
ar: creating ../../lib/libauxtools.a
a - mymalloc.o
a - strerror.o
a - split_at.o
a - tsk_endian.o
a - unicode.o
a - data_buf.o
a - tsk_version.o
a - tsk_error.o
a - tsk_parse.o
ranlib ../../lib/libauxtools.a
cd src/afflib/lib; make "CC=gcc" MAKELEVEL=
g++ -c -g -Wall -I/usr/local/ssl/include -I/usr/sfw/include -I. -Ilib   -o aff_db.o aff_db.cpp
In file included from aff_db.cpp:8:
afflib_i.h:53:18: error: zlib.h: No such file or directory
afflib_i.h:60:26: error: openssl/rand.h: No such file or directory
make: *** [aff_db.o] Error 1
make: *** [no-perl] Error 2
poweruser@f205-19:~/Desktop/sleuthkit-2.04$
```

---

### Post by tonyr on 2006-05-17
In case you didn't see my response in the other thread,
zlib.h is in package **zlibg1-dev**;
openssl/rand.h is in package **libssl-dev**.

It looks like you need to
```

sudo apt-get install zlib1g-dev libssl-dev

```

---

### Post by Joshatdot on 2006-05-17
Thanks tonyr...I wasnt sure what board to post my issue on.

Looks like that did something correct, I'll [sudo make clean[/b] and try again.

WOOT!! Its compiling 100x thanks tonyr

---

### Post by Joshatdot on 2006-05-24
is **aptitude** and **apt-get** the same thing? they sure seem the same.

---

### Post by tonyr on 2006-05-24
Well, yes and no.  **aptitude** is a front-end for **apt** with a lot of
nice bells and whistles and organizing features.  It arranges to do a lot of
things for you that would otherwise require a lot of steps and complex command
line options to accomplish.  **apt** is implemented as a collection of programs,
for package management, of which **apt-get** is one.

---

