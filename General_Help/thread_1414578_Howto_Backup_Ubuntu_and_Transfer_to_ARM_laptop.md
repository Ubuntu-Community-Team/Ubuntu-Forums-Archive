---
title: "Howto: Backup Ubuntu and Transfer to ARM laptop"
date: 2010-02-23
forum: General Help
---

### Post by Martiini on 2010-02-23
Request:

Tutorial for a complete novice how to back up Ubuntu partition (recommended backup applications, commands) and transfer to different hardware (from Intel laptop to ARM laptop). 
Specifically, copy Ubuntu from "HP AMD Turion 64 X2 TL-58" to  "Netwalker i.MX515 Cortex-A8"
[http://www.engadget.com/2009/08/27/sharps-5-inch-pc-z1-netwalker-honors-the-zaurus-legacy/](http://www.engadget.com/2009/08/27/sharps-5-inch-pc-z1-netwalker-honors-the-zaurus-legacy/)

Which partition imaging tools or commands would one use?
Does one have to switch kernels, modules - if so, how?

---

### Post by Martiini on 2010-02-24
bump ... anyone .. how do I find out, please ... dd or clonezilla or ghost or...

---

### Post by julipanno on 2010-02-26
As the hardware is vastly different on the two computers, you can't reuse your existing installation from one on the other. You have to install a new Ubuntu on the ARM laptop. The ARM version of Ubuntu is also not displayed on the standard download page; you have to go to Alternative Download Locations, choose your closest one and find the file that is called ubuntu-9.10-desktop-armel+imx51.img  

You can, however, transfer your home folder once you have installed Ubuntu, by simply copying its contents to the same folder on the new laptop.

---

### Post by switch10 on 2010-02-26
I would just copy your /home folder somewhere, and restore it on a fresh install.  you will have to re-install packages, but all of your settings will be there.  you can do the same with etc/sources.list and /etc/fstab.  And others that you may have edited,

---

