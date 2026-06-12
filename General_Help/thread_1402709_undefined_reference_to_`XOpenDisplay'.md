---
title: "undefined reference to `XOpenDisplay'"
date: 2010-02-09
forum: General Help
---

### Post by lvkarl on 2010-02-09
Programming error:  not clear what forum you would like this question in..:
got this link error:

root@progserver:/sources/ccode/test# $PATH
-bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin: No such file or directory
root@progserver:/sources/ccode/test# gcc -Wall main.c -o main
/tmp/ccqW12JE.o: In function `define_scr':
main.c:(.text+0xe): undefined reference to `XOpenDisplay'
collect2: ld returned 1 exit status

Message says to me can not find XOpenDisplay, or the library file which contains XOpenDisplay is not in my path.

Expected them to be in /usr/lib.

Tried to add /usr/lib to path but does not add, suppose the "No Such file or directory" is the real problem?

root@progserver:/sources/ccode/test# $PATH="/usr/lib:$PATH"
-bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin=/usr/lib:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin: No such file or directory
root@progserver:/sources/ccode/test# $PATH
-bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin: No such file or directory

Is that correct "No such file" is real problem?
How to I fix this broken path?

---

### Post by lvkarl on 2010-02-09
I'm thinking it is not a I can't find library issue now.   
As I copied the libraries to local directory and still get same error.
Did the format of library files change??

root@progserver:/sources/ccode/test# gcc --version
gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

root@progserver:/sources/ccode/test# gcc main.c -o main.exe -l X11.so
/usr/bin/ld: cannot find -lX11.so
collect2: ld returned 1 exit status
root@progserver:/sources/ccode/test# ls
main.c  main.o  main.s  X11.a  X11.so

---

### Post by J_R on 2010-04-12
Hi. Looking for an answer to this one myself & came across your post. Couldn't find an answer either, but eventually got there by trial & error.

Assuming you have installed the X11 libraries in default location (sudo aptitude install xorg-dev) & man pages, if required (sudo aptitude install libx11-dev), then all you should need to do is add the library to the linker options on command line -

gcc -Wall main.c -o main [COLOR=Red]-lX11[/COLOR]

Need to add the preprocessor directive to top of source file as well, of course -

#include<X11/Xlib.h>

Worked for me (Ubuntu 9.10), so hope it helps & not too late!

---

