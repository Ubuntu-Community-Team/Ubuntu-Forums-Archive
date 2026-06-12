---
title: "Unable to boot Ubuntu 11.04 with Grub2"
date: 2011-05-02
forum: General Help
---

### Post by Toyota4Runner on 2011-05-02
Just finished installing Ubuntu 11.04 32 bit version from the alternate cd.  This is a clean install.  1 IDE drive with only Ubuntu installed on the computer.  Installed without any errors.  After rebooting I was presented with the Grub 2 shell.  Rebooted the system with the CD in the drive and selected the rescue a broken system.  Dropped down to a shell with root of /dev/sda1 (the installed partition) and removed and purged both grub-pc and grub-common (apt-get remove grub-pc grub-common --purge).  Re-installed grub-pc and grub-common (apt-get install grub-pc grub-common).  Installed grub to /dev/sda (MBR).  Grub installed successfully with no errors.  Rebooted the computer and still just get the Grub 2 Shell.  I have included the output of Boot Info Script as an attachment.

Thanks in advance for all the help

---

