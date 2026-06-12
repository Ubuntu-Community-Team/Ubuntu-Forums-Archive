---
title: "How do I install iometer on 9.10?"
date: 2009-11-12
forum: General Help
---

### Post by BFG on 2009-11-12
EDIT:  I really need to add iometer as I have problems with my ReadyNAS network storage, and **[COLOR="Red"]the support guys at netgear need the output from iometer[/COLOR]** as it's their benchmark for diagnosis.


On the iometer download page
[http://www.iometer.org/doc/downloads.html](http://www.iometer.org/doc/downloads.html)

There's an image "Prebuild binaries".  I've downloaded this tarball.
Their documentation is for the windows version only and I can find nothing anywhere saying how to get the linux version running.

The tarball contains:

> $ tar xzvf iometer-2006_07_27.linux.i386-bin.tgz 
iometer-2006_07_27.linux.i386-bin/
iometer-2006_07_27.linux.i386-bin/src/
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/iomtr_kstat.h
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/Makefile-Linux24
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/Makefile-test
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/load26.sh
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/Makefile-Linux26
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/load24.sh
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/iomtr_kstat.c
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/test.c
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/unload.sh
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/README.first
iometer-2006_07_27.linux.i386-bin/src/iomtr_kstat/INSTALL
iometer-2006_07_27.linux.i386-bin/src/dynamo
iometer-2006_07_27.linux.i386-bin/src/scripts/
iometer-2006_07_27.linux.i386-bin/src/scripts/iom-indent
iometer-2006_07_27.linux.i386-bin/src/scripts/ccntmknod.README
iometer-2006_07_27.linux.i386-bin/src/scripts/ccntmknod
iometer-2006_07_27.linux.i386-bin/CREDITS
iometer-2006_07_27.linux.i386-bin/CHANGELOG
iometer-2006_07_27.linux.i386-bin/README
iometer-2006_07_27.linux.i386-bin/DEVGUIDE
iometer-2006_07_27.linux.i386-bin/LICENSE


Can someone advise me where to start?    The README file in the above does not contain any useful advice. Any help appreciated. :)

---

### Post by BFG on 2009-11-17
Bump

---

### Post by BFG on 2009-11-19
Bump.  The readme's and help files do not contain any help.

---

### Post by BFG on 2009-11-24
Final Bump. And top thread edited.

---

### Post by cvid on 2010-04-12
execute iometer-2006_07_27.linux.i386-bin/src/dynamo

---

### Post by BFG on 2010-04-12
Thanks cvid for the reply.
That was the first thing I tried.

It just waits.

```
mark@BLACKu:~/Downloads/iometer-2006_07_27.linux.i386-bin/src$ ./dynamo 
Fail to open kstat device file. You can ignore this warning
unless you are running dynamo on XSCALE CPU.

Dynamo not running as super-user.
       All available disks might not be reported 
       Cannot get TCP statistics from the kernel 
Sending login request...
   BLACKu
   127.0.1.1 (port 43636)


```

---

### Post by latebeat on 2010-04-29
I've just bumped into this thread as I'm looking for the answer too.

---

### Post by swamytk on 2010-09-21
Though it is too late, may be useful for some one. IOMeter has two parts: engine and gui tool. A engine called dynamo which does actual benchmarking and gui tool is front end for this engine. It can run on Win/Linux/Netware platforms. Where as the GUI tool to connect to engine (front end) is available only for Windows. 

So in this case, you are running dynamo only. Start IOMeter front end from any windows machine and configure (IP Address and port) it to connect to this linux machine for benchmark data. You can also try running IOMeter from Wine in linux.

---

