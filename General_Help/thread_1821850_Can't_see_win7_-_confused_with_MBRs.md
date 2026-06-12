---
title: "Can't see win7 - confused with MBRs"
date: 2011-08-09
forum: General Help
---

### Post by Quarkrad on 2011-08-09
Newbie - 10.10 64 bit.  I'm building a new PC that came with a 1T HD with win7 pre-installed. I have installed a 2nd 500 GB hard disk (both are sata) and cloned the win7 installed from the 1T to the 500. I then reformatted the 1T (NTFS) as it will be used as a backup for the 500GB HD. 

I then partitioned the 500G, the order of partitions is win7 (sda1), ubuntu 10.10 (sda4), a storage partition called 'store' (sda3) and a swap partition (sda2).  I reformatted the 1T HD (ntfs) and called it 'backup' (sdb5). 

Having cloned the 500GB with win7 I then repartitioned and installed ubuntu 10.10.  Although I have dual booted many times I cannot get GRUB2 to see my win7/sda1 partition - the PC just boots to ubuntu. I have done some reading and downloaded the boot info script and now I'm worried.  The script, attached, is telling me that Windows is installed in the MBR of /dev/sdb. Although I reformatted the 1T I think perhaps the MBR is still there and confusing things.  Do I have a MBR on sda1 and one on sdb1?  The output of fdisk -l is:

[B]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa0c1e50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12749   102400000    7  HPFS/NTFS
/dev/sda2           59782       60802     8192000   82  Linux swap / Solaris
/dev/sda3           25497       59782   275393536    7  HPFS/NTFS
/dev/sda4   *       12749       25497   102400000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x638c197f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976760832    5  Extended
/dev/sdb5               1      121602   976759808    7  HPFS/NTFS[/B]

Any help would be much appreciated - I think I'm in a bit of a mess.

---

### Post by oldfred on 2011-08-09
You did not copy all of windows. Win7 default install has a separate sda1 boot/recovery partition of 200MB. It has two of the three boot files that the boot script shows. Also windows partition boot sector has to have the exact size of the NTFS partition and some other parameters. Any resize or move requires those to be reset or repaired. Sometimes its chkdsk and sometimes its fixBoot (for PBR).

With two drives I prefer to have each operating system on different drives. Avoids some conflicts. Does not change total size you have available.

Windows MBR only boots active partition (or boot flag) on that drive. Unless you install another boot loader you do not normally erase it, it would not be used unless you change BIOS to try to boot from it.

Vista/7 -  you are missing the one's in red, but can repair your install to add them.
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

Edit - to repair windows you have to have boot flag on NTFS system partition. Otherwise it will try to repair the Linux partition with boot flag and error out as it knows it not windows. Grub does not use boot flag. use gparted or Disk Utilities to move boot flag

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd


Part of why I prefer systems on separate drives.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by Quarkrad on 2011-08-10
Thank you for your replies.  I managed to restore everything using the BootRec.exe commands from the win7 install disk.  Much appreciated.

---

