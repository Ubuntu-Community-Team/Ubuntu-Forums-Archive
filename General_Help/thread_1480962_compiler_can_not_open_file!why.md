---
title: "compiler can not open file!why?"
date: 2010-05-12
forum: General Help
---

### Post by Milenkonslisboa on 2010-05-12
I have written a program in FORTRAN77.When I enter make command,I get this:
f77 -O3 -c surfce.f -o surfce.o
   surfce:
Cannot open file D2AS6INC.F
/usr/bin/f77: aborting compilation
Why?

---

### Post by John Bean on 2010-05-12
> **Milenkonslisboa said:**
> I have written a program in FORTRAN77.When I enter make command,I get this:
f77 -O3 -c surfce.f -o surfce.o
   surfce:
Cannot open file D2AS6INC.F
/usr/bin/f77: aborting compilation
Why?

From the look of the error message f77 seems to expect upper case filenames. Just a guess though, I've never used it.

Edit: on reflection that's probably nonsense, it looks more like a missing include file.

---

### Post by Milenkonslisboa on 2010-05-12
Thanks John!

---

### Post by Milenkonslisboa on 2010-05-12
I have changed everything into uppercase letters,but...
gcc: SURFCE.O: No such file or directory
f77 -O3 -C PHASE.F -O PHASE.O
   phase:
gcc: PHASE.O: No such file or directory
f77 -O3 -O SURFACE SURFCE.O PHASE.O
gcc: SURFACE: No such file or directory
gcc: SURFCE.O: No such file or directory
gcc: PHASE.O: No such file or directory

---

### Post by John Bean on 2010-05-12
The "-O" should be "-o" surely? Options are case sensitive whatever the filenames may be.

In any case, I said in my (edited) reply above that I think the error was a missing include file rather than the case of the files.

---

