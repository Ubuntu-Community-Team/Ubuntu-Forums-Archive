---
title: "sYSMALLOc AND gcc-4.1-base=4.1.2-21ubuntu1"
date: 2012-05-08
forum: General Help
---

### Post by superflexo on 2012-05-08
Hi everybody,
I have the following problem:
I need to use an old fortran programme (written by an other person)  which, even though can be successfully compiled, it gives me this message once running:
```
interpol_modeles: malloc.c:3096: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
```
I am running it on Ubuntu 10.10 .

Surprisingly it works perfectly on another computer with an original set-up of Ubuntu 8.04...although it is of course a programming problem (which I do not know how to solve...the programme has several lines and performs delicate calcs), I wonder if installing the 8.04 fortran compilers will fix the problem...I tried the following command:
```
sudo apt-get install gcc-4.1=4.1.2-21ubuntu1 gcc-4.1-base=4.1.2-21ubuntu1 cpp-4.1=4.1.2-21ubuntu1 g++-4.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cpp-4.1 is already the newest version.
gcc-4.1 is already the newest version.
gcc-4.1-base is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 g++-4.1 : Depends: gcc-4.1-base (= 4.1.2-27ubuntu1) but 4.1.2-21ubuntu1 is to be installed
           Depends: gcc-4.1 (= 4.1.2-27ubuntu1) but 4.1.2-21ubuntu1 is to be installed
           Depends: libstdc++6-4.1-dev (= 4.1.2-27ubuntu1) but it is not going to be installed
E: Broken packages
```
but I cannot force the installation of the 4.1.2-21ubuntu1 compilers version. Can anyone help me, please?
Thank you in advance,
Paolo

---

