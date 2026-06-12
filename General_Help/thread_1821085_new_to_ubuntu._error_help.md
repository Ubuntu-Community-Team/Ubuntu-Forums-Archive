---
title: "new to ubuntu. error help???"
date: 2011-08-08
forum: General Help
---

### Post by sinbowden on 2011-08-08
what does this error mean?

error: conversion to ‘Uint16’ from ‘unsigned int’ may alter its value In file included from game/aiplugman.cpp:9: ./include/playerpool.h: In member function ‘Uint8 PlayerPool::getNumPlayers() const’: ./include/playerpool.h:38: error: conversion to ‘Uint8’ from ‘size_t’ may alter its value make[1]: *** [game/aiplugman.o] Error 1

---

### Post by lkjoel on 2011-08-08
What application are you trying to run/compile?
It looks like a bug in the program.

---

### Post by sinbowden on 2011-08-08
> **lkjoel said:**
> What application are you trying to run/compile?
It looks like a bug in the program.

I am not sure I think its GNU. how do i check what compiler I use?

---

### Post by lkjoel on 2011-08-08
Could you give me the output of these commands? The output doesn't look GNU.
```
ls
pwd
which gcc; which cc; which gpp; which g++

```

---

### Post by sinbowden on 2011-08-08
mark@blaze:~$ ls
Desktop  Documents  Downloads  freecol  Music  Pictures  Public  Templates  Videos
mark@blaze:~$ pwd
/home/mark
mark@blaze:~$ which gcc; which cc; which gpp; which g++
/usr/bin/gcc
/usr/bin/cc
/usr/bin/g++

---

### Post by sinbowden on 2011-08-08
o, i see what you mean. i just need to slow down and take my time!

---

### Post by lkjoel on 2011-08-08
The problem is that the developers of the program made the Makefile for debugging, and not for general use.

Could you give me the output of this Terminal command (and could you wrap it in code tags):
```
cat ~/Downloads/FreeCNC/freecnc++/*akefile

```

---

### Post by sinbowden on 2011-08-08
> **lkjoel said:**
> The problem is that the developers of the program made the Makefile for debugging, and not for general use.

Could you give me the output of this Terminal command (and could you wrap it in code tags):
```
cat ~/Downloads/FreeCNC/freecnc++/*akefile

```
  

I was just reading over that... I am unfamiliar? what should i read about to make me familiar with what I need to do? 


mark@blaze:~/Downloads/FreeCNC/freecnc++$ sdl-config
Usage: sdl-config [--prefix[=DIR]] [--exec-prefix[=DIR]] [--version] [--cflags] [--libs] [--static-libs]
mark@blaze:~/Downloads/FreeCNC/freecnc++$ cat ~/Downloads/FreeCNC/freecnc++/*akefile
include setup/base/config_base_base
include setup/test_base
include setup/test_data

# MSYS's uname returns the OS as part of -s, e.g. MINGW32_NT-4.0
# So we translate this into something nicer.
SYSTEM=$(shell uname -s | sed -e 's/MINGW.*/Mingw/g')
SYSFILES=$(wildcard setup/$(SYSTEM)/config*)

# TODO: This should be refactorred into a foreach
default: config
        +$(MAKE) -C src
#       +$(MAKE) -C plugins
        +$(MAKE) -C tools

config: setup/base/* $(SYSFILES)
        $(foreach test, $(TESTS), $(call TEST_template, $(test)))
        @echo Going to use $(SYSTEM) specific settings
        @cat -- setup/base/config* > config
        @cp -- $(SYSFILES) . || cp -- setup/Linux/config* .
        @cat config_* >> config
        @rm -f config_*

reconfig:
        @echo Resetting config
        -rm -f config config_*
        @$(MAKE) config

.PHONY: clean cleaner doxygen

# TODO: This should be refactorred into a foreach
clean:
        +$(MAKE) -C src clean || (touch config; $(MAKE) -C src clean; rm config)
        +$(MAKE) -C plugins clean || (touch config; $(MAKE) -C plugins clean; rm config)
        +$(MAKE) -C tools clean || (touch config; $(MAKE) -C tools clean; rm config)

cleaner: clean
        -rm -f config config_* freecnc.log audplay.log shpview.log tmpinied.log

doxygen:
        cd doc/tech/doxygen && doxygen

---

### Post by sinbowden on 2011-08-08
here is the TODO.txt

---

### Post by lkjoel on 2011-08-08
The problem is that one of the makefiles is corrupted. This is not normal, but it is possible to fix.
Could you give me the output of these commands?
```
cat ~/Downloads/FreeCNC/freecnc++/setup/test_base
cat ~/Downloads/FreeCNC/freecnc++/setup/test_data
cat ~/Downloads/FreeCNC/freecnc++/setup/base/config_base_base

```

---

### Post by sinbowden on 2011-08-08
mark@blaze:~/Downloads/FreeCNC/freecnc++$ cat ~/Downloads/FreeCNC/freecnc++/setup/test_base
define TEST_template
@echo Checking for $($(join $1,_NAME))
@$(CC) $(join setup/tests/test,$1).c $($(join $1,_CFLAGS)) $($(join $1,_LIBS)) -o $(join test,$1) || true
@$(join ./test, $1) && cp $(join setup/config_,$1) . || cp $(join setup/config_no,$1) .
@rm -f $(join test,$1)

endef
mark@blaze:~/Downloads/FreeCNC/freecnc++$ cat ~/Downloads/FreeCNC/freecnc++/setup/test_data
TESTS=

#test_NAME     = Test
#test_CFLAGS   = `test-config --cflags`
#test_LIBS     = `test-config --libs`

mark@blaze:~/Downloads/FreeCNC/freecnc++$ cat ~/Downloads/FreeCNC/freecnc++/setup/base/config_base_base
# Workaround for FreeBSD crazyness
SDLCONFIG = `which sdl-config 2> /dev/null || which sdl11-config`

# Avoid running sdl-config in backticks for every invocation of gcc
SDLCFLAGS = $(shell $(SDLCONFIG) --cflags)
SDLLIBS = $(shell $(SDLCONFIG) --libs) -lSDL_mixer

DEBUG_FLAGS = -g
#DEBUG_FLAGS = -g -DDEBUG
OPT_FLAGS   = # -Os
BASE_CFLAGS = -Wall -Werror $(DEBUG_FLAGS) $(OPT_FLAGS) $(SDLCFLAGS)
CFLAGS      = $(BASE_CFLAGS) $(CSTRICTNESS)
CXXFLAGS    = $(BASE_CFLAGS) $(CXXSTRICTNESS)
LIBS        = $(SDLLIBS) # -s -Wl,O1
mark@blaze:~/Downloads/FreeCNC/freecnc++$

---

### Post by lkjoel on 2011-08-08
Type this into a Terminal window:
```
sed -i 's/BASE_CFLAGS = -Wall -Werror $(DEBUG_FLAGS) $(OPT_FLAGS) $(SDLCFLAGS)/BASE_CFLAGS = -Wall $(DEBUG_FLAGS) $(OPT_FLAGS) $(SDLCFLAGS)/g' ~/Downloads/FreeCNC/freecnc++/setup/base/config_base_base

```
It should be fixed!

---

### Post by sinbowden on 2011-08-08
i didnet work. I am thankful for the help. this was my output from sudo make:

mark@blaze:~/Downloads/FreeCNC/freecnc++$ sudo make
[sudo] password for mark: 
Going to use Linux specific settings
make -C src
make[1]: Entering directory `/home/mark/Downloads/FreeCNC/freecnc++/src'
g++ -Wall -g  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -std=c++98 -Wconversion -W -Wno-unused -c game/aiplugman.cpp -o game/aiplugman.o -I./include  -I./include/lua
In file included from game/aiplugman.cpp:5:
./include/ccmap.h: In member function ‘bool CnCMap::getResource(Uint32, Uint8*, Uint8*) const’:
./include/ccmap.h:140: warning: conversion to ‘unsigned char’ from ‘short unsigned int’ may alter its value
./include/ccmap.h:141: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
./include/ccmap.h: In member function ‘void CnCMap::translateCoord(Uint32, Uint16*, Uint16*) const’:
./include/ccmap.h:248: warning: conversion to ‘short unsigned int’ from ‘Uint32’ may alter its value
./include/ccmap.h:251: warning: conversion to ‘short unsigned int’ from ‘Uint32’ may alter its value
In file included from ./include/playerpool.h:9,
                 from game/aiplugman.cpp:9:
./include/player.h: In member function ‘Uint16 Player::getStructureLosses() const’:
./include/player.h:83: warning: conversion to ‘Uint16’ from ‘unsigned int’ may alter its value
In file included from game/aiplugman.cpp:9:
./include/playerpool.h: In member function ‘Uint8 PlayerPool::getNumPlayers() const’:
./include/playerpool.h:38: warning: conversion to ‘Uint8’ from ‘size_t’ may alter its value
g++ -Wall -g  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -std=c++98 -Wconversion -W -Wno-unused -c game/buildqueue.cpp -o game/buildqueue.o -I./include  -I./include/lua
In file included from ./include/playerpool.h:9,
                 from game/buildqueue.cpp:6:
./include/player.h: In member function ‘Uint16 Player::getStructureLosses() const’:
./include/player.h:83: warning: conversion to ‘Uint16’ from ‘unsigned int’ may alter its value
In file included from game/buildqueue.cpp:6:
./include/playerpool.h: In member function ‘Uint8 PlayerPool::getNumPlayers() const’:
./include/playerpool.h:38: warning: conversion to ‘Uint8’ from ‘size_t’ may alter its value
game/buildqueue.cpp: In member function ‘virtual void BuildQueue::BQEvent::run()’:
game/buildqueue.cpp:147: warning: conversion to ‘Uint8’ from ‘unsigned int’ may alter its value
game/buildqueue.cpp: In member function ‘ConStatus BuildQueue::BQEvent::getStatus(UnitOrStructureType*, Uint8*, Uint8*) const’:
game/buildqueue.cpp:199: warning: conversion to ‘unsigned char’ from ‘unsigned int’ may alter its value
g++ -Wall -g  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -std=c++98 -Wconversion -W -Wno-unused -c game/dispatcher.cpp -o game/dispatcher.o -I./include  -I./include/lua
In file included from game/dispatcher.cpp:2:
./include/ccmap.h: In member function ‘bool CnCMap::getResource(Uint32, Uint8*, Uint8*) const’:
./include/ccmap.h:140: warning: conversion to ‘unsigned char’ from ‘short unsigned int’ may alter its value
./include/ccmap.h:141: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
./include/ccmap.h: In member function ‘void CnCMap::translateCoord(Uint32, Uint16*, Uint16*) const’:
./include/ccmap.h:248: warning: conversion to ‘short unsigned int’ from ‘Uint32’ may alter its value
./include/ccmap.h:251: warning: conversion to ‘short unsigned int’ from ‘Uint32’ may alter its value
In file included from ./include/playerpool.h:9,
                 from game/dispatcher.cpp:7:
./include/player.h: In member function ‘Uint16 Player::getStructureLosses() const’:
./include/player.h:83: warning: conversion to ‘Uint16’ from ‘unsigned int’ may alter its value
In file included from game/dispatcher.cpp:7:
./include/playerpool.h: In member function ‘Uint8 PlayerPool::getNumPlayers() const’:
./include/playerpool.h:38: warning: conversion to ‘Uint8’ from ‘size_t’ may alter its value
In file included from game/dispatcher.cpp:8:
./include/structure.h: At global scope:
./include/structure.h:268: error: ISO C++ forbids declaration of ‘BuildingAnimEvent’ with no type
./include/structure.h:268: error: expected ‘;’ before ‘*’ token
./include/structure.h: In member function ‘void Structure::changeImage(Uint8, Sint16)’:
./include/structure.h:177: warning: conversion to ‘short unsigned int’ from ‘int’ may alter its value
In file included from game/dispatcher.cpp:9:
./include/unit.h: In member function ‘Uint8 InfantryGroup::getFreePos() const’:
./include/unit.h:324: warning: conversion to ‘Uint8’ from ‘int’ may alter its value
./include/unit.h: In member function ‘Uint8 InfantryGroup::getImageNums(Uint32**, Sint8**, Sint8**)’:
./include/unit.h:340: warning: conversion to ‘signed char’ from ‘int’ may alter its value
./include/unit.h:341: warning: conversion to ‘signed char’ from ‘int’ may alter its value
./include/unit.h: In member function ‘void InfantryGroup::getSubposOffsets(Uint8, Uint8, Sint8*, Sint8*)’:
./include/unit.h:348: warning: conversion to ‘signed char’ from ‘int’ may alter its value
./include/unit.h:349: warning: conversion to ‘signed char’ from ‘int’ may alter its value
game/dispatcher.cpp: In member function ‘void Dispatcher::Dispatcher::unitMove(Unit*, Uint32)’:
game/dispatcher.cpp:51: warning: conversion to ‘Uint16’ from ‘Uint32’ may alter its value
game/dispatcher.cpp: In member function ‘bool Dispatcher::Dispatcher::structurePlace(const StructureType*, Uint32, Uint8)’:
game/dispatcher.cpp:116: warning: conversion to ‘Uint16’ from ‘Uint32’ may alter its value
game/dispatcher.cpp: In member function ‘bool Dispatcher::Dispatcher::structurePlace(const char*, Uint32, Uint8)’:
game/dispatcher.cpp:131: warning: conversion to ‘Uint16’ from ‘Uint32’ may alter its value
game/dispatcher.cpp: In member function ‘bool Dispatcher::Dispatcher::unitCreate(const char*, Uint32, Uint8, Uint8)’:
game/dispatcher.cpp:176: warning: conversion to ‘Uint16’ from ‘Uint32’ may alter its value
make[1]: *** [game/dispatcher.o] Error 1
make[1]: Leaving directory `/home/mark/Downloads/FreeCNC/freecnc++/src'
make: *** [default] Error 2

---

### Post by lkjoel on 2011-08-08
This is an error with the program. Do you have the latest version?

---

### Post by sinbowden on 2011-08-08
yes I downloaded it from sorceforge. could it be a problem with my iso or my compiler? im downloading it again just to be sure.

---

### Post by lkjoel on 2011-08-08
No, it's a problem with the application.
Could you give me the download link? I could see if I could fix it.

---

### Post by sinbowden on 2011-08-08
[http://sourceforge.net/projects/freecnc/files/FreeCNC%20Snapshots/2004-12-19/freecnc-20041219-source.tgz/download](http://sourceforge.net/projects/freecnc/files/FreeCNC%20Snapshots/2004-12-19/freecnc-20041219-source.tgz/download)

---

### Post by lkjoel on 2011-08-08
This project is full of bugs. Sorry I can't fix them.
But there is another project that works great.

```
mkdir openra; cd openra
wget http://openra.res0l.net/assets/downloads/linux/deb/openra_release.20110511_all.deb
sudo apt-get install libopenal1 mono-runtime libmono-winforms2.0-cil libfreetype6 libsdl1.2debian libgl1-mesa-glx libgl1-mesa-dri libmono-i18n2.0-cil
sudo dpkg -i openra_release.20110511_all.deb

```
And to run:
```
openra

```
Notice: It will have to download some data at the first run.

---

### Post by sinbowden on 2011-08-09
Thanks for the work and info! i tried to install openra and the installation was sucsessful with the exeption of the project wont launch! I reported the bug to [http://bugs.open-ra.org/](http://bugs.open-ra.org/) This is what the output the terminal gave me. 

Unhandled Exception: System.InvalidOperationException: GL Error: 1282
  at OpenRA.Renderer.Glsl.GraphicsDevice.CheckGlError () [0x00000] in <filename unknown>:0 
  at OpenRA.Renderer.Glsl.Shader..ctor (OpenRA.Renderer.Glsl.GraphicsDevice dev, System.String type) [0x00000] in <filename unknown>:0 
  at OpenRA.Renderer.Glsl.GraphicsDevice.CreateShader (System.String name) [0x00000] in <filename unknown>:0 
  at OpenRA.Graphics.Renderer..ctor () [0x00000] in <filename unknown>:0 
  at OpenRA.Game.Initialize (OpenRA.Arguments args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Run (System.String[] args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0

---

### Post by lkjoel on 2011-08-09
Do you have a Graphics Card, and the Driver? If you don't, that is the problem.

---

