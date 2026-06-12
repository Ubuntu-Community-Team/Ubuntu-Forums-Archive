---
title: "C Compiler Problem"
date: 2006-01-20
forum: General Help
---

### Post by Sym on 2006-01-20
Ok finally got my ATI display working so I start building WINE using apt-get
and I run the command

apt-get --build source wine

to which I get the error 

"checking for C compiler default output file name... configure: error: C compiler cannot create executables"

So after a quick search I find that I do have a gcc compiler ( gcc version 4.0.2 20050808 ) on my system and it can compile a simple Hello World program that I fed it.

Anyone have any idea's as to what went wrong?

btw I'm running Ubuntu AMD 64 which is why I'm compiling it myself in the first place.

---

### Post by nrwilk on 2006-01-20
Open up synaptic/adept and download "build-essential"

Then try again.

---

### Post by Captain Picard on 2006-01-21
Im having the same problem but Ive installed/reinstalled build essential, gcc 3.4 and others several times. Can/should I force the configure script past this check or to use a different make program?

---

### Post by Sym on 2006-01-23
Ok so I checked my packages, and build-essentials is there as are all of the required packages for building WINE.

---

