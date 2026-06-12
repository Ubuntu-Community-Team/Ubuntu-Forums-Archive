---
title: "compiling for multiple architectures"
date: 2010-08-13
forum: General Help
---

### Post by hwttdz on 2010-08-13
I'm trying to compile some of the gnu utils (the version on some of the computers I work on are terribly out of date).  The issue is that many machines share the same filesystem, and I'd like to not have a different executable for each machine. 

Anyways, I've read that

./configure CC="gcc -arch i686 -arch x86_64 " --prefix=/home/user/bin

should work.  But of course it doesn't.  apparently -arch is not an argument accepted by gcc.

---

### Post by sdennie on 2010-08-13
You will probably need "-march=686 -m32" instead of "-arch=686 -arch=x86_64".  That will make 32bit binaries that are capable of running on almost any machine.  That doesn't mean they actually *will* run on any machine because differences in shared libraries may make it impossible.  You could try compiling "-march=686 -m32 -static" which will make the binaries much larger but, if they are able to be compiled that way, will make them more likely to run on any machine.

---

