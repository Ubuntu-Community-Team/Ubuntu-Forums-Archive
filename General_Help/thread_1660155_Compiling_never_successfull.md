---
title: "Compiling never successfull"
date: 2011-01-05
forum: General Help
---

### Post by kleinempfaenger on 2011-01-05
Hi, I have tried several times, but compiling always fails.
I want to compile a litte program called dwg2dxf. 
I think all the needed programs are installed.
First I unpack the tar.gz file on my desktop. Open Terminal, enter directory, then type
"./configure"
Everything fine, some files are created. config.log doesnt show errors (See config.log file).
"make"
Some errors occur
enters some directories without doing anything, then
main.cpp:39: fatal error: iostream.h: (translation) Doesnt exist.

This is the text from the terminal:

familia@familia-laptop:~/Escritorio/dwg2dxf-2.1$ make
make  all-recursive
make[1]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1»
Making all in dwg2dxf
make[2]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf»
Making all in docs
make[3]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs»
Making all in en
make[4]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs/en»
make[4]: No se hace nada para «all».
make[4]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs/en»
make[4]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs»
make[4]: No se hace nada para «all-am».
make[4]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs»
make[3]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs»
make[3]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf»
c++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -c main.cpp
main.cpp:39: fatal error: iostream.h: No existe el fichero o el directorio
compilation terminated.
make[3]: *** [main.o] Error 1
make[3]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf»
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf»
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1»
make: *** [all-recursive-am] Error 2


This is config.log:

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

configure:561: checking for a BSD compatible install
configure:614: checking whether build environment is sane
configure:671: checking whether make sets ${MAKE}
configure:717: checking for working aclocal
configure:730: checking for working autoconf
configure:743: checking for working automake
configure:756: checking for working autoheader
configure:769: checking for working makeinfo
configure:786: checking for gcc
configure:899: checking whether the C compiler (gcc  ) works
configure:915: gcc -o conftest    conftest.c  1>&5
configure:941: checking whether the C compiler (gcc  ) is a cross-compiler
configure:946: checking whether we are using GNU C
configure:955: gcc -E conftest.c
configure:974: checking whether gcc accepts -g
configure:1010: checking for c++
configure:1042: checking whether the C++ compiler (c++  ) works
configure:1058: c++ -o conftest    conftest.C  1>&5
configure:1084: checking whether the C++ compiler (c++  ) is a cross-compiler
configure:1089: checking whether we are using GNU C++
configure:1098: c++ -E conftest.C
configure:1117: checking whether c++ accepts -g
configure:1151: checking for ranlib


What is the problem?
Thanks,
kleinempfaenger

---

### Post by anglican on 2011-01-05
> **kleinempfaenger said:**
> Hi, I have tried several times, but compiling always fails.
I want to compile a litte program called dwg2dxf. 

...

What is the problem?
Thanks,
kleinempfaenger
iostream.h is deprecated.  Do "#include <iostream>" instead.   You'll have to remember to do std::cout and std::cin rather than just  cout and cin.

If you don't want to put "std::" throughout the program, you can write  the line "using namespace std;" just below your header file declaration.  
For example,

#include <iostream>
using namespace std;


H

---

### Post by mc4man on 2011-01-05
It's probably an old source, whether it will work right don't know.

As far as the error  try opening the main.cpp file in the dwg2dxf folder. Look for a line that's like this
#include <iostream.h> and remove the .h as in 
#include <iostream>

---

### Post by kleinempfaenger on 2011-01-05
Thanks for your answers.
But still compiling fails.
This is the first part of my main.cpp file, with modifications as suggested:

#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

/*   Some comments
*/


#define AD_PROTOTYPES

#define PATHCHAR '/'
#define DOT '.'

#include <iostream>
using namespace std;
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <string.h>
#include <fcntl.h>
#include "ad2.h"
#include "odio.h"

#define AUDIT

After "./configure" there are some announcements in the termial that some files couldnt be found.

checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... found

Do I have to install them?
Thanks,
kleinempfaenger

---

### Post by tgalati4 on 2011-01-05
You only need to install one working "make" program (it comes in many flavors) in order to "make" your program.  Were there other error messages?

It doesn't hurt to install multiple "make" programs, such as automake.  Usually the ./configure script has methods for several popular make programs, it just needs to find one of them.

If you are simply trying to convert a CAD drawing from one format to another, you might try qcad.  It's in the repositories.  I've used it for some conversions before.

---

### Post by kleinempfaenger on 2011-01-05
Thanks tgalati, 
indeed I work with QCad. But as far as I know it doesnt support the AutoCad .dwg-format. Thats the problem.
So I have to open the files in AutoCad under Windows and then save them in dxf format, what I dont like.
I need to convert them easily.
ok, I paste the results from "make", maybe there is an error, that I didnt find. Or maybe there isnt any error. Maybe in the last third there is something strange happening.

root@familia-laptop:/home/familia/Escritorio/dwg2dxf-2.1# make
make  all-recursive
make[1]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1»
Making all in dwg2dxf
make[2]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf»
Making all in docs
make[3]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs»
Making all in en
make[4]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs/en»
make[4]: No se hace nada para «all».
make[4]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs/en»
make[4]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs»
make[4]: No se hace nada para «all-am».
make[4]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs»
make[3]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf/docs»
make[3]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf»
c++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -c main.cpp
main.cpp: In function ‘void locprinthandle(unsigned char*)’:
main.cpp:324: warning: format not a string literal and no format arguments
c++  -g -O2  -o dwg2dxf  main.o ad2.a 
make[3]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf»
make[2]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1/dwg2dxf»
make[2]: se ingresa al directorio «/home/familia/Escritorio/dwg2dxf-2.1»
make[2]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1»
make[1]: se sale del directorio «/home/familia/Escritorio/dwg2dxf-2.1»

---

### Post by kleinempfaenger on 2011-01-05
Ok, it is done. There was no error. The program "works", but doesnt do anything. That is because I need the opendwg library. Which is unable to find, because as I understand AutoCad doesnt like experiments with the .dwg format. Had the same problem before. Maybe somebody has a file called "adinit.dat" or so, or could tell me where to find it?

As I wrote in the first post, I had never reached to compile a program. Thanks again, people, because I got it and learned some usefull things for the next time.

Greetings, kleinempfaenger

---

### Post by mc4man on 2011-01-05
edit: Missed your post

Other than not understanding the lang. it looks fine - look inside the dwg2dxf folder for a binary
went ahead and grabbed, built your source - seems fine (nothing to test on
> ~/Downloads/dwg2dxf-2.1/dwg2dxf$ ./dwg2dxf
dwg2dxf -- Convert dwg files to dxf files
Released under the GNU Public License

Usage: dwg2dxf infile [outfile] [version]

Required arguments:
infile:  is the path and name of the drawing file

Optional arguments:
outfile: is the path and name of the output dxf file.  If omitted the
	path and name of the input file will be used with the extension .dxf

version: is the AutoCAD version to be written.  If omitted the dxf file will
	be written in the same version as the drawing file.  Allowed values are:
		25 for ACAD version 2.5
		26 for ACAD version 2.6
		9  for ACAD version 9
		10 for ACAD version 10
		11 for ACAD version 11
		12 for ACAD version 12
		13 for ACAD version 13
		14 for ACAD version 14
		2000 for ACAD version 2000

you can either run a sudo make install or checkinstall should work here

```
sudo checkinstall --fstrans=no --default

```

---

