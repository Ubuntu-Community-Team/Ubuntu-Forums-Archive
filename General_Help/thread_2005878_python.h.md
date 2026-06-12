---
title: "python.h"
date: 2012-06-18
forum: General Help
---

### Post by essential1 on 2012-06-18
Hi all, 

I use Ubuntu 11.04. I don't really like C, so after finding out I can call Python from a C program, I am trying to follow a guide on doing this. 

The first step is to include a line to tell C you need a python module, however after including the line :

#include "Python.h"

when trying to recompile I get the error message:

fatal error: Python.h: No such file or directory

Googling this suggests installing python-devel. I've done this, restarted the machine, and I get the same error message. I'm not sure why it isn't working. I can't find any other solutions. I'm very confused.

---

### Post by Simian Man on 2012-06-18
Python and C integration is a pretty tricky thing to do.  If you don't like C, why use C and Python instead of just Python?

---

### Post by essential1 on 2012-06-18
I'm trying to modify QEMU to do some extra things for me. It seemed so much easier to do the stuff I need in Python.

---

### Post by vazduxosbra4kania on 2012-06-18
> **Simian Man said:**
> Python and C integration is a pretty tricky thing to do.  If you don't like C, why use C and Python instead of just Python?

great point :)

---

### Post by Simian Man on 2012-06-18
Ah, I see.  It will likely be much easier to just modify the C code.  In order to use Python to make the changes, you will have to embed a Python interpreter inside QEMU and use the Python/C API to expose the functionality of QEMU to the Python code.  This alone will likely be trickier than your actual modifications.  See [this tutorial]("http://docs.python.org/extending/embedding.html") to see if this sounds like it's worth pursuing.

---

