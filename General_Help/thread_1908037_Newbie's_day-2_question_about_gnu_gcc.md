---
title: "Newbie's day-2 question about gnu gcc"
date: 2012-01-12
forum: General Help
---

### Post by chenxinghao on 2012-01-12
I just installed Ubuntu 11.10 a day ago. I used to have access to a Sun Microsystems' workstation with gnu gcc installed and I have some C/C++ programs that I want to recompile and run in Ubuntu.
 
So my day-2 question is wheter or not the free gnu gcc package can work within Ubuntu and if there is any success story in this regard.
 
Thank you.

---

### Post by MG&amp;TL on 2012-01-12
> **chenxinghao said:**
> I just installed Ubuntu 11.10 a day ago. I used to have access to a Sun Microsystems' workstation with gnu gcc installed and I have some C/C++ programs that I want to recompile and run in Ubuntu.
 
So my day-2 question is wheter or not the free gnu gcc package can work within Ubuntu and if there is any success story in this regard.
 
Thank you.



Er...ubuntu is based around open-source and GNU, so yes. :)

Open a teminal (ctrl-alt-t) and type:

```
sudo apt-get install gcc g++ build-essential
```

which will install gcc (for C), g++ (for C++), and build-essential (some stuff to make it work, I think. Clarification please!)

As to solaris -> Linux, not sure but I imagine as long as you didn't link against anything too weird, it should be okay.

---

### Post by |{urse on 2012-01-12
yep, I've done it a couple times, but not on ubuntu yet, the host compile was fedora core 8.


[http://wiki.osdev.org/Canadian_Cross](http://wiki.osdev.org/Canadian_Cross) <-- check this out 

[http://airs.com/ian/configure/configure_6.html](http://airs.com/ian/configure/configure_6.html) <-- then this

---

### Post by chenxinghao on 2012-01-12
It appears that GNU gcc is installed.
 
I opened a terminal and typed "man gcc" and the entry says that it is a GNU C and C++ compiler. Does that mean GNU C++ is already installed as well.
 
If gcc is for GNU C and C++, what is g++ for? The Software Center says gcc is a GNU 
C compiler and g++ is a GNU C++ compiler.
 
I am confused.

---

### Post by gordintoronto on 2012-01-12
Actually, build-essential includes the other two.

---

### Post by MG&amp;TL on 2012-01-13
> **chenxinghao said:**
> It appears that GNU gcc is installed.
 
I opened a terminal and typed "man gcc" and the entry says that it is a GNU C and C++ compiler. Does that mean GNU C++ is already installed as well.
 
If gcc is for GNU C and C++, what is g++ for? The Software Center says gcc is a GNU 
C compiler and g++ is a GNU C++ compiler.
 
I am confused.

Yup, sorry, should have been clearer.

gcc = C.
g++ = C++.

and build-essential installs those two as well, apparently. :)

You may already have installed gcc, it's not a problem. :)

---

### Post by chenxinghao on 2012-01-13
I am a newbie and still confused:
 
I have not manually installed GNU gcc and so it must come with the Ubuntu 11.10 installation and the immediate 287 something (automatic) updates right after I installed Ubuntu. (This is not important.)
 
Anyways, in the Software Center, it shows that gnu gcc is installed and gnu g++ is not. But in a Terminal window after tying "man gcc" the top line reads "GNU C and C++ compiler." So, the confusing is the Software Center says g++ is not installed, while the "man gcc" readout seems telling me that gcc is a compiler for C AND C++ (and is already installed).
 
If there is already a C++ compiler (with gcc), it seems to me there is no need to install another one (GNU g++, in this case).

---

### Post by |{urse on 2012-01-13
What kind of program are you trying to compile for solaris at work? is it just a console program? What all are you linking to? can you post your #includes? It's kind of a shot in the dark unless you know whether the programs dependencies are already met on both systems and the target execute machines cpu arch is compatible with the compile host machines arch.

At the very least I see you having to ifndef a few stray libs for it to work unless its just a hello world program using standard c libs. That's why I was suggesting a cross compile above.

I might be totally wrong here so please, someone enlighten me if I need it.

---

### Post by chenxinghao on 2012-01-13
I have some old C/C++ programs developed many years ago that could ran on Sun Microsystems work stations and HPs. The last time I recompiled them was with GNU gcc several years back on a SUN Microsystems' Sparc station (Intel CPU) running Solaris, at school, with very minor changes in the makefile. 
 
The programs are very simple and elementary, for learning purposes. I now decide to pick up the learning again.
 
If the installed GNU gcc has C and C++ covered, then I should be fine and will start load the old programs to recompile them and make changes as necessary. I just want to make sure the installed GNU gcc has the C++ capability as well before working on the old programs. I don't want to complicate the system by installing another C++ compiler (the GNU g++) unless it is absolutely needed.
 
Right now the Software Center says GNU gcc is installed and "man gcc" says it is a C and C++ Compiler. If this means that I already have a compiler for both C and C++ programs, there is no need to install the GNU g++.

---

### Post by MG&amp;TL on 2012-01-13
> **chenxinghao said:**
> I have some old C/C++ programs developed many years ago that could ran on Sun Microsystems work stations and HPs. The last time I recompiled them was with GNU gcc several years back on a SUN Microsystems' Sparc station (Intel CPU) running Solaris, at school, with very minor changes in the makefile. 
 
The programs are very simple and elementary, for learning purposes. I now decide to pick up the learning again.
 
If the installed GNU gcc has C and C++ covered, then I should be fine and will start load the old programs to recompile them and make changes as necessary. I just want to make sure the installed GNU gcc has the C++ capability as well before working on the old programs. I don't want to complicate the system by installing another C++ compiler (the GNU g++) unless it is absolutely needed.
 
Right now the Software Center says GNU gcc is installed and "man gcc" says it is a C and C++ Compiler. If this means that I already have a compiler for both C and C++ programs, there is no need to install the GNU g++.


Oh I get it. You DO need both gcc and g++, but the manpage is the same one because they take the same options.

```
man gcc
man g++
```

gives the same manpage. g++ is really not a big download.

---

### Post by chenxinghao on 2012-02-28
Thanks for all the inputs.

I have migrated my old C codes and compiled them successfully.

Now I wrote a some C++ code with a makefile and the make says g++ command not found.

So it is clear now that I need to install the GNU C++ option.

It was suggested that I do the following

sudo apt-get install gcc g++ build-essential
Since I have GNU C compiler in the Ubuntu already, should I remove gcc from the above line?

---

