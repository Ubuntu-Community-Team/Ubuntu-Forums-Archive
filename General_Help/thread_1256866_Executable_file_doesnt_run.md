---
title: "Executable file doesnt run"
date: 2009-09-03
forum: General Help
---

### Post by arquitecto on 2009-09-03
Hi!
I am relatively new to Xubuntu but I am loving it!
Nevertheless I am stuck with a program I can t run this fantastic stand alone program:
[Ivy generator]("http://graphics.uni-konstanz.de/~luft/ivy_generator/package/ivy_generator_Linux_qt4_1.3.tar.gz")
 
The executable doest seem to run.
It runned with the 8.04 so I assume its a bug in jaunty jackalope.
 
Does any one have a package for me to use? Or is there any solution to this? :(
 
Thanks in advance to all!

---

### Post by P4man on 2009-09-03
seems to run fine here on jaunty.
Do you have qt4 libs and accelerated videodrivers?

---

### Post by arquitecto on 2009-09-03
> **P4man said:**
> seems to run fine here on jaunty.
Do you have qt4 libs and accelerated videodrivers?
 
I Have qt4 installed.
it came by default on my live cd installation.
 
But no videodrivers. Is an old pentium III deschutes.

---

### Post by Bachstelze on 2009-09-03
> **arquitecto said:**
> 
The executable doest seem to run.

What happens when you try to run it?

---

### Post by P4man on 2009-09-03
the program needs accelerated OpenGL. 
Thats probably your problem. 
What videocard do you have in that machine?

---

### Post by arquitecto on 2009-09-03
> **HymnToLife said:**
> What happens when you try to run it?
 
Nothing. Absolutly nothing.

---

### Post by arquitecto on 2009-09-03
> **P4man said:**
> the program needs accelerated OpenGL. 
Thats probably your problem. 
What videocard do you have in that machine?
 
So old I cant tell...
Dont you think the fact that I have already used this program nicely in my previous installation of xubuntu 8.04, before I upgraded to 9.04 has something to do with this?

---

### Post by P4man on 2009-09-03
> **arquitecto said:**
> So old I cant tell...
Dont you think the fact that I have already used this program nicely in my previous installation of xubuntu 8.04, before I upgraded to 9.04 has something to do with this?

Well, versions before ubuntu 9.04 could use legacy videodrivers for even older videocards from ATI and nVidia. So its quite likely you had binary drivers for you videocard, even if its as old as a TNT2. In jaunty, that no longer works, it requires newer video driver, which in turn require a newer videocard.

To check what videocard you have, you can run

```
lspci
```

in a terminal. post the output here. If its an ATI card, we might get it working with opensource drivers, if its an nvidia card, then don't have too much hope.

---

### Post by Vaphell on 2009-09-03
```
hwinfo --short 
```  gives much cleaner list of devices
or
```
hwinfo --gfxcard
```

---

### Post by arquitecto on 2009-09-03
I will check it as soon as possible
 
I think its an old matrox G200.
The processor is 350Mhz. 
The card has the same age, there fore i almost certain that is a G200.
 
But why do I need the drivers?
Shouldnt xubuntu 's default installation support it?
 
I have blender, yafaray, totem, installed, (wich need a nice videocard) and they all work fine!
 
Strange.:(

---

### Post by P4man on 2009-09-03
well maybe you dont, Im not sure if the default opensource matrox drivers offer opengl acceleration.

try running glxgears in a terminal, if that works, that we're probably on the wrong track. try launching ivy generator from a terminal then, and see if you get any output at all?

---

### Post by arquitecto on 2009-09-03
> **P4man said:**
> well maybe you dont, Im not sure if the default opensource matrox drivers offer opengl acceleration.
 
try running glxgears in a terminal, if that works, that we're probably on the wrong track. try launching ivy generator from a terminal then, and see if you get any output at all?
 
When I typed IvyGenerator with the terminal opened in the bin folder I got the command not found answer.
 
I have already used this program before I upgraded
 
What are glxgears? Sorry but I am very new to linux...:(

---

### Post by P4man on 2009-09-03
doh.. heh. ok. Im sorry, I may have made this more complicated than needed.

Lets go over this step by step

download it here:

[http://graphics.uni-konstanz.de/~luft/ivy_generator/package/ivy_generator_Linux_qt4_1.3.tar.gz](http://graphics.uni-konstanz.de/~luft/ivy_generator/package/ivy_generator_Linux_qt4_1.3.tar.gz)

Save it to your desktop. Open  the archive, then extract the "ivy_generator_linux_qt4_1.3" folder to your homefolder (you might want to rename it later).

Then open that extracted folder , go to the "bin" subfolder and double click IvyGenerator.

If that fails, then something is wrong :)

In that case, open a terminal, type

cd ivy_ (then press TAB key to avoid typing everything, so so you get::
```
cd ivy_generator_linux_qt4_1.3
cd bin
./IvyGenerator

```

(note uppercases)

then what output do you get?

as for glxgears, its just a small app to test if openGL works. You can run in a terminal

```
glxgears
```

If you see a few gears turning and you have a reasonable framerate then all is well

---

### Post by arquitecto on 2009-09-04
Hi!
 
Sorry for my ignorance!:)
 
When I type
./IvyGenerator
I get this error:
**error while loading shared libraries: libQtOpenGL.so.4: cannot open shared object file: No such file or directory**
 
When I type glxgears nothing happens!
 
I will try to install that library...

---

### Post by P4man on 2009-09-04
Took me a while to figure out the need for "./" as well. In linux, the directory you are in is not part of the path. Kinda weird, but if you type in a command, it will look everywhere in the path, but not in the directory you are in. "./" means current directory, so it will look there too :)

As for the errors, well, Im not sure. But perhaps my initial thought (no OpenGL acceleration) was correct after all.. gotta run now, Ill check later.

---

### Post by 3rdalbum on 2009-09-04
Have you got the "libqt4-opengl" package installed?

---

### Post by arquitecto on 2009-09-04
> **3rdalbum said:**
> Have you got the "libqt4-opengl" package installed?
 
Nope.
No internet nocection on that machine.
I will download it and I will install the package and I will post the results.

---

### Post by arquitecto on 2009-09-07
I installed de package and guess what 
 
THE APP IS RUNNING NOW!
 
:popcorn:
 
Thanks a lot guys!
This is definatly a forum to stay close!

---

