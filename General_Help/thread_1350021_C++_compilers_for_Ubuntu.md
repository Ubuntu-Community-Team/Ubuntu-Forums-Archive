---
title: "C++ compilers for Ubuntu"
date: 2009-12-08
forum: General Help
---

### Post by Vignesh S on 2009-12-08
I'm learning some C++ at the moment, but I have no idea if there is even a C++ compiler for Ubuntu. Any ideas as to which C++ compiler I should use? I'm trying codelite, but I have no idea how to run the program or even how to compile the code.

---

### Post by Sam on 2009-12-08
Install [build-essential](apt:build-essential). The compiler is gcc.

---

### Post by Vignesh S on 2009-12-09
Right, I think I just want to know how to even use CodeLite for C++ development. I mean, I can't even test the code I've made. I'm totally lost with it, let alone using build-essential for compiling the source code :-(

---

### Post by Ninja Tux on 2009-12-09
One simple command can solve your problem. 

Open up a terminal and type:

```
sudo apt-get install g++
```

If this won't work, ask your system administrator to install it for you.

---

### Post by mickie.kext on 2009-12-09
> **Vignesh S said:**
> Right, I think I just want to know how to even use CodeLite for C++ development. I mean, I can't even test the code I've made. I'm totally lost with it, let alone using build-essential for compiling the source code :-(

If you need good IDE, i sugest NetBeans. For compiler, just use g++

---

### Post by grundygreen on 2009-12-09
> **Vignesh S said:**
> I'm learning some C++ at the moment, but I have no idea if there is even a C++ compiler for Ubuntu. Any ideas as to which C++ compiler I should use? I'm trying codelite, but I have no idea how to run the program or even how to compile the code.

C is the foundation of unix. So of course linux will have Support for C and its derivatives. As others have noted GCC will compile C++ as well as other languages.

You might try the eclipse IDE as well.
[http://www.eclipse.org](http://www.eclipse.org)

[https://help.ubuntu.com/community/EclipseI](https://help.ubuntu.com/community/EclipseI)

---

### Post by Vignesh S on 2009-12-09
I'm liking Eclipse. But how on Earth do I use it to make C++ code? I'm really stuck when it comes to that :-(

---

### Post by mickie.kext on 2009-12-10
> **Vignesh S said:**
> I'm liking Eclipse. But how on Earth do I use it to make C++ code? I'm really stuck when it comes to that :-(

You need Eclipse CDT if you want to use it for C++. If you have CDT and you have G++ compiler, than this guide will help you to set it up:
[http://max.berger.name/howto/cdt/ar01s04.jsp](http://max.berger.name/howto/cdt/ar01s04.jsp)

---

### Post by cholericfun on 2009-12-10
i;m not a C man myself so i prob sound a bit too naive but as far as i would guess you just type 
```
g++ [some options-see manpage] myfile.c
``` 
for simple one-file c++ code.
also if youre doing some time intensive stuff then consider getting the intel c compiler from their web-page. in fortran at least they work much faster even on AMD.

anyhow
heres uncle googles answer:

[http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html)

and others.

---

