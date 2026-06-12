---
title: "fortran compilation error"
date: 2010-10-16
forum: General Help
---

### Post by jvsingh on 2010-10-16
Dear Friends,

I have successfully compiled and running TINKER molecular modeling source code on Ubuntu 10.04 LTS ( Dell D610 laptop). Next, I have been trying to compile an in house code (piscf.f) which uses the subroutines in the TINKER source code. Therefore, when i compile piscf.f using command line as :

gfortran -ffixed-line-length-0 -std=legacy piscf.f 

I get the following errors. 

/tmp/cc3XBXfK.o: In function `piscf_':
piscf.f.(text+0xe47): undefined reference to `overlap_'
piscf.f.(text+0xe6f): undefined reference to `overlap_'
piscf.f.(text+0x147a): undefined reference to `jacobi_'
piscf.f.(text+0x3db9): undefined reference to `jacobi_'
piscf.f.(text+0x3dfd): undefined reference to `jacobi_'
/tmp/cc3XBXfK.o: In function `pitilt_':
piscf.f.(text+0x5ed5): undefined reference to `overlap_'
/usr/lib/gcc/i486-linux-gnu/4.4.3/libgfortranbegin.a(fmain.o): In function `main':
(.text+0x27): undefined reference to `MAIN__'
collect2: ld returned 1 exit status

###########################################

When I use : gfortran -o3 -ffree-form piscf.f 
I get following errors: 

piscf.f:1:

c
1
Error: Unclassifiable statement at (1)
piscf.f:2:

c
1
Error: Unclassifiable statement at (1)
piscf.f:3:

###########################################

If I simply type : f77 piscf.f  I get the following errors:

piscf:
   pitilt:
   pimove:
   pialter:
piscf.o: In function `piscf_':
fort77-3447-1.c.(text+0xc85): undefined reference to `overlap_'
fort77-3447-1.c.(text+0xca9): undefined reference to `overlap_'
fort77-3447-1.c.(text+0x1165): undefined reference to `jacobi_'
fort77-3447-1.c.(text+0x308c): undefined reference to `jacobi_'
fort77-3447-1.c.(text+0x30c: undefined reference to `jacobi_'
piscf.o: In function `pitilt_':
fort77-3447-1.c.text+0x4b17): undefined reference to `overlap_'
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libf2c.so: undefined reference to `MAIN__'
collect2: ld returned 1 exit status


Any hint/suggestion will be great. Thanks.:P
Jay krishna Singh
University of Houston

---

### Post by KirbySmith on 2010-10-17
A hint is the best I can do, never having run gfortran, only Digital Fortran and Absoft Fortran, and those some time ago.  However, I was reading the on-line notes for gfortran recently and was left with the impression, possibly mistaken, that it could do free form or fixed form, but not a mixture of both.  It may be necessary to compile the modules separately using the appropriate switches and then make the executable from the resulting object files.

kirby

---

