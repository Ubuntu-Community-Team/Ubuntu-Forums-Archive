---
title: "SuperPi problem?"
date: 2010-04-15
forum: General Help
---

### Post by chisle on 2010-04-15
when i try and run superpi this is what i get, not quite sure why its giving me this> Why isnt it running properly?

---

### Post by chisle on 2010-04-15
bump?

---

### Post by john newbuntu on 2010-04-15
I didn't know what superpi was.  Just learnt that it calculates the value of pi to a certain number of digits.
The error you are getting is a segmentation fault meaning that the underlying libraries (C/C++) are trying to access memory locations that it does not have control of.  The memory stack at the time this problem occurred is dumped into a file called core and hence the core dump.
My guess is you have the wrong set of libraries or there is a mismatch between the way the program was compiled and run (possibly wrong OSs)

---

### Post by chisle on 2010-04-15
thank you. kind of new to linux, and just starting to use the terminal more.

---

