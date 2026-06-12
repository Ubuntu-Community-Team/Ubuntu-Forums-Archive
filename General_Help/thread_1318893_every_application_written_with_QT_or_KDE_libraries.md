---
title: "every application written with QT or KDE libraries seems to crash with bus error"
date: 2009-11-08
forum: General Help
---

### Post by Stan-O on 2009-11-08
I Just installed new ubuntu 9.10 and then I got some really bad problems.
 
I have a problem that every program that uses QT library like amarok or K3B or keepassx or skype crash with bus error at startup making them unusable. If I run any of this programs with GDB I get following output after run command:
 Program received signal SIGBUS, Bus error.
0x001b847e in ?? () from /lib/ld-linux.so.2
 The Address is different for each program but the error is the same.
 
Can somebody help me solve this problem?

---

### Post by juzzlin on 2009-11-08
Hmm...bus error usually tells about unaligned memory location. Could you try to reinstall your Qt libraries?

sudo apt-get install --reinstall libqtgui4

---

### Post by Stan-O on 2009-11-08
Thank you for the replay. I have tried to reinstall qt4 but it has not helped. Then I uninstall all kde and qt libraries and programs and installed them again with dependencies and after that everything works again. Somehow the original installation messed up the qt3 and qt4 libraries.

---

