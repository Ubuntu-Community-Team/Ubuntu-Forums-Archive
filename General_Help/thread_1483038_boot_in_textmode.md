---
title: "boot in textmode"
date: 2010-05-14
forum: General Help
---

### Post by WDYSUN on 2010-05-14
Dear members,

is there any simple way to boot karmic in text mode, I want see to booting process from start to end.

I tried other solutions prposed in this (and other forums) but while some of those suggestions worked in Ubuntu 8.0 I couldn't apply them in Karmic.

Best Wishes
Pietro

---

### Post by r_s on 2010-05-14
just remove the *quiet splash* from your boot menu list

---

### Post by oldos2er on 2010-05-14
If you're using grub2, edit /etc/default/grub and change the line "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to"GRUB_CMDLINE_LINUX_DEFAULT="text"
Then run **sudo update-grub**

---

### Post by drs305 on 2010-05-14
Just to elaborate on what's been posted already. 

Removing "quiet splash" will show the text then boot to the Desktop.

Replacing "quiet splash" with "text" will leave you at a login prompt. Once logged on, if you want the Desktop type "startx".

You can also view some of the log files, such as syslog, via System, Admin, Log File Viewer to show you some of the messages you see during startup.

---

