---
title: "Can't install 10.04/EMC2, broken package"
date: 2011-06-27
forum: General Help
---

### Post by grey1beard on 2011-06-27
On my new installation of 10.04 on a Toshiba A30, I'm trying to install EMC2, using an installer file downloaded from linuxcnc.org.
At the end of the process, I get the error message below after trying to fix the broken package with package manager.

E:/var/cache/apt/archives/rtai-modules-2.6.32-122-rtai_3.8.1-linuxcnc1_i386.deb: trying to overwrite '/etc/udev/rules.d/99-rtai.rules', which is also in package rtai-modules-2.6.24-16-rtai 0

Can anyone help me get past this problem ?

Is it as simple as removing the rtai-modules-2.6.24-16-rtai 0 package ?
Do I need this one ? Is it replaced by the newer one, the rtai-modules-2.6.32-122-rtai_3.8.1 ? 

Many thanks
John

---

### Post by grey1beard on 2011-06-28
I think I've found the solution by tracking down and reading the EMC documentation Wiki: Ubuntu10.04PackageNotes.
Under known problems is this very one, and purging the previous rtai seems to be the answer.Will try tomorrow, and mark this as solved if it proves to be the case.

John

---

### Post by grey1beard on 2011-06-29
Yes, that's done it OK.
Mind you, I had to try twice - got the wrong rtai typed in first time round :oops:

John

---

