---
title: "OpenGL + Mesa 3D + MinGW"
date: 2010-01-02
forum: General Help
---

### Post by petike on 2010-01-02
Hello,
I program C++ applications on (Ubuntu) Linux and compile them to 2 operating systems: natively to *Linux* by using "g++" (GNU C++ compiler) and cross-compile them to *Windows* by using "i386-mingw32-g++" (MinGW C++ cross-compiler).
  Now, I am trying to cross-compile "OpenGL" applications (from Linux to Windows) - for that I need some OpenGL library files.

As an implementation of OpenGL, I use "Mesa 3D" open source library. Fortunately, Ubuntu offers "precompiled" mesa3d libraries (*libgl1-mesa-dev* and *libglu1-mesa-dev*) for Linux, but unfortunately, there are not any precompiled libraries for using with MinGW cross-compiler (thus Windows versions of them) - so I "MUST" manually compile them "from source" (which can be downloaded from [http://www.mesa3d.org]("http://www.mesa3d.org/") homepage).


  But I have no idea to do that. Within the mesa3d source code, there are some documents how to build the libraries for some specific platforms - specifically there is "README.MINGW32" readme file.
But just on the first lines there is some command
  ```
mingw32-make -f Makefile.mgw [OPTIONS...]
```  which I cannot run because I don't have any "mingw32-make" program installed. By other softwares, I used to build them with the "classic"
  ```
./configure -> make -> make install
```  procedure, but this is not working on mesa3d libraries.
For example, I have also tried
  ```
./configure --host=i386-mingw32
```  and it has been configured ok but after typing
  ```
make
```  it threw some error
  ```
error: #error No PIPE_SUBSYSTEM_WINDOWS_xxx subsystem defined.
```  and now I am LOST :-( .


  [SIZE=3]So does anybody know how to build the mesa3d libraries for using them with mingw32?[/SIZE]

  *P.S.:* And of course, **I DON'T WANT** to use Microsoft Visual Studio NEVER MORE :-) . And also I would like to do all the required things to build up OpenGL environment from Linux and using mingw32 for cross-compiling. I hope it is possible.
  *P.S.2:* On [http://www.mesa3d.org/systems.html](http://www.mesa3d.org/systems.html) page there is written that using MinGW with Mesa 3D is "deprecated". I am on the right way to use it just that way?

Thanks.

---

### Post by petike on 2010-01-02
Hello again,
I have solved this problem on another forum.
Here is the answer from that forum:

===========================================
There is no need to compile Mesa3D for MinGW. MinGW includes the GL library; it's just not called libGL.a nor libGLU.a; the libraries are instead called libopengl32.a and libglu32.a. Sadly, this is what Microsoft decided to call them under Windows on Visual Studio, so both Windows and GNU/Linux release of MinGW decided to include the libraries named as above.
  So, when cross compiling for Windows, just change:
  ```
-lGL -lGLU
```  into
  ```
-lopengl32 -lglu32
```===========================================

---

### Post by SlowBrute on 2010-05-08
Have you got this working with glui by any chance? I tried using -lglui and -lglui32 but neither work with minw32. 

I keep getting an error for my source file: "main.cpp:18:21: error: GL/glui.h: No such file or directory"

I can compile just fine for my linux machine, but not the cross-compiler

---

