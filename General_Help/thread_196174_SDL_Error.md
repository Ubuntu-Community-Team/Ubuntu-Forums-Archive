---
title: "SDL Error"
date: 2006-06-13
forum: General Help
---

### Post by Turkten on 2006-06-13
I am trying to install Dosbox and ZSNES from their src tars. Whenever I try either one I get the error saying that my SDL version is lower than 1.2.0 . I'm assuming it's wanting perl-SDL-1.2.0 but I can't seem to locate it anywhere. No luck with apt-get or aptitude, either. Anyone got a clue? Thanks for any help!

Term stuff:

checking build system type... powerpc-unknown-linux-gnu
checking host system type... powerpc-unknown-linux-gnu
checking target system type... powerpc-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for a BSD-compatible install... /usr/bin/install -c
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: SDL >= 1.2.0 is required

---

### Post by 23meg on 2006-06-13
You may need the dev files to compile; see if you have libsdl1.2-dev installed. And the perl bindings package is called libsdl-perl, if that's what you need.

---

### Post by Turkten on 2006-06-13
I don't have libsdl1.2-dev, how do I install the libsdl-perl pack? I am still new with linux.. sorry if this is a silly question...

---

### Post by 23meg on 2006-06-13
```
sudo apt-get install libsdl-perl
```Make sure you've enabled the Universe repository. 

[http://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](http://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by 23meg on 2006-06-13
By the way, it's much easier to install the apps you want from the repositories if you don't have a specific reason to be compiling from source:```
sudo apt-get install zsnes dosbox
```

---

### Post by Turkten on 2006-06-16
Ok, I got Dbox with adept and I didn't know that zsnes was 90% assembly so it won't compile on ppc, just 386 and up. Thanks for the help guys, I appreciate it. The enabling of universal repositories was nice, I didn't realize that I needed to do that. Thanks again!

---

