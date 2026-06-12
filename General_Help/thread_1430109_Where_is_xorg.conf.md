---
title: "Where is xorg.conf"
date: 2010-03-14
forum: General Help
---

### Post by satimis on 2010-03-14
Hi folks,

Host - Ubuntu 9.10 64bit
virtualizer - Sun VirtualBox
VM - Ubuntu 9.10 64bit

On VM;
I need to edit xorg.conf to sort out the problem on display resolution, color depth, languages, etc.  But I can't find /etc/X11/xorg.conf

Please help.  TIA

B.R.
satimis

---

### Post by lidex on 2010-03-15
xorg.conf was deprecated somewhere around Jaunty. You can, however, create one and it will be utilized.

---

### Post by mikemelen on 2010-03-15
One of the changes on the Ubuntu 9.10 is that xorg.conf is missing. The reason for this is that the configuration to be done on user level. The file xorg.conf will be in use only if it exists.

In order to generate xorg.conf you need to switch to one virtual console using the key combination CTRL + ALT + F1.


 Now execute the following commands:


 **# sudo service gdm stop**
 This command will stop the X.
 Now we need to generate the xorg.conf file:
 **# sudo Xorg -configure**
 This has generated the file in ~/xorg.conf.new.
 We need to make the X using it so we have to put this file inside /etc/X11/
 **# sudo mv ~/xorg.conf.new /etc/X11/xorg.conf**
 After moving this file to the proper location you can start the X again and see what happens:
 **# sudo service gdm start**

---

