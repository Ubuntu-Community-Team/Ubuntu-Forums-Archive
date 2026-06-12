---
title: "Helpppp! dd just erased first 5Mb of my (only) HDD!"
date: 2012-08-03
forum: General Help
---

### Post by nikonian on 2012-08-03
Hi guys.

I was making a floppy image in dd, and accidentally specified the wrong drive, and ran this:

```
 sudo dd if=/dev/zero of=/dev/sda bs=512 count=10000 
```

So I have now written 5MB of zeroes to my first (and only) drive - a 1Tb WD sata... arrghh! lol!

It seems the first 200Mb is some oddball Windows "system" partition, so nothing much would be lost there.

### I HAVE NOT REBOOTED THE PC ###

I am running "testdisk" on the drive to see what can be found & recovered, but it's taking it's sweet time to scan... is there a faster/simpler way to do this, than testdisk?

It seems that the only thing my mistake could have done is to erase the MBR and File Allocation Table, and a tiny chunk of the 200Mb Win7 System partition... am I right?

If you can suggest anything, I would be most grateful, as I am verging on losing almost 2 years of files, due to my negligence.

Thank you :D

---

### Post by oldfred on 2012-08-04
If you boot with grub2, see if you can reinstall it to the MBR. It may want partition table first.

sudo grub-install /dev/sda

Then see if you can recover partition table:

If not rebooted, use fdisk to manually recreate table posts by srs5694 post34 on page#4
[http://ubuntuforums.org/showthread.php?t=1668247](http://ubuntuforums.org/showthread.php?t=1668247)

Windows normally has a hidden 100MB boot/repair partition as the first partition, although some installs have the vendor recovery first, others have it last.

Did you make the Windows repairCD or USB? The you can restore/repair that partition. It has to be NTFS and not just from partition table, but partition boot sector has to have the NTFS boot sector with internal info on partition start & size and reference to bootmgr (for Vista/7) or ntldr for XP. If you only overwrote the start of the the first partition testdisk may be able to restore partition boot sector from its backup.

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

or:
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

---

### Post by nikonian on 2012-08-04
Testdisk fixed it. Thanks

---

