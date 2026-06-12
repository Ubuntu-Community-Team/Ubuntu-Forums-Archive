---
title: "Make grub detect Windows Server 2k8"
date: 2012-06-05
forum: General Help
---

### Post by nisargshah on 2012-06-05
Hello,
   I have an installation of Ubuntu (Natty Narwhal) along with XP and Windows Server 2008. I had some problems due to which I had lost my MBR which made my computer unbootable. Then I used Rescatux to install grub but grub only detects XP. Is there any way to make grub detect Windows Server without re-installing it? Any help would be appreciated.
Apologies if I have posted in the wrong section.

Thanks in advance.

---

### Post by oldfred on 2012-06-05
Windows normally only boots from the NTFS partition with the boot flag or active partition. All boot files are in that one partition, so grub only finds one Windows boot file.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If both are installed to primary partitions, you may be able to separate boot files and run Windows repairs on each install. Windows only repairs install with boot flag, so you have to repair one, move boot flag and repair other.

Post link to Boot-info to see details:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by nisargshah on 2012-06-13
Here's the BootInfo report - [http://paste.ubuntu.com/1038859/](http://paste.ubuntu.com/1038859/)

---

### Post by oldfred on 2012-06-13
Several issues, but since Windows is in a logical partition it can only boot from sda1, the primary Windows boot partition.

A drive can only have one boot flag. Grub does not use a boot flag, a few BIOS has to see a boot flag to even start to boot, so I normally suggest one boot flag. Windows will only boot from or repair the NTFS primary partition with the boot flag. Use gparted to remove boot flag from sda6 as Windows would not use a boot flag on a logical anyway.

You have installed grub2's boot loader to sda5 which is a NTFS partition. NTFS partitions (PBR- partition boot record) have to have a NTFS boot signature (even in not bootable), so Windows will not see sda5.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Your sda6 also looks like it was copied.  NTFS boot sector or PBR has wrong start/size info in it. Not sure if Windows will repair that or not, but you can try to repair with a Windows 7 repairCD. Both chkdsk and fixboot would be required.

---

### Post by dcstar on 2012-06-14
> **nisargshah said:**
> Here's the BootInfo report - [http://paste.ubuntu.com/1038859/](http://paste.ubuntu.com/1038859/)

If the Windows drive is a Dynamic Disk and not a Basic Disk I don't know if Grub is capable of auto-detecting them.

You may be able to edit the appropriate Grub config file to manually add in a Windows entry to boot the particular partition.

---

### Post by oldfred on 2012-06-14
Boot script shows dynamic partitions as SFS. It did not used to show anything else, but NTFS driver must have some changes as now it sees some info. I do not see dynamic partitions, but two primary, one of which is the extended and the logical partitions. That should be ok.

---

### Post by nisargshah on 2012-06-14
I reinstalled Windows Server 2008 and used EasyBCD to add GRUB to the Windows' bootloader list and now when I get the grub options after the windows bootloader if I choose to login to Ubuntu and it works. Thanks for all your support. I'll keep this thread as a reference for future.

---

