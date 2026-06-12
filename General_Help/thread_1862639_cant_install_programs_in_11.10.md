---
title: "cant install programs in 11.10"
date: 2011-10-17
forum: General Help
---

### Post by korben88 on 2011-10-17
Whenever i try to install from the software center i get this error:

AN unhandlable error occurred

there seems to be a programming error in aptdaemon, the software that alows you to installl/remove software and to perform other package management related tasks...

---

### Post by hwttdz on 2011-10-17
I'd try

apt-get update
apt-get install -f

and see if that gives any errors.

---

