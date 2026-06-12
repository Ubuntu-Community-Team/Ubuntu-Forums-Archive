---
title: "Fbida not in regular repository"
date: 2009-09-28
forum: General Help
---

### Post by consoleman on 2009-09-28
Hi.

I want to instal Fbida since I want to be able to read PDFs from console. Most of the websites around suggest installing it witha sudo apt-get install fbida, but it doesnt work for me, it just says package is not found. I am trying to find a repositry where this app may be downloaded from, but I have had no succedss. Also, no luck with .DEBs nor tar.bz (I found the latter  but I just cant make it work.

Any help to install this program would be great.

Cheers.

pd: please don't suggest to use gnome pdf readers.

---

### Post by jonobr on 2009-09-28
Looking at a few threads on this, this seems to consist of two packages,
fbi and ida,
Fbi is in the repos but ida is not.

Therefore you will needf to obtain yourself

Heres a link to the software
[Here]("http://dl.bytesex.org/releases/fbida/")

If you have trouble installing , recommend you post your efforts here to see whats going wrong

---

### Post by jonobr on 2009-09-28
BTW

Welcome to the forums!

---

### Post by consoleman on 2009-09-28
Cool, jonobr. First I tried the usual ./configure, make, make install. I skipped directly to make since there was no congigure file. This is where the thing fails.

edit: just read you welcoming... :)

> 
consoleman@consoleman-laptop:~/downloads/fbida-2.07$ make
checking for libdir name ... lib
checking for X11 app-defaults prefix ... /etc/X11
checking for endian.h ... yes
checking for linux/fb.h ... yes
checking for libexif/exif-log.h ... no
checking for fopencookie ... yes
checking for strcasestr ... yes
checking for pcd_open in pcd ... no
checking for DGifOpenFileName in ungif ... no
checking for png_read_info in png ... no
checking for TIFFOpen in tiff ... no
checking for Magick-config ... no
checking for sane_init in sane ... no
checking for curl_easy_init in curl ... no
checking for lirc_init in lirc_client ... no
checking for XmStringGenerate in Xm ... no

Make.config written, edit if needed

checking for libdir name ... lib
CC exiftran.o
exiftran.c:12:31: error: libexif/exif-data.h: No such file or directory
exiftran.c:14:21: error: jpeglib.h: No such file or directory
In file included from exiftran.c:15:
jpeg/transupp.h:89: error: expected specifier-qualifier-list before &#8216;boolean&#8217;
jpeg/transupp.h:101: warning: return type defaults to &#8216;int&#8217;
jpeg/transupp.h:101: warning: no previous prototype for &#8216;EXTERN&#8217;
jpeg/transupp.h: In function &#8216;EXTERN&#8217;:
jpeg/transupp.h:101: error: expected declaration specifiers before &#8216;jtransform_request_workspace&#8217;
jpeg/transupp.h:104: error: expected declaration specifiers before &#8216;EXTERN&#8217;
jpeg/transupp.h:109: error: expected declaration specifiers before &#8216;EXTERN&#8217;
jpeg/transupp.h:125: error: storage class specified for parameter &#8216;JCOPY_OPTION&#8217;
jpeg/transupp.h:130: error: expected declaration specifiers before &#8216;EXTERN&#8217;
jpeg/transupp.h:133: error: expected declaration specifiers before &#8216;EXTERN&#8217;
exiftran.c:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;ExifData&#8217;
exiftran.c:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
exiftran.c:52: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
exiftran.c:75: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
exiftran.c:113: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
exiftran.c:269: error: old-style parameter declarations in prototyped function definition
exiftran.c:269: error: expected &#8216;{&#8217; at end of input
make: *** [exiftran.o] Error 1Then I found this piece of text in linux.com that suggest another way to install it.

> *Installing fbida from source is a bit different than the usual ./configure; make; make install, but it's not that difficult either. First run make Make.config to create the Make.config file based on libraries found on your system. To disable or enable a particular feature, edit Make.config and change the HAVE_SOMETHING value to either yes or no. For example, to disable the installation of ida, change the value of HAVE_MOTIF to no. When you're done with the configuration, run make CC=gcc to compile the program and make install (as root) to install it*.Then I try that and this is what I get:

> 
consoleman@consoleman-laptop:~/downloads/fbida-2.07$ make Make.config
checking for libdir name ... lib
make: `Make.config' is up to date.

consoleman@consoleman-laptop:~/downloads/fbida-2.07$ make CC=gcc
checking for libdir name ... lib
CC exiftran.o
exiftran.c:12:31: error: libexif/exif-data.h: No such file or directory
exiftran.c:14:21: error: jpeglib.h: No such file or directory
In file included from exiftran.c:15:
jpeg/transupp.h:89: error: expected specifier-qualifier-list before &#8216;boolean&#8217;
jpeg/transupp.h:101: warning: return type defaults to &#8216;int&#8217;
jpeg/transupp.h:101: warning: no previous prototype for &#8216;EXTERN&#8217;
jpeg/transupp.h: In function &#8216;EXTERN&#8217;:
jpeg/transupp.h:101: error: expected declaration specifiers before &#8216;jtransform_request_workspace&#8217;
jpeg/transupp.h:104: error: expected declaration specifiers before &#8216;EXTERN&#8217;
jpeg/transupp.h:109: error: expected declaration specifiers before &#8216;EXTERN&#8217;
jpeg/transupp.h:125: error: storage class specified for parameter &#8216;JCOPY_OPTION&#8217;
jpeg/transupp.h:130: error: expected declaration specifiers before &#8216;EXTERN&#8217;
jpeg/transupp.h:133: error: expected declaration specifiers before &#8216;EXTERN&#8217;
exiftran.c:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;ExifData&#8217;
exiftran.c:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
exiftran.c:52: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
exiftran.c:75: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
exiftran.c:113: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
exiftran.c:269: error: old-style parameter declarations in prototyped function definition
exiftran.c:269: error: expected &#8216;{&#8217; at end of input
make: *** [exiftran.o] Error 1



---

### Post by jonobr on 2009-09-28
Mmmm....

Looking at your post (good response btw =D> )
IT reads that you should do it as root, so in this case you made need to sudo your commands.

Im thinking given your not found errors may be that its looking on your user path and not root path.

If you continue to have issues, Ill try installing and running here 

cheers

---

### Post by consoleman on 2009-09-28
I tried  the commands with sudo but I am getting the exact same error.

---

### Post by consoleman on 2009-09-28
hey jonobr, did you give it a try in your system.... that would be cool.

---

### Post by jonobr on 2009-09-29
Hello


Ill try it today.... Sorry bout the delay.


I will let you know how it goes

Cheers

---

### Post by jonobr on 2009-09-29
Hello


I checked the installation and sawa few things.
When I uncompressed the file and untarred it I checked out the README and install file.

In the README it mentions that you need openmotif and a few libs relating to png tiff and jpeg.

I seemed to have the libs for the graphic formats, however, open motif was a different story,
I found a post saying to get it from multiverse, however, it does not appear to be there when I add multiverse into my sources.list.

I then went to download from sourceforge but ran into problems compiling it.

Did you get to install motif? did it work for you?


Heres the section of the README Im referring to

> build
=====

Check the INSTALL file for detailed build instructions.

ida uses Motif 2.x features (utm, render tables).  This means you need
openmotif, lesstif does *not* cut it.

It also uses the usual graphics libraries (libtiff, libpng, libjpeg,
...), you should have them installed to get support for these image
formats.



Looking at the INSTALL file it tells me you need to have GNU MAKE
Im trying to do some research on that, and im coming up short, 
Im still looking though

Heres the piece from the INSTALL

> really short install instructions
---------------------------------

	$ make
	$ su -c "make install"



the more detailed version
-------------------------

Make sure you use GNU make.  The file name "GNUmakefile" isn't a joke,
this package really requires GNU make.

As first step make will do some config checks on your system and write
the results to Make.config.  If you want to have a look at Make.config
before the actual build starts you can run this step separately using
"make config".

The Makefiles use the usual GNU-ish Makefile conventions for variable
names and default values, i.e. prefix=/usr/local, ...

The values for some frequently adapted variables are initialized from
the enviroment.  Thus you can change the defaults simply by setting
environment variables:

	$ prefix="/usr"
	$ CFLAGS="-O3 -mcpu=i686"
	$ export prefix CFLAGS


---

### Post by consoleman on 2009-09-30
geez... this doesnt look very nice... tried to compile openmotiff, but this appeared:

> consoleman@laptop:~/Desktop/openmotif-2.3.1$ make
Making all in bindings
make[1]: Entering directory `/home/roberto/Desktop/openmotif-2.3.1/bindings'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/roberto/Desktop/openmotif-2.3.1/bindings'
Making all in bitmaps
make[1]: Entering directory `/home/roberto/Desktop/openmotif-2.3.1/bitmaps'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/roberto/Desktop/openmotif-2.3.1/bitmaps'
Making all in config
make[1]: Entering directory `/home/roberto/Desktop/openmotif-2.3.1/config'
Making all in cf
make[2]: Entering directory `/home/roberto/Desktop/openmotif-2.3.1/config/cf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/roberto/Desktop/openmotif-2.3.1/config/cf'
Making all in imake
make[2]: Entering directory `/home/roberto/Desktop/openmotif-2.3.1/config/imake'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/roberto/Desktop/openmotif-2.3.1/config/imake'
Making all in makedepend
make[2]: Entering directory `/home/roberto/Desktop/openmotif-2.3.1/config/makedepend'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/roberto/Desktop/openmotif-2.3.1/config/makedepend'
Making all in util
make[2]: Entering directory `/home/roberto/Desktop/openmotif-2.3.1/config/util'
gcc -DHAVE_CONFIG_H -I. -I../../include -I../../lib/Xm     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter  -MT makestrs.o -MD -MP -MF .deps/makestrs.Tpo -c -o makestrs.o makestrs.c
makestrs.c:51:21: error: X11/Xos.h: No such file or directory
makestrs.c: In function &#8216;WriteHeaderProlog&#8217;:
makestrs.c:115: warning: implicit declaration of function &#8216;strcmp&#8217;
makestrs.c: In function &#8216;CopyTmplProlog&#8217;:
makestrs.c:228: warning: implicit declaration of function &#8216;strlen&#8217;
makestrs.c:228: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
makestrs.c:231: warning: implicit declaration of function &#8216;strncmp&#8217;
makestrs.c: In function &#8216;WriteHeader&#8217;:
makestrs.c:275: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
makestrs.c:279: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
makestrs.c: In function &#8216;DoLine&#8217;:
makestrs.c:483: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
makestrs.c:513: warning: implicit declaration of function &#8216;strcpy&#8217;
makestrs.c:513: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
makestrs.c:532: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
makestrs.c:547: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
makestrs.c:589: warning: implicit declaration of function &#8216;index&#8217;
makestrs.c:589: warning: incompatible implicit declaration of built-in function &#8216;index&#8217;
makestrs.c:595: warning: implicit declaration of function &#8216;strcat&#8217;
makestrs.c:595: warning: incompatible implicit declaration of built-in function &#8216;strcat&#8217;
makestrs.c: In function &#8216;IntelABIIndexEntries&#8217;:
makestrs.c:631: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
makestrs.c: In function &#8216;DefaultIndexEntries&#8217;:
makestrs.c:646: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
makestrs.c: In function &#8216;DoComment&#8217;:
makestrs.c:676: warning: incompatible implicit declaration of built-in function &#8216;index&#8217;
makestrs.c:681: warning: implicit declaration of function &#8216;strncpy&#8217;
makestrs.c:681: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
makestrs.c: In function &#8216;main&#8217;:
makestrs.c:736: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
make[2]: *** [makestrs.o] Error 1
make[2]: Leaving directory `/home/roberto/Desktop/openmotif-2.3.1/config/util'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/roberto/Desktop/openmotif-2.3.1/config'
make: *** [all-recursive] Error 1
Perhaps its time to think on other ways to read PDF from console.

---

### Post by jonobr on 2009-10-01
Misery loves company,
I was getting the same error.,

The only thing I can think of is the requirement to use Gnu make.

It may be worth your while posting another thread asking about installation of OpenMotif.

I have never used or installed it before, so the problem could be simple or complex, Im not sure.
However, if you get Openmotif installed I get the feeling that may resolve some of your issues as your original installation bitched about missing applications

---

### Post by birchy91 on 2011-02-05
Here's your issue:
> exiftran.c:12:31: error: libexif/exif-data.h: No such file or directory
exiftran.c:14:21: error: jpeglib.h: No such file or directory

To fix the first error install libexif from [http://libexif.sourceforge.net/](http://libexif.sourceforge.net/)

For the second error...
It looks like they've copied some headers from The Independent JPEG Group's JPEG software.
Line 14 assumes the headers are available:
> #include <jpeglib.h>
So, install libjpeg from [http://www.ijg.org/](http://www.ijg.org/)

----

Next I ran into the following issue:
> exiftran.c: In function ‘dump_exif’:
exiftran.c:42: error: too few arguments to function ‘exif_entry_get_value’
make: *** [exiftran.o] Error 1

This is because HAVE_NEW_EXIF isn't defined for some reason... but we just installed it!
So add the following to the top of your file and viola! We're off to the races. :)
```
#define HAVE_NEW_EXIF
```

---

