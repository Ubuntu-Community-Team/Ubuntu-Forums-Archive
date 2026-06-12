---
title: "make modules failing &quot;No rule to make target&quot;, mismatched versions?"
date: 2006-04-15
forum: General Help
---

### Post by rupy on 2006-04-15
> 
root@xyz:/usr/src/linux# sudo make modules
  CHK     include/linux/version.h
make[1]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make: *** [arch/i386/kernel] Error 2


I am fairly new to linux and even newer to Ubuntu, been messing around with it a bit and I think I may have mixed up my linux headers or something when I upgraded the linux version. I also remember seeing some issues with the build directory earlier on which is probably related?

Could anyone give me some advice on how to fix this and/or clean it up a bit?

---

### Post by hawkbane on 2006-10-04
I am gettingthis as well.  Any ideas out there?

Thanx

---

### Post by Death_Sargent on 2007-03-15
I got something similar

> make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.


So I used the command " sudo gedit /usr/shar/qt3/mkspecs/default/qmake.conf " to see if I could solve the problem myself. 

All i got was a blank window from gedit (I mean the file had nothing in it gedit was working fine)

---

### Post by sefs on 2007-04-22
We need a solution to these problems...what is causing these compiliation failures.

---

