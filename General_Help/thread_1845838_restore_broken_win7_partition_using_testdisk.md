---
title: "restore broken win7 partition using testdisk"
date: 2011-09-17
forum: General Help
---

### Post by yduck on 2011-09-17
hi, guys

I used Acronis (a disk management software) in win7 to shrink volume of 40GB from the 370GB of my windows7 ntfs partition. It requires to reboot the system. On rebooting, the software runs to 99% and stops with some errors. When I restart the computer, I cannot boot to win7 anymore. 

If I run "sudo fdisk -l" on ubuntu, which is installed on a separate partition in the same computer, the result is: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75e12b35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       43273   347383804+   7  HPFS/NTFS
/dev/sda3           43274       58876   125324571+   f  W95 Ext'd (LBA)
/dev/sda4           58876       60788    15361024    7  HPFS/NTFS
/dev/sda5           48679       54637    47854592   83  Linux
/dev/sda6           54637       54896     2082808   82  Linux swap / Solaris
/dev/sda7           54897       58876    31958016    7  HPFS/NTFS

Then I used testdisk from linux to deep analyze the hardrive, the result is: 


Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0  32 33    25 159  6     409600
D HPFS - NTFS             25 159  6    51  30 42     409600
D HPFS - NTFS             25 159  7 43272 231 24  694767609
D HPFS - NTFS             25 159  7 54896 120  8  881500160
D HPFS - NTFS             25 159 14 43272 231 31  694767609
D Linux                48678 233  4 54636 136 28   95709184
D FAT32 LBA            49345 229 37 49409 163 34    1024000 [SDCARD]
D Linux                51571 155 41 57529  59  2   95709184
D Linux                51576 180 61 57534  84 22   95709184
D Linux                51582 113 52 57540  17 13   95709184
D Linux                51583  86 24 57540 244 48   95709184
D FAT32 LBA            52642  19 50 52705 208 47    1024000 [SDCARD]
D Linux Swap           54636 168 61 54895 244 53    4165616
D HPFS - NTFS          54896 152 41 56171  74 31   20477952 [LENOVO]
D HPFS - NTFS          54896 152 41 58875  47 52   63916032 [LENOVO]
* HPFS - NTFS          58875  47 53 60787 139 24   30722048 [LENOVO_PART]

what should do to restore the damaged partition?

I really appreciate it!

---

### Post by oldfred on 2011-09-18
Do you want to undo the changes you made. That would be what you could use testdisk for.

But it sounds like you have a Windows issue. Windows will run a chkdsk after any resize and it sounds like the chkdsk did not complete. You have to run chkdsk until there are not errors.

You can use your Windows repair CD or possibly when booting press f8 as soon as you press Windows in grub. That should get you into the repair console. Some say it is very quick from grub to Windows and you may have to try several times.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

