---
title: "Fortran Compilers"
date: 2010-06-14
forum: General Help
---

### Post by tjb891 on 2010-06-14
I am trying to run some rather old Fortran Code and I have an issue with the gfortran and the Intel Fortran Compiler. Can anyone suggest any other free compilers to try?

---

### Post by beren.olvar on 2010-06-14
Intel has a very good fortran compiler, which is free for non-comercial use.
Check it out here: 
[http://software.intel.com/en-us/articles/non-commercial-software-download/](http://software.intel.com/en-us/articles/non-commercial-software-download/)

---

### Post by towheedm on 2010-06-14
gcc says it can compile Fortran.

---

### Post by JKyleOKC on 2010-06-14
> **tjb891 said:**
> I am trying to run some rather old FORTRAN Code and I have an issue with the gfortran and the Intel FORTRAN Compiler. Can anyone suggest any other free compilers to try?Depends on how old your FORTRAN code is! I know of at least three different varieties of FORTRAN, each incompatible with the other, and I suspect that most modern compilers are for the FORTRAN-77 version while your code may be the much older FORTRAN-2.

Best suggestion I can offer is to google not for just "FORTRAN" but for "FORTRAN-2" which should show any compilers that exist...

---

### Post by sdennie on 2010-06-14
If neither gcc or the Intel compiler will build it, you may have to port it to one of those compilers.  I don't know about the quality of either of those Fortran compilers but, I used to work in the compilers group of another major vendor and it was often the case that old Fortran code would often have to be ported to newer (where even F77 is new) compilers to work.

---

### Post by tjb891 on 2010-06-15
The code is from 1986 so I assume it is FORTRAN 77. When it is compiled on Microsoft Visual Studio or similar on a windows machine it is fine but when it is run on gcc or the intel Fortran compiler it gives memory errors when run on linux

---

