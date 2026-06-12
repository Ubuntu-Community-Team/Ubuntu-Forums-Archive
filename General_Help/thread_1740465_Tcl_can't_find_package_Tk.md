---
title: "Tcl can't find package Tk"
date: 2011-04-27
forum: General Help
---

### Post by estratos on 2011-04-27
On my 32-bit 10.04 system, I'm trying to run a tcl script that uses tk ("package require Tk") but I'm always getting this error:

can't find package Tk
    while executing
"package require Tk"

tcl version is 8.5 whilst tk is 8.4.16-2 and tklib is 0.5-2. It seems that tcl is not able to find tklib so I wonder if there is a way to tell tll where to find the package.

Thanks for your help!

---

### Post by estratos on 2011-04-27
Problem solved.

Switching to tk 8.5 solved the problem.

Thanks!

---

