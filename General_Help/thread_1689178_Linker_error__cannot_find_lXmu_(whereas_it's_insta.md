---
title: "Linker error : cannot find lXmu (whereas it's installed)"
date: 2011-02-16
forum: General Help
---

### Post by FluidBlow on 2011-02-16
**[SIZE=2]Hello,[/SIZE]**

I'm trying to compile a file with the following line : 
```
gcc lesson2.c -o lesson2 -I /usr/X11R6/include/ -L /usr/lib/ -L/usr/X11R6/lib/ -L /usr/X11R6/lib64/ -lglut -lGL -lGLU -lX11 -lXmu -lm
```But i got the error : */usr/bin/ld: cannot find -lXmu*

I'm using this to compile a simple OpenGL file, and if I remove lxmu (and lxi, wiche gives me the same error), it got the all clear, but when I tun my program, I got an "Segmentation fault" error (I think because of the missing librairies)...

When I did a *locate libXmu* :
```
/usr/lib/libXmu.so.6
/usr/lib/libXmu.so.6.2.0
/usr/lib/libXmuu.so.1
/usr/lib/libXmuu.so.1.0.0
```I tried including the library's path but, always the same error...
Do I have to search for the header files ? What can I do to link my lXmu to the one requested ?

Thank you for helping :)

---

### Post by gmargo on 2011-02-16
Install the **libxmu-dev** package to link with "-lXmu".

However, the "missing libraries" is not why you got a segmentation fault.

---

### Post by FluidBlow on 2011-02-16
Thanks for replying.

I've already seen that, but I'm on an public computer, so I can't install new packages..

---

