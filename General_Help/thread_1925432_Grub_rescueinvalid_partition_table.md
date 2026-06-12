---
title: "Grub rescue/invalid partition table"
date: 2012-02-14
forum: General Help
---

### Post by jamesp92 on 2012-02-14
Okay so the other day i installed ubuntu 11.10 on my system to run alongside windows 7, i then uninstalled ubuntu, then went back into windows and deleted what i thought were just ubuntu partitions. 

however on restart all i get is grub rescue after bios.

ive tryed booting ubuntu on usb from bios boot menu, it then just says invalid table partition.

im really stuck here, i have no idea what to do. if i cant sort it myself i will have to take it to a repairs shop and i dont really want to do that.

by the way its on a m11x so i have no cd drive, usb is the only option for booting.

Thanks, James.

---

### Post by jamesp92 on 2012-02-14
Help me please someone! :D

---

### Post by oldfred on 2012-02-14
Computers boot from a small bit of code in the MBR called the boot loader. Now that is so small that all it does is link to more code elsewhere. Grub is looking for the partition you have deleted.

You need to install the Windows boot loader. Do you have a Windows repairCD. You should have repairCD or USB for the current version of every system you have installed.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

If you have a working Ubuntu liveUSB, you can install a boot loader that works just like Windows. You just want the part of lilo

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by jamesp92 on 2012-02-14
Thanks oldfred ill give it a go

---

### Post by jamesp92 on 2012-02-14
hmm i think the problem is deeper than this, the system is coming up with grub rescue which is obviously ubuntu. however there is no ubuntu system on the drive just windows 7, im confused.

---

### Post by efflandt on 2012-02-14
As mentioned, the MBR is rather small, so it only has room for a small stub of grub that tries to jump to more of itself and configuration in the /boot/grub directory that you removed when you removed the Ubuntu partition(s).  So you get grub rescue instead of a full grub because grub cannot find the rest of itself.

You need to replace the MBR with a standard MSDOS/Windows MBR which would be easy from a Windows system disk.  But that MBR is identical to, or at least works the the same as the MBR for **lilo** or **syslinux**, so the mbr of either of those can be used.

You also need to make sure that the proper partition is marked as the boot partition, which may not be obvious.  For example my Dell had 3 partitions, a utility partition, RECOVERY, and OS (Win7), at it actually booted the RECOVERY partition (sda2), the Windows partition (sda3).  Hopefully when you deleted partitions you did not delete something essential to Windows.

---

### Post by jamesp92 on 2012-02-15
okay so heres what ive done, ive installed ubuntu 11.10 onto an external hard drive, i set to boot it and my laptop came up with "exiting intel PXE rom then "invalid partition table" so im guessin my only option is to boot the ubuntu from external hdd through grub rescue.

what commands should i use?

---

### Post by oldfred on 2012-02-15
Did you install grub to the external drive's MBR?

The exiting PXE boot is where the BIOS cannot find anything to boot and trys booting from the network.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

and/or
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

