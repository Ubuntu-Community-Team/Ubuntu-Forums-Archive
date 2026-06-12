---
title: "Connect to samba printer and samba file server w/ Lubuntu"
date: 2011-03-09
forum: General Help
---

### Post by vacco on 2011-03-09
My university provides instructions for connecting to their printers and network shares in Ubuntu. They work pretty smooth, but I've run into a couple of problems when trying to follow these instructions in Lubuntu:

1. Windows Printer via Samba printer is missing under Add-->Network Printer in the printer utility (system-config-printer 1.2.3, same one as in standard Ubuntu) I'm guessing I need to install some samba related packages that standard Ubuntu includes by default, but which ones?

2. To access network disks in standard Ubuntu, for example your pesonal space, you select Go-->Location in Nautilus and enter an address of the format smb://something.university.domain/resource. How can I access such locations with PCManFM?

---

### Post by SteveDee on 2011-03-10
> **vacco said:**
> ...I'm guessing I need to install some samba related packages that standard Ubuntu includes by default, but which ones?

...How can I access such locations with PCManFM?

This may help: [http://ubuntuforums.org/showthread.php?t=1623346](http://ubuntuforums.org/showthread.php?t=1623346)

---

### Post by Morbius1 on 2011-03-10
> 1. Windows Printer via Samba printer is missing under Add-->Network Printer in the printer utilityInstall the following packages - some of them may already be installed but it will tell you that:
```
sudo apt-get install smbclient
sudo apt-get install libsmbclient
sudo apt-get install python-smbc
```[COLOR=Blue][B]
EDIT:[/B][/COLOR] Um .... you may have to restart cups after installing those packages:
```
 sudo service cups restart
```

---

