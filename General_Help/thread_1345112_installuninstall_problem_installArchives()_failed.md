---
title: "install/uninstall problem: installArchives() failed"
date: 2009-12-03
forum: General Help
---

### Post by Eugene_Bondarenko on 2009-12-03
Every time I try to install/uninstall (via software center) software I get "Package operation failed" error. The full log is below. The weird thing is that the actual install/uninstall runs successfully and the software gets added or removed. Do you have any idea what is happening and how do I fix this?
```

installArchives() failed: Selecting previously deselected package 3dchess.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 142336 files and directories currently installed.)

Unpacking 3dchess (from .../3dchess_0.8.1-16_i386.deb) ...

Processing triggers for desktop-file-utils ...

Processing triggers for man-db ...

Setting up rabbitvcs (0.12.1-1~karmic) ...

dpkg: error processing rabbitvcs (--configure):

 subprocess installed post-installation script returned error exit status 10

Setting up 3dchess (0.8.1-16) ...



Processing triggers for python-support ...

Errors were encountered while processing:

 rabbitvcs

```

---

### Post by Eugene_Bondarenko on 2009-12-04
*up*

---

### Post by Eugene_Bondarenko on 2009-12-04
The issue is fixed (thanks to rabitvcs support). The fix is described in the first post here
[http://code.google.com/p/rabbitvcs/issues/detail?id=240](http://code.google.com/p/rabbitvcs/issues/detail?id=240)

---

