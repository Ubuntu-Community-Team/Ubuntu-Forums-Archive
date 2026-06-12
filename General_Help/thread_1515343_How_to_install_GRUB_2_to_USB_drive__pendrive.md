---
title: "How to install GRUB 2 to USB drive / pendrive"
date: 2010-06-22
forum: General Help
---

### Post by sundar_ima on 2010-06-22
I know this can be done with install-grub command in recent ubuntu release.  How can i install it from puppy linux or distro which does not use grub 2. Will my pendrive boot if i copy /boot/grub from ubuntu 10.04 live cd to /boot/grub of my pendrive?

---

### Post by sundar_ima on 2010-06-24
Any help???

---

### Post by oldfred on 2010-06-24
I installed grub2 to a 4GB flash drive and boot several ISOs directly. If you have another system on the flash drive you would have to figure out the correct grub2 entry for that system.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

---

### Post by sundar_ima on 2010-06-25
> **oldfred said:**
> I installed grub2 to a 4GB flash drive and boot several ISOs directly. If you have another system on the flash drive you would have to figure out the correct grub2 entry for that system.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

Thank you **oldfred** for your reply.

I am aware  that this command **sudo grub-install --root-directory=/media/USBFolderName /dev/sdx** will install GRUB 2 in to pendrive. But this command will not work on puppy linux or any other distros which does not have grub 2 as its default boot manager.  How will you install in that case??

---

### Post by oldfred on 2010-06-25
Just because the default is not grub2 does not mean it cannot be booted with grub2. Figuring out the settings can be fun. If an install uses old grub I would consider a chainboot entry. That can easily be added to grub2 and old grub installed to the system partition. Not sure you can chainboot with USB as space in partition may not be available.

[http://www.murga-linux.com/puppy/viewtopic.php?t=54992&sid=9d881832f6ed599e16542410010ef851](http://www.murga-linux.com/puppy/viewtopic.php?t=54992&sid=9d881832f6ed599e16542410010ef851)

This is with boot loader in MBR change to (hdX,Y) if in PBR. Where X is drive & Y is partition.
menuentry "9.04 on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

USB drives may get renumbered depending on where the system puts them so sometimes the entires have to be adjusted.

---

### Post by C.S.Cameron on 2010-06-25
Have a look in the Puppy forums, there is discussion of grub2 booting there.

---

