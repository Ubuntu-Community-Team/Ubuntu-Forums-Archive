---
title: "Installation issues, SDL_image_h"
date: 2011-01-05
forum: General Help
---

### Post by Giraffemonster on 2011-01-05
Hello, as the title states, I can't successfully install freedroidRPG. I've followed the instructions, and I have all the prerequisites, but it still won't work. This is version 0.14.1 also. Ubuntu's package repository doesn't have it.

The instructions were to download it, untar it, configure it, then make it. I downloaded it, then decompressed the package using the terminal, and ran the configure script. Then whenever I run "make", I get an error. This is what I get whenever I enter make.

make  all-recursive
make[1]: Entering directory `/home/owner/Downloads/freedroidrpg-0.14.1'
Making all in src
make[2]: Entering directory `/home/owner/Downloads/freedroidrpg-0.14.1/src'
gcc -DHAVE_CONFIG_H -I. -I..     -g -O2  -Wall  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT menu.o -MD -MP -MF .deps/menu.Tpo -c -o menu.o menu.c
In file included from menu.c:33:
system.h:113: fatal error: SDL_image.h: No such file or directory
compilation terminated.
make[2]: *** [menu.o] Error 1
make[2]: Leaving directory `/home/owner/Downloads/freedroidrpg-0.14.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/owner/Downloads/freedroidrpg-0.14.1'
make: *** [all] Error 2

I do have SDL_image.h though. I did some google searches too, just to make sure that I have the mentioned file. I ran "apt-file search SDL_image.h". I got this:

libsdl-image1.2-dev: /usr/include/SDL/SDL_image.h

What exactly should I do? The INSTALL and README documents don't address this, neither does the homepage.

EDIT: I got it solved. I just had to install libsdl_mixer and libsdl_image manually, instead of using the Ubuntu repositories via terminal.

---

