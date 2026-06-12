---
title: "GRUB dosen't find Windows Server 2008 R2"
date: 2010-11-21
forum: General Help
---

### Post by Adrenaline Rampage on 2010-11-21
Hi!

I want to dual boot Windows Server 2008 r2 and Ubuntu 10.10 . First, I installed Server 2008 r2 then Ubuntu. After the installation, Grub only found Ubuntu, and "Windows Recovery Enviroment (loader)" on dev/sda1. The Windows OS is installed on dev/sda2.
When i load "Windows Recovery Enviroment (loader)" it does a chdsk, then reboot the PC.

How can i make grub find the Windows OS?

Edit: The partition on dev/sda1 is called System Reserved

---

### Post by Adrenaline Rampage on 2010-11-21
When i open gParted, it gives a warning about dev/sda1:

"Unable to find mounting point
 Unable to read the contents of this file system
 Because of this, some operations may be unavailable

 The following list of software packages is required for ntfs filesystem support: ntfsprogs "

---

