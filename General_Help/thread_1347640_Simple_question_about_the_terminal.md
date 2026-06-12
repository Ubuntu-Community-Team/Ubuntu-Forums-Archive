---
title: "Simple question about the terminal"
date: 2009-12-06
forum: General Help
---

### Post by linux_dream on 2009-12-06
I've learned that in order to compile a .f90 (fortran) file into a .exe, I need to type 
gfortran test.f90 -o test

But it won't find my test.f90 file.  I guess I previously have to type "cd desktop" or something like that, to tell the terminal to search in my desktop.
But what is the exact command to tell the terminal to search on my desktop?

---

### Post by oldos2er on 2009-12-06
Linux is case-sensitive, so to change to your desktop directory, run **cd Desktop**

---

### Post by linux_dream on 2009-12-06
> **oldos2er said:**
> Linux is case-sensitive, so to change to your desktop directory, run **cd Desktop**
Thanks!  It worked, however I still have my problem with compiling my f.90 file into a .exe file.
Here's what I type and what I get : 
isaac@isaac-desktop:~/Desktop$ gfortran test.f90 -o test
gfortran: test.f90: No such file or directory

But I have the file test.f90 in my desktop.  What is happening?

---

### Post by Sam on 2009-12-06
Beware, filenames are case sensitive !!

---

### Post by linux_dream on 2009-12-06
> **Sam said:**
> Beware, filenames are case sensitive !!
I renamed my file "Test.f90" and tried ...
isaac@isaac-desktop:~/Desktop$ gfortran Test.f90 -o Test
gfortran: Test.f90: No such file or directory


Edit : How strange!  I did the same, it just worked.

---

### Post by Sam on 2009-12-06
What if you use an absolute filename ?```
gfortran ~/Desktop/Test.f90 -o Test
```


EDIT: Just read your edit, great ! ;)

---

