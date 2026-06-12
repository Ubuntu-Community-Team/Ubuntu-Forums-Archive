---
title: "xsane - no devices available"
date: 2012-10-06
forum: General Help
---

### Post by Quarkrad on 2012-10-06
Running 12.04 on two local pc's.  I have a hp (photosmart premium) printer/scanner that is usb connected to a desktop.  xsane gives the message above in the title and installing Skanlite also gives **Sorrv. No devices found.**  I have another desktop in the same room that is wirelessly connected to the same printer/scanner and that is able to scan fine.  Both desktops are using the same 'latest' hplib driver so I need help.  Scanning use to work - perhaps it was an upgrade via Software Update some where but both machines are up to date.  Any help appreciated.

---

### Post by Quarkrad on 2012-10-06
Launched hp Device Manager.  Configure/Preferences then commands(Advanced) tab.  At bottom of window click on Set Defaults.  Problem solved - error in /usr/bin/simple-scan %SANE_URI% line.

---

### Post by lisanels47 on 2013-01-04
I had the same issue.  Fixed with the following line:

apt-get install hplip-gui

---

