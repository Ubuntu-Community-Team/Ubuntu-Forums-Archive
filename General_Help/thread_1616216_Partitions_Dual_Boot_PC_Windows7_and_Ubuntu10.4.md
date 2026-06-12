---
title: "Partitions: Dual Boot PC: Windows7 and Ubuntu10.4"
date: 2010-11-07
forum: General Help
---

### Post by pratikparikh on 2010-11-07
p { margin-bottom: 0.21cm; }> **[FONT=Courier 10 Pitch]Background/Environment:[/FONT]**
[FONT=Courier 10 Pitch]Hello, My computer is dual boot. [/FONT] 
 [FONT=Courier 10 Pitch]During booting I can select Ubuntu 10.4 or Windows 7.[/FONT]
 

 [FONT=Courier 10 Pitch]This PC has 2 hard-disks.[/FONT]
 [FONT=Courier 10 Pitch]	Hard-disk1: 80GB: Linux and WindowsOS are installed here[/FONT]
 [FONT=Courier 10 Pitch]	Hard-disk2: 1 TB: For data storage. 400GB is unallocated and remaining 600GB is allocated to four volumes (All are NTFS) which is visible in Windows as well as in Ubuntu.[/FONT]


 [FONT=Courier 10 Pitch][COLOR=Green]_**Problem1 :**_ Now I want to create 2 more volumes of 50GB each using this 400GB unallocated space of Hard-disk2. I want to use these 2 volumes in both Ubuntu as well as in Windows7. [/COLOR][/FONT] 
 [FONT=Courier 10 Pitch][COLOR=Green]Should I do it from Windows or from Ubuntu? If yes, How?[/COLOR][/FONT]
[FONT=Courier 10 Pitch][COLOR=Green]
 [/COLOR][/FONT]
 

 [FONT=Courier 10 Pitch][COLOR=Navy]_**Problem2 :**_ gparted/Fdisk is only showing the analysis of Hard-disk2 as a big 1TB disk. It is not able to see those 600GB allocated space and those 4 volumes. Why? Is there anyway to fix it or do you recommend any other software tool. 
[/COLOR][/FONT]
 

 [FONT=Courier 10 Pitch]Thanks in advance.[/FONT]
 

 > *Note: Windows 7's disk manager is analyzing both the hard-disks correctly and it is even allowing me to create a new volumes in those 600GB unallocated free space.*
 

 [FONT=Courier 10 Pitch]Following information might be useful to the linux experts in the analysis of these problems.[/FONT]
 [FONT=Courier 10 Pitch]===========================================================[/FONT]
> [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]root@Nathdwara:~# [SIZE=5]**fdisk -l **[/SIZE][/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray] [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Disk /dev/sda: 80.0 GB, 80000000000 bytes [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]255 heads, 63 sectors/track, 9726 cylinders [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Units = cylinders of 16065 * 512 = 8225280 bytes [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Sector size (logical/physical): 512 bytes / 512 bytes [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]I/O size (minimum/optimal): 512 bytes / 512 bytes [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Disk identifier: 0x12a812a7 [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray] [/COLOR][/FONT]
    [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Device Boot      Start         End      Blocks   Id  System [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]/dev/sda1   *           1        2435    19559106    7  HPFS/NTFS [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]/dev/sda2            2436        9725    58556925    f  W95 Ext'd (LBA) [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]/dev/sda5            2436        4870    19559106    7  HPFS/NTFS [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]/dev/sda6            7306        9725    19438618+   b  W95 FAT32 [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]/dev/sda7            4871        7198    18699628+  83  Linux [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]/dev/sda8            7199        7305      859446   82  Linux swap / Solaris 
[/COLOR][/FONT]
[FONT=Courier 10 Pitch][COLOR=DarkSlateGray]
[/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray] [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Partition table entries are not in disk order [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray] [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]255 heads, 63 sectors/track, 121601 cylinders [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Units = cylinders of 16065 * 512 = 8225280 bytes [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Sector size (logical/physical): 512 bytes / 512 bytes [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]I/O size (minimum/optimal): 512 bytes / 512 bytes [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Disk identifier: 0x5e7f8d7f [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray] [/COLOR][/FONT]
    [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]Device Boot      Start         End      Blocks   Id  System [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]/dev/sdb1               1      121601   976760001   42  SFS [/COLOR][/FONT]
  [FONT=Courier 10 Pitch][COLOR=DarkSlateGray]root@Nathdwara:~# [/COLOR]
[/FONT]


[FONT=Courier 10 Pitch]Following entries are there in /etc/fstab[/FONT]
> [COLOR=RoyalBlue]
[/COLOR] 
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]# [SIZE=5]/etc/fstab[/SIZE]: static file system information. [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]# [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]# Use 'vol_id --uuid' to print the universally unique identifier for a [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]# device; this may be used with UUID= as a more robust way to name devices [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]# that works even if disks are added and removed. See fstab(5). [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]# [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]# <file system> <mount point>   <type>  <options>       <dump>  <pass> [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]proc            /proc           proc    defaults        0       0 [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]# / was on /dev/sda7 during installation [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]UUID=2a1bd8f5-fe32-46e2-abbd-ea8a5ae52a58 /               ext3    relatime,errors=remount-ro 0       1 [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]# swap was on /dev/sda8 during installation [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]UUID=ff168730-9fa9-4ab7-aa1c-a8652432a5ee none            swap    sw              0       0 [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 [/COLOR][/FONT]
 [FONT=Courier 10 Pitch][COLOR=RoyalBlue]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/COLOR] [/FONT]
[FONT=Courier 10 Pitch]~                                                                            [/FONT] 
 [FONT=Courier 10 Pitch]====================================================================[/FONT]
Now here is the mount command output...

> [COLOR=Sienna]root@Nathdwara:~# [/COLOR][SIZE=5][COLOR=Sienna]mount[/COLOR][/SIZE][COLOR=Sienna]
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shiva/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shiva)
root@Nathdwara:~#[/COLOR] [FONT=Courier 10 Pitch]


[/FONT]

---

### Post by oldfred on 2010-11-08
Windows has converted your drive to sfs. That is a window proprietary partition scheme that windows does not use anymore. It is something like LVM in linux as dynamic partitions. It is a workaround to the MBR 4 partition limit.

[http://www.linuxforums.org/forum/red-hat-fedora-linux/122563-help-required-accessing-sfs-filesystem.html](http://www.linuxforums.org/forum/red-hat-fedora-linux/122563-help-required-accessing-sfs-filesystem.html)
[http://www.vistax64.com/server-general/253150-re-converting-dynamic-disk-back-basic-disk.html](http://www.vistax64.com/server-general/253150-re-converting-dynamic-disk-back-basic-disk.html)

With MBR/msdos you can have 4 primary partitions. When they quickly notice that was a limit they made it that you could convert one primary to an extended and add many logical partitions inside the extended. Windows will read logical NTFS partitions. Linux both boots & reads from logical partitions.

Apple and newer windows servers have converted to gpt for large drives. It is an alternative to MBR, but windows will not boot from gpt unless it is an efi system.

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by srs5694 on 2010-11-08
The [Partition Wizard](http://www.partitionwizard.com/) software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Another option might be to create volumes in Windows and then use mkfs in Linux to convert them to Linux partitions. (Linux can read and write Windows dynamic disks, but AFAIK there are no utilities to modify the volume definitions in Linux.) I'd be a bit reluctant to do this, though, since I'm not sure how Windows will react to one of its NTFS or FAT dynamic volumes turning into a Linux filesystem. In a worst-case scenario, it might not react initially, but then do something very damaging when you launch some obscure utility.

---

