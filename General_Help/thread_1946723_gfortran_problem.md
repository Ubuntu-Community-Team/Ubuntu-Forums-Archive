---
title: "gfortran problem"
date: 2012-03-25
forum: General Help
---

### Post by pulsarmnj on 2012-03-25
Hi,

I am using Ubuntu 10.04.2 LTS. I am trying to call a fortran function (say fortranfunction.f) from a C++ code say cprog.c.
In my c code, I have defined the fortran function prototype as 
===
 extern "C"
{
  double fortranfunction_(double, double );
 } 
==
then calling it from main as :
int main() {
 double x,y,z;
 .............
.........
   z=fortranfunction_(x, y);
.......
......
 return(0);
}
==============
Now I am compiling this as :
    gfortran -c fortranfunction.f
g++ -o cprog cprog.c fortranfunction.o -lm
==========
And I am getting lots of error messages as :

fortranfunction.o: In function `indexx_':
fortranfunction.f:(.text+0xd8b): undefined reference to `_gfortran_stop_string'
fortranfunction.o: In function `trapzd_':
fortranfunction.f:(.text+0xfda): undefined reference to `_gfortran_pow_i4_i4'
collect2: ld returned 1 exit status
========
trapzd and indexx are two fortran subroutines in fortranfunction.f. There are few other subroutines and functions in my fortran porgramme.
Earlier, when I was calling this fortran function from another fortran function, I did not have any problem.

Can anyone please help me ?

---

### Post by davea88 on 2012-03-25
The traditional reason for this is that g++ does not
know about the gfortran support libraries so it does
not link against them.   But the compiler assumes,
when you compile the fortran source, that you will link
against the gfortran libs.

So if you figure out what -l<something> you need to add
by hand(?) on the link line
it will get you closer to working.

It can be tricky as both fortran and C++ have 
startup and library code they need  --  but not necessarily
the same startup or library code.

This note based on knowledge of Fortran compilers
generally, not specifically gfortran. Sorry.

---

### Post by pulsarmnj on 2012-03-25
Thanks davea88,

I have already figured out by trial and error method. I need to use gfrotran instead of g++ even in the second step.
gfortran can actually compile any c prog (atleast the few I have tried), independent of whether any fortran code is related or not.

Thanks again.

---

