---
title: "checking system information"
date: 2009-09-26
forum: General Help
---

### Post by deepaksrm on 2009-09-26
I have installed Ubuntu 9.04 on my laptop.
How do i check if it is a 64bit version or 32bit version?
Thanks

---

### Post by fuzzyk.k on 2009-09-26
use > uname in terminal with parameters depending on you , check below

check this out , may help
[http://www.computerhope.com/unix/uuname.htm](http://www.computerhope.com/unix/uuname.htm)

---

### Post by QIII on 2009-09-26
```
uname -a
```gets you the OS, specifically.

```
man uname
```tells you all about using uname.

---

### Post by deepaksrm on 2009-09-26
> uname -a
Linux deepak-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 200

This is what i get! 
How can i find if it is 32bit version or 64bit version from it?

---

### Post by wojox on 2009-09-26
```
uname -m
```

i686 = 32 bit

x86_64 = 64 bit

---

### Post by fuzzyk.k on 2009-09-26
try this
> uname -arv

---

### Post by deepaksrm on 2009-09-26
Thanks

---

### Post by QIII on 2009-09-26
uname -a

Actually gets you exactly what uname -arv got you.

uname -a just broke to a second line, which you didn't C&P.

The r and v switches get you the kernel release and version, which is given in -a anyway.

A word about -m:  Be careful about carrying -m to other distros.  According to the man pages, -m gives you hardware information.  In Ubuntu, it apparently gives you the machine architecture towards which the OS is targeted.

But you got what you needed, which is what matters.

---

