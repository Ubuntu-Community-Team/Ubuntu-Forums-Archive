---
title: "Python Qt/SIP/PyQt installation problem"
date: 2011-04-08
forum: General Help
---

### Post by bd314159 on 2011-04-08
I am attempting to use python with two different programs: QtiPlot and Eric (Python IDE).  I started with Ubuntu 9.04 and Python 2.6.4 and was not able to use QtiPlot with python scripting.  I ended up upgrading to Ubuntu 10.10 and Python 2.6.6 and I still get messages that QtiPlot has been compiled with a different version of Qt/SIP/PyQt than is on my system.  I started to work with the Eric IDE and I get the message:

File "/usr/share/eric/modules/eric4.py", line 21, in <module>
    from PyQt4.QtCore import QTextCodec, SIGNAL, SLOT, qWarning, \
ImportError: /usr/lib/python2.6/dist-packages/PyQt4/QtCore.so: undefined symbol: PyUnicodeUCS2_FromUnicode

As far as I can tell, PyQt4, Qt and SIP are all installed and the latest versions.  I also created a virtual machine as a test system running Ubuntu 10.4 and was able to install and run both programs with no difficulty whatsoever.  

I have created a small app that runs dpkg -p <module> recursively to get the versions of a package and all its dependent packages.  I compared the working system and the non-working system and both are essentially the same as far as I can tell.  The only difference is that a number of packages might have something like:

Package: libtiff4  Version: 3.9.2-2ubuntu-0.6
Package: libtiff4  Version: 3.9.2-2

or 

Package: libpam-modules  Version: 1.1.1-2ubuntu5
Package: libpam-modules  Version: 1.1.1-2ubuntu2

These are not the only differences, I only post them as examples.  If the full list is needed, please let me know and I can post it.  

Thanks in advance for your help.

---

### Post by sanguinoso on 2011-04-08
Try reinstalling these packages; perhaps something went wrong during the install/upgrade.

---

### Post by bd314159 on 2011-04-08
I have tried reinstalling.  It did not work.

---

### Post by Pand5461 on 2011-04-15
AFAIK default Ubuntu QtiPlot package is built without Python scripting support. You can download the latest version from [here]("http://soft.proindependent.com/qtiplot.html") and build it. There are instructions for compiling in [this thread]("http://ubuntuforums.org/showthread.php?t=1521703")

---

