---
title: "How to install Caph"
date: 2010-11-22
forum: General Help
---

### Post by keithclark on 2010-11-22
Anyone have step by step instructions on how to install Caph?  I cannot find a package in the repos and I'm not familiar with compiling my own software.  I downloaded it from their own website, and tried to follow the directions, but the required libraries are also not available in the repos.

Here are the directions:

Make sure that you have installed following packages,

libSDL
libpng
OpenGL	(optional)

If you do not want compile Caph with OpenGL comment out appropriate line in
'confg' script.

After, go to the 'src' directory and perform,

$ ./confg
$ ./build

I tried to install the first 'libSDL' via synaptic and it said it could not be found.

Keith

---

### Post by sanderd17 on 2010-11-22
for libdsl, try the package with the name "libdsl1.2-all" and check if you get further.

---

### Post by keithclark on 2010-11-22
> **sanderd17 said:**
> for libdsl, try the package with the name "libdsl1.2-all" and check if you get further.

Nope.  I installed 'libsdl-1.2-all' and synaptic installed 'libsdl-1.2-debian'.

Installation still goes as follows:

keithclark@HP1211N:~/Games/caph-1.1/src$ ./confg
confg: libSDL is required
keithclark@HP1211N:~/Games/caph-1.1/src$

---

