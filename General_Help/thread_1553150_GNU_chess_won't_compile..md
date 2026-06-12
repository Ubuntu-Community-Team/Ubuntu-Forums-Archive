---
title: "GNU chess won't compile."
date: 2010-08-14
forum: General Help
---

### Post by takisan on 2010-08-14
OK, um, I'm trying to compile GNU chess from the website, and I get this for the output:
```
$ make
Making all in src
make[1]: Entering directory `/home/jonah/Desktop/gnuchess-5.07/src'
make  all-am
make[2]: Entering directory `/home/jonah/Desktop/gnuchess-5.07/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -MT atak.o -MD -MP -MF ".deps/atak.Tpo" \
          -c -o atak.o `test -f 'atak.c' || echo './'`atak.c; \
        then mv -f ".deps/atak.Tpo" ".deps/atak.Po"; \
        else rm -f ".deps/atak.Tpo"; exit 1; \
        fi
In file included from atak.c:29:
common.h:748: error: ‘getline’ redeclared as different kind of symbol
/usr/include/stdio.h:651: note: previous declaration of ‘getline’ was here
make[2]: *** [atak.o] Error 1
make[2]: Leaving directory `/home/jonah/Desktop/gnuchess-5.07/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jonah/Desktop/gnuchess-5.07/src'
make: *** [all-recursive] Error 1
$     
```
I have run ./configure, but I have no idea what's wrong (Compiling my own software is way out of my league unless it's a simple C++ file.)
[./configure output]("http://dl.dropbox.com/u/7267364/chess.configure.txt")
Thanks in advance;

---

### Post by takisan on 2010-08-14
Never mind, but I'd still like some help compiling it for a Mac.

---

### Post by Bachstelze on 2010-08-14
GNU chess is very old code (more than 7 years old), it most likely requires some adjustments to make it suitable for modern systems.

*EDIT:* You can use the Debian patches: [http://archive.ubuntu.com/ubuntu/pool/universe/g/gnuchess/gnuchess_5.07-7.diff.gz](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnuchess/gnuchess_5.07-7.diff.gz) Compiles fine on OS X here.

---

