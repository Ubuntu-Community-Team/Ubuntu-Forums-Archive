---
title: "TCL/TK erro"
date: 2010-08-26
forum: General Help
---

### Post by rahulburra on 2010-08-26
hi,
when i try to install tk using the command

> **dpkg --install tk*.deb **i get the following error> 


(Reading database ... 123410 files and directories currently installed.)
Preparing to replace tk8.4 8.4.12-1 (using tk8.4_8.4.12-1_i386.deb) ...
Unpacking replacement tk8.4 ...
Preparing to replace tk8.4-dev 8.4.12-1 (using tk8.4-dev_8.4.12-1_i386.deb) ...
Unpacking replacement tk8.4-dev ...
Preparing to replace tk8.4-doc 8.4.12-1 (using tk8.4-doc_8.4.12-1_all.deb) ...
Unpacking replacement tk8.4-doc ...
Setting up tk8.4 (8.4.12-1) ...

dpkg: dependency problems prevent configuration of tk8.4-dev:
 tk8.4-dev depends on x-dev | xlibs-dev; however:
  Package x-dev is not installed.
  Package xlibs-dev is not installed.
 tk8.4-dev depends on libx11-dev | xlibs-dev; however:
  Package libx11-dev is not configured yet.
  Package xlibs-dev is not installed.
 tk8.4-dev depends on libxt-dev | xlibs-dev; however:
  Package libxt-dev is not installed.
  Package xlibs-dev is not installed.
dpkg: error processing tk8.4-dev (--install):
 dependency problems - leaving unconfigured
Setting up tk8.4-doc (8.4.12-1) ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 tk8.4-devcould anyone please help me solve this problem **ASAP** im much worried about this as it relates to my project
thankyou

---

### Post by luigi_mb on 2010-08-26
Did you manually download a tk*.deb package? I suggest you use Synaptic instead and search for "tk". Then click on Apply. 

/luigi

---

### Post by rahulburra on 2010-08-27
no i downloaded all the files related to tk such as dev,doc. i'm installing all at a time using tk*.deb

---

### Post by luigi_mb on 2010-08-27
Where did you download these files from? Why don't you try top use synaptic and install tk and tk-dev and tk-doc ?

/luigi

---

