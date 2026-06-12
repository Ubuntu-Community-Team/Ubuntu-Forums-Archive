---
title: "64bit support packages-Package dependencies cannot be resolved"
date: 2012-08-20
forum: General Help
---

### Post by sumanth nani on 2012-08-20
Hello everyone,

I am using ubuntu 12.04-64 bit version on my dell 1558 laptop. while i  was trying to install some 64bit support packages through Ubuntu  software center, namely *lib64gcc1*, *lib64gomp1*, I got the following message:

**Package dependencies cannot be resolved**
*            This error could be caused by required additional  software packages which are missing or not installable. Furthermore  there could be a conflict between software packages which are not  allowed to be installed at the same time.*

Please help me resolve  this issue.

Thanking you.

---

### Post by oldos2er on 2012-08-20
Could you open a terminal (Ctrl-Alt-t) and run ```
sudo apt-get update && sudo apt-get install lib64gcc1 lib64gomp1
``` and if there are errors, please copy and paste all the terminal output here?

---

