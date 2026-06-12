---
title: "Booting from secondary HD"
date: 2010-09-18
forum: General Help
---

### Post by theXact on 2010-09-18
I have an HP computer which I recently installed Ubuntu on with a secondary HD that I installed. I set this new hard drive as the primary hard drive and it was working fine booting up GRUB and asking if I wanted to use Windows 7 or Ubuntu.  This morning, however, it has stopped doing this and goes straight into Windows 7.  If I go into the boot menu and tell it to boot with the primary hard drive it will go into GRUB, but otherwise it seems as if it is going straight to my secondary HD with Windows 7 on it.  This seems weird since up until today it was working fine.  

Does anyone know why this is and how to fix it? I tried reinstalling Ubuntu but that didn't change anything.

---

### Post by blueridgedog on 2010-09-18
Your bios will load the boot loader it finds in the drive listed as the first boot drive.  When you install Ubuntu you are asked where to install GRUB, this is typically in the boot sector of the primary hard drive.  If your system fails to load GRUB, it means it is booting from the other drive, indicating that the other drive can't be seen by the bios when the system is powered on or that the bios is configured to boot from the other drive.

---

