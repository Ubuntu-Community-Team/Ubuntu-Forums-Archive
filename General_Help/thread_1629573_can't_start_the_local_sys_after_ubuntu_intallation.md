---
title: "can't start the local sys after ubuntu intallation in U-disk"
date: 2010-11-23
forum: General Help
---

### Post by Danicaell on 2010-11-23
help!!!!!
 
I can't start the sys after I intalled ubuntu in U-disk.The boot menu was in the U-disk not the local machine.
 
The error " no such device grub ".
 
The machine will boot from the U-disk.I don't know how to change the grub and boot the local sys from the local machine not the U-disk.
 
 
Thanks!!Does anyone give me a hand~thanks very much!!!

---

### Post by efflandt on 2010-11-23
It sounds like you accidentally put grub in the mbr of your main hard drive instead of on the USB disk.

First install grub on the mbr of the USB drive by booting to Ubuntu on that. Then to make sure that you know which drive is your USB drive type mount in a terminal and see which drive is /.  If you only have one internal drive, the USB drive would typically be /dev/sdb, but if you have a multi-card reader it might end up /dev/sdf (don't pay attention to the number at the end of the / device, just the letters).  Then in this case assuming it is /dev/sdb (or substitute that with your actual USB drive if something else) do:

**sudo grub-install /dev/sdb**

Then reboot from the USB drive and do:

**sudo update-grub**

How to restore your Windows mbr on your main hard drive depends upon which Windows version.  If it is WinXP, if you can boot a Windows disk to the recovery console you can run **fixmbr**.  Or for Vista or Win7 run **bootrec /fixmbr**.  Or this tells you how to do that from Ubuntu [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

