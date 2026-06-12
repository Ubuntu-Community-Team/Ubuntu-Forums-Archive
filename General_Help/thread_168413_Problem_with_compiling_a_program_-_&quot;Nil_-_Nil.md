---
title: "Problem with compiling a program - &quot;Nil - Nil isn't Liero&quot;"
date: 2006-04-30
forum: General Help
---

### Post by Dr_Deadmeat on 2006-04-30
I have tried to compile this program from source cause I don't want to use libSDL 1.0 when I can use libSDL 1.2. When I compile it everything works fine until I tries to run the make file. I just get this error:

```

andreas@andreas:~/nil/nil$ make

make  all-recursive
make[1]: Entering directory `/home/andreas/nil/nil'
Making all in nil
make[2]: Entering directory `/home/andreas/nil/nil/nil'
Making all in docs
make[3]: Entering directory `/home/andreas/nil/nil/nil/docs'
Making all in en
make[4]: Entering directory `/home/andreas/nil/nil/nil/docs/en'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/andreas/nil/nil/nil/docs/en'
make[4]: Entering directory `/home/andreas/nil/nil/nil/docs'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/andreas/nil/nil/nil/docs'
make[3]: Leaving directory `/home/andreas/nil/nil/nil/docs'
make[3]: Entering directory `/home/andreas/nil/nil/nil'
source='raw_surface.cpp' object='raw_surface.o' libtool=no \
depfile='.deps/raw_surface.Po' tmpdepfile='.deps/raw_surface.TPo' \
depmode=gcc3 /bin/sh ../depcomp \
g++ -DHAVE_CONFIG_H -I. -I. -I..   -I/usr/include/SDL -D_REENTRANT  -g -O2 -c -o raw_surface.o `test -f 'raw_surface.cpp' || echo './'`raw_surface.cpp
raw_surface.cpp: In function &#8216;void draw_stretch(const Raw_surface*, Mutable_raw_surface*, int, int, int, int, int, int, int, const BlendFunc&)&#8217;:
raw_surface.cpp:379: error: &#8216;const class Raw_surface&#8217; has no member named &#8216;_get_xsize&#8217;
raw_surface.cpp:382: error: &#8216;xsize&#8217; was not declared in this scope
make[3]: *** [raw_surface.o] Error 1
make[3]: Leaving directory `/home/andreas/nil/nil/nil'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/andreas/nil/nil/nil'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/andreas/nil/nil'
make: *** [all] Error 2

andreas@andreas:~/nil/nil$

```

Does anyone know what to do?

BTW: I use Ubuntu 5.10 on a 386 cpu

EDIT: Fixed the code tag

---

### Post by Kevinator on 2006-04-30
There are any number of possible causes for a build failure, but since you are trying to build something that is not part of Ubuntu you are unlikely to find good help here. The forums for the software you are trying to build would probably be a better place to ask.

---

### Post by Dr_Deadmeat on 2006-05-02
*bump*

I will only bump this once, but it looks like the project is shut down or something because it haven't been any news from that site in about 1 year. Just wondered if any have a clue about what to do or a package I could use. That would be appreciated =)

---

