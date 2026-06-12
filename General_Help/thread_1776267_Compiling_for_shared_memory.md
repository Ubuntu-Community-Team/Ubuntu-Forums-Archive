---
title: "Compiling for shared memory"
date: 2011-06-05
forum: General Help
---

### Post by salmontres on 2011-06-05
Hi guys,

I'm trying to compile a program for shared memory. (Multiple cores on one machine.) Now, this program requires both the PGI Fortran compiler, and the GNU C compiler. Most of the parallel code is in Fortran. So, when using my OpenMP library, should I specify the library from PGI (to take care of the Fortran)? Or, should I load both OpenMP libraries (PGI and GNU)libraries, although I'm pretty sure this is going to crash quickly.

(For anyone interested, I'm trying to compile WRF 3.2.1.)

Any help would be greatly appreciated!

---

### Post by salmontres on 2011-06-06
I just wanted to mention that I did try using both OpenMP libraries, and it did fail rather quickly. If anyone has any suggestions to try or documents to read, I'm more than happy to try anything right now.

---

