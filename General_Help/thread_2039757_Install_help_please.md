---
title: "Install help please"
date: 2012-08-09
forum: General Help
---

### Post by Hickerbilly on 2012-08-09
I want to do a clean start on my system with ubuntu and get rid of all the microsoft crap. 
I downloaded ubuntu to an SDHC card through a USB adapter and can't figure out how to install it.
I clicked the ubuntu icon in the download and it told me to reboot to start the installation... I rebooted and nothing happened.
I tried going into boot devices but... there is no choice for using the USB to boot from.
I do not have a disc drive.
Can someone please tell me how to wipe everything out on my system and install ubuntu?

---

### Post by Dngrsone on 2012-08-09
Try going into the system BIOS and enable booting from external drives, then look for a USB drive or external drive to boot from.

---

### Post by Sef on 2012-08-09
Here's how to [install]("https://help.ubuntu.com/12.04/installation-guide/i386/boot-drive-files.html") from a hard drive or the net.

---

### Post by Hickerbilly on 2012-08-09
> **Dngrsone said:**
> Try going into the system BIOS and enable booting from external drives, then look for a USB drive or external drive to boot from. 
Thanks but I do not have either of those as a choice in BIOS.
I am running a pre-released version of windows8 and it stinks!
I no longer have the ol' Restore option either and can't return to vista.:(

---

### Post by gordintoronto on 2012-08-09
> **Hickerbilly said:**
> 
I downloaded ubuntu to an SDHC card through a USB adapter and can't figure out how to install it.

If you saved the .iso onto the SDHC card, that was not a useful approach. Copy it to your hard drive, and install pendrivelinux. It will make a bootable SDHC card.

You also need to make sure your BIOS settings let you boot from an external device. It could be labelled "USB hard drive", or something like that. Even though the SDHC is not a hard drive, it looks like one for booting.

---

