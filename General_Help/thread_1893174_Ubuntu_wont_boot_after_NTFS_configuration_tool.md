---
title: "Ubuntu wont boot after NTFS configuration tool"
date: 2011-12-09
forum: General Help
---

### Post by hurricanedt on 2011-12-09
Hey everyone,

Im new here and need a little help. Today i tried to use the ntfs config tool to access my win xp files on ubuntu 11.10. I followed the instructions on the tool to restart the computer. And when i tried to boot into ubuntu: nothing. The screen went black. And ive tried to boot a couple times and still wont work. I have an ubuntu bootable usb if that helps. Feel free to ask any questions in case i havent explained everything right. Thanks for your help.

---

### Post by seawolf167 on 2011-12-09
Can you boot off your usb (or a bootable live cd), then download and run this boot script

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and then reply and put the script inside [noparse]```
[/noparse]   [noparse]
```[/noparse] tags.

You may need to reinstall Grub following [these instructions]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2"), but the script will let us know for sure.

---

### Post by hurricanedt on 2011-12-09
Here it is:

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 1325954 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    20,973,567    20,971,520  12 Compaq diagnostics
/dev/sda2    *     20,973,568   312,560,639   291,587,072   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2017 MB, 2017525248 bytes
64 heads, 63 sectors/track, 977 cylinders, total 3940479 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *            129     3,907,007     3,906,879   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        749ACDBB9ACD79DE                       ntfs       PQSERVICE
/dev/sda2        38A0D07EA0D04452                       ntfs       OS
/dev/sdd1        15F6-1629                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=10
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

=============================== StdErr Messages: ===============================

/home/ubuntu/Documents/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by seawolf167 on 2011-12-09
It looks like you are running Ubuntu as a Wubi install - I'm afraid that I don't know too much about troubleshooting Wubi issues so you'll have to wait for someone more knowledgeable in this area to come along, but this section

```
Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1
```is saying that the Wubi install is inaccessible which is why it won't boot up.

---

### Post by hurricanedt on 2011-12-09
Ok well thank you for trying! I hope someone else knows.

---

### Post by bcbc on 2011-12-10
You'll need to fsck the root.disk. Boot from an Ubuntu CD, select "Try Ubuntu", drop to a terminal (Ctrl + Alt + T), mount the windows partition, and fsck the root.disk:
```
sudo mount /dev/sda2 /mnt
sudo fsck /mnt/ubuntu/disks/root.disk
```

Hopefully that fixes it.

---

### Post by hurricanedt on 2011-12-11
When i try to mount windows:
```
mount: can't find /dev/sda2/mnt in /etc/fstab or /etc/mtab
```Is this because i am booting off a usb drive? Would a disk work instead?

EDIT:
Nevermind, did the command "sudo mount /dev/sda2 /mnt" instead of "sudo mount /dev/sda2/mnt" and it worked perfectly! booted back up, and I am now back to ubuntu goodness! thank you very much bcbc. oh, how i missed you ubuntu.

---

