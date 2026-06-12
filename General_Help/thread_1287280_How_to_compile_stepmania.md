---
title: "How to compile stepmania"
date: 2009-10-10
forum: General Help
---

### Post by xxterry1xx on 2009-10-10
Hey guys how do you compile stepmania 3.9? cause when i launch it and play a song randomly it crashes the x server and returns to login screen ending all programs

[http://www.stepmania.com/wiki/Downloads](http://www.stepmania.com/wiki/Downloads)

theres the linux binary that crashes

and the source code is what i need to compile? how do i compile?

i tryed this 

terry@terry-linksoftware:~$ cd Desktop
terry@terry-linksoftware:~/Desktop$ cd StepMania-3.9-src
terry@terry-linksoftware:~/Desktop/StepMania-3.9-src$ Make install
bash: Make: command not found
terry@terry-linksoftware:~/Desktop/StepMania-3.9-src$ ./configure
./configure: line 1008: config.log: Permission denied
terry@terry-linksoftware:~/Desktop/StepMania-3.9-src$ sudo -s
root@terry-linksoftware:~/Desktop/StepMania-3.9-src# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking whether byte ordering is bigendian... no
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for glPushMatrix in -lGL... no
configure: error: No OpenGL library could be found.
root@terry-linksoftware:~/Desktop/StepMania-3.9-src# make
make: *** No targets specified and no makefile found.  Stop.
root@terry-linksoftware:~/Desktop/StepMania-3.9-src# sudo make install
make: *** No rule to make target `install'.  Stop.
root@terry-linksoftware:~/Desktop/StepMania-3.9-src# clean install
bash: clean: command not found
root@terry-linksoftware:~/Desktop/StepMania-3.9-src# 

and yes i have the  build-essentials i also tryed automake but that didnt work 
and i have the (stepmania source and stepmania binary) in a folder which is StepMania-3.9-src on the desktop


thanks

---

### Post by lloyd_b on 2009-10-10
You're missing some of the "dependencies" (external libraries and such).  Try running this command (I found it on their website [here]("http://www.stepmania.com/wiki/Build_the_StepMania_Source_in_Linux")):```
sudo apt-get install libasound2-dev libmad0-dev libvorbis-dev libpng-dev libjpeg-dev libglu1-mesa-dev libgl1-mesa-dev xorg-dev libxrandr-dev automake build-essential subversion curl g++
```  Note that some of these will tell you "... already installed" if you've installed "build-essential".

Lloyd B.

---

### Post by xxterry1xx on 2009-10-10
> **lloyd_b said:**
> You're missing some of the "dependencies" (external libraries and such).  Try running this command (I found it on their website [here]("http://www.stepmania.com/wiki/Build_the_StepMania_Source_in_Linux")):```
sudo apt-get install libasound2-dev libmad0-dev libvorbis-dev libpng-dev libjpeg-dev libglu1-mesa-dev libgl1-mesa-dev xorg-dev libxrandr-dev automake build-essential subversion curl g++
```  Note that some of these will tell you "... already installed" if you've installed "build-essential".

Lloyd B.
checking for SDL - version >= 1.2.6... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.

*** SDL 1.2.6 or greater is required to build StepMania; please
*** make sure that it is installed to continue the build process.

i tryed apt-get install SDL 1.2.6 
but it doesnt exist... help

---

### Post by GolemdX on 2009-10-10
Have you tried going into Synaptic Package Manager and finding a package that supplies SDL 1.2.6?

I've always ran Stepmania... by opening the file Stepmania. Sure, it crashed X sometimes, but I wasn't the one playing it :P.

---

### Post by xxterry1xx on 2009-10-10
> **GolemdX said:**
> Have you tried going into Synaptic Package Manager and finding a package that supplies SDL 1.2.6?

I've always ran Stepmania... by opening the file Stepmania. Sure, it crashed X sometimes, but I wasn't the one playing it :P.
cant find anything

---

### Post by lloyd_b on 2009-10-10
There are several SDL libraries you may need (as well as the development headers to compile against them).
```
sudo apt-get install libsdl1.2-dev libsdl-gfx1.2-dev libsdl-image-1.2-dev libsdl-mixer-1.2-dev libsdl-sound1.2-dev libsdl-net1.2-dev
``` should install most if not all of the ones you need.  Note that installing the "-dev" package will auto-install the base library if it's not already installed.

Lloyd B.

---

### Post by xxterry1xx on 2009-10-10
> **lloyd_b said:**
> There are several SDL libraries you may need (as well as the development headers to compile against them).
```
sudo apt-get install libsdl1.2-dev libsdl-gfx1.2-dev libsdl-image-1.2-dev libsdl-mixer-1.2-dev libsdl-sound1.2-dev libsdl-net1.2-dev
``` should install most if not all of the ones you need.  Note that installing the "-dev" package will auto-install the base library if it's not already installed.

Lloyd B.
E: Couldn't find package libsdl-image-1.2-dev


arrr i just want to compile this dam thing

unless you can compile it for me :)

---

### Post by lloyd_b on 2009-10-10
That was a typo on my part.  "libsdl-image1.2-dev", not "libsdl-image-1.2-dev".  Also, the one after that should be "libsdl-mixer1.2-dev".

Note: If you fire up "Synaptic", and type "libsdl" in the search box, these should all be easy to find...

Lloyd B.

---

### Post by xxterry1xx on 2009-10-10
> **lloyd_b said:**
> That was a typo on my part.  "libsdl-image1.2-dev", not "libsdl-image-1.2-dev".  Also, the one after that should be "libsdl-mixer1.2-dev".

Note: If you fire up "Synaptic", and type "libsdl" in the search box, these should all be easy to find...

Lloyd B.
E: Couldn't find package libsdl-mixer-1.2-dev

lol

edit:
got all the packages and heres what i did but it failed...
root@terry-linksoftware:~/Desktop/StepMania-3.9-src# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking whether byte ordering is bigendian... no
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers in standard search path
checking for XTestQueryExtension in -lXtst... yes
checking for glPushMatrix in -lGL... yes
checking for gluGetString in -lGLU... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.6... yes
checking for png_create_read_struct in -lpng... yes
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for jpeg_read_scanlines in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for lua-config50... lua-config50
checking for inflate in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for ogg_stream_init in -logg... yes
checking for vorbis_comment_add in -lvorbis... yes
checking for ov_open in -lvorbisfile... yes
checking for mad_synth_init in -lmad... yes
checking for TLS... yes
checking for library containing avcodec_init... no
checking for library containing guess_format... no
checking for library containing dladdr... -ldl
checking for crash handler components... ok
checking for working cxa_demangle... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS... -lasound
checking for libasound headers version >= 0.9.0... found.
checking for snd_ctl_open in -lasound... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking whether OSS_GETVERSION is declared... yes
checking for stdint.h... (cached) yes
checking for inttypes.h... (cached) yes
checking endian.h usability... yes
checking endian.h presence... yes
checking for endian.h... yes
checking if cstdlib breaks llabs... yes
checking for pthread_create in -lpthread... yes
checking for pthread_mutex_timedlock in -lpthread... yes
checking whether powf is declared... yes
checking whether sqrtf is declared... yes
checking whether sinf is declared... yes
checking whether tanf is declared... yes
checking whether cosf is declared... yes
checking whether acosf is declared... yes
checking whether roundf is declared... yes
checking whether truncf is declared... yes
checking whether SIGPWR is declared... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands
root@terry-linksoftware:~/Desktop/StepMania-3.9-src# Make install
bash: Make: command not found
root@terry-linksoftware:~/Desktop/StepMania-3.9-src# make
Making all in src
make[1]: Entering directory `/home/terry/Desktop/StepMania-3.9-src/src'
make  all-am
make[2]: Entering directory `/home/terry/Desktop/StepMania-3.9-src/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/lua50 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -finline-limit=300   -Wall -W -Wno-unused -Wno-switch -O3 -MT Screen.o -MD -MP -MF ".deps/Screen.Tpo" \
      -c -o Screen.o `test -f 'Screen.cpp' || echo './'`Screen.cpp; \
    then mv -f ".deps/Screen.Tpo" ".deps/Screen.Po"; \
    else rm -f ".deps/Screen.Tpo"; exit 1; \
    fi
In file included from Actor.h:7,
                 from ActorFrame.h:6,
                 from Screen.h:6,
                 from Screen.cpp:2:
ActorCommands.h:20: warning: type qualifiers ignored on function return type
ActorCommands.h:21: warning: type qualifiers ignored on function return type
ActorCommands.h:22: warning: type qualifiers ignored on function return type
In file included from Grade.h:6,
                 from GameState.h:9,
                 from Screen.cpp:4:
RageUtil.h:145: error: &#8216;INT_MAX&#8217; was not declared in this scope
In file included from Screen.cpp:4:
GameState.h:88: error: extra qualification &#8216;GameState::&#8217; on member &#8216;GetRandomCharacter&#8217;
GameState.h:89: error: extra qualification &#8216;GameState::&#8217; on member &#8216;GetDefaultCharacter&#8217;
In file included from Screen.cpp:7:
ThemeManager.h:114: warning: type qualifiers ignored on function return type
ThemeManager.h:123: warning: type qualifiers ignored on function return type
ThemeManager.h:132: warning: type qualifiers ignored on function return type
In file included from Profile.h:10,
                 from ProfileManager.h:8,
                 from Screen.cpp:10:
HighScore.h: In member function &#8216;void HighScore::Unset()&#8217;:
HighScore.h:42: error: &#8216;memset&#8217; was not declared in this scope
make[2]: *** [Screen.o] Error 1
make[2]: Leaving directory `/home/terry/Desktop/StepMania-3.9-src/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/terry/Desktop/StepMania-3.9-src/src'
make: *** [all-recursive] Error 1
root@terry-linksoftware:~/Desktop/StepMania-3.9-src# sudo make install
Making install in src
make[1]: Entering directory `/home/terry/Desktop/StepMania-3.9-src/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/lua50 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -finline-limit=300   -Wall -W -Wno-unused -Wno-switch -O3 -MT Screen.o -MD -MP -MF ".deps/Screen.Tpo" \
      -c -o Screen.o `test -f 'Screen.cpp' || echo './'`Screen.cpp; \
    then mv -f ".deps/Screen.Tpo" ".deps/Screen.Po"; \
    else rm -f ".deps/Screen.Tpo"; exit 1; \
    fi
In file included from Actor.h:7,
                 from ActorFrame.h:6,
                 from Screen.h:6,
                 from Screen.cpp:2:
ActorCommands.h:20: warning: type qualifiers ignored on function return type
ActorCommands.h:21: warning: type qualifiers ignored on function return type
ActorCommands.h:22: warning: type qualifiers ignored on function return type
In file included from Grade.h:6,
                 from GameState.h:9,
                 from Screen.cpp:4:
RageUtil.h:145: error: &#8216;INT_MAX&#8217; was not declared in this scope
In file included from Screen.cpp:4:
GameState.h:88: error: extra qualification &#8216;GameState::&#8217; on member &#8216;GetRandomCharacter&#8217;
GameState.h:89: error: extra qualification &#8216;GameState::&#8217; on member &#8216;GetDefaultCharacter&#8217;
In file included from Screen.cpp:7:
ThemeManager.h:114: warning: type qualifiers ignored on function return type
ThemeManager.h:123: warning: type qualifiers ignored on function return type
ThemeManager.h:132: warning: type qualifiers ignored on function return type
In file included from Profile.h:10,
                 from ProfileManager.h:8,
                 from Screen.cpp:10:
HighScore.h: In member function &#8216;void HighScore::Unset()&#8217;:
HighScore.h:42: error: &#8216;memset&#8217; was not declared in this scope
make[1]: *** [Screen.o] Error 1
make[1]: Leaving directory `/home/terry/Desktop/StepMania-3.9-src/src'
make: *** [install-recursive] Error 1

---

### Post by lloyd_b on 2009-10-10
> **xxterry1xx said:**
> E: Couldn't find package libsdl-mixer-1.2-dev

lol

I pointed out in my previous message that I had typo'ed on that one as well.

Lloyd B.

---

### Post by xxterry1xx on 2009-10-10
> **lloyd_b said:**
> I pointed out in my previous message that I had typo'ed on that one as well.

Lloyd B.
i edited the post above

---

### Post by lloyd_b on 2009-10-10
Here's the critical section of your ./configure:```
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
```In this case, it probably means you need the gtk development headers, so "sudo apt-get libgtk2.0-dev libglib2.0-dev".

Don't be too surprised if there are still more dependencies that appear after this - it's called "dependency hell", and is one of the major reasons that package systems like "apt" were developed...

Lloyd B.

---

### Post by xxterry1xx on 2009-10-13
> **lloyd_b said:**
> Here's the critical section of your ./configure:```
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
```In this case, it probably means you need the gtk development headers, so &quot;sudo apt-get libgtk2.0-dev libglib2.0-dev&quot;.

Don't be too surprised if there are still more dependencies that appear after this - it's called &quot;dependency hell&quot;, and is one of the major reasons that package systems like &quot;apt&quot; were developed...

Lloyd B.

terry@terry-linksoftware:~$ sudo apt-get libgtk2.0-dev libglib2.0-dev E: Invalid operation libgtk2.0-dev sorry for a late reply iv been a little busy and ubuntu messed up dam kleansweep so i have kubuntu now.

---

### Post by lloyd_b on 2009-10-14
> **xxterry1xx said:**
> terry@terry-linksoftware:~$ sudo apt-get libgtk2.0-dev libglib2.0-dev E: Invalid operation libgtk2.0-dev sorry for a late reply iv been a little busy and ubuntu messed up dam kleansweep so i have kubuntu now.

Another typo on my part.  It should be "sudo apt-get **install** libgtk2.0-dev libglib2.0-dev"

Lloyd B.

---

### Post by xxterry1xx on 2009-10-17
> **lloyd_b said:**
> Another typo on my part.  It should be "sudo apt-get **install** libgtk2.0-dev libglib2.0-dev"

Lloyd B.
root@terry-linksoftware:~/Desktop/StepMania-3.9# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking whether byte ordering is bigendian... no
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers in standard search path
checking for XTestQueryExtension in -lXtst... yes
checking for glPushMatrix in -lGL... yes
checking for gluGetString in -lGLU... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.6... yes
checking for png_create_read_struct in -lpng... yes
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for jpeg_read_scanlines in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for lua-config50... no
checking for lua-config... no
checking for lua_open in -llua... no
checking for lua_open in -llua50... no
checking for luaopen_base in -llualib... no
checking for luaopen_base in -llualib50... no

*** liblua is required to build StepMania; please make sure that
*** it is installed to continue the installation process.
root@terry-linksoftware:~/Desktop/StepMania-3.9# apt-get install liblua
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package liblua

---

### Post by Bachstelze on 2009-10-17
You want liblua50-dev.

---

### Post by xxterry1xx on 2009-10-17
> **Bachstelze said:**
> You want liblua50-dev.
Making all in src
make[1]: Entering directory `/home/terry/Desktop/StepMania-3.9/src'
make  all-am
make[2]: Entering directory `/home/terry/Desktop/StepMania-3.9/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/lua50 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -finline-limit=300   -Wall -W -Wno-unused -Wno-switch -O3 -MT Screen.o -MD -MP -MF ".deps/Screen.Tpo" \
      -c -o Screen.o `test -f 'Screen.cpp' || echo './'`Screen.cpp; \
    then mv -f ".deps/Screen.Tpo" ".deps/Screen.Po"; \
    else rm -f ".deps/Screen.Tpo"; exit 1; \
    fi
In file included from Actor.h:7,
                 from ActorFrame.h:6,
                 from Screen.h:6,
                 from Screen.cpp:2:
ActorCommands.h:20: warning: type qualifiers ignored on function return type
ActorCommands.h:21: warning: type qualifiers ignored on function return type
ActorCommands.h:22: warning: type qualifiers ignored on function return type
In file included from Grade.h:6,
                 from GameState.h:9,
                 from Screen.cpp:4:
RageUtil.h:145: error: ‘INT_MAX’ was not declared in this scope
In file included from Screen.cpp:4:
GameState.h:88: error: extra qualification ‘GameState::’ on member ‘GetRandomCharacter’
GameState.h:89: error: extra qualification ‘GameState::’ on member ‘GetDefaultCharacter’
In file included from Screen.cpp:7:
ThemeManager.h:114: warning: type qualifiers ignored on function return type
ThemeManager.h:123: warning: type qualifiers ignored on function return type
ThemeManager.h:132: warning: type qualifiers ignored on function return type
In file included from Profile.h:10,
                 from ProfileManager.h:8,
                 from Screen.cpp:10:
HighScore.h: In member function ‘void HighScore::Unset()’:
HighScore.h:42: error: ‘memset’ was not declared in this scope
make[2]: *** [Screen.o] Error 1
make[2]: Leaving directory `/home/terry/Desktop/StepMania-3.9/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/terry/Desktop/StepMania-3.9/src'
make: *** [all-recursive] Error 1

kk i think im doing the commands wrong how do i make a deb package out of this so i can just install it and play o also if i make a deb package will other people using ubuntu 9.04 or 9.10 will it work for them?

---

### Post by xxterry1xx on 2009-10-18
> **xxterry1xx said:**
> Making all in src
make[1]: Entering directory `/home/terry/Desktop/StepMania-3.9/src'
make  all-am
make[2]: Entering directory `/home/terry/Desktop/StepMania-3.9/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/lua50 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -finline-limit=300   -Wall -W -Wno-unused -Wno-switch -O3 -MT Screen.o -MD -MP -MF &quot;.deps/Screen.Tpo&quot; \
      -c -o Screen.o `test -f 'Screen.cpp' || echo './'`Screen.cpp; \
    then mv -f &quot;.deps/Screen.Tpo&quot; &quot;.deps/Screen.Po&quot;; \
    else rm -f &quot;.deps/Screen.Tpo&quot;; exit 1; \
    fi
In file included from Actor.h:7,
                 from ActorFrame.h:6,
                 from Screen.h:6,
                 from Screen.cpp:2:
ActorCommands.h:20: warning: type qualifiers ignored on function return type
ActorCommands.h:21: warning: type qualifiers ignored on function return type
ActorCommands.h:22: warning: type qualifiers ignored on function return type
In file included from Grade.h:6,
                 from GameState.h:9,
                 from Screen.cpp:4:
RageUtil.h:145: error: ‘INT_MAX’ was not declared in this scope
In file included from Screen.cpp:4:
GameState.h:88: error: extra qualification ‘GameState::’ on member ‘GetRandomCharacter’
GameState.h:89: error: extra qualification ‘GameState::’ on member ‘GetDefaultCharacter’
In file included from Screen.cpp:7:
ThemeManager.h:114: warning: type qualifiers ignored on function return type
ThemeManager.h:123: warning: type qualifiers ignored on function return type
ThemeManager.h:132: warning: type qualifiers ignored on function return type
In file included from Profile.h:10,
                 from ProfileManager.h:8,
                 from Screen.cpp:10:
HighScore.h: In member function ‘void HighScore::Unset()’:
HighScore.h:42: error: ‘memset’ was not declared in this scope
make[2]: *** [Screen.o] Error 1
make[2]: Leaving directory `/home/terry/Desktop/StepMania-3.9/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/terry/Desktop/StepMania-3.9/src'
make: *** [all-recursive] Error 1

kk i think im doing the commands wrong how do i make a deb package out of this so i can just install it and play o also if i make a deb package will other people using ubuntu 9.04 or 9.10 will it work for them?

bump help i also installed checkinstall and other libs

---

### Post by xxterry1xx on 2009-10-21
> **xxterry1xx said:**
> bump help i also installed checkinstall and other libs bump

---

### Post by lloyd_b on 2009-10-21
> ...
from Screen.cpp:4:
[COLOR="Red"]RageUtil.h:145: error: ‘INT_MAX’ was not declared in this scope[/COLOR]
In file included from Screen.cpp:4:
[COLOR="Orange"]GameState.h:88: error: extra qualification ‘GameState::’ on member ‘GetRandomCharacter’
GameState.h:89: error: extra qualification ‘GameState::’ on member ‘GetDefaultCharacter’[/COLOR]
In file included from Screen.cpp:7:
ThemeManager.h:114: warning: type qualifiers ignored on function return type
ThemeManager.h:123: warning: type qualifiers ignored on function return type
ThemeManager.h:132: warning: type qualifiers ignored on function return type
In file included from Profile.h:10,
from ProfileManager.h:8,
from Screen.cpp:10:
HighScore.h: In member function ‘void HighScore::Unset()’:
[COLOR="Red"]HighScore.h:42: error: ‘memset’ was not declared in this scope[/COLOR]
make[2]: *** [Screen.o] Error 1
...
The red lines are most likely bugs in the source - they can *probably* be fixed with a "#include ..." directive.

I'm not sure what's causing the lines in orange - they *could* be a result of the preceding error, or they might not be.

Net result - the code is broke.  Short of downloading it and debugging it myself, there's no way I can tell what needs to be changed.

I'd suggest finding a forum for that particular software, and posting the issues there...

Lloyd B.

---

