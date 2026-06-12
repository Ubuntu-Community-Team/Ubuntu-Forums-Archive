---
title: "Problem with QGLViewer"
date: 2010-11-08
forum: General Help
---

### Post by tani1974 on 2010-11-08
Hello,
I have a program that uses QGLViewer library. I compiled the program
in one machine(ubuntu) .Later I used the executable to run the program in another machine (ubuntu) (because earlier machine is not working any more). For that I installed all necessary libraries.  exe is working fine on the new machine.

But when I tried to compile the code  it gave following error message:
/usr/bin/ld: cannot find -lQGLViewer

I checked inside the usr/lib and found it contains qglviewer.a qglviewer.so etc.

then I change the make file to -lqglviewer

now it is giving new error messages like:

undefined reference to `QGLViewer::QGLViewer(QWidget*, QGLWidget const*, QFlags<Qt::WindowType>)'
 etc.

Do any one have any idea, what actually causes the problem ?

Thanks in advance

---

### Post by dino99 on 2010-11-08
found this thread:

[https://yade-dem.org/wiki/New:Porting_QGLViewer_to_kubuntu](https://yade-dem.org/wiki/New:Porting_QGLViewer_to_kubuntu)

but why you dont use package from synaptic: 2.3.4-2 are available into natty

---

