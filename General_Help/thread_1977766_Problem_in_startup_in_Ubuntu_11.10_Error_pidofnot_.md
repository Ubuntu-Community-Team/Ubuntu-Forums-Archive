---
title: "Problem in startup in Ubuntu 11.10 Error: pidof:not found in etc/acpl/power.sh"
date: 2012-05-10
forum: General Help
---

### Post by r20rock on 2012-05-10
Hello everyone,
I am new to Ubuntu and recently installed Ubuntu 11.10. Today I tried starting Ubuntu and it showed the following error:

**/etc/acpl/power.sh: 9 pidof not found **

and after that, start up process terminates.
I have no idea of this implies and how should I proceed.

It is **not** the 1st time I am starting Ubuntu. I have already used it for sometime but never faced any such problem.
Today I tried switching between users and nothing else new, and then restarted the Ubuntu and got this error.

Please Help Me!
Thanx

---

### Post by erikthedrink on 2012-06-18
Instead of pidof, in the terminal, type
ps -e
This should list all processes like pidof used to.
:guitar:

---

