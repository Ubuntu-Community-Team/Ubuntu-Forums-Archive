---
title: "install Qt in ubuntu"
date: 2010-08-29
forum: General Help
---

### Post by dato1989 on 2010-08-29
[LEFT]i have   ubuntu 10.04      and need help to install Qt   for c++ application please help how to do it?
[/LEFT]

---

### Post by Vaphell on 2010-08-29
goto synaptic and look for libqt packages
if you need that for programming, then look for qt-...-dev (dev=development)

to find exactly what you need you can run **ldd <binary_file>** to get the list of libraries required by the app and then use **apt-cache search <library_name>** (without .so.some_number part)
it will print out the list of likely packages you may want, pick the ones you need
**sudo apt-get install <package_name>**

---

### Post by Sub101 on 2010-08-29
You can install it from Synaptic as said above.

However I always prefer to install from the website;

[http://qt.nokia.com/downloads](http://qt.nokia.com/downloads)

---

