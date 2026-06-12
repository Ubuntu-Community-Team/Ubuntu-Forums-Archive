---
title: "Debugging a Fortran Program"
date: 2010-02-06
forum: General Help
---

### Post by CaKiwi on 2010-02-06
I have compiled a Fortran program by using

gfortran -ggdb file.f90

To try to step through it in the debugger, I enter

gdb a.out

but I cannot create a break point. I have tried a number of commands including

b <line number>
b <subroutine name>

What am I missing here?

I also posted this in the programming talk forum.

---

### Post by CaKiwi on 2010-02-06
It has started working, for reasons unknown. Perhaps I was using the wrong number for the lins number

---

