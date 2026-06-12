---
title: "Python .pyc files created, but not executable by default"
date: 2009-08-10
forum: General Help
---

### Post by gordonsowner on 2009-08-10
Hi,

Running Python 2.5.2 on Ubuntu 8.04.1.  I am running python, and it is creating .pyc files in my directory, but they are not executable.  How can I configure my systems so that .pyc files that are created are created with executable permissions?  Do I need to change my whole umask, or is there something else I can tweak?

Thanks,
Matt

---

### Post by DaithiF on 2009-08-10
Hi,
compiled python modules are not themselves executable, so they should not have the executable flag set.  This is normal behaviour.

cheers
D

---

### Post by gordonsowner on 2009-08-10
OK, thanks... so they work as advertised if they are just readable then, I'm deducing...

---

### Post by DaithiF on 2009-08-11
yes exactly ... python will read them when a process imports those modules

---

