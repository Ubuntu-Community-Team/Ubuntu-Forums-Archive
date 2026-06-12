---
title: "Ubuntu 10.04 LTS crashes after enabling visual effects"
date: 2011-01-02
forum: General Help
---

### Post by Vignesh Sundaram on 2011-01-02
Hi,

Ubuntu works fine until I enable the visual effects to EXTRA. The computer then freezes, no mouse response, no keyboard response, have to hard restart.

These info might help you.
Version: Ubuntu 10.04 LTS
----
Results of sudo lspci |more

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
----
I went to System--> Administration --> Hardware drivers and it says, no proprietary drivers are in use in this system

---

### Post by coldraven on 2011-01-02
I'm no expert but I know that some older Intel cards will not work well or at all with 10.04.
My neighbors PC  worked fine with 8.04 but when I installed 10.04 it was unusable.
I cannot remember what version card he had.
I think the problem is with no support for OpenGL or something! (some of the screensavers use it and will crash badly)
Good luck!

---

### Post by Vignesh Sundaram on 2011-01-02
thanks for your reply. so can we say that "maybe" buying in some new graphic card might fix this?

---

### Post by coldraven on 2011-01-02
Yes, do some searching on the forum.
For example my ATI X1250 card was really useless with 9.04 but was usable with 10.04 and is much better now on 10.10.
As usual, the lack of open source support from the manufacturers is the cause of these problems.
However if you have a very elderly Intel card then unless you are happy with 8,04 replace it.
Ubuntu  8.04 will use the Intel propriety driver.
If you think about it, 8.04 is still only a three year old OS.
XP is how old?

---

