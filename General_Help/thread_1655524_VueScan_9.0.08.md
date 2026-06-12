---
title: "VueScan 9.0.08"
date: 2010-12-29
forum: General Help
---

### Post by mark bower on 2010-12-29
Using Ubuntu 9.10/Epson Perfection V500

1) I downloaded and extracted VueScan 9.0.08.
2) The executable does not execute.
3) Trying a cmd line execution (./vuescan) I get "./vuescan /lib/tls/i686/cmov/libc.so.6: version 'GLIBC_2.11' not found (required by ./vuescan)
4) However, libc.so.6 (link to shared lib) is located at /lib///cmov.  It is linked to libc-2.10.1.so (shared lib) which is also located in /etc///cmov.

So what may be the problem?  My scanner works with Xsane, Iscan & VueScan 8.6.08.  Unfortunately, Ed Hamrick ([www.hamrick.com](www.hamrick.com)) does not support this type of problem(linux library compatibility issues), though a very nice application when the versions are compatible for Linux.

(Update) Please see my post #10.

mark bower

---

### Post by mark bower on 2010-12-30
bump for help

---

### Post by mark bower on 2010-12-31
bump for help

---

### Post by mark bower on 2010-12-31
bump again

---

### Post by luigi_mb on 2010-12-31
Try the latest version: 9.0.09. If it still gives you the error, it is possible that in the past you used the 8.6.6 version and that ~/.vuescan still reflects that version. Delete ~/.vuescan and try again. It should work. 

/luigi

---

### Post by JD_Bugs on 2010-12-31
I got this version of Vuescan to run only after upgrading to 10.04. Earlier versions did not work.

---

### Post by mark bower on 2010-12-31
@luigi_mb i tried 9.0.8 first, then without success, i put the 8 version on the same drive, different directory, so 100% sure there is not a vuescan version issue - but good to be aware of.

@JD_Bugs i sort of mused that there might be a version problem.  Hamrick says he built (compliled?) his 9 version on Ubuntu 10.10.  i am going to try and keep this post going for a while, but your answer may be the only answer - upgrade the Ubuntu version.

thank you both
mark

---

### Post by mark bower on 2011-01-01
anyone else have an idea why VueScan 9.0.08 will not recognize libraries that are in fact present.

mark

---

### Post by mark bower on 2011-01-02
From the top.

With Ubuntu 9.10, VueScan 9.0.08 will not execute.  When executed from the cmd line, it gives the error message: "./vuescan  /lib/tls/i686/cmov/libc.so.6: version 'GLIBC_2.11' not found (required by ./vuescan)".  In fact, libc.so.6 is present in /lib/tls/i686/cmov/.

What can be done to get VueScan to see libc.so.6 at /etc///cmov/?  I would point out again, disappointingly, that Ed Hamrick (hamrick.com) does not provide support for this problem.

[Note:  An earlier version of VueScan, Xsane, Iscan, etc all work]

---

### Post by mark bower on 2011-01-02
o.k.  I believe I understand the problem, but not readily corrected.  

The version of libc.so.6 installed with Ubu 9.10 is 2.10.1.  VueScan 9.0.xx is not backwards compatible and is looking for libc.so.6 in version 2.11.  Thus the error msg in my case:   "./vuescan  /lib/tls/i686/cmov/libc.so.6: version 'GLIBC_2.11' not found (required by ./vuescan)".  The library is involved with security so is not obtained as one normally might.  Please see the link below which shows the exact parallel to the problem I encountered with VueScan 9.0.xx.

[http://codetrips.blogspot.com/2010/12/latest-update-for-android-sdk-breaks.html](http://codetrips.blogspot.com/2010/12/latest-update-for-android-sdk-breaks.html)

Upgrading to 10.04 or 10.10 would take care of the problem - see post #6.  I just do not want to upgrade at this time.

---

