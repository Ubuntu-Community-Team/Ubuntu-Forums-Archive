---
title: "How to fix GRUB on Windows disk using Live Bootup"
date: 2011-03-10
forum: General Help
---

### Post by epsteins on 2011-03-10
(I'm a first time poster.)

I have a netbook with a corrupted GRUB bootloader.  I can't boot 
to the Windows XP on the drive, it immediately goes to the grub
prompt. grub> does not recognize ANY of the commands I have
researched so far. I can boot from a 'live' Ubuntu 10.04.2 LTS USB stick.
From Ubuntu, how can I repair or remove GRUB on the primary
(Windows XP) disk so default behavior will be to successfully boot
Windows XP? Have looked, but haven't quite found the answer I
need. Thank you.

---

### Post by Rubi1200 on 2011-03-10
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by epsteins on 2011-03-10
Many thanks for your help.

Here are the results:



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   302,246,909   302,246,847   7 HPFS/NTFS
/dev/sda2         302,246,910   312,496,379    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6C648DAC648D7A1A                       ntfs                                     
/dev/sda2        CCED-990E                              vfat       PE                            
/dev/sda3: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb         64EB-A08F                              vfat       UBUNTU10 04                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```

---

### Post by Rubi1200 on 2011-03-10
Did you remove your Ubuntu install?

If not, where is it supposed to be?

---

### Post by YesWeCan on 2011-03-10
Yes, something went badly wrong here.
You can use lilo from the live CD to replace the MBR so XP will boot:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Or you can use your XP CD to repair it.

---

### Post by epsteins on 2011-03-10
[A long story...] :(

The primary disk never had an Ubuntu image. 
A while back, while installing Ubuntu on a portable
drive, an incomplete GRUB was installed on the
primary disk; for a long time, this didn't matter,
because the portable drive had a good GRUB
which would allow booting the Windows on 
primary, or the Ubuntu on the portable.
Unfortunately, the portable drive has become
corrupted and won't boot, or take a successful
install. Right now, my only viable way of 
booting is via the live USB stick. If I can clean up
the primary Windows disk from the live, I should be fine...

---

### Post by epsteins on 2011-03-10
It works! 

lilo did the trick!

Many thanks for all the help...

---

### Post by Rubi1200 on 2011-03-10
Excellent! Glad you got things sorted out :-)

---

