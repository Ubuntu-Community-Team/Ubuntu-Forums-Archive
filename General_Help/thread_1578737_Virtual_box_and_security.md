---
title: "Virtual box and security"
date: 2010-09-20
forum: General Help
---

### Post by spuny on 2010-09-20
If I installed MS-Windows/Chrome OS on Virtualbox and one of them got virus, will ubuntu get that virus too or it's safe? because I want to remove windows permanently and only have it on Virtualbox in case I needed it. And what should I disable in Virtualbox in case someone hacked my windows so he won't get access to ubuntu.

---

### Post by snowpine on 2010-09-20
If your virtual machine gets infected, the infection will be confined to the virtual machine. :) (However, be careful with shared folders.)

Furthermore, if you use the "snapshot" feature, you can roll back to before you got infected, very handy!

---

### Post by CharlesA on 2010-09-20
Windows viruses cannot affect Ubuntu. However, they can affect other Windows machines.

---

### Post by SeijiSensei on 2010-09-21
You might also take a look in /home/username/.Virtualbox.  (You'll probably have to tell nautilus or dolphin to show "hidden" files, which are files whose names begin with a period.)  You'll see a directory called HardDisks in which the machine images are stored in files with .vdi extensions.  Once you got Windows configured as you like it, you can copy the drive image to another location to insure you have a safe copy you can revert to if things go awry.

---

### Post by CharlesA on 2010-09-21
> **SeijiSensei said:**
> You might also take a look in /home/username/.Virtualbox.  (You'll probably have to tell nautilus or dolphin to show "hidden" files, which are files whose names begin with a period.)  You'll see a directory called HardDisks in which the machine images are stored in files with .vdi extensions.  Once you got Windows configured as you like it, you can copy the drive image to another location to insure you have a safe copy you can revert to if things go awry.

It's easier just to use "Export Appliance" from the file menu in VirtualBox.

---

