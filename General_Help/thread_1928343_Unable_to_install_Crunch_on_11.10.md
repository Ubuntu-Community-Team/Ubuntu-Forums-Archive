---
title: "Unable to install Crunch on 11.10"
date: 2012-02-19
forum: General Help
---

### Post by zkzeroxvirus on 2012-02-19
Hello I'm fairly new to linux. I was trying to make a numeric words list dictionary with crunch, but i've been unable to install it.```
sirin@ubuntu:~$ cd crunch3.2
sirin@ubuntu:~/crunch3.2$ make
Building binary...
/usr/bin/gcc -Wall -lm -pthread -std=c99  crunch.c -o crunch
crunch.c: In function ‘PrintPercentage’:
crunch.c:1006:20: warning: variable ‘finall’ set but not used [-Wunused-but-set-variable]
crunch.c: In function ‘renamefile’:
crunch.c:1032:12: warning: variable ‘pidret’ set but not used [-Wunused-but-set-variable]
crunch.c: In function ‘main’:
crunch.c:1805:8: warning: variable ‘loaded’ set but not used [-Wunused-but-set-variable]
/tmp/ccqWIgti.o: In function `count_strings':
crunch.c:(.text+0x1c1e): undefined reference to `pow'
crunch.c:(.text+0x1dd5): undefined reference to `pow'
crunch.c:(.text+0x1fd1): undefined reference to `pow'
collect2: ld returned 1 exit status
make: *** [crunch] Error 1
sirin@ubuntu:~/crunch3.2$ 

```


I tried searching around the forum and the googles and found this.

> **foodfight2 said:**
> I had the same problem. the math libraries (math.h) isn't linked.

just cd into the directory containing crunch.c and do this:

#   /usr/bin/gcc -Wall -lm -pthread -std=c99 -m32 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 crunch.c -o crunch -lm

to insert the man page, do

 #  install crunch.1 -m 644 -o root -g root /usr/share/man/man1/
 It didnt work. Heres what happenes when i use the first command
```
sirin@ubuntu:~/crunch3.2$ /usr/bin/gcc -Wall -lm -pthread -std=c99 -m32 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 crunch.c -o crunch -lm
In file included from /usr/include/assert.h:37:0,
                 from crunch.c:225:
/usr/include/features.h:323:26: fatal error: bits/predefs.h: No such file or directory
compilation terminated.
sirin@ubuntu:~/crunch3.2$ 

```
The second command seems to do something although im not quite sure.

---

### Post by beepus on 2012-03-28
Hi, if you ar an a ADM64 platform change -m32 to -m64
```

/usr/bin/gcc -Wall -lm -pthread -std=c99 -m64 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 crunch.c -o crunch -lm

```

::beep

---

### Post by cabal1209 on 2012-05-19
Thank you for the info Beepus did the work

---

