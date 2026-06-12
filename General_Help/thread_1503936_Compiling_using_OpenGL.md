---
title: "Compiling using OpenGL"
date: 2010-06-07
forum: General Help
---

### Post by someoney3000 on 2010-06-07
Hello, I'm new to Ubuntu.  I was using fedora before and all the opengl development files were in a single package (+ dependencies).  I can't seem to track down that for Ubuntu.

Sure, I found the mesa libraries (libgl1-mesa-dev and libglu1-mesa-dev) and even tried freeglut3-dev, but none compiles the opengl program that runs on my fedora fine.

I get this error message:

```

/tmp/ccFnAvO6.o: In function `display()':
RoamingTerrain.cpp:(.text+0x6067): undefined reference to `gluLookAt'
/tmp/ccFnAvO6.o: In function `myReshape(int, int)':
RoamingTerrain.cpp:(.text+0x60e5): undefined reference to `gluPerspective'
collect2: ld returned 1 exit status

```

Anyone know what I am missing?  I compile via g++ -lglut RoamingTerrain.cpp

---

### Post by dino99 on 2010-06-07
only googled around :

[http://stackoverflow.com/questions/859501/learning-opengl-in-ubuntu](http://stackoverflow.com/questions/859501/learning-opengl-in-ubuntu)

---

### Post by someoney3000 on 2010-06-07
> **dino99 said:**
> only googled around :

[http://stackoverflow.com/questions/859501/learning-opengl-in-ubuntu](http://stackoverflow.com/questions/859501/learning-opengl-in-ubuntu)

Thank you.  It seems that I didn't tell the compiler to link the libraries.

How can we tell what the libraries are named though?

---

