---
title: "Installing programs"
date: 2006-02-23
forum: General Help
---

### Post by Cactus Jack on 2006-02-23
I am trying to install a program that is not a Debian or RPM file.  I can't get it to install with apt-get or Synaptic Package Manager.  How would I go about installing the program.  :-k 

Thanks,
Cactus

---

### Post by darth_vector on 2006-02-23
did you get the source code for the software or an installer in the form of a .run file?

---

### Post by Cactus Jack on 2006-02-23
I have the source code.  Also there is an install file, but I can't get it to work.
It says to install use "make ./race " .  But this doesn't work?

Cactus

---

### Post by darth_vector on 2006-02-23
try "sudo make ./race"

there should be installation instructions in a file called README, at the bottom of the source tree. these instructions usually asume you have a root terminal. if you follow their instructions and use sudo where required you should have no problems.

---

### Post by nanotube on 2006-02-23
to be able to build from source, you also have to install a package called "build-essential". you can find it in synaptic. 
then you will have all the necessary tools (including "make") to build and install from source.

---

### Post by darth_vector on 2006-02-23
^ ah, yes. forgot that little detail :-)

---

### Post by Cactus Jack on 2006-02-23
"build-essential" is installed.  When I type "sudo make ./race" , I get, "make: *** No rule to make target race' . Stop. "

Cactus

---

### Post by Cactus Jack on 2006-02-24
Some reason it can't find the program.  I have it on my desktop.  Is this ok?

Cactus

---

### Post by aysiu on 2006-02-24
Can you post the output of these commands (and the commands themselves)? ```
cd ~/Desktop
ls
```

---

### Post by joshuapurcell on 2006-02-24
[QUOTE=Cactus Jack]"build-essential" is installed.  When I type "sudo make ./race" , I get, "make: *** No rule to make target race' . Stop. "

Cactus[/QUOTE]Adding **./race** after **sudo make** seems weird. Usually compiling from source follows something like these steps:```
./configure
make
sudo make install
```You may not have to run the **./configure** portion, but the rest is pretty much the norm.

---

### Post by Cactus Jack on 2006-02-25
Here is a copy of my Desktop:

bar-004e69810d.desktop   larry-00e7221576.desktop  rtai-3.3
bar-007d5b5a17.desktop   picservo                  rtic-manual.0.6.4.ps
blah-00a1181032.desktop  race-0.5                  temp
brent@ubuntu2:~/Desktop$

Cactus

---

### Post by Cactus Jack on 2006-02-28
What does no rule to make target mean?

Cactus

---

### Post by RAOF on 2006-02-28
It means that the makefile doesn't have instructions to build what you asked.  In your case, you asked it to build "./race" (which is what "make ./race" means), which looks a bit odd.

Have you tried just running "make" (in the directory with the sourcecode)?

---

### Post by Cactus Jack on 2006-02-28
When I do I get several syntax errors and warnings.  It may be that this program has some problems. It says in the install file that "Have successfully built on the following systems: Debian 3.0 x86, 2.4.18 kernel, NVidiaGL 2960" .  Being that it has run on a older kernel and not 2.6 be a problem?

Cactus

---

### Post by RAOF on 2006-02-28
[QUOTE=Cactus Jack]When I do I get several syntax errors and warnings.  It may be that this program has some problems. It says in the install file that "Have successfully built on the following systems: Debian 3.0 x86, 2.4.18 kernel, NVidiaGL 2960" .  Being that it has run on a older kernel and not 2.6 be a problem?

Cactus[/QUOTE]
It's obviously an old program, but it shouldn't care about the kernel version (too much).

Could you post some/all (if you're not sure what's relevant) of the error messages?  You probably don't have all the required development libraries installed to compile the program.

It's much easier to help if you post the actual errors, but I think you might be out of luck - does the program have some sort of support board/howto?  Where did you get it?

Finally, does the race-0.5 directory contain a "configure" file?  If it does, run it with "./configure" when you're in the race-0.5 directory.  It will scan for the necessary libraries, and tell you what libraries it needs that you don't have.

---

### Post by Cactus Jack on 2006-02-28
Here goes!  I do appreciate you helping with this.


brent@ubuntu2:~/Desktop/race-0.5$ make
Building and Linking Race Game
gcc -Wall -ansi src/main.c     -c `sdl-config --cflags`
/bin/sh: sdl-config: command not found
In file included from src/main.c:1:
src/global.h:8:19: error: GL/gl.h: No such file or directory
src/global.h:9:20: error: GL/glu.h: No such file or directory
src/global.h:10:17: error: SDL.h: No such file or directory
src/global.h:11:23: error: SDL_image.h: No such file or directory
src/global.h:12:23: error: SDL_mixer.h: No such file or directory
In file included from src/main.c:1:
src/global.h:32: error: syntax error before ‘GLfloat’
src/global.h:32: warning: no semicolon at end of struct or union
src/global.h:33: warning: type defaults to ‘int’ in declaration of ‘y’
src/global.h:33: warning: data definition has no type or storage class
src/global.h:34: error: syntax error before ‘z’
src/global.h:34: warning: type defaults to ‘int’ in declaration of ‘z’
src/global.h:34: warning: data definition has no type or storage class
src/global.h:35: warning: type defaults to ‘int’ in declaration of ‘VERTEX’
src/global.h:35: warning: data definition has no type or storage class
src/global.h:38: error: syntax error before ‘GLfloat’
src/global.h:38: warning: no semicolon at end of struct or union
src/global.h:39: warning: type defaults to ‘int’ in declaration of ‘y’
src/global.h:39: warning: data definition has no type or storage class
src/global.h:40: error: syntax error before ‘z’
src/global.h:40: warning: type defaults to ‘int’ in declaration of ‘z’
src/global.h:40: warning: data definition has no type or storage class
src/global.h:41: warning: type defaults to ‘int’ in declaration of ‘VECTOR’
src/global.h:41: warning: data definition has no type or storage class
src/global.h:44: error: syntax error before ‘GLfloat’
src/global.h:44: warning: no semicolon at end of struct or union
src/global.h:45: warning: type defaults to ‘int’ in declaration of ‘b’
src/global.h:45: warning: data definition has no type or storage class
src/global.h:46: error: syntax error before ‘c’
src/global.h:46: warning: type defaults to ‘int’ in declaration of ‘c’
src/global.h:46: warning: data definition has no type or storage class
src/global.h:47: error: syntax error before ‘d’
src/global.h:47: warning: type defaults to ‘int’ in declaration of ‘d’
src/global.h:47: warning: data definition has no type or storage class
src/global.h:48: warning: type defaults to ‘int’ in declaration of ‘PLANE’
src/global.h:48: warning: data definition has no type or storage class
src/global.h:62: error: syntax error before ‘GLfloat’
src/global.h:62: warning: no semicolon at end of struct or union
src/global.h:63: warning: type defaults to ‘int’ in declaration of ‘MODEL’
src/global.h:63: warning: data definition has no type or storage class
src/global.h:66: error: syntax error before ‘GLfloat’
src/global.h:66: warning: no semicolon at end of struct or union
src/global.h:67: warning: type defaults to ‘int’ in declaration of ‘vel’
src/global.h:67: warning: data definition has no type or storage class
src/global.h:68: error: syntax error before ‘dir’
src/global.h:68: warning: type defaults to ‘int’ in declaration of ‘dir’
src/global.h:68: warning: data definition has no type or storage class
src/global.h:69: error: syntax error before ‘maxvel’
src/global.h:69: warning: type defaults to ‘int’ in declaration of ‘maxvel’
src/global.h:69: warning: data definition has no type or storage class
src/global.h:70: error: syntax error before ‘accel’
src/global.h:70: warning: type defaults to ‘int’ in declaration of ‘accel’
src/global.h:70: warning: data definition has no type or storage class
src/global.h:71: error: syntax error before ‘rot’
src/global.h:71: warning: type defaults to ‘int’ in declaration of ‘rot’
src/global.h:71: warning: data definition has no type or storage class
src/global.h:72: error: syntax error before ‘rotvel’
src/global.h:72: warning: type defaults to ‘int’ in declaration of ‘rotvel’
src/global.h:72: warning: data definition has no type or storage class
src/global.h:73: error: syntax error before ‘rotdir’
src/global.h:73: warning: type defaults to ‘int’ in declaration of ‘rotdir’
src/global.h:73: warning: data definition has no type or storage class
src/global.h:74: error: syntax error before ‘rotmax’
src/global.h:74: warning: type defaults to ‘int’ in declaration of ‘rotmax’
src/global.h:74: warning: data definition has no type or storage class
src/global.h:75: error: syntax error before ‘rotacc’
src/global.h:75: warning: type defaults to ‘int’ in declaration of ‘rotacc’
src/global.h:75: warning: data definition has no type or storage class
src/global.h:76: error: syntax error before ‘xmax’
src/global.h:76: warning: type defaults to ‘int’ in declaration of ‘xmax’
src/global.h:76: warning: type defaults to ‘int’ in declaration of ‘xmin’
src/global.h:76: warning: data definition has no type or storage class
src/global.h:77: error: syntax error before ‘zmax’
src/global.h:77: warning: type defaults to ‘int’ in declaration of ‘zmax’
src/global.h:77: warning: type defaults to ‘int’ in declaration of ‘zmin’
src/global.h:77: warning: data definition has no type or storage class
src/global.h:78: error: syntax error before ‘xtilt’
src/global.h:78: warning: type defaults to ‘int’ in declaration of ‘xtilt’
src/global.h:78: warning: type defaults to ‘int’ in declaration of ‘ztilt’
src/global.h:78: warning: data definition has no type or storage class
src/global.h:79: error: syntax error before ‘}’ token
src/global.h:79: warning: type defaults to ‘int’ in declaration of ‘SHIP’
src/global.h:79: warning: data definition has no type or storage class
src/global.h:98: error: syntax error before ‘*’ token
src/global.h:98: warning: type defaults to ‘int’ in declaration of ‘surface’
src/global.h:98: warning: data definition has no type or storage class
src/global.h:99: error: syntax error before ‘event’
src/global.h:99: warning: type defaults to ‘int’ in declaration of ‘event’
src/global.h:99: warning: data definition has no type or storage class
src/global.h:100: error: syntax error before ‘base’
src/global.h:100: warning: type defaults to ‘int’ in declaration of ‘base’
src/global.h:100: warning: data definition has no type or storage class
src/global.h:101: error: syntax error before ‘texture’
src/global.h:101: warning: type defaults to ‘int’ in declaration of ‘texture’
src/global.h:101: warning: data definition has no type or storage class
src/global.h:102: error: syntax error before ‘i’
src/global.h:102: warning: type defaults to ‘int’ in declaration of ‘i’
src/global.h:102: warning: type defaults to ‘int’ in declaration of ‘j’
src/global.h:102: warning: type defaults to ‘int’ in declaration of ‘vi’
src/global.h:102: warning: type defaults to ‘int’ in declaration of ‘ti’
src/global.h:102: warning: data definition has no type or storage class
src/global.h:103: error: syntax error before ‘player’
src/global.h:103: warning: type defaults to ‘int’ in declaration of ‘player’
src/global.h:103: warning: data definition has no type or storage class
src/global.h:104: error: syntax error before ‘*’ token
src/global.h:104: warning: type defaults to ‘int’ in declaration of ‘chunk’
src/global.h:104: warning: data definition has no type or storage class
src/global.h:105: error: syntax error before ‘*’ token
src/global.h:105: warning: type defaults to ‘int’ in declaration of ‘music’
src/global.h:105: warning: data definition has no type or storage class
In file included from src/main.c:5:
src/game.h:12: error: syntax error before ‘ship’
In file included from src/main.c:7:
src/font.h:6: error: syntax error before ‘x’
src/main.c: In function ‘killgame’:
src/main.c:11: warning: implicit declaration of function ‘glDeleteLists’
src/main.c:12: warning: implicit declaration of function ‘glDeleteTextures’
src/main.c:15: warning: implicit declaration of function ‘Mix_FreeChunk’
src/main.c:16: warning: implicit declaration of function ‘Mix_CloseAudio’
src/main.c:17: warning: implicit declaration of function ‘SDL_QuitSubSystem’
src/main.c:17: error: ‘SDL_INIT_AUDIO’ undeclared (first use in this function)
src/main.c:17: error: (Each undeclared identifier is reported only once
src/main.c:17: error: for each function it appears in.)
src/main.c:20: warning: implicit declaration of function ‘SDL_Quit’
src/main.c: In function ‘resize’:
src/main.c:27: error: ‘GLfloat’ undeclared (first use in this function)
src/main.c:27: error: syntax error before ‘width’
src/main.c:28: warning: implicit declaration of function ‘glViewport’
src/main.c:28: error: ‘GLint’ undeclared (first use in this function)
src/main.c:28: error: syntax error before ‘width’
src/main.c:29: warning: implicit declaration of function ‘glMatrixMode’
src/main.c:29: error: ‘GL_PROJECTION’ undeclared (first use in this function)
src/main.c:30: warning: implicit declaration of function ‘glLoadIdentity’
src/main.c:31: warning: implicit declaration of function ‘gluPerspective’
src/main.c:32: error: ‘GL_MODELVIEW’ undeclared (first use in this function)
src/main.c: In function ‘events’:
src/main.c:39: error: request for member ‘type’ in something not a structure or union
src/main.c:40: error: ‘SDL_VIDEORESIZE’ undeclared (first use in this function)
src/main.c:41: warning: implicit declaration of function ‘SDL_SetVideoMode’
src/main.c:41: error: request for member ‘resize’ in something not a structure o r union
src/main.c:41: error: request for member ‘resize’ in something not a structure o r union
src/main.c:41: warning: assignment makes pointer from integer without a cast
src/main.c:44: error: request for member ‘resize’ in something not a structure o r union
src/main.c:44: error: request for member ‘resize’ in something not a structure o r union
src/main.c:46: error: ‘SDL_KEYDOWN’ undeclared (first use in this function)
src/main.c:47: error: request for member ‘key’ in something not a structure or u nion
src/main.c:48: error: ‘SDLK_F1’ undeclared (first use in this function)
src/main.c:49: warning: implicit declaration of function ‘SDL_WM_ToggleFullScree n’
make: *** [all] Error 1
brent@ubuntu2:~/Desktop/race-0.5$

Cactus

---

### Post by RAOF on 2006-02-28
Well, the first couple of errors:
```
src/global.h:8:19: error: GL/gl.h: No such file or directory
src/global.h:9:20: error: GL/glu.h: No such file or directory
src/global.h:10:17: error: SDL.h: No such file or directory
src/global.h:11:23: error: SDL_image.h: No such file or directory
src/global.h:12:23: error: SDL_mixer.h: No such file or directory

```
Tell me that it's after (at least) the SDL-dev packages, the SDL-image-dev packages & the SDL-mixer-dev packages.  Also, it's after some opengl dev packages.

Search in Synaptic for "sdl", "sdl-mixer", "sdl-image" and install the -dev packages.  You'll also need to search for the OpenGL packages - I **think** that the mesa-dev packages are what you're after, here.

---

### Post by Cactus Jack on 2006-02-28
It is looking alot better!  I am not real efficient with Linux.  This is what I have got know.

brent@ubuntu2:~/Desktop/race-0.5$ make
Building and Linking Race Game
gcc -Wall -ansi src/main.c     -c `sdl-config --cflags`
gcc -Wall -ansi src/timing.c   -c `sdl-config --cflags`
gcc -Wall -ansi src/vector.c   -c `sdl-config --cflags`
gcc -Wall -ansi src/fifo.c     -c `sdl-config --cflags`
gcc -Wall -ansi src/ortho.c    -c `sdl-config --cflags`
gcc -Wall -ansi src/audio.c    -c `sdl-config --cflags`
gcc -Wall -ansi src/font.c     -c `sdl-config --cflags`
gcc -Wall -ansi src/init.c     -c `sdl-config --cflags`
gcc -Wall -ansi src/textures.c -c `sdl-config --cflags`
gcc -Wall -ansi src/terrain.c  -c `sdl-config --cflags`
gcc -Wall -ansi src/menu.c     -c `sdl-config --cflags`
gcc -Wall -ansi src/game.c     -c `sdl-config --cflags`
gcc -Wall -ansi src/hud.c      -c `sdl-config --cflags`
gcc -Wall -ansi src/messages.c -c `sdl-config --cflags`
gcc -Wall -ansi src/camera.c   -c `sdl-config --cflags`
gcc -Wall -ansi main.o timing.o vector.o fifo.o ortho.o audio.o font.o \
init.o textures.o terrain.o menu.o game.o hud.o messages.o \
camera.o \
-o race -lGL -lGLU -lSDL_image -lSDL_mixer -lm `sdl-config --libs`

Cactus

---

### Post by RAOF on 2006-02-28
Looks like that's worked!  You should be able to run it by typing "./race" in the source directory.

---

### Post by Cactus Jack on 2006-03-01
Thank you RAOF! Works perfect!

---

