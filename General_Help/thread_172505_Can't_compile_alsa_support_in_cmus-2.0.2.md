---
title: "Can't compile alsa support in cmus-2.0.2"
date: 2006-05-08
forum: General Help
---

### Post by TLE on 2006-05-08
Hi everybody
I use this program cmus, which is a console based music player. It is not in the repositories so I have to compile it form source. After some trial and error I managed to install tha packages needed to get most of it working, but I simply can not figure out how to get alsa to work. This is the output of the ./configure
```
checking for program gcc... /usr/bin/gcc
checking for CC flag -std=gnu99 -pipe -Wall -Wshadow -Wcast-align -Wpointer-arith -Wwrite-strings -Wundef -Wmissing-prototypes -Wredundant-decls... yes
checking for CC flag -Wdeclaration-after-statement... yes
checking for CC flag -Wold-style-definition... yes
checking for CC flag -Wno-pointer-sign... yes
checking if CC can generate dependency information... yes
checking byte order... little-endian
checking dynamic linking loader... -ldl -Wl,--export-dynamic
checking POSIX Threads (-lpthread)... yes
checking ncurses (-lncursesw)... yes
checking iconv (-liconv)... no
assuming libc contains iconv
checking FLAC (-lFLAC -lm)... no
checking for program pkg-config... /usr/bin/pkg-config
checking mad (pkg-config)... yes
checking CFLAGS for mad...
checking LIBS for mad... -lmad -lm
checking libmodplug (pkg-config)... yes
checking CFLAGS for modplug... -I/usr/include/libmodplug
checking LIBS for modplug... -lmodplug -lstdc++ -lm
checking MPC (-lmpcdec)... no
checking vorbisfile (pkg-config)... no
checking vorbis (-lvorbisfile -lvorbis -lm -logg)... no
checking alsa (pkg-config)... no
*** Package alsa was not found in the pkg-config search path.
*** Perhaps you should add the directory containing `alsa.pc'
*** to the PKG_CONFIG_PATH environment variable
*** No package 'alsa' found
checking ao (pkg-config)... no
checking ao (-lao)... no
checking arts (artsc-config)... no
checking for header <sys/soundcard.h>... yes
checking for header <sys/audioio.h>... no

Configuration:
flac:                n
mad:                 y
modplug:             y
mpc:                 n
vorbis:              n
wav:                 y
alsa:                n
ao:                  n
arts:                n
oss:                 y
sun:                 n
tremor:              n
wide char support:   y

Compiler Settings:
CC:                  gcc
LD:                  gcc
CFLAGS:              -O2 -std=gnu99 -pipe -Wall -Wshadow -Wcast-align -Wpointer-arith -Wwrite-strings -Wundef -Wmissing-prototypes -Wredundant-decls -Wdeclaration-after-statement -Wold-style-definition -Wno-pointer-sign -MMD -MP -MF .dep-$@
LDFLAGS:
SOFLAGS:             -fPIC

Installation Directories:
bindir:              /usr/local/bin
datadir:             /usr/local/share
libdir:              /usr/local/lib
mandir:              /usr/local/share/man

Installation:
make                 build cmus
make install         install cmus
make install-html    install html docs (same content in the man pages)

```
As you can see it wants a alsa.pc file, but I don't have that on my system. There is an alsa.c file in the package, perhaps it is supposed to be compiled n some way?
I hope somebody with more "compile from source" experience can help.
Thanks in advance Regards TLE

---

### Post by TLE on 2006-05-08
Ahhh sorry for bothering you guys. I've just solved it myself. The README says that I need development files for some of it, so searching in synaptic for "alsa dev" gave, among others, this hit libasound2.dev with the description "ALSA library development files", doh. So once again, my apoligies.

---

### Post by TLE on 2006-05-08
Ok so this is starting to look like I'm just trying to get my bean count up *G*
But I still need help, now I'm ready to install version 2.0.2 with alsa, but I would like first to remove the old version 2.0.0 without alsa. Unfortunately I only learned about the checkinstall command today so the old version is installed in the "make install" manner. So how do I uninstall it. If I do "locate cmus" I get this which is og interest:
```
/usr/local/bin/cmus
/usr/local/bin/cmus-remote
/usr/local/lib/cmus
/usr/local/lib/cmus/ip
/usr/local/lib/cmus/ip/modplug.so
/usr/local/lib/cmus/ip/mad.so
/usr/local/lib/cmus/ip/wav.so
/usr/local/lib/cmus/op
/usr/local/lib/cmus/op/oss.so
/usr/local/share/doc/cmus
/usr/local/share/doc/cmus/examples
/usr/local/share/doc/cmus/examples/cmus-status-display
/usr/local/share/man/man1/cmus-remote.1
/usr/local/share/man/man1/cmus.1
/usr/local/share/cmus
/usr/local/share/cmus/rc
/usr/local/share/cmus/default.theme
/usr/local/share/cmus/cyan.theme

```
So is that it, do I just delete the executeables in /usr/local/bin and the directories /usr/local/lib/cmus /usr/local/share/doc/cmus /usr/local/share/cmus and the man files ?

---

