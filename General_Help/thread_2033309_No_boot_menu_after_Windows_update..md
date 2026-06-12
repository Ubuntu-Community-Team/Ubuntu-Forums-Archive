---
title: "No boot menu after Windows update."
date: 2012-07-25
forum: General Help
---

### Post by StickyMick on 2012-07-25
Installed Ubuntu on a friends laptop (Windows Vista) as a dual boot.
A few days ago he tells me that the boot options menu no longer shows when starting up after doing Windows updates.
I haven't had access to the laptop since then, but I want to know in advance how to solve the issue.

I have 1 idea that Windows Update has reset the boot options to defaults (Single O/S Only), so just boots straight through to windows. I'm guessing a visit to Windows boot options and just re-enable the O/S choice boot menu, or is it a bit more complicated than that.

Any help muchly appreciated. :D

---

### Post by oldfred on 2012-07-26
Best to have several repair tools handy. 

Windows repairCD. Should be same version, but I have run chkdsk from Windows 7 64 bit on my XP install.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


Current version of Ubuntu liveCD or USB (if system boots from USB).

Gui tool - often easiest but you have to download it into liveCd or download its liveCD:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

Another tool that often lets you boot a working install with broken grub2, so you can repair from inside your install.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

