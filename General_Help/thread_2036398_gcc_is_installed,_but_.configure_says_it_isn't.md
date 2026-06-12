---
title: "gcc is installed, but ./configure says it isn't"
date: 2012-08-01
forum: General Help
---

### Post by Rikeshar on 2012-08-01
Hey everyone, I'm trying to compile a program. When I execute the ./configure command I get:

```

configure: Makefile configuration program for Scidb
    Tcl/Tk version: 8.5
    Your operating system is: Linux 3.2.0-27-generic-pae
    Checking if your system has gcc installed: no,
    'gcc: command not found'
```

When I do "gcc --version" though, I get:


```
gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE
```.

and "whereis gcc" shows:

```
gcc: /usr/bin/gcc /usr/lib/gcc /usr/bin/X11/gcc /usr/share/man/man1/gcc.1.gz
```


Any ideas why the compile script wouldn't be using it? I appear to have it installed.

---

### Post by Rikeshar on 2012-08-01
Nevermind, I was missing another component.

---

