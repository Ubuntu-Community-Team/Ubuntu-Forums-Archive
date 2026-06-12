---
title: "Boot Ubuntu from USB"
date: 2011-01-06
forum: General Help
---

### Post by ErichFranz on 2011-01-06
I want to boot Ubuntu from a flash drive.  I'm using Universal USB installer to do it, but I would like to know how do it without using Universal USB installer.  How would I go about doing this?  Do I just format the USB with the correct file system and move the iso file to the USB or is it more complicated than that?

---

### Post by C.S.Cameron on 2011-01-06
There are several methods besides Universal, none as simple as just putting the iso on USB, these include:

Startup Disk Creator from the Live CD.
Unetbootin.
MultiBootUSB  [http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

You can also do a Full install to USB similar to internal HDD.

---

### Post by Merlin2007 on 2011-01-06
Here is a method using a live ubuntu cd.

[http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/](http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/)

---

### Post by ErichFranz on 2011-01-06
I guess what I was asking is, how can I do it manually, without having to use a program.

---

### Post by C.S.Cameron on 2011-01-06
> **ErichFranz said:**
> I guess what I was asking is, how can I do it manually, without having to use a program.

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

Shows how to manually boot iso files using Grub2.
Same as the method used in the MultiBootUSB script.

Check out pendriveLinux.com for other manual methods.

---

### Post by oldfred on 2011-01-06
I did it totally manually, the issue was finding the correct boot stanza to paste into grub. Before they posted some of the scripts posted above I used panticz as reference.

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)


I have also downloaded the scripts and looked at the bash script to find what they paste into grub.cfg.

---

