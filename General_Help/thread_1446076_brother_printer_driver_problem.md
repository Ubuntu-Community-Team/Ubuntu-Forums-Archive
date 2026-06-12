---
title: "brother printer driver problem"
date: 2010-04-03
forum: General Help
---

### Post by lela19 on 2010-04-03
I can't install printer Brother MFC-495 CW in ubuntu 10.04 (64 bit)
I installed all the libs, the cups and lpr driver, I tried to force it....it didn't work. I get this message even if I navigate to nautilus and double click on the package. ....
dpkg: error processing mfc495lpr-1.1.2-1.i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
mfc495lpr-1.1.2-1.i386.deb 

 maybe I'm just too stupid to move to right directory...

any ideas???

---

### Post by Wiebelhaus on 2010-04-03
Try to install via command line and report back with output please.

```

dpkg -i filename.deb
```

---

### Post by lela19 on 2010-04-03
this is the output:

~$ dpkg -i mfc495cwcupswrapper-1.1.2-2.i386.deb
dpkg: requested operation requires superuser privilege
 with sudo command:

~$ sudo dpkg -i mfc495cwcupswrapper-1.1.2-2.i386.deb
dpkg: error processing mfc495cwcupswrapper-1.1.2-2.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc495cwcupswrapper-1.1.2-2.i386.deb

---

