---
title: "cannot compile .f (fortran) program"
date: 2010-10-12
forum: General Help
---

### Post by ubun_tut on 2010-10-12
Hi,

I have a fortran program that I am trying to compile. when I use the command

```


gfortran marge.f


```

I get this whole list of errors below.

```


marge.f:61.11:

     *  ST1=ST+1,ST2=ST+ST,SE=SD+2,SF=SU+SU+SU+SU+2)                    
          1
Error: Parameter 'sust1' at (1) has not been declared or is a variable, which does not reduce to a constant expression
marge.f:67.21:

       PARAMETER(SAa=SA,SSs=SS,SUu=SU,SDd=SD,S11=S1,SEe=SE)             
                    1
Error: Parameter 'sa' at (1) has not been declared or is a variable, which does not reduce to a constant expression
marge.f:104.19:

       WRITE (*,*) 'for axisymmetric, randomly-oriented, homogeneous par
                  1
Error: Unterminated character constant beginning at (1)
marge.f:157.19:

       WRITE (*,*) 'Please refer to subroutine TNATURAL for more informa
                  1
Error: Unterminated character constant beginning at (1)
marge.f:159.19:

       WRITE (*,*) 'Enter value for KReq (Re=equal-volume-sphere radius)
                  1
Error: Unterminated character constant beginning at (1)
marge.f:162.19:

       WRITE (*,*) 'Please refer to subroutine TNATURAL for more informa
                  1
Error: Unterminated character constant beginning at (1)
marge.f:252.72:

        BX1(N,N1+1,M+N2MAX+1)=BX1(N,N1+1,M+N2MAX+1)+CGN(M-IAM1+1)*AX1(N,
                                                                       1
Error: Expected array subscript at (1)
marge.f:253.72:

        BX2(N,N1+1,M+N2MAX+1)=BX2(N,N1+1,M+N2MAX+1)+CGN(M-IAM1+1)*AX2(N,
                                                                       1
Error: Expected array subscript at (1)
marge.f:266.72:

         if(BX1(N,N1+1,M+N2MAX+1).ne.0.and.BX1(NSO,N1+1,M+N2MAX+1).ne.0)
                                                                       1
Error: Cannot assign to a named constant at (1)
marge.f:269.12:

         end if                                                         
           1
Error: Expecting END DO statement at (1)
marge.f:270.72:

         if(BX2(N,N1+1,M+N2MAX+1).ne.0.and.BX2(NSO,N1+1,M+N2MAX+1).ne.0)
                                                                       1
Error: Cannot assign to a named constant at (1)
marge.f:273.12:

         end if                                                         
           1
Error: Expecting END DO statement at (1)
marge.f:281.72:

        if(BX1(N,N1+1,M+N2MAX+1).ne.0.and.BX1(NSO,N1+1,2-M+N2MAX+1).ne.0
                                                                       1
Error: Syntax error in IF-expression at (1)
marge.f:284.11:

        end if                                                          
          1
Error: Expecting END DO statement at (1)
marge.f:500.19:

       WRITE (*,*) 'Want Mueller matrix data stored in file? (1=yes, 0=n
                  1
Error: Unterminated character constant beginning at (1)
marge.f:510.19:

       WRITE (*,*) 'Mueller matrix elements stored on files mm1.dat, mm2
                  1
Error: Unterminated character constant beginning at (1)
marge.f:84.29:

       complex*16 G3(SDd),G4(SDd),G5(SDd)                               
                            1
Error: Variable 'sdd' cannot appear in the expression at (1)
marge.f:84.33:

       complex*16 G3(SDd),G4(SDd),G5(SDd)                               
                                1
Error: The module or main program array 'g4' at (1) must have constant shape
marge.f:76.17:

       real*8 A1(SAa),A2(SAa),A3(SAa),A4(SAa),B1(SAa),B2(SAa),ANG(SAa)  
                1
Error: Variable 'saa' cannot appear in the expression at (1)
marge.f:76.21:

       real*8 A1(SAa),A2(SAa),A3(SAa),A4(SAa),B1(SAa),B2(SAa),ANG(SAa)  
                    1
Error: The module or main program array 'a1' at (1) must have constant shape
marge.f:75.36:

       real*8 AE1(SAa),AE2(SAa),AE3(SAa),AE4(SAa),BE1(SAa),BE2(SAa)     
                                   1
Error: Variable 'saa' cannot appear in the expression at (1)
marge.f:75.40:

       real*8 AE1(SAa),AE2(SAa),AE3(SAa),AE4(SAa),BE1(SAa),BE2(SAa)     
                                       1
Error: The module or main program array 'ae3' at (1) must have constant shape
marge.f:75.18:

       real*8 AE1(SAa),AE2(SAa),AE3(SAa),AE4(SAa),BE1(SAa),BE2(SAa)     
                 1
Error: Variable 'saa' cannot appear in the expression at (1)
marge.f:75.22:

       real*8 AE1(SAa),AE2(SAa),AE3(SAa),AE4(SAa),BE1(SAa),BE2(SAa)     
                     1
Error: The module or main program array 'ae1' at (1) must have constant shape
marge.f:76.41:

       real*8 A1(SAa),A2(SAa),A3(SAa),A4(SAa),B1(SAa),B2(SAa),ANG(SAa)  
                                        1
Error: Variable 'saa' cannot appear in the expression at (1)
Fatal Error: Error count reached limit of 25.


```

I think it is a problem with finding the right commands to compile it. I referred to this post [http://ubuntuforums.org/showthread.php?t=1164769](http://ubuntuforums.org/showthread.php?t=1164769) and tried out the command that is suggested there (gfortran -ffree-form -o), and get a whole new list of errors.

```


marge.f:1:

C ARTURO QUIRANTES SIERRA
1
Error: Unclassifiable statement at (1)
marge.f:2:

C Department of Applied Physics, Faculty of Sciences
1
Error: Unclassifiable statement at (1)
marge.f:3:

C University of Granada, 18071 Granada (SPAIN)
1
Error: Unclassifiable statement at (1)
marge.f:4:

C http://www.ugr.es/local/aquiran/codigos.htm
1
Error: Unclassifiable statement at (1)
marge.f:5:

C aquiran@ugr.es
1
Error: Unclassifiable statement at (1)
marge.f:6:

C
1
Error: Unclassifiable statement at (1)
marge.f:7:

C Last update: 20 september 2007
1
Error: Unclassifiable statement at (1)
marge.f:8:

C 
1
Error: Unclassifiable statement at (1)
marge.f:9:

C This is MARGE, a computer code to calculate light-scattering properties
1
Error: Unclassifiable statement at (1)
marge.f:10:

C for randomly-oriented, homogeneous nonspherical scatterers
1
Error: Unclassifiable statement at (1)
marge.f:11:

C It is based on a T-matrix code, combined with Mishchenko's
1
Error: Unclassifiable statement at (1)
marge.f:12:

C orientation averaging scheme: JOSA A 8, 871-882 (1991)
1
Error: Unclassifiable statement at (1)
marge.f:13:

C
1
Error: Unclassifiable statement at (1)
marge.f:14:

C This code is made available on the following conditions:
1
Error: Unclassifiable statement at (1)
marge.f:15:

C
1
Error: Unclassifiable statement at (1)
marge.f:16:

C - You can use and modify it, as long as acknowledgment is given
1
Error: Unclassifiable statement at (1)
marge.f:17:

C   to the author (that's me).  I'd appreciate a reprint or e-copy
1
Error: Unclassifiable statement at (1)
marge.f:18:

C   of any paper where my code has been used.
1
Error: Unclassifiable statement at (1)
marge.f:19:

C
1
Error: Unclassifiable statement at (1)
marge.f:20:

C - You can not sell it or use it in any way to get money out of it
1
Error: Unclassifiable statement at (1)
marge.f:21:

C   (save for the research grants you might get thanks to it :)
1
Error: Unclassifiable statement at (1)
marge.f:22:

C
1
Error: Unclassifiable statement at (1)
marge.f:23:

C - I'm making this code available to the best of my knowledge.
1
Error: Unclassifiable statement at (1)
marge.f:24:

C   It has been tested as throughly as possible, but bugs may remain
1
Error: Unclassifiable statement at (1)
marge.f:25:

C   and overflow errors, particularly for large sizes and/or extreme
1
Error: Unclassifiable statement at (1)
Fatal Error: Error count reached limit of 25.


```

Can someone pls tell me how I can properly compile it? This program is publicly available at [http://www.ugr.es/~aquiran/codigos.htm;](http://www.ugr.es/~aquiran/codigos.htm;) it’s the one called ‘Marge’.

Thanks!

---

### Post by anglican on 2010-10-12
> **ubun_tut said:**
> Hi,

I have a fortran program that I am trying to compile. when I use the command

Try:
```
sudo apt-get install fort77
f77 marge.f
```

H

---

### Post by ubun_tut on 2010-10-12
hey that worked like magic! thanks!

how does it work? isn't gfortran supposed to compile anything written in 77, 90 or 95?

---

### Post by eveningsky339 on 2010-10-12
> **ubun_tut said:**
> hey that worked like magic! thanks!

how does it work? isn't gfortran supposed to compile anything written in 77, 90 or 95?

From Wikipedia:

 > gfortran has replaced the *g77* compiler, which stopped development before GCC version 4.0. It includes support for the [Fortran 95]("http://en.wikipedia.org/wiki/Fortran#Fortran_95") language and is compatible with *most* language extensions supported by g77[[1]]("http://en.wikipedia.org/wiki/Gfortran#cite_note-gcc_ml_2007-01-0"), allowing it to serve as a drop-in replacement in many cases.

---

### Post by ubun_tut on 2010-10-12
does this mean that the code i am trying to compile is one of those few exceptions that gfortran cant compile? sorry but i have never used fortran before...

---

### Post by anglican on 2010-10-13
> **ubun_tut said:**
> does this mean that the code i am trying to compile is one of those few exceptions that gfortran cant compile? sorry but i have never used fortran before...No, it just means you need to find the right compile options for gfortran... which are (trumpet roll):
```
gfortran -ffixed-line-length-0 -std=legacy marge.f
```

H

---

