---
title: "cannot find libgfortran.so.3"
date: 2011-10-31
forum: General Help
---

### Post by bluestorm7 on 2011-10-31
Hi All,

I am very new to ldconfig and I was wondering if someone could shed some light into a problem. 
I am trying to get "vodom" to run. ([https://launchpad.net/vodom](https://launchpad.net/vodom))

I installed all the pre-requisites, but now I get the following problem:

$ vodom
vodom: error while loading shared libraries: libgfortran.so.3: cannot open shared object file: No such file or directory

I am running Ubuntu 11.04 Natty and have the gfortran package installed. When I run ldconfig -v I can see:


/usr/lib/x86_64-linux-gnu:

libgfortran.so.3 -> libgfortran.so.3.0.0

I can try installing gfortran manually...but it sounds like it will be a bad idea. (as it seems to linked with gcc interesting ways...)

Any help or guidance will be greatly appreciated!
Thank you!

---

### Post by dabraude on 2011-11-01
I had a similar problem and it might be because it is a 32bit application (I do not know if yours is) but I fixed it by installing libgfortran3:i386:

sudo apt-get install libgfortran3:i386

---

### Post by bluestorm7 on 2011-11-01
thank you for your suggestion. I will give it a shot tonight and keep it posted

---

### Post by bluestorm7 on 2012-01-25
Hey!

this actually worked.
Thank you for your help

---

### Post by raja.genupula on 2012-01-25
Hi , please don't forget marking your thread as solved from thread tools after solving your issue .

Thank you . :D:D

---

### Post by Amar Vashishth on 2013-03-03
thank you !!!

---

