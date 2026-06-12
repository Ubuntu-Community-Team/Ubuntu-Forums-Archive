---
title: "Compiling SheepShaver on Karmic"
date: 2009-11-11
forum: General Help
---

### Post by afrodeity on 2009-11-11
Keep getting this error when running ./autogen.sh

```

checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for file... /usr/bin/file
checking for perl... /usr/bin/perl
checking for PowerPC target CPU... no
./configure: line 4434: syntax error near unexpected token `('
./configure: line 4434: `case "(($ac_try" in'

```

---

### Post by lubod on 2009-11-30
Trying to mess with this myself, stuck at same point. Near as I can tell, the autogen.sh script in the source prepares the system for compiling by checking if files/libraries need are installed. It then executes ./configure. This is usually followed by make and make install, but those run separately, autogen.sh doesn't call them, the user does.

The ./configure step is failing, and where this line 4434 with the syntax error lives seems to be the file named simply configure, in the /SheepShaver/src/Unix directory. Now the fun of sorting the actual error continues. :-)

You might be interested in following this other thread, one guy says he compiled SheepShaver successfully, doesn't specify Karmic or Jaunty, but hey if it works on one, getting the other one to work should be easier than starting from scratch, right?

Thread URL:
[http://ubuntuforums.org/showthread.php?t=1334190](http://ubuntuforums.org/showthread.php?t=1334190)

FWIW (not much!) :-( I tried:
./configure --enable-sdl-static --enable-sdl-video --enable-sdl-audio --disable-vosf
and
./configure --enable-sdl-static --enable-sdl-video --enable-sdl-audio --enable-vosf

instead of plain:

./configure

hoping the additional options might help, since the lines above work to compile it on OS X, according to emaculation.com forums. No go.

---

### Post by gamgee911 on 2009-12-19
bump!  I too am having similar problems :(

---

### Post by afrodeity on 2009-12-19
[http://www.uluga.ubuntuforums.org/showthread.php?t=1334190](http://www.uluga.ubuntuforums.org/showthread.php?t=1334190)

---

