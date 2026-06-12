---
title: "using LAPACK and levmar (nonlinear regression)"
date: 2010-08-25
forum: General Help
---

### Post by ubun_tut on 2010-08-25
hi,

i am trying to run the levmar algorithm (found here [http://www.ics.forth.gr/~lourakis/levmar/index.html](http://www.ics.forth.gr/~lourakis/levmar/index.html)), which is a levenberg-marquardt nonlinear regression algorithm, on ubuntu 8.04. after downloading the package from the above website, i installed the packages liblapack3gf and liblapack-dev from the synaptic package manager, as levmar requires LAPACK to run.

and then, following instructions in the readme, i typed 'make' at the terminal, and got the following error:

```

gcc   -O3 -funroll-loops -Wall    -c -o lm.o lm.c
gcc   -O3 -funroll-loops -Wall    -c -o Axb.o Axb.c
gcc   -O3 -funroll-loops -Wall    -c -o misc.o misc.c
gcc   -O3 -funroll-loops -Wall    -c -o lmlec.o lmlec.c
gcc   -O3 -funroll-loops -Wall    -c -o lmbc.o lmbc.c
gcc   -O3 -funroll-loops -Wall    -c -o lmblec.o lmblec.c
gcc   -O3 -funroll-loops -Wall    -c -o lmbleic.o lmbleic.c
ar crv liblevmar.a lm.o Axb.o misc.o lmlec.o lmbc.o lmblec.o lmbleic.o
a - lm.o
a - Axb.o
a - misc.o
a - lmlec.o
a - lmbc.o
a - lmblec.o
a - lmbleic.o
ranlib liblevmar.a
gcc   -O3 -funroll-loops -Wall    -c -o lmdemo.o lmdemo.c
gcc -L/usr/local/lib  -L. lmdemo.o -o lmdemo -llevmar -llapack -lblas -lf2c  -lm
/usr/bin/ld: cannot find -lf2c
collect2: ld returned 1 exit status
make: *** [lmdemo] Error 1

```

does anyone know how i can go about solving this? this error is actually mentioned in the Makefile, but i am not sure if the LAPACK i installed is fortran or f2c'ed.

thanks in advance.

---

