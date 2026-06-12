---
title: "Compiling program from source problem"
date: 2006-02-24
forum: General Help
---

### Post by jofre on 2006-02-24
Hi lads, 

I am trying to compile Scilab. In the Readme file, says to run ./configure.
This gives my an error: 

checking for X... no
configure: error: X Window not found

the instrucctions says that it needs X11R4, X11R5 or X11R6. 
But X11R6 is intalle in my Breeze!

Any ideas? I guess is something to do with paths, but I don't know how to change this:( 

Thanks a million, Jofre

---

### Post by LordBug on 2006-02-24
You have the *binaries* of X installed, but not the *development* files.  Look for X11-dev or something similar in Synaptic (at work, no Synaptic).  You'll probably need more than this as well.

---

### Post by linear on 2006-02-24
Might be: **libx11-dev**

---

### Post by jofre on 2006-02-24
Thanks Lordbug.

I had to install: libx11-dev (and xlibs-dev got automatically selected as well...)

Lordbug was right, I have to install more packages, but just by installing "complaining-package-dev" did the job.

A step forward to have the whole computer from source :D 

Thanks a million both of you, Jofre.

---

