---
title: "Can't install packages"
date: 2010-06-06
forum: General Help
---

### Post by crazyfuturamanoob on 2010-06-06
**Short description of the problem: I need to have *freeglut3-dev*, *libglu1-mesa-dev*, *libgl1-mesa-dev* and *libgl1-mesa-swx11* installed at the same time. How to do it?**

There are no hardware drivers for my GPU (ATI Radeon HD 4290), so I must use the software rasterizer: *libgl1-mesa-swx11*. Fortunately I have a very fast hex-core CPU so rendering in software doesn't slow down the computer.

I make OpenGL games in C, so I need these packages to be able to compile my games:
[list]
[*]freeglut3-dev
[*]libglu1-mesa-dev
[*]libgl1-mesa-dev
[/list]
But if they are installed, *libgl1-mesa-swx11* must be replaced by *libgl1-mesa-glx*.
[I]
libgl1-mesa-glx[/I] is the hardware rasterizer and doesn't work, because I don't have the needed hardware drivers.

Currently, I have to install/remove/reinstall those 4 packages before compiling a program and then do it again after compiling to be able to run the program, that's insane! :mad:

---

### Post by crazyfuturamanoob on 2010-06-07
I solved it on my own:
```

cd /usr/include
sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev freeglut3-dev
*<libgl1-mesa-swx11 replaced with libgl1-mesa-glx and -dev packages installed>*
sudo cp -dpR GL OpenGL
sudo apt-get install libgl1-mesa-swx11
*<libgl1-mesa-glx replaced with libgl1-mesa-swx11 and -dev packages removed>*
sudo cp -dpR OpenGL GL

```
Now I have both software rasterizer and OpenGL headers. :guitar:

---

