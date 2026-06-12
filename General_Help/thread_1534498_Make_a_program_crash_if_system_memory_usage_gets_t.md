---
title: "Make a program crash if system memory usage gets too igh"
date: 2010-07-19
forum: General Help
---

### Post by Zorgoth on 2010-07-19
Basically I have a machine with 16GB of RAM and have just discovered that using all of it can crash the whole system over one process.  How could I run a process on the system in such a way that if more than 90% of system memory is used, the process immediately crashes?

---

### Post by AlphaLexman on 2010-07-19
16 Gigabytes or 16 Megabytes?

What are you running that eats up 16 Gigabytes of Ram?

---

### Post by Zorgoth on 2010-07-19
Gigabytes.  This is a *big* process.

---

### Post by patchwork on 2010-07-19
The monitoring daemon monit can do this.  It is found in the repositories.



> **What Monit can do**

                                                          Monit can start a process if it does not  run,                             restart a process if it does not respond and  stop                             a process if it uses too much resources....

from [http://mmonit.com/monit/](http://mmonit.com/monit/)

---

