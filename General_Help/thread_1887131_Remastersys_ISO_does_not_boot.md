---
title: "Remastersys ISO does not boot"
date: 2011-11-26
forum: General Help
---

### Post by CaponeSA on 2011-11-26
Hi all.  I've been using Remastersys for many years to make backups for myself and to share custom installations with friends.  I however encountered a problem with (x)buntu 11.10.  The ISO is created perfectly, but when booting it (either in a VM or on the main PC from a DVD), it hangs at the first line and does not display the liveCD GUI menu.  This happened on my pc with all Remastersys versions after 2.015.  The earlier versions did not have a liveCD GUI and the text based selection works, but even the new version 3 of Remastersys did not boot past the first line.  

The problem is due to the syslinx files.  When you have different versions of syslinux files on the PC (VMware for instance has it's own version), Remastersys possibly links to the incorrect version.

The fix is easy - put the following in an executable file (I called mine "Remastersys_Fix.sh"), run it and Remastersys works correctly again and boots the ISO into the liveCD GUI

#!/bin/bash
sudo cp /usr/lib/syslinux/isolinux.bin /etc/remastersys/customisolinux

sudo cp /usr/lib/syslinux/vesamenu.c32 /etc/remastersys/customisolinux

sudo cp /etc/remastersys/isolinux/isolinux.cfg.vesamenu /etc/remastersys/customisolinux/

sudo mv /etc/remastersys/customisolinux/isolinux.cfg.vesamenu /etc/remastersys/customisolinux/isolinux.cfg

sudo cp /etc/remastersys/isolinux/splash.png /etc/remastersys/customisolinux/


You can naturally use your own "splash.png"

---

### Post by elliotn on 2011-11-26
were do I put the .sh file , in the ISO I created with remastersys or before I create the ISO?

---

### Post by CaponeSA on 2011-11-26
Hi all, sorry I did not make my post clear enough.  The files must be copied and renamed (the .sh file will do this) BEFORE making the ISO.  The problem is that remastersys sometimes links the incorrect files as was explained, and hence compiles the incorrect files to the ISO.  This must be fixed prior to creating ISO backups.

---

### Post by elliotn on 2011-11-26
> **CaponeSA said:**
> Hi all, sorry I did not make my post clear enough.  The files must be copied and renamed (the .sh file will do this) BEFORE making the ISO.  The problem is that remastersys sometimes links the incorrect files as was explained, and hence compiles the incorrect files to the ISO.  This must be fixed prior to creating ISO backups.

my next question, were do I place the .sh, do I run it then run remastersys or? 

thanks

---

