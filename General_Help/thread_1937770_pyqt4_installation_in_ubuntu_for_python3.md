---
title: "pyqt4 installation in ubuntu for python3"
date: 2012-03-08
forum: General Help
---

### Post by akhil123k on 2012-03-08
[B]I downloaded sip-4.13.2 and PyQt-x11-gpl-4.9.1 and installed sip but while installing PyQt following problem occurs :
[/B]"Error: Unable to create the C++ code."

**Can nybody help?I have given the entire snapshot below:**

akhil@akhil-Inspiron-1545~/Desktop/PyQt-x11-gpl-4.9.1$ sudo python3 configure.py -q /usr/bin/qmake-qt4
Determining the layout of your Qt installation...
This is the GPL version of PyQt 4.9.1 (licensed under the GNU General Public
License) for Python 3.1.2 on linux2.

Type '2' to view the GPL v2 license.
Type '3' to view the GPL v3 license.
Type 'yes' to accept the terms of the license.
Type 'no' to decline the terms of the license.

Do you accept the terms of the license? yes
Found the license file pyqt-gpl.sip.
Checking to see if the QtGui module should be built...
Checking to see if the QtHelp module should be built...
Checking to see if the QtMultimedia module should be built...
Checking to see if the QtNetwork module should be built...
Checking to see if the QtDBus module should be built...
Checking to see if the QtDeclarative module should be built...
Checking to see if the QtOpenGL module should be built...
Checking to see if the QtScript module should be built...
Checking to see if the QtScriptTools module should be built...
Checking to see if the QtSql module should be built...
Checking to see if the QtSvg module should be built...
Checking to see if the QtTest module should be built...
Checking to see if the QtWebKit module should be built...
Checking to see if the QtXml module should be built...
Checking to see if the QtXmlPatterns module should be built...
Checking to see if the phonon module should be built...
Checking to see if the QtAssistant module should be built...
Checking to see if the QtDesigner module should be built...
Checking to see if the dbus support module should be built...
DBus v1 does not seem to be installed.
Qt v4.7.0 free edition is being used.
SIP 4.13.2 is being used.
The Qt header files are in /usr/include/qt4.
The shared Qt libraries are in /usr/lib.
The Qt binaries are in /usr/bin.
The Qt mkspecs directory is in /usr/share/qt4.
These PyQt modules will be built: QtCore, QtGui, QtHelp, QtNetwork, QtDBus,
QtDeclarative, QtOpenGL, QtScript, QtScriptTools, QtSql, QtSvg, QtTest,
QtWebKit, QtXml, QtXmlPatterns, QtDesigner.
The PyQt Python package will be installed in /usr/lib/python3/dist-packages.
PyQt is being built with generated docstrings.
PyQt is being built with 'protected' redefined as 'public'.
The Designer plugin will be installed in /usr/lib/qt4/plugins/designer.
The PyQt .sip files will be installed in /usr/share/sip/PyQt4.
pyuic4, pyrcc4 and pylupdate4 will be installed in /usr/bin.
Generating the C++ source for the QtCore module...
sip: /home/akhil/Desktop/PyQt-x11-gpl-4.9.1/sip/QtCore/QtCoremod.sip:28: syntax error
Error: Unable to create the C++ code.

---

### Post by micramm on 2012-04-23
I had the same issue, it was resolved by installing the latest snapshots of the next versions of SIP and PyQt from [http://www.riverbankcomputing.co.uk/software/pyqt/intro](http://www.riverbankcomputing.co.uk/software/pyqt/intro)

---

