---
title: "Need to uninstall Linux kubuntu from portable hard drive and grub too"
date: 2010-12-30
forum: General Help
---

### Post by Bbwhizkidlinux on 2010-12-30
Hi I have installed 
Kubuntu onto a 1tb portable hard drive and I always have to boot from it and grub.  I want to uninstallit and go back to windows 7 that is on my built in hard drive on my hp laptop.
:confused::confused:

---

### Post by Scooter_X on 2010-12-30
...so you can use the 1TB just for storage/backup on the side, I assume?

How did you originally install Kubuntu onto the 1TB HD? Did you just run the installer and let it do all the default stuff?

---

### Post by oldfred on 2010-12-30
If you do not do the manual install and choose to put grub on the external drive it defaults to the drive you normally boot or the internal.

You need to reinstall a windows boot loader to the internal drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you want to keep your Kubuntu, you should boot into it and from it install grub to sdb (if sdb is your external). Then only when you in BIOS select to boot the external will grub load and let you choose either windows or Kubuntu.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then after rebooting:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first screens & besure to choose sdb as install drive.

---

