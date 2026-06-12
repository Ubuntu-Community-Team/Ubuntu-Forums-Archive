---
title: "libstdc++.so.5: cannot open shared object file: No such file or directory"
date: 2009-09-08
forum: General Help
---

### Post by aneuryzma on 2009-09-08
Hi,

I get this error message when I run a bash script:

> ../../bin/pursuit: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
../../bin/prey: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
../../bin/prey: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
../../bin/pursuit_monitor: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


I've checked and I noticed on my system I've installed a most updated version:

> libstdc++.so.6
libstdc++.so.6.0.10

What can I do to fix it ?

Should I install the old 5.0 library as well ?

thanks

---

### Post by Creap on 2009-11-15
Did you ever solve this problem? I tried to install libstdc++5 but I only get:
> Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate


> $ locate libstdc
/usr/lib/libstdc++.so.6
/usr/lib/libstdc++.so.6.0.13
/usr/lib/gcc/i486-linux-gnu/4.4/libstdc++.a
/usr/lib/gcc/i486-linux-gnu/4.4/libstdc++.so
..

no so.5

I tried linking /usr/lib/libstdc++.so.5 to /usr/lib/libstdc++.so.6 but then I got other errors.

---

### Post by Demonizer on 2009-11-21
Same problem... trying to fix ut2004 that way. Any help would be great.

---

### Post by realzippy on 2009-11-21
[http://ubuntuforums.org/showthread.php?t=1311200](http://ubuntuforums.org/showthread.php?t=1311200)

---

### Post by sainageswar on 2009-11-30
Getting same problem.I find libstdc.so.6 installed but the application which i want to install demands version 5.

---

### Post by mariusbutuc on 2010-02-24
Since you don't find the libstdc++.so.5 package in the karmic repository, I installed it from the jaunty one: [http://packages.ubuntu.com/en/jaunty/libstdc++5](http://packages.ubuntu.com/en/jaunty/libstdc++5) and it worked.

---

### Post by hawthornso23 on 2010-02-24
[http://ubuntuforums.org/showthread.php?t=1395980](http://ubuntuforums.org/showthread.php?t=1395980)

---

