---
title: "g77 not available for Ubuntu 10.04 / program build"
date: 2010-06-21
forum: General Help
---

### Post by arctica1963 on 2010-06-21
Hello

I have a program that should be possible to compile under Linux, but when I went to run make, it could not find g77 (fortran compiler); using Ubuntu 10.04. The gnu C++ compiler is there (gcc). It looks like g77 was available for earlier Ubuntu versions but not part of the present setup.

I did a search for the g77 compiler and tried to install that, but it was not compatible with Ubuntu 10.04; is there a way around this issue?

I have attached the original tar file for help. The program uses GMT and computes slices through the Earth's mantle based on velocity variations and using a data file of spherical harmonics I believe.

Thanks for any help.

Cheers

Lester

---

### Post by roncrump on 2010-06-21
> **arctica1963 said:**
> Hello

I have a program that should be possible to compile under Linux, but when I went to run make, it could not find g77 (fortran compiler); using Ubuntu 10.04. The gnu C++ compiler is there (gcc). It looks like g77 was available for earlier Ubuntu versions but not part of the present setup.

... is there a way around this issue?


Use the gfortran compiler instead of g77 (gfortran is the FORTRAN90 compiler that is part of the gcc suite - is it wasn't installed with gcc search for it in synaptic).

FORTRAN90 compilers will compile FORTRAN77 code unless there are extensions to the standard that are not known to the F90 compiler. Assuming the program was previously compiled by someone with g77 I would think gfortran would know about any non-standard FORTRAN used by it.

Ron.

---

### Post by arctica1963 on 2010-06-21
Hi Ron

Yes I found the gfortran :) The makefile I have (one of a few) has the following:

FFc = g77 -c -fno-silent -ffixed-line-length-none -Wno-globals -fno-automatic -finit-local-zero
MAKE = make
LIBDIR = ..

.f.a:
    ${FFc}  $<
    ar rv $@ $*.o
    rm -f $*.o
                                                                                
$(LIBDIR)/libS20.a: \
    $(LIBDIR)/libS20.a(addata.o) \
    $(LIBDIR)/libS20.a(convpack.o) \
    $(LIBDIR)/libS20.a(dcopy.o) \
    $(LIBDIR)/libS20.a(scopy.o) \
    $(LIBDIR)/libS20.a(dot.o) \
    $(LIBDIR)/libS20.a(getfdp.o) \
    $(LIBDIR)/libS20.a(integ.o) \
    $(LIBDIR)/libS20.a(istlen.o) \
    $(LIBDIR)/libS20.a(inittrf.o) \
    $(LIBDIR)/libS20.a(legndr.o) \
    $(LIBDIR)/libS20.a(modtrf.o) \
    $(LIBDIR)/libS20.a(rmod.o) \
    $(LIBDIR)/libS20.a(saxpy.o) \
    $(LIBDIR)/libS20.a(sdot.o) \
    $(LIBDIR)/libS20.a(splh.o) \
    $(LIBDIR)/libS20.a(strgrep.o) \
    $(LIBDIR)/libS20.a(rsphhead.o) \
    $(LIBDIR)/libS20.a(rsple.o) \
    $(LIBDIR)/libS20.a(rspln.o) \
    $(LIBDIR)/libS20.a(splhsetup.o) \
    $(LIBDIR)/libS20.a(wsphhead.o) \
    $(LIBDIR)/libS20.a(wspthead.o) \
    $(LIBDIR)/libS20.a(wint2ch.o) \
    $(LIBDIR)/libS20.a(ylm.o)

    ranlib $(LIBDIR)/libS20.a

I guess I just need to change the reference to g77 to gfortran and check the options.

Been trying to get this things working for a while both on Linux and Sun without much luck, but it should compile.

Cheers

Lester


> **roncrump said:**
> Use the gfortran compiler instead of g77 (gfortran is the FORTRAN90 compiler that is part of the gcc suite - is it wasn't installed with gcc search for it in synaptic).

FORTRAN90 compilers will compile FORTRAN77 code unless there are extensions to the standard that are not known to the F90 compiler. Assuming the program was previously compiled by someone with g77 I would think gfortran would know about any non-standard FORTRAN used by it.

Ron.

---

### Post by arctica1963 on 2010-06-23
Hi Ron

Managed to build the library file by changing a few bits (g77 to gfortran) and that seemed to work although it threw up some warnings.

Building the main app with make all still a non-starter.

Cheers

Lester

> **roncrump said:**
> Use the gfortran compiler instead of g77 (gfortran is the FORTRAN90 compiler that is part of the gcc suite - is it wasn't installed with gcc search for it in synaptic).

FORTRAN90 compilers will compile FORTRAN77 code unless there are extensions to the standard that are not known to the F90 compiler. Assuming the program was previously compiled by someone with g77 I would think gfortran would know about any non-standard FORTRAN used by it.

Ron.

---

### Post by malaw_glenn on 2010-06-30
That is strange, I installed g77 using synaptic package manager on my 10.04

---

