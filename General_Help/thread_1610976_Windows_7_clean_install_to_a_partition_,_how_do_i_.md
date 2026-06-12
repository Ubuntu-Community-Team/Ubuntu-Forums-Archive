---
title: "Windows 7 clean install to a partition , how do i keep grub?"
date: 2010-11-01
forum: General Help
---

### Post by cor2y on 2010-11-01
Ok so i am going to install windows 7 into a partition on which ubuntu 10.10 is the main os but xp is installed on the partition i plan to wipe and install windows 7.
However i see that windows 7 bootloader does not play nice with linux i have been searching online and have been seeing complicated  methods as well as third party apps/bootloaders that have to be installed in order to get windows to play well with linux if you are installing windows after ubuntu instead of the other way around.
Can anyone point me to a clear and concise tutorial?

---

### Post by WorMzy on 2010-11-01
You can't keep grub installed immediately after a Windows installation. However, [you can reinstall grub fairly easily]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html"). I would recommend that you do this rather than messing around with other bootloaders.

---

### Post by EricJonsson on 2010-11-01
This is somewhat tricky. The Windows installer will create two partitions, one of which will overwrite MBR and the other that holds the actual Windows installation. The first one is quite small and holds (among other things) the Windows bootloader. This is what GRUB chainloads in most dual-boot setups.

Furthermore, you have no option of where to place this special Windows partition -- it automatically installs to the first harddrive.

My strategy was to install Windows onto the first harddrive, then switch a few cables and make the disk with Ubuntu the first one. That way I could load GRUB at startup and then chainload into the Windows 7 bootloader if I so wished.

---

### Post by Quackers on 2010-11-01
It seems that when Windows 7 comes pre-installed it creates 2 primary partitions, one for a couple of boot files and the other for the main system and remaining boot files, as EricJonsson has said. However I installed W7 just last week and it has installed in only one partition.

---

### Post by oldfred on 2010-11-01
Windows creates the two partition version on new installs to a empty drive or to free space where two primary partitions are available. It wants a separate boot partition in case you want to encrypt the primary partition.

But if over installing Vista, XP, or install to a previously created NTFS partition it will install to one primary partition. Make sure you have a primary partition or it will not install. You also need the boot flag on the partition, although it should add it, if not there.

To reinstall grub you can use WorMzy's link and sometimes that version is required. But usually you can use a simplified version. Just make sure you have a working liveCD or USB flash that boots a liveCD or working install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by cor2y on 2010-11-06
Hi folks, thanks for the feedback and help.
So i went ahead and did the microsoft way of doing things and while it did install widows 7 somehow it ended up eating/murdering/making my root partition unallocated space, thankfully /home was not affected.
So i had to reinstall ubuntu however now i had a new mbr thanks to windows 7 taking over everything but a quick reboot into the live usb key and reinstalling grub2 got me back to ubuntu and updating grub within the install put windows 7 now in the grub menu.
So hopefully things will be alright now.

---

### Post by Quackers on 2010-11-06
That sounds like a bit of work. The outcome is good though. It is usually better if W7 is the first installed OS as it likes to think it is the only OS on the system. It has ideas of grandeur (wrongly, I have to say! :-) )

---

### Post by cor2y on 2010-11-07
Yes if i had known about [this thread]("http://ubuntuforums.org/showthread.php?t=1154829") before re-installing ubuntu it could have saved me some time.
Turns out this is business as usual for windows 7 if you dont first preformat the space to ntfs, you plan to use if you dont it unallocates your nearest partition.

---

