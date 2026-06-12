---
title: "installing prob"
date: 2010-04-03
forum: General Help
---

### Post by nischalinn on 2010-04-03
I am installing a file from .tar.bz2 file. I am using the commands as given in the **"READ ME**"file. 
[B] $ cd artha-<version>                # change to the top-level directory
  $ ./configure                    # run the `configure' script
  $ make        [/B]


But when I do _**make**_ it shows:
[B]"  XXX@XXX-Desktop:~/Desktop/artha-1.0.1$ make
make: *** No targets specified and no makefile found.  Stop."

[/B]*********************************************************************
[B]XXX@XXX-desktop:~/Desktop/artha-1.0.1$ ls
aclocal.m4  ChangeLog    configure     data         Makefile.in  src
AUTHORS     config.h.in  configure.ac  INSTALL      NEWS         TODO
build-aux   config.log   COPYING       Makefile.am  README

[/B]Now what to do? How do I install it?

---

### Post by legends2k on 2010-05-04
Looks like you don't have the development packages required to build programs from source. You can install them by entering 

```

sudo apt-get install build-essential

```
# if you don't have make, automake or autoconf install them by  entering 
```

sudo apt-get install make automake autoconf

```

However, building from source is the hard way to do it; it's recommended that you install Artha using a .deb file depending on your processor (32 or 64 bit) from Artha's [Downloads]("http://artha.sourceforge.net/wiki/index.php/Download") page.

---

