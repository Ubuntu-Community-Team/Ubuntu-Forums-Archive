---
title: "build XFree86"
date: 2010-07-15
forum: General Help
---

### Post by worksofcraft on 2010-07-15
I'm interested in the internals of X11 gui and trying to build it from latest Sources extracted from XFree86 CVS.

The code relies on system architecture and so for my 64 bit architecture I found that file "limits.h" now resides in folder "include-fixed" instead of the expected "include" folder.

However moving on the make needed an include called "asm/page.h" and sadly that too was not in the expected place :(
There are dozens of different "page.h" files with my installation so I don't know which one is wanted. Any explanation of which page.h file does what would be appreciated :confused:

---

### Post by worksofcraft on 2010-07-16
I put in a bunch of symbolic links from /usr/local/include to /usr/src/linux-headers-2.6.32-23 corresponding folders and now it can find all the header files but presumably I got the wrong combination because it still won't compile... things like:


/usr/local/include/asm/page.h:38:3: error: #error Unsupported page size!
XF86DGA.c: In function ‘MapPhysAddress’:
XF86DGA.c:499: error: ‘PAGE_SHIFT’ undeclared

Is there any kind of tool that configures c/c++ libraries and headers for my hardware?

---

### Post by worksofcraft on 2010-07-17
I also tried building this version 4.8 of x11 on a 32 bit system but it falls over at exactly the same place:

XF86DGA.c:22:40: error: asm/page.h: No such file or directory
make[3]: *** [XF86DGA.o] Error 1


Just for the record, I used xfree86.org website to subscribe to their Devel list i hope of take part in their forums. Alas all I get is:
---------->
Bug in Mailman version 2.0.9

We're sorry, we hit a bug!

Please inform the webmaster for this site of this problem. Printing of traceback and other system information has been explicitly inhibited, but the webmaster can find this information in the Mailman error logs.
<----------

So I did send their webmaster an email as suggested. Anyone else having problems with x11? It doesn't look like a 64 bit issue afterall :(

---

### Post by Sef on 2010-07-17
> I'm interested in the internals of X11 gui and trying to build it from latest Sources extracted from XFree86 CVS.

[XFree86]("http://www.xfree86.org/") does not develop X11. [X.org]("http://www.x.org/wiki/") develops X11.

---

### Post by ezsit on 2010-07-17
> XFree86 does not develop X11. X.org develops X11.

Did you actually go to the websites you correctly posted? Both [www.xfree86.org](www.xfree86.org) and [www.x.org](www.x.org) develop their own versions of X11, both groups are active, and X.org is more popular because of licensing issues. XFree86 was the original version and X.org splintered off from an earlier version of XFree86

---

### Post by worksofcraft on 2010-07-17
I first used CVS as directed on xfree86.org website to get the sources. Then I repeated it with the tar files that are also available:

XFree86-4.8.0-src-1.tgz
XFree86-4.8.0-src-2.tgz
XFree86-4.8.0-src-3.tgz

that time I uncommented "#define BuildFonts NO" in the host.def file. Both produced exactly the same source code tree.

Thanks for the explanations about x.org I'll have try with the sources and build instructions available from there :)

---

### Post by worksofcraft on 2010-07-18
looks like x.org have been modularizing it and, well after using "git" and apt-get etcetera etcetera as instructed I eventually seem to have all the source trees.

I try

./build.sh -f built.modules
but it doesn't matter what arguments I specify to build it just keeps spamming me with the same
Usage: ./build.sh [options] prefix...

That is on 32 bit Ubuntu 8.04 running in a virtual machine. The whole lot fell over much earlier with a variety of errors like segmentation fault on 64 bit Ubuntu 10.04

I also tried x.org's version 6.9 which still had same kind of simple procedure as xfree86.org but that failed with syntax errors in #include directives :O

Not quite sure what to try next :(
If anyone can actually build this stuff on Ubuntu... I would love to know more about their system setup please :)

---

### Post by worksofcraft on 2010-07-19
Whatever

I persevered a bit and decided I give you a progress report.

First my 64 bit Ubuntu 10.04 dead end:

$> sudo apt-get install autoconf

well it ends with
"Segmentation fault"

... everytime

so next... copying it to a 32 bit environment was NOT a good idea. Eventually I notice:

Error while copying ....
There was an error copying the file into smb://...
Symlinks not supported by backend

and so all the symbolic links were failing and I gave up and just installed it all from scratch again... bleh there goes my broadband allocation :/

However that's not the end of it.

The x.org source distribution eventually expires because it doesn't include a thing called "zlib.h"... and even if I do get that out of what I installed from xfree86.org's distribution it just goes on and on with more problems like that!
I think I go learn something else :P

---

### Post by worksofcraft on 2010-07-21
... like how to read instructions ;D
ok I installed all the prerequisites now (I think)... but I'm still not getting result. What do you make of this?
(oh yeah, note: I am using ~/x.org folder instead of /tmp as instructed, because things in /tmp have annoying habit to disappear and I not really want to 'git' them all again :P if I can help it) 


autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal -I /home/cjs/Desktop/x.org/modular/share/aclocal 
configure.ac:41: warning: macro `AM_PROG_LIBTOOL' not found in library
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac:35: installing `./config.guess'
configure.ac:35: installing `./config.sub'
configure.ac:26: installing `./install-sh'
configure.ac:26: installing `./missing'
Makefile.am:1: Libtool library used but `LIBTOOL' is undefined
Makefile.am:1:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
Makefile.am:1:   to `configure.ac' and run `aclocal' and `autoconf' again.
Makefile.am:1:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
Makefile.am:1:   its definition is in aclocal's search path.
Makefile.am: installing `./depcomp'
autoreconf: automake failed with exit status: 1


so could AC_PROG_LIBTOOL be an typo of AM_PROG_LIBTOOL macro that wasn't found, or something like that?

---

