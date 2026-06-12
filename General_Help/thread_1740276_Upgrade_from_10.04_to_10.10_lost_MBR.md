---
title: "Upgrade from 10.04 to 10.10 lost MBR"
date: 2011-04-26
forum: General Help
---

### Post by Athas on 2011-04-26
Cross post with [http://askubuntu.com/questions/37195/upgrade-from-10-04-to-10-10-lost-mbr](http://askubuntu.com/questions/37195/upgrade-from-10-04-to-10-10-lost-mbr)

     2     down vote      [favorite]("http://askubuntu.com/questions/37195/upgrade-from-10-04-to-10-10-lost-mbr#")                    share [fb]     share [tw]  
                                                            I think I've lost my MBR upgrading from ubuntu 10.04 to 10.10.
  During the upgrade it gave me a message saying which partitions did I  want the grub details to go on, saying if I was unsure to select all of  them.
  After reboot I just end up in a grub recovery console.
  The system was a dual boot with windows vista.
  Any Idea how I can get both my operating systems to work?

                   Boot Info Script 0.55    dated February 15th, 2010                      ============================= Boot Info Summary: ==============================   => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in      partition #256 for /boot/grub.  sda1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:   /bootmgr /Boot/bcd  sda2: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows Vista     Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe                         /wubildr.mbr /wubildr  sda3: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr                         /ubuntu/disks/root.disk /ubuntu/disks/swap.disk  sda3/Wubi: _________________________________________________________________________      File system:       ext4     Boot sector type:  Grub 2     Boot sector info:  Grub 2 is installed in the boot sector of sda3/Wubi                         and looks at sector 21294336 of the same hard drive                         for core.img, but core.img can not be found at this                         location.     Mounting failed: mount: wrong fs type, bad option, bad superblock on /dev/loop1,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail  or so   =========================== Drive/Partition Info: =============================  Drive: sda ___________________ _____________________________________________________  Disk /dev/sda: 250.1 GB, 250059350016 bytes 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sda1                  63    24,563,384    24,563,322  27 Hidden HPFS/NTFS /dev/sda2    *     24,563,712   256,700,415   232,136,704   6 FAT16 /dev/sda3         256,700,416   488,394,751   231,694,336   7 HPFS/NTFS   blkid -c /dev/null: ____________________________________________________________  Device           UUID                                   TYPE       LABEL                           /dev/loop0                                              squashfs                                  /dev/loop1       c0de1566-8c76-4392-ac90-9f026a82f928   ext4                                      /dev/sda1        443C1D3EE49BED2A                       ntfs       PQSERVICE                      /dev/sda2        B898B25F98B21BB6                       ntfs       ACER                           /dev/sda3        A4202E96202E6F8A                       ntfs       DATA                           /dev/sda: PTTYPE="dos"   ============================ "mount | grep ^/dev  output: ===========================  Device           Mount_Point              Type       Options  aufs             /                        aufs       (rw) /dev/sr0         /cdrom                   iso9660    (ro,noatime) /dev/loop0       /rofs                    squashfs   (ro,noatime)

---

### Post by trollger on 2011-04-26
there are tools on this web page that should do the trick

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by oldfred on 2011-04-26
I do not know how you formated boot script, it is just about unreadable. You should use code tags which are the # in the edit panel above your post as you enter it. Paste between code tags. or highlight and click on the # to put tags around the highlighted entry.

You have wubi not dual boot. With wubi you have to use the windows boot loader in the MBR. Do not install grub to partitions unless you are very advanced. Note in instructions was totally wrong.

See problem #1 and solutions:
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Fix for 10.04 upgrade fail bcbc copy wubildr or edit grub.cfg
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

