---
title: "Unistalling ubuntu"
date: 2006-02-22
forum: General Help
---

### Post by suckmetal on 2006-02-22
i installed ubuntu 5.10 on the same drive as windows but was having problems loading it. i was getting grub error#21. so i used fixmbr from windows boot to switch back to windows. i want to delete the linux partition on the drive and reinstall it. i tried using GParted live cd, i booted using it. it goes on the main screen, and shows scanning for drives and then shuts down. How do i delete that partition? :confused:

---

### Post by gibson on 2006-02-22
well you can use something like partitionmagic in windows, however, i think it is better you just put in the install disk again and overwrite and format your linux partition - there is no need to delete

---

### Post by ajgreeny on 2006-02-22
You don't need to uninstall ubuntu in order to reinstall, just start again at the beginning and do an install using the partitions you already have ubuntu on as the place where you put it this second time.
Error 21 means that grub couldn't find the disk for some reason and this may be more to do with your BIOS than either grub or ubuntu.  One possible answer is to put grub on a floppy if you have a floppy drive (I seem to remember there is an option to do this when you install) and then boot from floppy.  Once this is all OK you can transfer grub to the MBR using sudo grub-install /dev/hda or wherever your MBR is.  Good luck.

---

