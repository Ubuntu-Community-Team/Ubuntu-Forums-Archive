---
title: "Compile program help."
date: 2009-07-17
forum: General Help
---

### Post by Peacefulpieofdeath on 2009-07-17
Ok im trying to install Nuclear Chess and ./configure seems to work

> root@Ubuntu-destop:/home/eric/Documents/Download/DownloadFF/nuclearchess-1.0.0# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for an ANSI C-conforming const... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for main in -lSDL_image... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating gfx/Makefile
config.status: executing depfiles commandsbut when i go make it does not work at all.

> root@Ubuntu-destop:/home/eric/Documents/Download/DownloadFF/nuclearchess-1.0.0# make
Making all in gfx
make[1]: Entering directory `/home/eric/Documents/Download/DownloadFF/nuclearchess-1.0.0/gfx'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/eric/Documents/Download/DownloadFF/nuclearchess-1.0.0/gfx'
Making all in src
make[1]: Entering directory `/home/eric/Documents/Download/DownloadFF/nuclearchess-1.0.0/src'
if gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"nuclearchess\" -DVERSION=\"1.0.0\" -I. -I.     -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DDATADIR="\"/usr/local/share/nuclearchess\"" -Wall -MT gfx.o -MD -MP -MF ".deps/gfx.Tpo" -c -o gfx.o gfx.c; \
    then mv -f ".deps/gfx.Tpo" ".deps/gfx.Po"; else rm -f ".deps/gfx.Tpo"; exit 1; fi
gfx.c:1:23: error: SDL_image.h: No such file or directory
gfx.c:12: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gfx.c:13: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘blitrect’
gfx.c: In function ‘Update’:
gfx.c:19: warning: implicit declaration of function ‘SDL_UpdateRects’
gfx.c:19: error: ‘Screen’ undeclared (first use in this function)
gfx.c:19: error: (Each undeclared identifier is reported only once
gfx.c:19: error: for each function it appears in.)
gfx.c:19: error: ‘blitrects’ undeclared (first use in this function)
gfx.c: At top level:
gfx.c:23: error: expected ‘)’ before ‘blitrect’
gfx.c: In function ‘ComplainAndExit’:
gfx.c:32: warning: implicit declaration of function ‘fprintf’
gfx.c:32: warning: incompatible implicit declaration of built-in function ‘fprintf’
gfx.c:32: error: ‘stderr’ undeclared (first use in this function)
gfx.c:32: warning: implicit declaration of function ‘SDL_GetError’
gfx.c:32: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
gfx.c: At top level:
gfx.c:36: error: expected ‘)’ before ‘*’ token
gfx.c:38: error: expected ‘)’ before ‘*’ token
gfx.c:48: error: expected ‘)’ before ‘*’ token
gfx.c:58: error: expected ‘)’ before ‘*’ token
gfx.c:78: error: expected ‘)’ before ‘*’ token
gfx.c: In function ‘init_SDL’:
gfx.c:95: warning: implicit declaration of function ‘SDL_Init’
gfx.c:95: error: ‘SDL_INIT_VIDEO’ undeclared (first use in this function)
gfx.c:98: error: ‘SDL_INIT_TIMER’ undeclared (first use in this function)
gfx.c:100: error: ‘SDL_Quit’ undeclared (first use in this function)
gfx.c:104: error: ‘Screen’ undeclared (first use in this function)
gfx.c:104: warning: implicit declaration of function ‘SDL_SetVideoMode’
gfx.c:104: error: ‘SDL_FULLSCREEN’ undeclared (first use in this function)
gfx.c:110: error: ‘BackBuffer’ undeclared (first use in this function)
gfx.c:110: warning: implicit declaration of function ‘SDL_AllocSurface’
gfx.c:118: warning: implicit declaration of function ‘printf’
gfx.c:118: warning: incompatible implicit declaration of built-in function ‘printf’
gfx.c:118: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
gfx.c:119: error: ‘FadeBuffer’ undeclared (first use in this function)
gfx.c:127: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
gfx.c:133: error: ‘_PutPixel’ undeclared (first use in this function)
gfx.c:133: error: ‘fast_putpixel1’ undeclared (first use in this function)
gfx.c:136: error: ‘fast_putpixel2’ undeclared (first use in this function)
gfx.c:139: error: ‘fast_putpixel3’ undeclared (first use in this function)
gfx.c:142: error: ‘fast_putpixel4’ undeclared (first use in this function)
gfx.c: In function ‘lock’:
gfx.c:149: warning: implicit declaration of function ‘SDL_MUSTLOCK’
gfx.c:149: error: ‘Screen’ undeclared (first use in this function)
gfx.c:150: warning: implicit declaration of function ‘SDL_LockSurface’
gfx.c: In function ‘unlock’:
gfx.c:156: error: ‘Screen’ undeclared (first use in this function)
gfx.c:157: warning: implicit declaration of function ‘SDL_UnlockSurface’
gfx.c: In function ‘FullUpdate’:
gfx.c:163: warning: implicit declaration of function ‘SDL_UpdateRect’
gfx.c:163: error: ‘Screen’ undeclared (first use in this function)
gfx.c: In function ‘AddRect’:
gfx.c:181: error: ‘blitrect’ undeclared (first use in this function)
gfx.c:185: warning: incompatible implicit declaration of built-in function ‘printf’
gfx.c:189: warning: implicit declaration of function ‘AddThisRect’
gfx.c: At top level:
gfx.c:193: error: expected declaration specifiers or ‘...’ before ‘SDL_Surface’
gfx.c: In function ‘Blit’:
gfx.c:195: error: ‘blitrect’ undeclared (first use in this function)
gfx.c:197: error: ‘image’ undeclared (first use in this function)
gfx.c:200: warning: incompatible implicit declaration of built-in function ‘printf’
gfx.c:205: warning: implicit declaration of function ‘SDL_BlitSurface’
gfx.c:205: error: ‘Screen’ undeclared (first use in this function)
gfx.c:207: warning: implicit declaration of function ‘SDL_FreeSurface’
gfx.c: At top level:
gfx.c:213: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gfx.c:239: error: expected declaration specifiers or ‘...’ before ‘SDL_Surface’
gfx.c: In function ‘BlitToBB’:
gfx.c:241: error: ‘blitrect’ undeclared (first use in this function)
gfx.c:243: error: ‘image’ undeclared (first use in this function)
gfx.c:245: error: ‘BackBuffer’ undeclared (first use in this function)
gfx.c: At top level:
gfx.c:252: error: expected declaration specifiers or ‘...’ before ‘SDL_Surface’
gfx.c:252: error: expected declaration specifiers or ‘...’ before ‘SDL_Rect’
gfx.c: In function ‘BlitPart’:
gfx.c:254: error: ‘blitrect’ undeclared (first use in this function)
gfx.c:254: error: ‘srcrect’ undeclared (first use in this function)
gfx.c:258: error: ‘image’ undeclared (first use in this function)
gfx.c:258: error: ‘Screen’ undeclared (first use in this function)
gfx.c: In function ‘FadeScreen’:
gfx.c:268: error: ‘Sint32’ undeclared (first use in this function)
gfx.c:268: error: expected ‘;’ before ‘now’
gfx.c:270: error: ‘Screen’ undeclared (first use in this function)
gfx.c:270: error: ‘FadeBuffer’ undeclared (first use in this function)
gfx.c:271: error: ‘now’ undeclared (first use in this function)
gfx.c:271: warning: implicit declaration of function ‘SDL_GetTicks’
gfx.c:272: error: ‘i’ undeclared (first use in this function)
gfx.c:275: error: ‘blitrect’ undeclared (first use in this function)
gfx.c:276: warning: implicit declaration of function ‘SDL_SetAlpha’
gfx.c:276: error: ‘BackBuffer’ undeclared (first use in this function)
gfx.c:276: error: ‘SDL_SRCALPHA’ undeclared (first use in this function)
gfx.c:277: error: too many arguments to function ‘Blit’
gfx.c:281: error: too many arguments to function ‘Blit’
gfx.c: At top level:
gfx.c:285: error: expected ‘)’ before ‘*’ token
make[1]: *** [gfx.o] Error 1
make[1]: Leaving directory `/home/eric/Documents/Download/DownloadFF/nuclearchess-1.0.0/src'
make: *** [all-recursive] Error 1
Can you help me and show what's wrong w/ me or what i should install.

---

### Post by blueridgedog on 2009-07-17
The software you downloaded is two years old.  I suggest you drop Karl an email and ask for help:

[http://user.cs.tu-berlin.de/~karlb/aboutme/](http://user.cs.tu-berlin.de/~karlb/aboutme/)

---

### Post by rCXer on 2009-07-17
I think you are missing libsdl-image1.2.  If you want compile install these and try again.

```

sudo apt-get install libsdl-image1.2
sudo apt-get install libsdl-image1.2-dev

```

Otherwise just download it like blueridgedog said.

---

### Post by neu2buntu on 2009-07-17
also note that "./configure" and "make" commands can/should be ran as normal user...only the make install command needs root privileges as in "sudo make install"

---

### Post by blueridgedog on 2009-07-17
As an aside, learning about nuclear chess is cool.

---

