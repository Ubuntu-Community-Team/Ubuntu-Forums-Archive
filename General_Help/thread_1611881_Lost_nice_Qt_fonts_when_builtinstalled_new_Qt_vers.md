---
title: "Lost nice Qt fonts when built/installed new Qt vers"
date: 2010-11-02
forum: General Help
---

### Post by FeralUrchin on 2010-11-02
Am using Ubuntu 10.04, which appears to include Qt 4.6.2.  I downloaded qt-everywhere-opensource-src-4.6.3 from qt.nokia.com, built and installed it (in I believe the correct locations), and suddenly the Qt fonts were no longer "pretty" or anti-aliased.  My Qt apps specifically use Nimbus Sans L, and these had been displaying "pretty" fonts correctly.  I tried re-installing all the 10.04 Qt stuff, gtk stuff, and everything apparently having anything to do with fonts.  No joy.  The Qt4 Settings app in System/Preferences lists only the mysteriously appearing "ugly" fonts.

Another weird side effect of the above has been loss of the definition QMAKESPEC.  I have to manually export QMAKESPEC = /usr/share/qt4/mkspecs/linux-g++-64 in order to get qmake to work.

Short of reinstalling Ubuntu 10.04, does anyone have a suggestion on how I can recover my "pretty" Qt fonts and the definition of QMAKESPEC?

Thanks in advance for any help.

---

### Post by gmargo on 2010-11-02
I would download the Ubuntu source for Qt 4.6.2 and see how they compiled it.

---

