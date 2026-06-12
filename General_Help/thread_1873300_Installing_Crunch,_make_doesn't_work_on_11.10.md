---
title: "Installing Crunch, make doesn't work on 11.10"
date: 2011-11-01
forum: General Help
---

### Post by gandaran on 2011-11-01
```
mfp@PC:~/Downloads/crunch3.1$ make
Building binary...
/usr/bin/gcc -Wall -lm -pthread -std=c99 -m32 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 crunch.c -o crunch
crunch.c: In function ‘PrintPercentage’:
crunch.c:541:20: warning: variable ‘finall’ set but not used [-Wunused-but-set-variable]
crunch.c: In function ‘renamefile’:
crunch.c:567:12: warning: variable ‘pidret’ set but not used [-Wunused-but-set-variable]
crunch.c: In function ‘main’:
crunch.c:1310:8: warning: variable ‘loaded’ set but not used [-Wunused-but-set-variable]
crunch.c:1308:8: warning: variable ‘flag4’ set but not used [-Wunused-but-set-variable]
/tmp/ccMVsny1.o: In function `main':
crunch.c:(.text+0x6272): undefined reference to `pow'
crunch.c:(.text+0x6420): undefined reference to `pow'
crunch.c:(.text+0x686f): undefined reference to `pow'
crunch.c:(.text+0x6ac2): undefined reference to `pow'
collect2: ld returned 1 exit status
make: *** [crunch] Error 1
mfp@PC:~/Downloads/crunch3.1$ 
```
used to work fine on other ubuntu versions, whats wrong?

---

### Post by foodfight2 on 2011-11-05
I had the same problem. the math libraries (math.h) isn't linked.

just cd into the directory containing crunch.c and do this:

#   /usr/bin/gcc -Wall -lm -pthread -std=c99 -m32 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 crunch.c -o crunch -lm

to insert the man page, do

 #  install crunch.1 -m 644 -o root -g root /usr/share/man/man1/

---

