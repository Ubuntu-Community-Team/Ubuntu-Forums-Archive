---
title: "Ubuntu 8.04 64 bit with chroot 32 bit, opengl, x11 and ANSYS 6.1 (closed source)"
date: 2010-08-17
forum: General Help
---

### Post by jashale on 2010-08-17
Background:  I am mechanical engineer.  I do some advanced analysis using the Finite Element Method (FEM).  FEM uses massive computer resources.  I often hit memory usage with FEM programs of 6 Gigabytes of ram.  The most I have used is 13 Gigabytes of memory when I only had 9 Gigabytes of ram. Recently I discovered we have an old license of ANSYS 6.1 Mechanical.  ANSYS Mechanical is a closed source high end FEM program.  The price tag when it was purchased in 2002 was probably $35,000.  Its closed source.  At the time of release, an AMD64 compliant processor did not exist which means x86-64 is not supported by ANSYS 6.1.  ANSYS does support IA-64 (itanium) and other rare 64-bit hardware (sgi, sunsparc, irix, aix, etc).  However I do not have access to this type of 64-bit hardware.  IA-32/x86 is supported.  So I will use IA-32/x86.  

Problem:  I want to setup a x86 (32 bit) Ubuntu 8.04 chroot inside of x86-64 bit Ubuntu 8.04 with OpenGL and x11 support so that ANSYS 6.1 can use the maximum amount of ram which is 4 Gigabytes.  If I run a 32-bit ubuntu, some ram is consumed by the operating system and I do not want to fight the Ubuntu OS for resources.  I will be maxing out the the 32-bit 4 gig limit regularly.

Where I am at:  I have followed several guides and got a working chroot except for x11 and OpenGL.  I don't know where to go from here.  When I type glxgears inside the chroot, i get:

```
glxgears
Error:couldn't open display (null)
```

In short, How do I get x11 and openGL working inside a chroot?

---

