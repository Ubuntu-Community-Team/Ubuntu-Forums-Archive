---
title: "synaptics tomahawk: depends: libqt4-sql-sqlite but it is not going to be installed"
date: 2011-06-10
forum: General Help
---

### Post by misterbreadcrum on 2011-06-10
I get the error when trying to mark tomahawk for installation using synaptics.  I googled the error but couldn't find anything on it.  could some one help me figure out what's going on?

---

### Post by dFlyer on 2011-06-10
Here is the link to what you want to know:

[http://www.linuxquestions.org/questions/debian-26/help-with-apt-get-dependency-error-depends-but-is-not-going-to-be-installed-749121/](http://www.linuxquestions.org/questions/debian-26/help-with-apt-get-dependency-error-depends-but-is-not-going-to-be-installed-749121/)

---

### Post by misterbreadcrum on 2011-06-10
Unfortunately this doesn't quite answer my question or solve my problem.  It would appear that I either don't have the correct repositories or simply don't have all the ones I need. I've got the paulo-miguel-dias/tomahawk repo, but I know the libqt4-sql-sqlite is in the libqt4-dev package.
when I $sudo apt-get install libqt4-dev I get the following:

The following packages have unmet dependencies:
 libqt4-dev : Depends: libqt4-dbus (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-qt3support (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-xml (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqtcore4 (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqtgui4 (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-network (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-svg (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-sql (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-script (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-scripttools (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-xmlpatterns (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-designer (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-help (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-test (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-declarative (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Recommends: libqt4-opengl-dev (= 4:4.7.2-0ubuntu6) but it is not going to be installed
E: Broken packages

---

### Post by lonedancer on 2011-07-06
Do you have any version of virtualbox installed? If yes try to upgrade it. I had the same problem and after upgrade, even if the libqt4-core would not install, libqt4-dev did install without problems.

---

