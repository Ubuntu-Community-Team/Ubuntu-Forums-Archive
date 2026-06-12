---
title: "Installing garfield to Ubuntu 10.04 Lucid Lynx - gfortran"
date: 2010-12-03
forum: General Help
---

### Post by Cenko on 2010-12-03
After struggling for a while, I managed to install garfield (With important help of dinofelis) and decided to share my experince on compiling garfield on Ubuntu 10.04.
 
For information of garfield: [http://garfield.web.cern.ch/garfield/](http://garfield.web.cern.ch/garfield/)
 
If you don't have it yet, install gfortran
 
```
sudo apt-get install gfortran
```
 
install cernlib,libgsl from repositories
 
```
sudo apt-get install cernlib libgsl0-dev nypatchy
```
 
Create a directory (lets say /home/username/garfield/) and copy all necessary files from website to this directory:
 
```
garfield-7.car
garfadd-9.cra
garfield-9.cra
garfield.hlp
heed101garf.car
magboltz-7.car
patchy_step (It is defined as "Script to run Patchy" in the website)
```
 
(If you want another version of garfield you should download the corresponding .cra files.
 
Get NeBem from either its website, or the afs folders:
 
```
/afs/cern.ch/user/r/rjd/Garfield/Files/neBEM/V1.7e
```
 
For ease, copy this folder directly to your working folder as
 
```
./neBEM/V1.7e/
```
 
Now the essential thing: Normaly program is written to be compiled in g77, when you use gfortran, you get an error like:
 
```
undefined reference to `iargc_'
```
 
In gfortran, instead of iargc_() there is _gfortran_iargc() function. So you need to make your compiler
recognize iargc_() as _gfortran_iargc(). To do this paste this little code into a file named 

```
gfortran_iargc.c
```

and save it somewhere in your working directory, for example: ./extras/iarg.d/gfortran_iargc.c
 
```

extern int _gfortran_iargc(void);
int iargc_()
{
return _gfortran_iargc();
}

```
 
go to this directory and compile the code as:

```
gfortran -c _gfortran_iargc.c 
``` 
        
It will create the file "_gfortran_iargc.o".  Note that in the makefile you'll need to set variable $DUMMYIARGCOBJ
to the location of this file.(see: makefile)
        
Now you are ready to compile garfield, you can use a sample makefile and modify your folder names. To compile simply write
        
```
make garfield-9
``` 
        
The sample makefile is attached. YOu should change the name to makefile after downloading

---

### Post by flueke on 2010-12-29
First of all, thanks for your post! The Makefile and especially the gfortran_iargc part are very helpful.

I'm currently trying to build garfield-9 on a 32-bit Ubuntu 10.10 system. All the fortran files compile fine but at the final linking stage I run into this error:

```

gfortran  -o ~/garfield/garfield-9/bin/garfield-9 *.o ~/garfield/garfield-9/extras/gfortran_iargc.o \
        ./neBEM/V1.7.2/obj/GarfieldInterface.o ./neBEM/V1.7.2/obj/neBEMInterface.o \
        ./neBEM/V1.7.2/obj/ReTriM.o ./neBEM/V1.7.2/obj/ComputeProperties.o \
        ./neBEM/V1.7.2/obj/neBEM.o \
        -Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran -std=c99 \
        -Iinclude -L./neBEM/V1.7.2/lib \
        -lNR -lVector -lIsles  -L/usr/local/lib -lgslcblas -lgsl -lm -lgfortran
celcal.o: In function `celcal_':
celcal.f:(.text+0x17f5): undefined reference to `bemvoq_'
celspr.o: In function `celspr_':
celspr.f:(.text+0x1307): undefined reference to `bemvoq_'
celspr.f:(.text+0x2177): undefined reference to `bemvoq_'
celspr.f:(.text+0x2df6): undefined reference to `bemvoq_'
celspr.f:(.text+0x365e): undefined reference to `bemvoq_'
celspr.o:celspr.f:(.text+0x427e): more undefined references to `bemvoq_' follow
collect2: ld returned 1 exit status
make: *** [garfield-9] Error 1

```I'm not sure whether `bemvoq_` should be part of libneBEM or if the definition is just missing from garfield-7.car. **Note:** I was only able to get versions 1.7.1 and 1.7.2 of neBEM, not version 1.7e which you used to build garfield.

Any help or suggestions would be much appreciated.

---

### Post by igal on 2011-02-03
To install garfield on Ubuntu 10.04 LTS - the Lucid Lynx for a 64 bit machine some minor modifications have to be applied to Cenk's installation method

1/ install all lib32 via synaptic or *sudo apt*-*get install* ia32-libs

2/ some other libraries have to be added (I copied it from my 32bit desktop which is also working with Lucid Lynx)

libgraflib.a
libgraflib.so.1_gfortran.2006
libgraflib.so.1_gfortran
libgraflib.so
libkernlib.a
libkernlib.so.1_gfortran.2006
libkernlib.so.1_gfortran
libkernlib.so
libmathlib.a
libmathlib.so.2_gfortran.2006
libmathlib.so.2_gfortran
libmathlib.so
libpacklib1-gfortran
libpacklib.so.1_gfortran.2006
libpacklib.so.1_gfortran -> libpacklib.so.1_gfortran.2006
libpacklib.so -> libpacklib.so.1_gfortran.2006
libpacklib-lesstif.so.1_gfortran.2006
libpacklib-lesstif.so.1_gfortran -> libpacklib-lesstif.so.1_gfortran.2006
libpacklib-lesstif.so -> libpacklib-lesstif.so.1_gfortran.2006
libpacklib-lesstif.a
libpacklib.a
libgrafX11.a
libgrafX11.so.1_gfortran.2006
libgrafX11.so.1_gfortran
libgrafX11.so
liblapack.a
liblapackgf-3.a
liblapackgf-3.so
liblapack.so
liblapack.so.3gf.0
liblapack.so.3gf
libblas.so.3gf.0
libblas.so.3gf
[LEFT]
[/LEFT]
3/ 
gfortran -c _gfortran_iargc.c becomes gfortran -m32 -c _gfortran_iargc.c

---

### Post by igal on 2011-02-03
4/ compile neBEM with -m32 flag

G77=gfortran -m32 # on more recent versions of linux

CFLAGS=-Wall -std=c99 -O3 -m32 # last option necessary for Garfield

5/ in neBEM/V1.7e/lib
cp libIsles32.a libIsles.a

6/ compile garfield with -m32 flag and forcing to read the lib32 by -L/usr/lib32

FC = gfortran -m32
#LF=-Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm \
#-lpacklib -lnsl -lcrypt -ldl -lgfortran
LF=-Wl,-static -L/usr/lib32 -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm \
-lpacklib -lnsl -lcrypt -ldl -lgfortran

---

### Post by psyentist88 on 2011-02-10
I am trying to install Garfield on a 64 bit Ubuntu 10.10 recently, but so far without any succes.

Following Cenko's and igal's advices, I get this:

```
gfortran -m32  -o ~/garfield/bin//garfield-9 *.o ~/garfield//extras/iarg.d/gfortran_iargc.o \
    ./neBEM/V1.7.2/obj/GarfieldInterface.o ./neBEM/V1.7.2/obj/neBEMInterface.o \
    ./neBEM/V1.7.2/obj/ReTriM.o ./neBEM/V1.7.2/obj/ComputeProperties.o \
    ./neBEM/V1.7.2/obj/neBEM.o \
    -Wl,-static -L/usr/lib32 -lgraflib -lgrafX11 -lmathlib -Wl, -dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran -std=c99 \
    -Iinclude -L./neBEM/V1.7.2/lib \
    -lNR -lVector -lIsles  -L/usr/local/lib -lgslcblas -lgsl -lm -lgfortran
/usr/bin/ld: cannot find : No such file or directory
/usr/lib32/libX11.a(CrGlCur.o): In function `open_library':
(.text+0x3b): warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/bin/ld: cannot find -lgcc_s
/usr/lib/gcc/x86_64-linux-gnu/4.4.5/32/libgfortran.a(getlog.o): In function `_gfortran_getlog':
(.text+0x32): warning: Using 'getpwuid' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib32/libX11.a(xim_trans.o): In function `_XimXTransSocketUNIXConnect':
(.text+0xe23): warning: Using 'getaddrinfo' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
make: *** [garfield-9] Error 1
```By the way /usr/bin/ld exists. Does anyone have a clue what is wrong?

BTW I have put a 32 bit Ubuntu 10.10 on VirtualBox just in order to install Garfield. With the above mentioned method, it works for me too.

---

### Post by h010410225 on 2011-05-13
thanks for the post, i have a problem here, 
huang_sun@huang:~/garfield$ make garfield-9
rm *.f *.o
rm: &#26080;&#27861;&#21024;&#38500;"*.f": &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405; (can't delete '*.f',no such file or dir)
rm: &#26080;&#27861;&#21024;&#38500;"*.o": &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
make: [garfield-9.f] &#38169;&#35823; 1 (&#24573;&#30053;)   (err 1, ignor)
./patchy_step garfield-9

 Nypatchy executing with files / options
.........
 73  + +USE,P=SIGNAL,D=SIGADM,T=I.
    74  + +USE,P=SIGNAL,D=SIGFLS,T=I.
    75  + +USE,P=SIGNAL,D=SIGWRT,T=I.

    76  + +PAM,LUN=11,T=a,C. garfield-7.car

 ***!!! OPEN fails for file: garfield-7.car
 Perror has: Illegal seek

 ***!!! Kill the run for: OPEN failure !!!***
: not foundep: 3: 
make: *** [garfield-9.f] &#38169;&#35823; 127       (err 127)
,

could anyeone give me some help

---

### Post by yankang on 2011-06-26
Thanks to you all. The discussion is very helpful. But i have a problem. Just like     [h010410225:]("http://ubuntuforums.org/search.php?do=finduser&u=1299969")

[yanqiang@localhost garfield]$ make garfield-9
rm *.f *.o
rm: cannot remove `*.f': No such file or directory
rm: cannot remove `*.o': No such file or directory
make: [garfield-9.f] Error 1 (ignored)
./patchy_step garfield-9
./patchy_step: line 1: nypatchy: command not found
make: *** [garfield-9.f] Error 127

what this message means? I have checked the content of  patchy_step, it only have two lines:          nypatchy - $1 $1 - - - - - - - - - :GO 
                 # less y.lis
What the command nypatchy means? 
Any help will be most welcomed!!

---

### Post by Cenko on 2011-06-27
> What the command nypatchy means?
Any help will be most welcomed!! 

Sorry for not including that, it is part of CERNLIB, that you can download from ubuntu repositories.I'm adding it to main post. You can simply install it as follows before compiling garfield:

```
sudo apt-get install nypatchy
```

---

### Post by yankang on 2011-06-27
Thank you very much, Cenko! This problem has been solved by using your method. And another command fcaplit could be solved in the same way. Thank you !! Best wishes!!

---

### Post by yankang on 2011-06-30
Dear all, thank you for your post&#65281;After some problems were solved, more problems occured. Now a problem I encountered is about libpacklib.a. When the gfortran tried to link the program, an error appeared  like this:

........
dzbkhd.F:(.text+0x1fb): undefined reference to `do_fio'
/home/yanqiang/cern/2006/lib/libpacklib.a(dzbkhd.o):dzbkhd.F:(.text+0x24d): more undefined references to `do_fio' follow
/home/yanqiang/cern/2006/lib/libpacklib.a(dzbkhd.o): In function `dzbkhd_':
dzbkhd.F:(.text+0x3e6): undefined reference to `e_wsfi'
dzbkhd.F:(.text+0x429): undefined reference to `s_copy'
/home/yanqiang/cern/2006/lib/libpacklib.a(dziopr.o): In function `dziopr_':
dziopr.F:(.text+0x1a): undefined reference to `s_copy'
dziopr.F:(.text+0x2d): undefined reference to `s_copy'
dziopr.F:(.text+0xa7): undefined reference to `s_wsfi'
dziopr.F:(.text+0xbb): undefined reference to `do_fio'
dziopr.F:(.text+0xcf): undefined reference to `do_fio'
dziopr.F:(.text+0xe3): undefined reference to `do_fio'
dziopr.F:(.text+0x105): undefined reference to `do_fio'
dziopr.F:(.text+0x10a): undefined reference to `e_wsfi'
dziopr.F:(.text+0x164): undefined reference to `s_copy'
/home/yanqiang/cern/2006/lib/libpacklib.a(fzialn.o): In function `fzialn_':
fzialn.F:(.text+0x6a): undefined reference to `s_rsfe'
fzialn.F:(.text+0x8e): undefined reference to `do_fio'
fzialn.F:(.text+0xa3): undefined reference to `e_rsfe'
fzialn.F:(.text+0x1db): undefined reference to `s_rsfe'
fzialn.F:(.text+0x1fb): undefined reference to `do_fio'
fzialn.F:(.text+0x20c): undefined reference to `e_rsfe'
/home/yanqiang/cern/2006/lib/libpacklib.a(fzoaln.o): In function `fzoaln_':
fzoaln.F:(.text+0x81): undefined reference to `s_wsfe'
fzoaln.F:(.text+0xa1): undefined reference to `do_fio'
fzoaln.F:(.text+0xb2): undefined reference to `e_wsfe'
/home/yanqiang/cern/2006/lib/libpacklib.a(uh1toc.o): In function `uh1toc_':
uh1toc.F:(.text+0x49): undefined reference to `s_copy'
/home/yanqiang/cern/2006/lib/libpacklib.a(dziopd.o): In function `dziopd_':
dziopd.F:(.text+0x1b): undefined reference to `s_copy'
dziopd.F:(.text+0x2e): undefined reference to `s_copy'
dziopd.F:(.text+0xa4): undefined reference to `s_copy'
dziopd.F:(.text+0xe5): undefined reference to `s_copy'
/home/yanqiang/cern/2006/lib/libpacklib.a(dziopd.o):dziopd.F:(.text+0xfb): more undefined references to `s_copy' follow
/home/yanqiang/cern/2006/lib/libpacklib.a(dziopd.o): In function `dziopd_':
dziopd.F:(.text+0x288): undefined reference to `s_wsfi'
dziopd.F:(.text+0x29c): undefined reference to `do_fio'
dziopd.F:(.text+0x2c0): undefined reference to `do_fio'
dziopd.F:(.text+0x2d4): undefined reference to `do_fio'
dziopd.F:(.text+0x2d9): undefined reference to `e_wsfi'
dziopd.F:(.text+0x3cd): undefined reference to `s_copy'
dziopd.F:(.text+0x50e): undefined reference to `s_wsfi'
dziopd.F:(.text+0x52b): undefined reference to `do_fio'
dziopd.F:(.text+0x53f): undefined reference to `do_fio'
dziopd.F:(.text+0x544): undefined reference to `e_wsfi'
dziopd.F:(.text+0x596): undefined reference to `s_wsfi'
dziopd.F:(.text+0x5f0): undefined reference to `s_wsfi'
dziopd.F:(.text+0x64b): undefined reference to `s_wsfi'
dziopd.F:(.text+0x6b0): undefined reference to `s_wsfi'
dziopd.F:(.text+0x6c4): undefined reference to `do_fio'
dziopd.F:(.text+0x6c9): undefined reference to `e_wsfi'
dziopd.F:(.text+0x702): undefined reference to `s_wsfi'
........
collect2: ld returned 1 exit status
make: *** [garfield-9] Error 1

   Nearly every *.o file of libpacklib.a has this kind of  error. I have tried the cernlibs of version 2003 , following the guide from [http://www.icepp.s.u-tokyo.ac.jp/~nanjyo]("http://www.icepp.s.u-tokyo.ac.jp/%7Enanjyo") /html/garfield.html, and the  cernlibs of version 2006 compiled from the source, but all effort failed.I don't know where the problem lies, the cernlib(libpacklib.a) or other place?

   The make file I used was modified from what provided by Cenko, and I post it as attachment. Could anyone help me?

---

### Post by psyentist88 on 2011-07-14
yankang, I am not sure whether this solves your problem or not, but I compared your makefile with mine and I spotted that instead of the line
```
DUMMYIARGCOBJ=$(MYPLACE)/extras/iarg.d/gfortran_iargc.o
```
you have it just as a comment. Remove the # mark from the front, after that the fortran compiler will hopefully understand your orders.

---

### Post by usef on 2011-07-18
Excuse me,

I'm using Ubuntu 10.04

When I type 
./executable
I face with this error:
error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory

what should I do?

---

### Post by psyentist88 on 2011-07-18
> **usef said:**
> error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory

what should I do?

This may help you: [http://ubuntuforums.org/showthread.php?t=1051256](http://ubuntuforums.org/showthread.php?t=1051256)

---

### Post by physe on 2011-09-06
Hello, i am getting these errors while trying to compile:

```
# gfortran  -o /home/elena/garfield/bin/garfield-9 *.o -Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran
gfortran  -o /home/elena/garfield/bin/garfield-9 *.o /home/elena/garfield/extras/iarg.d/gfortran_iargc.o \
	/home/elena/garfield/neBEM/V1.7e/obj/GarfieldInterface.o /home/elena/garfield/neBEM/V1.7e/obj/neBEMInterface.o \
	/home/elena/garfield/neBEM/V1.7e/obj/ReTriM.o /home/elena/garfield/neBEM/V1.7e/obj/ComputeProperties.o \
	/home/elena/garfield/neBEM/V1.7e/obj/neBEM.o \
	-Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran -std=c99 \
	-Iinclude -L/home/elena/garfield/neBEM/V1.7e/lib \
	-lNR -lVector -lIsles  -L/usr/local/lib -lgslcblas -lgsl -lm -lgfortran
/usr/bin/ld: cannot find -lgraflib
/usr/bin/ld: cannot find -lgrafX11
/usr/bin/ld: cannot find -lmathlib
/usr/bin/ld: cannot find -lkernlib
/usr/bin/ld: cannot find -llapack
/usr/bin/ld: cannot find -lpacklib
/usr/bin/ld: cannot find -lgslcblas
/usr/bin/ld: cannot find -lgsl
collect2: ld returned 1 exit status
make: *** [garfield-9] Errore 1

```

Am I missing some packages, or is my makefile wrong? I attach my makefile, probably the problem is the line
```
LF=-Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm \
-lpacklib -lnsl -lcrypt -ldl -lgfortran
```

but I have no idea of how I should change it.
Any help would be really appreciated ;)


EDIT: [COLOR="Red"]**Solved**[/COLOR]. I was missing some packages, and cernlib wasn't properly installed. At last I ended up installing all of the following:
```
sudo apt-get install gfortran cernlib libgsl0-dev nypatchy libgraflib1-gfortran libgrafx11-1-gfortran libmathlib2-gfortran libkernlib1-gfortran liblapack3gf liblapack-dev libpacklib-lesstif1-gfortran libpacklib1-gfortran libgsl0-dbg libblas3gf gsl-bin libgsl0ldbl
```
which may be too much, but finally it worked :)

---

### Post by CLINT1985 on 2011-10-31
I did eveything to work this program , but when I wrote "make garfield-9" , it's doing somethings on Terminal.

At the end , it gives this error :

   gfortran  -o /home/mustafaegin/garfield/bin/garfield-9 *.o -Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran
gfortran  -o /home/mustafaegin/garfield/bin/garfield-9 *.o /home/mustafaegin/garfield/extras/iarg.d/_gfortran_iargc.o \
    ./neBEM/V1.7e/obj/GarfieldInterface.o ./neBEM/V1.7e/obj/neBEMInterface.o \
    ./neBEM/V1.7e/obj/ReTriM.o ./neBEM/V1.7e/obj/ComputeProperties.o \
    ./neBEM/V1.7e/obj/neBEM.o \
    -Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran -std=c99 \
    -Iinclude -L./neBEM/V1.7e/lib \
    -lNR -lVector -lIsles  -L/usr/local/lib -lgslcblas -lgsl -lm -lgfortran
celcal.o: In function `celcal_':
celcal.f:(.text+0x17f5): undefined reference to `bemvoq_'
celspr.o: In function `celspr_':
celspr.f:(.text+0x13b5): undefined reference to `bemvoq_'
celspr.f:(.text+0x22a7): undefined reference to `bemvoq_'
celspr.f:(.text+0x2f97): undefined reference to `bemvoq_'
celspr.f:(.text+0x384e): undefined reference to `bemvoq_'
celspr.o:celspr.f:(.text+0x44c7): more undefined references to `bemvoq_' follow
collect2: ld returned 1 exit status
make: *** [garfield-9] Hata 1

What should I do for solving this problem ?

---

### Post by skynokia on 2011-11-20
Hello Cenko 
       when i am trying to install garfield on ubuntu 10.04 use the method you support.A problem happened  to me 
# gfortran  -o /home/shenhuaya/garfield/bin/garfield-9 *.o -Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran
gfortran  -o /home/shenhuaya/garfield/bin/garfield-9 *.o /home/shenhuaya/garfield/neBEM/V1.8.6/gfortran_iargc.o \
    /home/shenhuaya/garfield/neBEM/V1.8.6/obj/GarfieldInterface.o /home/shenhuaya/garfield/neBEM/V1.8.6/obj/neBEMInterface.o \
    /home/shenhuaya/garfield/neBEM/V1.8.6/obj/ReTriM.o /home/shenhuaya/garfield/neBEM/V1.8.6/obj/ComputeProperties.o \
    /home/shenhuaya/garfield/neBEM/V1.8.6/obj/neBEM.o \
    -Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran -std=c99 \
    -Iinclude -L/home/shenhuaya/garfield/neBEM/V1.8.6/lib \
    -lNR -lVector -lIsles  -L/usr/local/lib -lgslcblas -lgsl -lm -lgfortran
/usr/bin/ld: skipping incompatible /home/shenhuaya/garfield/neBEM/V1.8.6/lib/libIsles.a when searching for -lIsles
/usr/bin/ld: cannot find -lIsles
collect2: ld returned 1 exit status
make: *** [garfield-9] Error 1

may be you or somebody can give me some constructive suggestion  

thank you very much

---

### Post by Cenko on 2011-11-22
Hi,

I used a compiled version of NeBem from afs folders of Rob. If you send me your email I can send you this version. Maybe there is an imcompatibility with neBem you are using.

Also since I wrote this guide, some things may have changed. I did not try to compile it recently.

---

### Post by psyentist88 on 2011-11-24
Hi skynokia,

In case if you are trying to install it on a 32 bit OS and the neBEM source was downloaded from the neBEM home page (tar file for version 1.8.6), go to neBEM/V1.8.6/lib directory and rename the libIsles32.a file to  libIsles.a (the originally included libIsles.a is for 64 bit OS). Not sure wether it is needed or not, but I made a "make clean; make all" combo in the neBEM directory too before installing Garfield.

---

### Post by skynokia on 2011-11-28
> **Cenko said:**
> Hi,

I used a compiled version of NeBem from afs folders of Rob. If you send me your email I can send you this version. Maybe there is an imcompatibility with neBem you are using.

Also since I wrote this guide, some things may have changed. I did not try to compile it recently.


"Hi Cenko   thank you very much,my email is:shenqiqiling@gmail.com"

---

### Post by skynokia on 2011-12-01
> **psyentist88 said:**
> Hi skynokia,

In case if you are trying to install it on a 32 bit OS and the neBEM source was downloaded from the neBEM home page (tar file for version 1.8.6), go to neBEM/V1.8.6/lib directory and rename the libIsles32.a file to  libIsles.a (the originally included libIsles.a is for 64 bit OS). Not sure wether it is needed or not, but I made a "make clean; make all" combo in the neBEM directory too before installing Garfield.

[COLOR=Blue]Hi  psyentist88 ,thanks for your opinion I have tried you method when i am compile neBEM
 in the terminal [/COLOR][COLOR=Blue] at  last[/COLOR][COLOR=Blue]  it shows:[/COLOR]
[COLOR=DarkOrchid]([/COLOR][COLOR=DarkOrchid]i am not sure it is compile successful or not)[/COLOR]
> 
gcc \
    -c src/Solve/ComputeProperties.c \
    -o obj/ComputeProperties.o \
    -Wall -std=c99 -O3 -m32  \
    -Iinclude
gcc \
    -c src/Solve/neBEM.c \
    -o obj/neBEM.o \
    -Wall -std=c99 -O3 -m32  \
    -Iinclude
src/Solve/neBEM.c: In function ‘ReadInvertedMatrix’:
src/Solve/neBEM.c:877: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
src/Solve/neBEM.c:887: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
src/Solve/neBEM.c: In function ‘Solve’:
src/Solve/neBEM.c:1600: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
src/Solve/neBEM.c:1603: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
src/Solve/neBEM.c: In function ‘ReadSolution’:
src/Solve/neBEM.c:1722: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
src/Solve/neBEM.c:1725: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
src/Solve/neBEM.c:1742: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
src/Solve/neBEM.c:1743: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
src/Solve/neBEM.c:1748: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
src/Solve/neBEM.c:1749: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
src/Solve/neBEM.c: In function ‘Solve’:
src/Solve/neBEM.c:1642: warning: ‘RawInf’ may be used uninitialized in this function
[COLOR=Blue]with the help by you and Cenko ,these days i am trying to compile garfield-9 on my computer ,
but the same problem always happen to me .I don't know how to solve it !the  problem shows as follow[/COLOR]
> 
# gfortran -m32 -o /home/shy/garfield/garfield-9 *.o -Wl,-static -L/usr/lib32 -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran
gfortran -m32 -o /home/shy/garfield/garfield-9 *.o /home/shy/garfield//extras/gfortran_iargc.o \
    /home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o /home/shy/garfield/neBEM/V1.7e/obj/neBEMInterface.o \
    /home/shy/garfield/neBEM/V1.7e/obj/ReTriM.o /home/shy/garfield/neBEM/V1.7e/obj/ComputeProperties.o \
    /home/shy/garfield/neBEM/V1.7e/obj/neBEM.o \
    -Wl,-static -L/usr/lib32 -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran -std=c99 \
    -Iinclude -L/home/shy/garfield/neBEM/V1.7e/lib \
    -lNR -lVector -lIsles  -L/usr/local/lib -lgslcblas -lgsl -lm -lgfortran
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `neBEMSameBoundaryConditions':
GarfieldInterface.c.text+0x18b): undefined reference to `bemsbc_'
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `neBEMVolumePrimitives':
GarfieldInterface.c.text+0x1bb): undefined reference to `bemvpr_'
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `neBEMVolumePoint':
GarfieldInterface.c.text+0x212): undefined reference to `celvpt_'
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `neBEMVolumeDescription':
GarfieldInterface.c.text+0x287): undefined reference to `bemvol_'
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `bemdis_':
GarfieldInterface.c.text+0x34c): undefined reference to `bemszd_'
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `neBEMGetBoundingPlanes':
GarfieldInterface.c.text+0x5bd): undefined reference to `bempla_'
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `neBEMGetPeriodicities':
GarfieldInterface.c.text+0x655): undefined reference to `bemper_'
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `neBEMGetPrimitive':
GarfieldInterface.c.text+0x6e2): undefined reference to `bempri_'
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `ionbem_':
GarfieldInterface.c.text+0xd1e): undefined reference to `celvpt_'
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `efcbem_':
GarfieldInterface.c.text+0xf11): undefined reference to `celvpt_'
/home/shy/garfield/neBEM/V1.7e/obj/GarfieldInterface.o: In function `neBEMGetNbPrimitives':
GarfieldInterface.c.text+0x75: undefined reference to `bemnpr_'
collect2: ld returned 1 exit status
make: *** [garfield-9] Error 1


---

### Post by psyentist88 on 2011-12-02
Hi skynokia.

By compiling neBEM I am getting a couple of warnings too, if there is no error written on the screen, I think it is ok.

Please confirm that you are using a 32 bit OS. Otherwise Cenko's guide will not work, or at least it was not working for me. 

I suggest you using the latest neBEM instead of the V1.7e (check this out: [https://indico.cern.ch/materialDisplay.py?contribId=52&sessionId=9&materialId=slides&confId=158402](https://indico.cern.ch/materialDisplay.py?contribId=52&sessionId=9&materialId=slides&confId=158402) ). According to the authors it is much faster and giving a better result, than the older versions. Do not forget to set the neBEM directory (BEMDIR) in the garfield makefile properly.

---

### Post by skynokia on 2011-12-05
> **psyentist88 said:**
> Hi skynokia.

By compiling neBEM I am getting a couple of warnings too, if there is no error written on the screen, I think it is ok.

Please confirm that you are using a 32 bit OS. Otherwise Cenko's guide will not work, or at least it was not working for me. 

I suggest you using the latest neBEM instead of the V1.7e (check this out: [https://indico.cern.ch/materialDisplay.py?contribId=52&sessionId=9&materialId=slides&confId=158402](https://indico.cern.ch/materialDisplay.py?contribId=52&sessionId=9&materialId=slides&confId=158402) ). According to the authors it is much faster and giving a better result, than the older versions. Do not forget to set the neBEM directory (BEMDIR) in the garfield makefile properly.
HI psyentist88
Thank you very much.I have try to compile it many times but it also shows the same problem.I know  set the neBEM directory (BEMDIR) in the garfield makefile properly is the point, but I don't know how to do this .
may be you can send your Makefile to me for reference!my email is [email]shenqiqiling@gmail.com[/email]

---

### Post by tbjc on 2012-03-05
Hi,

I followed your steps, but still do not make it.

When I tap in 
make garfield-9it gives me:

#-rm *.f *.o
./patchy_step garfield-9
make: execvp: ./patchy_step: Permission denied
make: *** [garfield-9.f] Error 127.

PS: I did 
sudo apt-get install cernlib libgsl0-dev nypatchy, no improvement. That means my problem is different from [yankang]("http://ubuntuforums.org/member.php?u=1325083")'s.

I have been struggling with this problem for days, please help me.

Thanks in advance

---

### Post by Cenko on 2012-03-05
> **tbjc said:**
> Hi,

I followed your steps, but still do not make it.

When I tap in 
make garfield-9it gives me:

#-rm *.f *.o
./patchy_step garfield-9
make: execvp: ./patchy_step: Permission denied
make: *** [garfield-9.f] Error 127.

PS: I did 
sudo apt-get install cernlib libgsl0-dev nypatchy, no improvement. That means my problem is different from [yankang]("http://ubuntuforums.org/member.php?u=1325083")'s.

I have been struggling with this problem for days, please help me.

Thanks in advance

Can you try following and rerun make garfield-9:

```
chmod +x patchy_step
```

---

### Post by tbjc on 2012-03-07
HI,

sorry to bother again, but I still can not make it work. It gives me another bunch of errors.

Hope you can give me some suggestion.

Thanks a lot,


386:x86-64 output
/usr/bin/ld: i386 architecture of input file `privolum.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `prnter.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `proint.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `pt.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `ptg.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `pth.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `pyafit.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `pyafun.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `quit.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `raffle.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rafflev.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rafflev2.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rafflevi.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rain.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `random.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `randset.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `ranfl.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndcov.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndde.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndexp.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndfun.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndhis.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndhwf.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndini.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndlap.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndnor.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndpol.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rnduni.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndvav.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `rndvvl.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `roucal.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `round.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `scont1.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `scont2.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `seta00.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setb1x.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setb1y.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setb2x.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setb2y.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setb7.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setb7i.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setc10.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setc2x.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setc2y.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setc30.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setd10.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setd20.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setd30.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setdip.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setnew.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `setup.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sgflag.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `shellfi.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigadd.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigadm.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigads.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigang.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigava.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigcal.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigchk.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigcls.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigcnv.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigcrn.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigetr.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigfls.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `siggen.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigini.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `siginp.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigion.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigior.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigipr.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigist.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigitr.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigmca.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `signoi.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigpar.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigpla.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigplp.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigplt.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigqin.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigthc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigwgt.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sigwrt.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `skip.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sort.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sourcede.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sourceph.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `splane.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `spline.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `spline2.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srlengmt.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srmdem.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srmdez.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srmdhd.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srmerr.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srmgen.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srmint.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srmmst.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srmplt.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srmrea.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `srmrks.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `sst.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `stdstro.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `strbuf.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `strcal.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `strlen.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `strsav.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `strtyp.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tcalc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `timlog.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tof.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tofg.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tofh.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tpasc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tplane.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tplanea.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tplaneg.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tplaneh.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tracls.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `tradel.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `traexb.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `traint.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `trapho.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `traplt.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `trarea.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `trasub.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `treatcel.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `treatdel.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `trmcal.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `trmgen.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `trmint.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `trmplt.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `trmree.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `trmrer.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `ttrack.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `turntrac.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `units.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `vectors.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `volnumzc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `volpathl.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `wldcrd.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `worpriab.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `worprirg.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `zroarg.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `zrocnt.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `zrofnd.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `zroloc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `zrotst.o' is incompatible with i386:x86-64 output
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ctrmv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zswap'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zsymm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cgeru'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_sgemm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ctrsv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_sgemv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_srotg'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zgemm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cdotu_sub'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dznrm2'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ddot'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_csymm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cher2k'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zdotu_sub'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_sdot'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_sdsdot'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cgerc'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_scnrm2'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ctrmm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_sscal'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_strmm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zcopy'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dsyrk'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cherk'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zherk'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zher'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ztrmv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_drotmg'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dswap'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_scopy'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_scasum'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zscal'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_drotg'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zdotc_sub'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cscal'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_caxpy'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zsyr2k'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ssyr2k'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_csyr2k'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ztrsm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ctrsm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ssymm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cdotc_sub'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zher2k'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_saxpy'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_idamax'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_snrm2'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dsdot'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cher'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dger'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cher2'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dzasum'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dsyr2'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ssyrk'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_strmv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dgemv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cgemm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dasum'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dsymv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_srotm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_sswap'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dtrmv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_isamax'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zhemv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zaxpy'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dcopy'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_sasum'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dsyr'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_strsm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_drot'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ztrsv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_izamax'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ssymv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_chemm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zgeru'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dtrsv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_sger'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_srot'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dsymm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ztrmm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zdscal'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zher2'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ssyr'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dtrmm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zgerc'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_csscal'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dsyr2k'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_chemv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dnrm2'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_drotm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_icamax'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zgemv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zhemm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cgemv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ssyr2'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_strsv'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dscal'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dgemm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_srotmg'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_dtrsm'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_ccopy'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_zsyrk'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_cswap'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_daxpy'
/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libgsl.so: undefined reference to `cblas_csyrk'
collect2: ld returned 1 exit status
make: *** [garfield-9] Error 1
tbjc@ubuntu:~/garfield$

---

### Post by Cenko on 2012-03-08
> HI,

sorry to bother again, but I still can not make it work. It gives me another bunch of errors.

Hope you can give me some suggestion.

Thanks a lot,

Do you have a 64 bit system? Can you post the output of 

```
uname -a
```

If you see x86_64 there, my guide may not work, but I believe psyentist88 managed to do it. You may try following his posts.

Another thing, since I did that guide, the source of garfield must have changed. The guide may not be valid anymore. I haven't tried compiling again since I made the guide.

Cheers

---

### Post by tbjc on 2012-03-08
Hi,

Anyway, thanks a lot. Although I can not make it work on my big lenovo, which is 64-bit, your steps work good on my mini-dell. I have been working on this for days. Your guide is really helpful.  

By the way, if you have installation guide for mac,please let me know. (the guide on the official web doesn't work)

Thanks again,

---

### Post by hli07 on 2012-04-20
Thanks for your post. I'm currently trying to build garfield-9 on a 32-bit Ubuntu 10.04 system. There is a problem at the end, like this:
> ck -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran -std=c99 \
    -Iinclude -L./neBEM/V1.8.10/lib \
    -lNR -lVector -lIsles  -L/usr/local/lib -lgslcblas -lgsl -lm -lgfortran
/usr/bin/ld: cannot open output file /home/hli/software/garfield/bin/garfield-9: No such file or directory
And there is also an error at the beginning, which is ignored: 
> 
rm garfield-9.f garfield-9.mkfca garfield-9.shfca y.lis
rm: cannot remove `y.lis': No such file or directory
make: [main-9.f] Error 1 (ignored)
rm garfadd-9.f garfadd-9.mkfca garfadd-9.shfca y.lis
rm: cannot remove `y.lis': No such file or directory
make: [main-9.f] Error 1 (ignored)
mv main.f main-9.f
and there are many warnings like this:
> 
Warning: Unused dummy argument 't' at (1)
trasub.f:2.26:
       SUBROUTINE TRASUB(T,X,V,F)                                       
                          1
Warning: Unused dummy argument 't' at (1)
rm *.f
Could you give me a help? Thanks a lot.

---

### Post by Cenko on 2012-04-20
Hi,

To be honest I'm not sure what it can be. It's been long time I made this guide, and there may be many changes in the source code. I'd suggest checking the web page of garfield for more help.

---

### Post by psyentist88 on 2012-04-25
Hi hli07,

The warnings about unused dummy arguments are ok, they are definetely not the source of your problem. I have no clue either what went wrong,  but maybe I can help you more if you attach the full log file.

---

### Post by hli07 on 2012-04-26
Hi psyentist88, thank you so much for your help!
i don't know how to get the full log file. i just got the message in the terminal, and i put the end part of the message:
>  

Warning: Unused dummy argument 'efld' at (1)
tplaneh.f:2.26:

      SUBROUTINE TPLANEH(T,E1,CX1,CY1,CZ1,EFLD,IPLANE)                  
                          1
Warning: Unused dummy argument 't' at (1)
trasub.f:2.26:

       SUBROUTINE TRASUB(T,X,V,F)                                       
                          1
Warning: Unused dummy argument 't' at (1)
rm *.f
# gfortran   -o /home/hli/software/garfield/bin/garfield-9 *.o -Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran
gfortran   -o /home/hli/software/garfield/bin/garfield-9 *.o /home/hli/software/garfield/extras/iarg.d/_gfortran_iargc.o \
    ./neBEM/V1.8.10/obj/GarfieldInterface.o ./neBEM/V1.8.10/obj/neBEMInterface.o \
    ./neBEM/V1.8.10/obj/ReTriM.o ./neBEM/V1.8.10/obj/ComputeProperties.o \
    ./neBEM/V1.8.10/obj/neBEM.o \
    -Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran -std=c99 \
    -Iinclude -L./neBEM/V1.8.10/lib \
    -lNR -lVector -lIsles  -L/usr/local/lib -lgslcblas -lgsl -lm -lgfortran
/usr/bin/ld: cannot open output file /home/hli/software/garfield/bin/garfield-9: No such file or directory
collect2: ld returned 1 exit status
make: *** [garfield-9] Error 1

> **psyentist88 said:**
> Hi hli07,

The warnings about unused dummy arguments are ok, they are definetely not the source of your problem. I have no clue either what went wrong,  but maybe I can help you more if you attach the full log file.

---

### Post by rpa.adak on 2012-05-03
I have follow the guideline of cenko in ubuntu10.04 but there are many warning and the last part of the error message is the following:



Warning: Unused dummy argument 't' at (1)
rm *.f
# gfortran  -o /home/ramap/Videos/garfield/bin/garfield-9 *.o -Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran
gfortran  -o /home/ramap/Videos/garfield/bin/garfield-9 *.o /home/ramap/Videos/garfield/extras/iarg.d/_gfortran_iargc.o    \
	./neBEM/V1.8.10/obj/GarfieldInterface.o ./neBEM/V1.8.10/obj/neBEMInterface.o \
	./neBEM/V1.8.10/obj/ReTriM.o ./neBEM/V1.8.10/obj/ComputeProperties.o \
	./neBEM/V1.8.10/obj/neBEM.o \
	-Wl,-static -lgraflib -lgrafX11 -lmathlib -Wl,-dy -lX11 -lkernlib -llapack -lm -lpacklib -lnsl -lcrypt -ldl -lgfortran -std=c99 \
	-Iinclude -L./neBEM/V1.8.10/lib \
	-lNR -lVector -lIsles  -L/usr/local/lib -lgslcblas -lgsl -lm -lgfortran
/usr/bin/ld: cannot open output file /home/ramap/Videos/garfield/bin/garfield-9: No such file or directory
collect2: ld returned 1 exit status
make: *** [garfield-9] Error 1


:( how to solve them?

---

### Post by psyentist88 on 2012-05-04
Hi hli07 & rpa.adak,

I have just installed the latest version of Garfield with neBEM 1.8.10 on a 32 bit Ubuntu 10.04 by following Cenko's suggestions in the first post, it works.

I downloaded the "tar file for version 1.8.10" from the neBEM home page. After extraction only a "make clean" and a "make all" command was needed (in the V1.8.10 directory, where the neBEM makefile is).

As far as I remember I have changed only the first line of the garfield makefile (which is attached here in the first post of the topic). It is now: FC = gfortran -m32 (the # before the -m32 was removed). Also you have to set the BINDIR, BEMDIR paths properly.

---

### Post by subhasis1 on 2012-05-09
Dear psyentist88,
I have tried to install garfield in 32bit  ubuntu 10.04 following Cenko's method but without any success.You wrote that you successfully installed the garfield. Will you kindly post the make file of Garfield.[URL="http://ubuntuforums.org/member.php?u=1224753"]
[/URL]

---

### Post by psyentist88 on 2012-05-09
Dear subhasis1,

As I already wrote my makefile is almost the same as the one attached in the first post of this topic. The differences are only in line 7 (FC = gfortran # -m32 -> FC = gfortran -m32) and lines 11-14 (setting BINDIR, BEMDIR, MYPLACE and DUMMYIARGCOBJ paths properly).

---

### Post by rpa.adak on 2012-05-15
I have followed the instructions from cenko. But there were still errors remain.
I want to add some steps in Cenko's Instructions.
After downloading V1.8.10. keep it in file 'neBEM' within "garfield". 
Go to V1.8.10. use the commands to compile nebem. 'make clean' and 'make all'.
Set the paths in the make file correctly(Line no 11->14).
then "make garfield-9".

You could try and run the following.
1. save the  lines in a file (let's say "bem")
2. start garfield interactively:
   type: garfield-9
   hit return(enter)
   (a window should appear)
   type: < bem
   (colourful plots should appear)

&CELL
solids
box centre  5  3  0 half-lengths 1 2 1 conductor-1 voltage=2000
box centre -5  3  0 half-lengths 1 2 1 conductor-1 voltage=-2000
box centre  2  3  0 half-lengths 2 2 1 dielectric-1 epsilon=3
* box centre -2  3  0 half-lengths 2 2 1 dielectric-1 epsilon=5

opt cell-pr
nebem max-elem 6 svd

&FIELD
area -10 -10 -10 10 10 10 view x+2*y+3*z=0 nebem
pl vect

area -10 -10 -10 10 10 10 view z=0 3d
grid 30
pl surface v

tr 0 4 7 4
pl gr ex

// Check epsilon boundary
Global y=6*(row(200)-1)/199.0
Call efield(-0.001,y,ex1)
Call efield(+0.001,y,ex2)
Call plot_graph(y,ex2/ex1,`y [cm]`,`Ex_out/Ex_in`,`Check epsilon`)
Call plot_end

// Timing
For i From 1 To 5000 Do
   If i=1 Then Global t0=time_left
   Call efield(-10+20*rnd_uniform,-10+20*rnd_uniform,ex,ey,ez,e,v)
Enddo
Global t1=time_left
Say "Time per call: {(t0-t1)/5000} sec"
time 1000

// Contour plot
area -5 -2 5 8 x-y
grid 10
pl cont v n=20

// Check E vs V and div.E
area -5 -5 10 10 x-y
grid 30
check maxwell noprint

// Check one point
Global eps=1e-4
Global x=1.2
Global y=1.2
Global z=0
Call efield3(x-eps,y,z,ex,ey,ez,e,vx1)
Call efield3(x+eps,y,z,ex,ey,ez,e,vx2)
Call efield3(x,y-eps,z,ex,ey,ez,e,vy1)
Call efield3(x,y+eps,z,ex,ey,ez,e,vy2)
Call efield3(x,y,z-eps,ex,ey,ez,e,vz1)
Call efield3(x,y,z+eps,ex,ey,ez,e,vz2)
Call efield3(x,y,z,ex,ey,ez,e,v)
Say "Check E vs V"
Say "Ex: gradient = {(vx2-vx1)/(2*eps)}, neBEM = {ex}"
Say "Ey: gradient = {(vy2-vy1)/(2*eps)}, neBEM = {ey}"
Say "Ez: gradient = {(vz2-vz1)/(2*eps)}, neBEM = {ez}"

&GAS
arg-50-eth-50
pressure 20 mbar
heed argon 50 ethane 50

&DRIFT
area -10 -7 -10  10 13 10 view x+2*y+3*z=0 3d
track 0 -10 0 10 muon energy 10 GeV
drift track

*&CELL
*solids
*cylinder centre 0 0 0 half-length 3 radius 2 dielectric eps=4
*cylinder centre 0 0 0 half-length 3 radius 2 conductor q=2
*cylinder centre 0 0 0 half-length 3 radius 2 epsilon 2
*cylinder centre 0 0 0 half-length 3 radius 2 voltage 2 parallel[IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]


and enjoy :guitar:

---

### Post by LastStarDust on 2012-05-28
I managed to compile garfield in an amd64 machine with Ubuntu 12.04. First I followed Cenko and igal advices but without succeeding. Then I downloaded this linux [makefile]("http://cern.ch/rjd/Garfield/makefile_linux") from garfield home and changed only some lines and all worked. The main problem is that neBEM 1.7 is no more available and version 1.8.10 compiles only in 64bit systems (at least this is what I assume). 

I resume all steps:

[LIST]
[*]First three steps are the same as Cenko:

> **Cenko said:**
> After struggling for a while, I managed to install garfield (With important help of dinofelis) and decided to share my experince on compiling garfield on Ubuntu 10.04.
 
For information of garfield: [http://garfield.web.cern.ch/garfield/](http://garfield.web.cern.ch/garfield/)
 
If you don't have it yet, install gfortran
 
```
sudo apt-get install gfortran
```
 
install cernlib,libgsl from repositories
 
```
sudo apt-get install cernlib libgsl0-dev nypatchy
```
 
Create a directory (lets say /home/username/garfield/) and copy all necessary files from website to this directory:
 
```
garfield-7.car
garfadd-9.cra
garfield-9.cra
garfield.hlp
heed101garf.car
magboltz-7.car
patchy_step (It is defined as "Script to run Patchy" in the website)
```
 
(If you want another version of garfield you should download the corresponding .cra files.


[*]garfadd-9.cra and garfield-9.cra files are replaced by garfadd-9_linux.cra and garfield-9_linux.cra. Anyway I created two links to these named as the previous ones.

[*]I found not to have also the programs libblas* and lapack

[*]Then I fixed neBEM and bin positions in makefile. In my case:
```
BINDIR=/home/<your user name>/garfield
BEMDIR = /home/<your user name>/garfield/V1.8.10
```

[*]No *gfortran_iargc.c* stuff

[*]I'm not at cern so ```
-L/afs/cern.ch/sw/lcg/external/GSL/1.10/slc4_amd64_gcc43/lib
``` changes into ```
-L/usr/local/lib
```

[*]I had some problems with GSL libraries so I needed to replace string ```
-lgslcblas -lgsl -lm
``` with ```
-Wl,--no-as-needed -lgsl -lgslcblas -lm
```

[*]type on the terminal ```
cernlib pawlib
``` and paste the output replacing LF="...". I can't remember why I did it but there must have been some good reasons.

[*]Eventually ```
make garfield-9
```
[/LIST]

All runs fine but I'm getting an annoying segmentation fault when I try to plot the field
```
&FIELD
PLOT-FIELD ...

```
I get the same segmentation error both on SL6 32bit and on Ubuntu 12.04 64bit. gdb tells me this:
```
Program received signal SIGSEGV, Segmentation fault.
0x00007ffff74b66e6 in XSetFillStyle () from /usr/lib/x86_64-linux-gnu/libX11.so.6
```

In attachments makefile. Enjoy it

---

### Post by psyentist88 on 2012-05-29
> **LastStarDust said:**
> The main problem is that neBEM 1.7 is no more available and version 1.8.10 compiles only in 64bit systems (at least this is what I assume

Actually you can compile it on a 32bit system too, you just have to rename the libIsles32.a file at the /lib directory to libIsles.a. This one is used when compiling and according to it's size, the original is for the 64bit systems.

Anyway thanks for the solution, I will try it later.

---

### Post by LastStarDust on 2012-05-29
> **psyentist88 said:**
> Actually you can compile it on a 32bit system too, you just have to rename the libIsles32.a file at the /lib directory to libIsles.a. This one is used when compiling and according to it's size, the original is for the 64bit systems.

Anyway thanks for the solution, I will try it later.

Actually I renamed that file but the main problem was the file libNR.a that hasn't got a 32bit equivalent . . .

---

### Post by subhasis1 on 2012-05-29
Dear Cenko,
 I am trying to install garfield on 32 bit ubuntu 12.04 laptop using your method which is for ubuntu 10.04.  There is an error .
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libgsl.so: undefined reference to `cblas_ccopy'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libgsl.so: undefined reference to `cblas_zsyrk'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libgsl.so: undefined reference to `cblas_cswap'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libgsl.so: undefined reference to `cblas_daxpy'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libgsl.so: undefined reference to `cblas_csyrk'
collect2: ld returned 1 exit status
make: *** [garfield-9] Error 1
what is the problem ? Is there any modification needed for 12.04 ?
Regards,
Subhasis

---

### Post by LastStarDust on 2012-05-29
> **LastStarDust said:**
> [LIST]
[*]I had some problems with GSL libraries so I needed to replace string ```
-lgslcblas -lgsl -lm
``` with ```
-Wl,--no-as-needed -lgsl -lgslcblas -lm
```
in the makefile
[/LIST]


This may solve your issue.

---

### Post by psyentist88 on 2012-05-29
> **LastStarDust said:**
> Actually I renamed that file but the main problem was the file libNR.a that hasn't got a 32bit equivalent . . .

Removing could solve the problem - when you type "make all", libNR.a and libVector.a are created. It still works for me.

---

### Post by kimhyeongi on 2012-05-30
test@ubuntu://home/test/garfield$ make garfield-9
rm *.f *.o
rm: cannot remove `*.f': No such file or directory
rm: cannot remove `*.o': No such file or directory
make: [garfield-9.f] Error 1 (ignored)
./patchy_step garfield-9

 Nypatchy executing with files / options

   1  PAM      -
   2  FORT      garfield-9.f
   3  read      garfield-9.cra
   4  print    tty
   5  CC       -
   6  AS       -
   7  DATA     -
   8  FO:2     -
   9  CC:2     -
  10  AS:2     -
  11  DA:2     -

 Version: PATCHY  5.05 /3  1996/06/29 17.00     .RJP, today: 12/05/30  7.01

     1  + +EXE.
     2  + +USE,CERN.
     3  + +USE,*LINUX.
     4  + +USE,MANYWIRE.
     5  - * +USE,BIGMAP.
     6  + +USE,HUGEMAP.
     7  + +USE,LONGLIST.
     8  + +USE,*GARFIELD.
     9  + +USE,*MAGGARF.
    10  + +USE,*HEEDGARF.
    11  + +USE,P=PROJECTION,D=PLABEM,T=I.
    12  + +USE,P=PROJECTION,D=PLAEQU,T=I.
    13  + +USE,P=PROJECTION,D=PLAOVL,T=I.
    14  + +USE,P=PROJECTION,D=PLATRC,T=I.
    15  + +USE,P=PROJECTION,D=PLAEXP,T=I.
    16  + +USE,P=PROJECTION,D=PLAEXC,T=I.
    17  + +USE,P=PROJECTION,D=PLAEXD,T=I.
    18  + +USE,P=PROJECTION,D=PLAEXI,T=I.
    19  + +USE,P=PROJECTION,D=PLAEXE,T=I.
    20  + +USE,P=NEBEM,T=I.
    21  + +USE,P=CELL,D=CELBEM,T=I.
    22  + +USE,P=CELL,D=CELSEL,T=I.
    23  + +USE,P=CELL,D=CELSOL,T=I.
    24  + +USE,P=CELL,D=CELSPR,T=I.
    25  + +USE,P=CELL,D=CELSCT,T=I.
    26  + +USE,P=CELL,D=MAPC4,T=I.
    27  + +USE,P=CELL,D=MAPC5,T=I.
    28  + +USE,P=CELL,D=MAPFM8,T=I.
    29  + +USE,P=CELL,D=MAPFM9,T=I.
    30  + +USE,P=MAGBOL7,D=MONTEFD,T=I.
    31  + +USE,P=MAGBOL7,D=DLCMIC,T=I.
    32  + +USE,P=MAGINTER,D=GASBMC,T=I.
    33  + +USE,P=MAGINTER,D=GASIDE,T=I.
    34  + +USE,P=MAGINTER,D=GASIDI,T=I.
    35  + +USE,P=MAGINTER,D=GASIDO,T=I.
    36  + +USE,P=MAGINTER,D=GASLEX,T=I.
    37  + +USE,P=MAGINTER,D=GASEXU,T=I.
    38  + +USE,P=MAGINTER,D=OUTEI7,T=I.
    39  + +USE,P=MAGBOL7,D=DLCMIC,T=I.
    40  + +USE,P=FIELDCAL,D=EFIELD,T=I.
    41  + +USE,P=FIELDCAL,D=EFCFMP,T=I.
    42  + +USE,P=DRIFTCAL,D=DLCEX1,T=I.
    43  + +USE,P=DRIFTCAL,D=DLCIO1,T=I.
    44  + +USE,P=DRIFTCAL,D=INTEXC,T=I.
    45  + +USE,P=DRIFTCAL,D=ERFIR,T=I.
    46  + +USE,P=DRIFTCAL,D=DLCCAL,T=I.
    47  + +USE,P=DRIFTCAL,D=DLCSTA,T=I.
    48  + +USE,P=DRIFTCAL,D=DLCWIR,T=I.
    49  + +USE,P=DRIFTCAL,D=DLCWIM,T=I.
    50  + +USE,P=DRIFTCAL,D=DLCEX1,T=I.
    51  + +USE,P=DRIFTCAL,D=DLCSOL,T=I.
    52  + +USE,P=SIGNAL,D=IONFMP,T=I.
    53  + +USE,P=SIGNAL,D=SIGADD,T=I.
    54  + +USE,P=SIGNAL,D=SIGADS,T=I.
    55  + +USE,P=SIGNAL,D=SIGADM,T=I.
    56  + +USE,P=SIGNAL,D=SIGFLS,T=I.
    57  + +USE,P=SIGNAL,D=SIGWRT,T=I.
    58  + +USE,P=SRIMREAD,T=I.
    59  + +USE,P=GRAPHICS,D=GRTXHIGZ,T=I.

    60  + +PAM,LUN=11,T=a,C. garfield-7.car

 ***!!! OPEN fails for file: garfield-7.car
 Perror has: Illegal seek

 ***!!! Kill the run for: OPEN failure !!!***
make: *** [garfield-9.f] Error 2


how to solved this problem,I don't know , plz somebody help me!

---

### Post by DrIcetar on 2012-11-29
Everytime I try to plot the field , only to get the error "Segmentation fault". How can I solve it?

---

### Post by sffvba[e0rt on 2012-11-29
*Old thread **closed**.*


404

---

