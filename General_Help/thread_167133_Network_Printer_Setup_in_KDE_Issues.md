---
title: "Network Printer Setup in KDE Issues"
date: 2006-04-27
forum: General Help
---

### Post by wglenncamp on 2006-04-27
I am trying to setup a printer in KControl.  But, when I go to select my network printer (Which is being shared by my wife's MS Box), I get an error in KControl that says NT_STATUS_ACCESS_DENIED.  I know that it is a good share, and I have it opened to everyone.  What gives?

Is there something that I am doing wrong?

---

### Post by daller on 2006-12-15
It happens to me too...

I don't know what causes this, but you can manually type in the name on the printer.

Workgroup: Scan finds that...
Server: Scan finds that...
Printer: Simply the share-name from the windows machine...

---

### Post by daller on 2006-12-15
**The bugreport: [https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/57666](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/57666)**

There's a workaround:
 - choose anonymous login
 - Scan the network
 - click the network group of your computer to see your computer's name
 - go back
 - choose guest login
 - click on the name of your computer
 - click on your printer's name
 - and it works ;)

---

