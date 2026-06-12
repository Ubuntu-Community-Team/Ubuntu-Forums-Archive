---
title: "installing GSL -- cannot find libgsl.a"
date: 2010-07-14
forum: General Help
---

### Post by ppowell271 on 2010-07-14
I am trying to use the GSL library (a numerical computing library for C/C++) and am using Eclipse.  I believe the library installation to have worked, but when I try to build my source code I get the following error message:

**** Build of configuration Debug for project SpecFunc ****

make all 
Building target: SpecFunc
Invoking: GCC C++ Linker
g++ -L/usr/local/lib -o"SpecFunc"  ./src/specfun.o   -l/usr/local/lib/libgsl.a -l/usr/local/lib/libgslcblas.a
/usr/bin/ld: cannot find -l/usr/local/lib/libgsl.a
collect2: ld returned 1 exit status
make: *** [SpecFunc] Error 1


I have given the path for the library file in the "Paths and Symbols" part of my project's properties, and if I open a file browser I can see libgsl.a (and libgslcblas.a, for that matter) right where it should be, so I don't understand the problem.

Any help is greatly appreciated!

---

