---
title: "-lg2c -ltoolbox -lcontrol not found.."
date: 2011-07-22
forum: General Help
---

### Post by saskiiaa on 2011-07-22
Hi everyone,

I'm trying to compile some programs and I'm getting the following error messages:

```
/usr/bin/ld: cannot find -lcontrol
/usr/bin/ld: cannot find -ltoolbox
/usr/bin/ld: cannot find -lg2c
collect2: ld returned 1 exit status
```What packages am I missing? The only thing I could find was a g77 package but it's obsolete by now. libg2c0 is also not available it seems, at least not for Natty Narwhal which is what I'm running right now.

Thanks for your help!

---

### Post by saskiiaa on 2011-07-22
I have found what I think is the solution:

Install gfortran:
```
sudo apt-get install gfortran
```You can then comment out the -lg2c in the Makefile and it will work.
The other two errors (lcontrol and ltoolbox) were specific libraries made by another program that I should have compiled first...

---

