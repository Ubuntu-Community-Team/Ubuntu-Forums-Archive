---
title: "&quot;Package operation failed&quot;"
date: 2010-04-04
forum: General Help
---

### Post by Mephistopelus on 2010-04-04
Hi, peoples. I have an annoying trouble on my 9.10 X64:
When i try to install or delete some program from my software center, i got this alert message "Package operation failed" and it is isn't depends on what i whant to install/uninstall. When i got this alert in installing process (usual on 90-95% of installation) , program installs, but not properly...
HELP!
*This is what in alert details:*
> installArchives() failed: (Reading database ... 
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
(Reading database ... 182832 files and directories currently installed.)
Removing gcursor ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...

---

### Post by ajgreeny on 2010-04-04
Try ```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Mephistopelus on 2010-04-04
> **ajgreeny said:**
> Try ```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
It helped, but after system restart, all the same.:sad:

---

### Post by AlexFox on 2010-04-04
Can you try installing an application with apt-get, and see if it provides more feedback about what the problem may be?

---

### Post by Mephistopelus on 2010-04-04
> **AlexFox said:**
> Can you try installing an application with apt-get, and see if it provides more feedback about what the problem may be?
It weird, but when i tried to install application, (which give me an alert when i installed it), terminal says, that it already installed.  Than i tried to remove it by the terminal command, and this is what it write:
```
mephistopelus@LinuX-Based:~$ sudo apt-get remove hplip-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-reportlab libqt4-test libqt4-script libqt4-designer intltool-debian
  python-renderpm libqt4-xmlpatterns libqt4-help python-qt4 mplayer-skins
  python-sip4 libqt4-sql libqt4-svg libqt4-assistant python-qt4-dbus html2text
  libqt4-sql-mysql libqt4-scripttools python-reportlab-accel
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  hplip-gui
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 139kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 203966 files and directories currently installed.)
Removing hplip-gui ...
Processing triggers for desktop-file-utils ...
**E: Directory '/var/log/apt/' missing**

```
This "E: Directory '/var/log/apt/' missing" message i receive pretty often, despite that i make it by "mkdir" many times before.

---

