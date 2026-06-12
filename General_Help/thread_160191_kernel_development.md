---
title: "kernel development"
date: 2006-04-14
forum: General Help
---

### Post by chocolatetoothpaste on 2006-04-14
Hey all, just wanted to ask a bit about kernel development.  I have gotten to the point in linux where I would say I am about intermediate, or at least an advanced beginner (if there is such a thing), however, I am less than satisfied with this.  I really want to get dirty, you know.  I want to be a power linux user.  Well, my question for the moment is, does anyone know of any resources on kernel development, or even software development in general on linux/ubuntu?  I would even like to learn more about rolling my own distro.  I don't want to try and make a mainstream distro, but just be able to customize my own.  One example of this would be devil linux.  I would like to be able to roll my own version of that, so it is optimized and preconfigured to my specific settings.  Anyway, ANY help that anyone has on these items would be greatly appreciated.

Edit:
What does anyone think of the book "Linux Kernel Development" by Robert Love?  Good/Bad/Ugly?

---

### Post by Sutekh on 2006-04-14
In regards to making your own distribution, try checking out [Linux From Scratch](www.linuxfromscratch.org/)

I want to give this a shot soon.

---

### Post by krismatth3 on 2006-04-14
[ftp://svr-ftp.eng.cam.ac.uk/pub/misc/love_C.ps.Z](ftp://svr-ftp.eng.cam.ac.uk/pub/misc/love_C.ps.Z) is a nice Unix oriented C tutorial (programming). C is what (most of the) Linux kernel uses.

A good starting point: [http://www.cyberdiem.com/vin/learn.html](http://www.cyberdiem.com/vin/learn.html) . I also like [http://codeproject.com/](http://codeproject.com/) (windows oriented) . Of course, googling for "c/c++ tutorial" will work too. :)

---

### Post by chocolatetoothpaste on 2006-04-14
Well, I have had significant experience with c++.  I have written several (very basic) windows apps, so I know how to do that.  I don't really know how to compile and all that in linux.  Plus, I am really confused on how the kernel is built  and used under an existing linux machine.

---

### Post by krismatth3 on 2006-04-14
Oh, I'm sorry. :) [http://plg.uwaterloo.ca/~itbowman/CS746G/a2/](http://plg.uwaterloo.ca/~itbowman/CS746G/a2/) is an overview of the architecture; I thinkthe best way to actually understand is to install the kernel source, build your own kernel, and dig into the source code / build system. 

(OT: Can we please leave religion/politics stuff out of this forum?)

---

