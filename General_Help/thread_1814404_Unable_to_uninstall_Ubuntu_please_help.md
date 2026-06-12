---
title: "Unable to uninstall Ubuntu please help"
date: 2011-07-29
forum: General Help
---

### Post by arronbartle on 2011-07-29
Hello, Ubuntu is too complicated for me... but when I am trying to uninstall Ubuntu, it will not let me, it is giving me the error message:  
An error occured:

The file or directory is corrupted and unreadable removing C:\ubuntu

For more information, please see the log file : c:docume~1\admini~2.arr\locals~1\temp\wubi-11.04-rev211.log



please can someone help, thanks, Arron.

---

### Post by linuxuser12345 on 2011-07-29
Have you installed Ubuntu through the Wubi program in Microsoft Windows?

---

### Post by arronbartle on 2011-07-29
whats the wubi program? where can i locate it?

---

### Post by linuxuser12345 on 2011-07-29
Did you install Ubuntu using Microsoft Windows, or did you boot your system up using the LiveCD or LiveUSB program to install it directly?

---

### Post by linuxuser12345 on 2011-07-29
And here is the "Wubi" Windows Installer:
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

### Post by Mark Phelps on 2011-07-29
> **linuxuser12345 said:**
> Have you installed Ubuntu through the Wubi program in Microsoft Windows?

Did you NOT see the "wubi" in the log file name?

---

### Post by linuxuser12345 on 2011-07-29
> **Mark Phelps said:**
> Did you NOT see the "wubi" in the log file name?
Omg, lol! I need to start reading the stuff that looks like it doesn't matter -.-

---

### Post by linuxuser12345 on 2011-07-29
Maybe this posting will help you? [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can also try re-installing Ubuntu and then trying to uninstall again.

---

### Post by bcbc on 2011-07-29
If it's corrupt then you probably have some ntfs file system issue that's preventing the \ubuntu directory from being deleted. You need to run chkdsk: 
go to my computer, right click on C:, Properties, Tools, Check disk for errors, check "fix automatically". It will tell you the drive is in use and ask to schedule for the next time you boot. Agree, and reboot to complete.

This will likely fix the problem. If the automatic uninstall is unavailable after that then there is the manual option covered here: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

