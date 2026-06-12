---
title: "questions about some basics (TeXLive and fortran)"
date: 2010-04-21
forum: General Help
---

### Post by elquin on 2010-04-21
Hi, all.
I just started to use Ubuntu with the last one, 9.10.
As a begineer, I'm in struggling with several problems as;

1. I installed TeXLive 2009.
I already used MikTeX in my window-based laptop.
How can I compile my tex document in Ubuntu?

2. Also, I just installed gfortran and lapack.
This is the main reason why I choose ubuntu.
I used fortran of computing server in my university, which is based on Intel fortran.
To make sample run with my ubuntu machine, it's little hard.
My test 'makefile' is shown as;
---------------------------------------------------
# Makefile
# Directory object:
MYDIR = /home/...

OBJS1 = ...
LIB   = -L /usr/share/man/man3/ -lmkl_lapack -lguide -lpthread
#libguide.a      libmkl_ias.so       libmkl_mc.so     libmkl_vml_def.so
#libguide.so     libmkl_lapack32.so  libmkl_p4n.so    libmkl_vml_mc.so
#libmkl_def.so   libmkl_lapack64.so  libmkl.so        libmkl_vml_p4n.so
#libmkl_em64t.a  libmkl_lapack.a     libmkl_solver.a  libvml.so

CENTRAL = ...
----------------------------------------------------

And the results are ;
---------------------------------------
gfortran -O3  -o myexe_...   -L /usr/share/man/man3/ -lmkl_lapack -lguide -lpthread 
/usr/bin/ld: cannot find -lmkl_lapack
/usr/bin/ld: cannot find -lmkl_lapack
collect2: ld returned 1 exit status
make: *** [myexe_tmp] Error 1
------------------------------

I installed lapack from 'Synaptic Package Manager'.
Maybe it comes from the wrong LIB.
How can I fix it?

Thanks,

---

