---
title: "gauss.c library"
date: 2010-02-21
forum: General Help
---

### Post by mirinamulhaq on 2010-02-21
hi
i want to do some numerical integration using emacs editor/gedit in ubuntu .now i need to inlude a library gauss.c but as i compile programme it shows an error that gauss.c file or directory doesnt exist.how can i know whether this library is available in my compiler or i need to install it .if i need to install it then where from can i get this 
(i general can anyone tell me how can i use my terminal to know about all the libraries that are present on my system)

---

### Post by Lampi on 2010-02-21
Install the ubuntu package [icov]("http://packages.ubuntu.com/search?searchon=contents&keywords=gauss.c&mode=exactfilename&suite=karmic&arch=any")

---

### Post by mirinamulhaq on 2010-02-23
thanku for your suggestion
i installed the same ,now how am i going to use it to know whether guass.c library is present in my system or not.and if it is not present then how can i install it.

---

### Post by gmargo on 2010-02-23
_Lampi_ had you install the **lcov** package.  As you can see from the link (s)he provided you, the path is **/usr/share/doc/lcov/examples/methods/gauss.c**. Check that examples directory for the header files etc.  Is this the **gauss.c** you were looking for?

You can see the full list of files in a package by using dpkg: 
```

$ dpkg -L lcov
/.
/usr
/usr/bin
/usr/bin/lcov
/usr/bin/genhtml
/usr/bin/geninfo
/usr/bin/genpng
/usr/bin/gendesc
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/geninfo.1.gz
/usr/share/man/man1/genpng.1.gz
/usr/share/man/man1/gendesc.1.gz
/usr/share/man/man1/lcov.1.gz
/usr/share/man/man1/genhtml.1.gz
/usr/share/man/man5
/usr/share/man/man5/lcovrc.5.gz
/usr/share/doc
/usr/share/doc/lcov
/usr/share/doc/lcov/copyright
/usr/share/doc/lcov/changelog.gz
/usr/share/doc/lcov/examples
/usr/share/doc/lcov/examples/descriptions.txt
/usr/share/doc/lcov/examples/example.c
/usr/share/doc/lcov/examples/gauss.h
/usr/share/doc/lcov/examples/iterate.h
/usr/share/doc/lcov/examples/Makefile
/usr/share/doc/lcov/examples/methods
/usr/share/doc/lcov/examples/methods/gauss.c
/usr/share/doc/lcov/examples/methods/iterate.c
/usr/share/doc/lcov/examples/README
/usr/share/doc/lcov/changelog.Debian.gz
/etc
/etc/lcovrc

```

---

### Post by mirinamulhaq on 2010-02-25
i did everything and then i again compiled my programme in which i used some libraries like math.c,etc and gauss.c but my programme is again showing me an error that the file gauss.c file or directory does not exist.do i ned to install some library package or the error is because of something else something else

---

### Post by rnerwein on 2010-02-25
hi
do you talking about libs ?  files ended with .c are C source files. libraries should ended with .so or .a
ciao

---

### Post by gmargo on 2010-02-25
> **mirinamulhaq said:**
> i did everything and then i again compiled my programme in which i used some libraries like math.c,etc and gauss.c but my programme is again showing me an error that the file gauss.c file or directory does not exist.do i ned to install some library package or the error is because of something else something else

There's just not enough information provided to figure out what you're talking about.

Can you 

[LIST]
[*]Post some as-minimal-as-possible code that demonstrates the problem, and
[*]Post the actual error message.
[/LIST]

---

### Post by mirinamulhaq on 2010-02-25
ok
i need to write a programme in c++ for finding out legendre /bessel /lagaure polynomials etc
my programme goes like this
#include<iostream>
#include<math.h>
#include<gauss.c>
intmain() {...........}
now when i am trying to compile programme the error message displayed is as
gauss.c no such file or directory found.
that is it
so i want to know how can i solve this problem

---

### Post by mirinamulhaq on 2010-02-25
sorry it is <math.c> in place of <math.h>

---

