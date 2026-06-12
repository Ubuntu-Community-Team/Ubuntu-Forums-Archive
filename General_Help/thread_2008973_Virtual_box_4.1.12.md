---
title: "Virtual box 4.1.12 ?"
date: 2012-06-23
forum: General Help
---

### Post by cowboy7305 on 2012-06-23
I am playing around with VB 4.1 and have loaded it onto Ubuntu 12.04 and have put win7 into VB all well 
been looking to expand the VB window and i keep reading use the guest add-ons that are to be found in the device manager, i cant find any thing that says device manager, i cant find guess add ons 
any help please

---

### Post by QIII on 2012-06-23
In the upper left toolbar for VBox, you will see "Machine", "View", "Devices" and "Help"

Click "Devices".  Click "Install Guest Additions..."

Restart your guest machine.

When it restarts, go to "Computer" and you will see a new device called "VirtualBox Guest Additions".  Right click, Open and find VBoxWindowsAdditions.  Run the .exe that corresponds to your architecture -- x86 or amd64.

Restart your guest machine.

When it opens,  go back to the VBox top menu.  Check "Auto-resize Guest Display"

RightCntl+F will toggle full screen mode on and off.

---

### Post by cowboy7305 on 2012-06-23
many thanks i keep forgetting about the icons on top panel

---

### Post by andrew.46 on 2012-06-24
Might be worthwhile installing a more recent version, 4.1.18 is out now with the usual small list of bug fixes:

[https://www.virtualbox.org/wiki/Changelog](https://www.virtualbox.org/wiki/Changelog)

---

