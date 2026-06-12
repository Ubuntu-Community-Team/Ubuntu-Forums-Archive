---
title: "Package version mismatch?  (Precise)"
date: 2012-08-16
forum: General Help
---

### Post by Ranko Kohime on 2012-08-16
I'm having quite a time with version mismatches.  As an example, qCad will not install because librecad will not install, because a slew of sub-dependent packages are a slightly different version.

```
libqt4-qt3support:
  Depends: libqt4-designer (=4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.2 is to be installed
  Depends: libqt4-network (=4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.2 is to be installed
  Depends: libqt4-sql (=4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.2 is to be installed
  Depends: libqt4-xml (=4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.2 is to be installed
  Depends: libqtcore4 (=4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.2 is to be installed
  Depends: libqtgui4 (=4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.2 is to be installed
```
If I attempt to force the version on any of these, Synaptic demands I remove a dozen or more applications that I use.

That's one example, and there are a half-dozen other applications that I would like to install, but cannot, due to this.

As near as I can tell, this is from the main repos, as I've disabled all of my independent repos and reloaded, and the .2 version remains the latest available.

Suggestions?

---

### Post by maxclaus on 2012-08-20
Hi Ranko,

i tried the same with the same result. Think we can only wait for newer versions of qcad/librecad or precise. To shorten waiting time download the latest qcad.exe and run it with wine. It's running perfectly and when the native Linux version will be available You can remove it.

Greetings/maxclaus

Edit: To specify a.m. here the according data:
latest librecad version: LibreCAD-Installer_1.0.2.exe
Adress for download: [http://sourceforge.net/projects/librecad/files/](http://sourceforge.net/projects/librecad/files/)

Greetings/maxclaus

---

