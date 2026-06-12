---
title: "creating a dual-boot of windows 7 with ubuntu installed first"
date: 2012-04-19
forum: General Help
---

### Post by toastermm on 2012-04-19
Hi, I'm running ubuntu 11.10 (oneric) x64, and have decided to run a dual boot with windows 7.  I have a windows 7 dvd for installation, and have found many guides to setting up a dual boot.

The problem is that these guides that I've found are for installing a dual-boot system on top of windows.  I need to do it the other way around.  I have ubuntu 11.10 all set up and tweaked the way I want it.  I would like to dual boot windows 7.

Again, I'm looking for how to dual boot windows 7 with ubuntu x64 when ubuntu is already installed and windows 7 isn't.  I thought I would ask before I screw everything up.  Has anyone done this and know how?

---

### Post by kc1di on 2012-04-19
Ideally windows should be intalled first. as it must have the first partition. Doesn't like to think it's sharing the drive with anyone.
But it can be done there is some good advice here:

[http://askubuntu.com/questions/92874/how-do-i-install-windows-7-alongside-a-pre-existing-ubuntu-installation]("http://askubuntu.com/questions/92874/how-do-i-install-windows-7-alongside-a-pre-existing-ubuntu-installation")

Good Luck

---

### Post by oldfred on 2012-04-19
Windows does not have to be the first partition but does have to be a primary partition formated NTFS and with the boot flag. Some have reported issues where they create a primary after the extended and have issues. Windows does read extended partitions if a NTFS partition, but does not see the Linux partitions correctly and can create issues with partition table.

[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

In kc1di's link is a recommendation for Boot-Repair. Many have used it and found it works well. You can download it into the Ubuntu liveCD or download it as a full liveCD. Worthwhile to have in tool box of repair CD/USBs.

---

