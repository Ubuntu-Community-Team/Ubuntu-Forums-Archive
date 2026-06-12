---
title: "Setup C++ and OpenGL"
date: 2010-10-21
forum: General Help
---

### Post by Urema on 2010-10-21
Hi,

Im trying to get OpenGL and C++ setup and working on ubuntu 10.04.
C++ works and OpenGL works with python etc but not with C++ i keep getting this error when running a C++ OpenGL programme : 
"
--- terrain ---
g++ -g -I. -I/usr/X11R6/include -L/usr/X11R6/lib terrain.cpp -o terrain -lpthread -lglut -lGLU -lGL -lm -lXi -lX11 -lXmu -lXext
/usr/bin/ld: cannot find -lXi
collect2: ld returned 1 exit status
"

Not sure what to do, does anyone have any idea?
By the way I dont want to try SDL, im sure its better etc but I do want C++ and OpenGL specifically nothing else.

Thanks greatly in advance,
Urema

---

