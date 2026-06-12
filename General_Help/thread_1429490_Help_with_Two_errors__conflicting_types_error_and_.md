---
title: "Help with Two errors? : conflicting types error and gcc: error trying to exec f951"
date: 2010-03-14
forum: General Help
---

### Post by Craif on 2010-03-14
Hi everyone,

I am currently trying to compile a program called GALPROP ([http://galprop.stanford.edu/web_galprop/galprop_home.html](http://galprop.stanford.edu/web_galprop/galprop_home.html)) and I am having quite a few problems trying to get this compile! 

There is two versions. The main version for which most people I assume download ([http://galprop.stanford.edu/codes/v50.1p.tgz](http://galprop.stanford.edu/codes/v50.1p.tgz)) and another version ([http://galprop.stanford.edu/forum/download/file.php?id=11](http://galprop.stanford.edu/forum/download/file.php?id=11)) which was edited by another user as the newest version of GALPROP seems to make lots of error messages and warning when compiling it when one has installed gcc4.3 or higher.

When I try to compile both of these versions I always get errors. So I am wondering if anyone could help me!?? Please?

When I install the main version, what I get is code: 

craig@ubuntu:~/Desktop/v50.1p$ make
f77 -fno-second-underscore  -c -o antiproton.o antiproton.f
   antiproton:
   tan_ng:
cc1: warning: command line option "-fno-second-underscore" is valid for Fortran but not for C
/tmp/fort77-3586-1.c:172: error: conflicting types for ‘tan_ng__’
/tmp/fort77-3586-1.c:62: note: previous declaration of ‘tan_ng__’ was here
/usr/bin/f77: aborting compilation
make: *** [antiproton.o] Error 25

Does anyone know how to fix this problem? So that it actually compiles? 

And when I try to compile to modified version I get:

craig@ubuntu:~/Desktop/Programs/Galpropaltered/galprop$ make
gcc -fno-second-underscore  -c -o antiproton.o antiproton.f
gcc: error trying to exec 'f951': execvp: No such file or directory
make: *** [antiproton.o] Error 1

Does anyone know how get get rid of the f951 error?

Thank you for your help in advance!!

Craig

---

