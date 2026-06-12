---
title: "GCC headers"
date: 2006-05-07
forum: General Help
---

### Post by pingveno on 2006-05-07
I just did a Ubuntu install and am in the process of doing all of those customizations that everyone loves. In this case, the customization is simple: I want to install g++.  After the pleasant experience of having it install in under a minute (I'm switching from Gentoo), I proceeded to compile something. That's when the not-so-pleasant experience happened:
```

In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:35,
                 from /usr/include/c++/4.0.2/iostream:43,
                 from main.cpp:1:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/os_defines.h:39:22: error: features.h: No such file or directory

```
I got so many compiler errors for a simple hello world program that they scrolled out of Konsole's history. The compiler is correct; there are no files named features.h anywhere on the system. I have the the g++ package installed, along with all of its dependencies (g++-4.0, gcc-4.0, gcc, etc.) That includes the libstdc++6-4.0-dev package. In fiddling around with apt, I managed to uninstall most of my system, necessitating a full reinstall. Still, same problem. Any thoughts out there on how to fix this?

Possibly useful information:
Thinkpad T43, with all of the default laptop packages
1.5 GB RAM
dual boot with Windows XP (ntfs & reiserfs) with a shared vfat partitioon
Kubuntu Breezy Badger

---

### Post by kaamos on 2006-05-07
Do you have libc6-dev installed?

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=features.h&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=features.h&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

EDIT: install also build-essential if you have not already

---

### Post by pingveno on 2006-05-07
Ah, thank you. Perfect. I wonder why that didn't show up as a dependencies...

---

