---
title: "openoffice in ubuntu"
date: 2012-02-09
forum: General Help
---

### Post by sn0m on 2012-02-09
Hi 
is there a way of installing oopen office instead of libreoffice. I can't get bibus to work with libreoffice.
I've downloaded openoffice tar.gz file, extracted it and tried sudo dpkg -i *.deb but I get this message:
koli@koli-K53E:~/Downloads$ sudo dpkg -i *.deb
[sudo] password for koli: 
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
Any help appreciated
Sokol

---

### Post by Vishnu V on 2012-02-09
Hi,
we use dpkg -i file.deb to install the deb file,
So try to download deb file of open office and install it using dpkg -i

---

### Post by Linuxisfast on 2012-02-09
Install latest Libre office 3.4.5 via their ppa at [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

---

### Post by Hagar Delest on 2012-02-09
See here to install the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Note that with this method, you can even install in parallel OOo and LibO.

---

