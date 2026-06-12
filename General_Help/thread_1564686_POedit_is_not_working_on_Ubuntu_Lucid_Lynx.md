---
title: "POedit is not working on Ubuntu Lucid Lynx"
date: 2010-08-30
forum: General Help
---

### Post by janoochen on 2010-08-30
I've been installing and uninstalling POedit 1.4.2-5build0.1 in Ubuntu 10.04 Lucid Lynx.

POedit is installed but it loads for around 10 seconds and then just go away.

I'm installing it using Synaptic

Any suggestions?

---

### Post by gordintoronto on 2010-08-31
Run it from the command line and see what error message appears.

---

### Post by janoochen on 2010-08-31
alex@alex-desktop:~$ sudo apt-get install poedit
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  poedit
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B/781kB of archives.
After this operation, 3,572kB of additional disk space will be used.
Selecting previously deselected package poedit.
(Reading database ... 165398 files and directories currently installed.)
Unpacking poedit (from .../poedit_1.4.2-5build0.1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up poedit (1.4.2-5build0.1) ...
update-alternatives: using /usr/bin/poeditor to provide /usr/bin/poedit (poedit) in auto mode.

alex@alex-desktop:~$ 

I think there's no errors

---

### Post by gordintoronto on 2010-09-01
Run the program (not the installation) from the command line.

---

