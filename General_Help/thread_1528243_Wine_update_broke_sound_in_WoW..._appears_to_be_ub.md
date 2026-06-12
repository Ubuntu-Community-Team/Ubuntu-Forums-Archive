---
title: "Wine update broke sound in WoW... appears to be ubuntu package related"
date: 2010-07-10
forum: General Help
---

### Post by QCompson on 2010-07-10
After upgrading to 1.2-rc7, sound stopped working in WoW.  Switching between OSS and alsa has no effect.  

Others are having this issue:

[http://bugs.winehq.org/show_bug.cgi?id=23594](http://bugs.winehq.org/show_bug.cgi?id=23594)
[http://bugs.winehq.org/show_bug.cgi?id=23588](http://bugs.winehq.org/show_bug.cgi?id=23588)


Is there any easy way for me to downgrade to the last version?  Hate to have to install from source.  TIA.

---

### Post by QCompson on 2010-07-10
Nevermind.  I fixed it.  I removed the wine PPA respository, then uninstalled wine, then reinstalled the older stable version.

---

