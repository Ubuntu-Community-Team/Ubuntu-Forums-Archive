---
title: "Package and driver installation"
date: 2009-11-27
forum: General Help
---

### Post by Mifune Funabashi on 2009-11-27
[FONT=Arial]hi, 
i'm trying to install the drivers for a brother dcp-385c and on the brother website it says

> Pre-required Procedure (5)
**Related distributions**: Debian 64 bit version, Ubuntu 64 bit version
**Related products/drivers: **printer/PC-FAX drivers
**Requirement****: ia32-libs** or **lib32stdc++** is required to be installed.now my questions:
am i running a 64 bit version? not too sure where to check:
> [FONT=Courier New]uname -a
Linux myubuntu 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux[/FONT]



also it says that ia32-libs or lib32stdc++ is required. i checked with synaptic, but there was no way to find it.

also running 
> [FONT=Courier New]sudo apt-get install ia32-libs[/FONT]
in the terminal, only returned that package ia32-libs couldn't be found.

could anyone please help?
thanks a lot![/FONT]

---

### Post by Mifune Funabashi on 2009-11-27
btw, ... i recently installed ubuntu 9.10 and done all the updates.

---

### Post by audiomick on 2009-11-27
I think the "i 686" bit in what you posted indicates 32 bit.
Mine is definitely 64 bit, and returns the following:

> Linux ubuntu-desktop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux

---

### Post by KeLa on 2009-11-27
Have you checked this thread:
[http://ubuntuforums.org/showthread.php?t=1182364](http://ubuntuforums.org/showthread.php?t=1182364)

---

