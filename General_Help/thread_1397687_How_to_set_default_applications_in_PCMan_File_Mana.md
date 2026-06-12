---
title: "How to set default applications in PCMan File Manager?"
date: 2010-02-03
forum: General Help
---

### Post by xycris on 2010-02-03
I have tried to make my own buntu running LXDE as the desktop environment though it is running smoothly on an old laptop it has a certain problem.

I have installed PCMan File Manager as the default file manager for the LXDE and not Thunar or Dolphin, but, I have a problem with opening files from there. The default application set to open all file types is the Terminal. 

What I currently do to open the file is right click and choose "Open with.." to open the file in the appropriate application. Is there a way to set the default applications?

I have Ubuntu 9.10 from minimal CD install then got LXDE and installed the following applications aside from the applications that came with LXDE:
-OpenOffice.org suite
-Mozilla Firefox
-Google Picasa
-Wine
-VLC Player

Thanks in advance for the help.

---

### Post by mathfreak123 on 2010-02-11
Hello. I installed LXDE on Ubuntu Karmic as well, and I had the same problem.

I found the solution here on launchpad: [https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344)

I added the lucid repositories to upgrade the pcmanfm package, and then I changed them all back to Karmic. This has solved my file association issue.

---

### Post by xycris on 2010-02-11
Hi mathfreak123,

Thank you very much for this.

I have long sought for a solution and I just learned that it is a bug. I will continue to watch the thread you suggested. :D

---

