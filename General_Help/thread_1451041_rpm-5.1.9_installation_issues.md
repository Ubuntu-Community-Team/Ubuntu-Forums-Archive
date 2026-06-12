---
title: "rpm-5.1.9 installation issues"
date: 2010-04-09
forum: General Help
---

### Post by outskut on 2010-04-09
Hey I'm still pretty new to Linux.  I'm trying to install rpm, and it failed to 'make' with the following output:

...
poptQV.c: In function ‘queryArgCallback’:
poptQV.c:226: error: ‘POPT_READFILE_TRIMNEWLINES’ undeclared (first use in this function)
poptQV.c:226: error: (Each undeclared identifier is reported only once
poptQV.c:226: error: for each function it appears in.)
make[3]: *** [poptQV.lo] Error 1
make[3]: Leaving directory `/home/outskut/Documents/InstallFiles/rpm-5.1.9/lib'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/outskut/Documents/InstallFiles/rpm-5.1.9/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/outskut/Documents/InstallFiles/rpm-5.1.9'
make: *** [all] Error 2


This sounds like a typical c/c++ compiler error, but I can't find any file named poptQV.c in the folder or using 'locate', but even if I could find it, why would there be a syntax error in a program that's already been released?   What can I do about this?

note:  I tried the same thing and got the exact same result with the previous release "rpm-5.1.8".

I'm using Ubuntu 9.10 (Karmic Koala) fully updated as of 4/9/2010.

---

