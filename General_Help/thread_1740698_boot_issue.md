---
title: "boot issue"
date: 2011-04-27
forum: General Help
---

### Post by thomas515 on 2011-04-27
ok so I have an HP Pavilion that was/still is running Vista.  I recently decided to dual-boot to Ubuntu from an external hard drive.  Both systems will boot up fine its just that for some reason it won't boot to the internal drive (with vista) unless the external is connected.  I just put the HD in another laptop only to have the same problem.  Any ideas on how to correct this?

---

### Post by pAsM on 2011-04-27
> **thomas515 said:**
> ok so I have an HP Pavilion that was/still is running Vista.  I recently decided to dual-boot to Ubuntu from an external hard drive.  Both systems will boot up fine its just that for some reason it won't boot to the internal drive (with vista) unless the external is connected.  I just put the HD in another laptop only to have the same problem.  Any ideas on how to correct this?
Hello,
    It seems that you overrode the Windows Boot Loader, fortunately this can be corrected
[INDENT]1) Boot into the Vista Install Disk
2) Go through he Keyboard Setup
3) Select "Repair My Computer"
4) Choose the option to launch a command prompt
5) Type bootrec.exe /FixMbr 

The bootrec.exe /FixMbr will tell windows to overwrite the MBR on your hard disk and replace it with the stock Windows MBR
[/INDENT]

---

### Post by thomas515 on 2011-04-27
Will i still be able to boot to the external as well?

---

### Post by thomas515 on 2011-04-27
Also I'm not sure if I still have the disk.

---

### Post by oldfred on 2011-04-27
You can do it all from Ubuntu. Lilo works just like the windows boot loader in the MBR as it searches for the partition with the boot flag and jumps there. We just do not install the full lilo boot loader as we still want to boot with windows. You also have to install grub2 to the MBR of the external probably sdb.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

You should have a repair CD or liveCD for every operating system you have installed.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by pAsM on 2011-04-27
> **thomas515 said:**
> Will i still be able to boot to the external as well?
Yes you will

---

### Post by oldfred on 2011-04-27
After installing grub2's boot loader to the  MBR of the external, you have to in BIOS set the external as first to boot. It will then boot grub, and if external not found it defaults to the internal drive and boots windows.

Grub will give you a choice to boot Ubuntu or windows.

If not already showing windows as  a choice, from Ubuntu:

sudo update-grub

---

### Post by thomas515 on 2011-04-28
> **oldfred said:**
> You can do it all from Ubuntu. Lilo works just like the windows boot loader in the MBR as it searches for the partition with the boot flag and jumps there. We just do not install the full lilo boot loader as we still want to boot with windows. You also have to install grub2 to the MBR of the external probably sdb.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

that worked perfectly.  thank you so much.

---

