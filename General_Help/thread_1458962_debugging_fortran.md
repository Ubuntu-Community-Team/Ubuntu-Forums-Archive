---
title: "debugging fortran"
date: 2010-04-20
forum: General Help
---

### Post by alidiyebiri on 2010-04-20
i have a fortran code, and i have its compiled file.
when i try to run it like ./filename its starting but then its give an error "segmentation fault"

i try it in gdb like "gdb filename", but it gives same error
programs code is very long how can i see the wrong line in code or wrong function?
how can i debug it?

waiting for your helps.

---

### Post by alidiyebiri on 2010-04-21
is there anybody here :)

---

### Post by alidiyebiri on 2010-04-21
where can i find help for programming gcc/gfortran?

---

### Post by gmargo on 2010-04-22
When you run it under gdb, and the segmentation fault occurs, type "bt" at the gdb prompt to get a stack backtrace.  Hopefully that will give you a clue as to what routine was running at the time.

---

