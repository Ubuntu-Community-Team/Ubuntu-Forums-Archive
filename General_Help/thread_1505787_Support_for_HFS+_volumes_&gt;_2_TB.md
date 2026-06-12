---
title: "Support for HFS+ volumes &gt; 2 TB?"
date: 2010-06-09
forum: General Help
---

### Post by obruchez on 2010-06-09
Hello,

According to this bug report, support for HFS+ volumes > 2 TB has been disabled because hfsplus tended to corrupt them:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=550010](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=550010)

Does anybody know if volumes > 2 TB will be supported anytime soon?

Who should I contact to know if someone is working on it?

Olivier

---

### Post by dcstar on 2010-06-10
> **obruchez said:**
> Hello,

According to this bug report, support for HFS+ volumes > 2 TB has been disabled because hfsplus tended to corrupt them:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=550010](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=550010)

Does anybody know if volumes > 2 TB will be supported anytime soon?

Who should I contact to know if someone is working on it?

Olivier

The reports says it was fixed in 2.6.31, why do you think it is still a problem?

---

### Post by obruchez on 2010-06-10
The initial bug was that HFS+ volumes larger than 2 TB were getting corrupted by hfsplus. The bug was "fixed" by making it impossible to mount volumes larger than 2 TB. Unless I missed something, of course.

---

### Post by sparkid on 2011-03-21
This tutorial fix Read Only file system >2TB hfsplus

[http://oursdigitallife.blogspot.com/2011/03/ubuntu-1010-hard-disk-break-2tb-hfsplus.html](http://oursdigitallife.blogspot.com/2011/03/ubuntu-1010-hard-disk-break-2tb-hfsplus.html)

Tested with ubuntu 10.10 kernel image 2.6.35-28-generic

---

