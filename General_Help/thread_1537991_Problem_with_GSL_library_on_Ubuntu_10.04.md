---
title: "Problem with GSL library on Ubuntu 10.04"
date: 2010-07-24
forum: General Help
---

### Post by Steelie678 on 2010-07-24
Hello everyone!

I am currently having some problems during the compilation / linking of the CERN ROOT package related to the GNU scientific library.
When compiling the MathMore component of ROOT, I get the following error message:

```
/usr/bin/ld: /usr/lib64/libgslcblas.a(sgemm.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/lib64/libgslcblas.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [lib/libMathMore.so] Error 1
```

Is it possible, the GSL libraries in the package manager were compiled without the -fPIC flag? And if so, can one expect a fix for this?

Thank you very much,
Michael

---

