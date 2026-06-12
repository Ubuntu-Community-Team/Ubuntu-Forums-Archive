---
title: "XSane error message"
date: 2010-02-02
forum: General Help
---

### Post by amoht on 2010-02-02
I have recently installed Ubuntu 9.04 and couldn't access my SCSI scanner. After searching the posts I found how to, by writing a udev.rule. However when I click on XSane an error message appears "Failed to create file.Permission denied". When I close this the XSane screen comes up and I can use the scanner. On closing XSane the error message again appears and I have to close it 3 times before I can exit.
Could someone advise me what file XSane is trying to create and how to stop this error message appearing? It doesn't appear if I start XSane by  sudo XSane, so I presume that only root has the permission to write the file.

Alan

---

### Post by plucky on 2010-02-02
Open a terminal and ```
ls -l ~/.sane
``` and make sure you are the owner of the folder.

See this [link](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/96011)

Good Luck

---

### Post by amoht on 2010-02-02
Thanks for the help. I changed the owner of ~/.sane and the error message no longer  occurs,

Problem fixed.

Alan

---

