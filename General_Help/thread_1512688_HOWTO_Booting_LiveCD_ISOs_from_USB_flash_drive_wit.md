---
title: "HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 - Please Update this."
date: 2010-06-18
forum: General Help
---

### Post by emarkay on 2010-06-18
[I]"In this tutorial you will prepare a USB  flash drive to make it bootable. After you booted it it shows you a menu  where you can choose which live system you want to boot.

So you might be interested in this tutorial if:[/I]   
[LIST]
[*]*You want to have multiple live systems on one USB flash drive*
[*]*In the future you want to create a new bootable live system just by  copying the ISO file onto the drive and edit the grub.cfg*
[*]*You don't want to or can't use Distro specific LiveUSB creator tools*
[*]*You prefer a cleaner solution than the most LiveUSB creator tools  which create several folders and files at the device root*
[*]*You  are feeling bored and want to see cool features of Grub2*
[/LIST]
*If you have a Grub2 version with Lua support you even don't need to  manually edit the grub.cfg when you add new or remove live systems."*

Remainder of information is found here:
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

This was found in a closed Karmic Development forum - can this be validated and updated if needed for Lucid?

---

### Post by philinux on 2010-06-18
Why not PM the poster?

---

### Post by oldfred on 2010-06-18
I think I used that site and these although panticz is a full script where I only used a few commands from it and the other sites.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

I did it with Karmic's grub2 but copied Lucid beta, RC and release onto the USB flash drive for install without any issues.

Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

---

