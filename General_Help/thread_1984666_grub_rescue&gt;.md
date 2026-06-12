---
title: "grub rescue&gt;"
date: 2012-05-22
forum: General Help
---

### Post by brainfarth on 2012-05-22
I run dual boot (ubuntu 12.04 and windows 7 64). My windows system was running slow so I tried to boot into safe mode to run anti-whatever software. I could not get into safemode, so I selected windows restore hoping that I could find the option. It was not there, so I rebooted again. Now I get the grub rescue> prompt when I boot up. I dont get the boot menu anymore. Fortunately I had ubuntu 11.something on a thumbdrive and that is how I'm sending this plea for help. I've searched through a bit of the forums and am unsure which direction to go without messing my system up even more.
Any help would be much appriciated.
-Mike

---

### Post by wilee-nilee on 2012-05-22
So from a ubuntu live cd or usb flash download the link, and extract it to your desktop, then run the command. A results text will be in your home copy, paste all the text in it to a reply. When you open the reply click on the # in the reply panel you will see code tags, paste the text between them.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by brainfarth on 2012-05-22
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:  Syslinux looks at sector 1745240 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     24,578,048    24,782,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          53,383,992   519,611,911   466,227,920   7 NTFS / exFAT / HPFS
/dev/sda4         519,612,414   625,137,344   105,524,931   f W95 Extended (LBA)
/dev/sda5         563,704,848   625,137,344    61,432,497   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4083 MB, 4083351552 bytes
128 heads, 63 sectors/track, 989 cylinders, total 7975296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             56     7,975,295     7,975,240   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE
/dev/sda2        3E82C93B82C8F903                       ntfs       SYSTEM RESERVED
/dev/sda3        4248D17748D16A65                       ntfs       ACER
/dev/sda5        01CCBDE13F4E9E70                       ntfs       Ubuntu
/dev/sdb1        A745-4949                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/Ubuntu            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  0f 7d 10 83 10 7d 10 83  0f 7d 0f 83 0f 7d 0f 82  |.}...}...}...}..|
00000010  10 7e 0f 81 0f 7e 0f 81  0d 7d 10 82 10 7c 10 82  |.~...~...}...|..|
00000020  10 7c 10 81 0f 7d 0d 80  0d 7e 0d 80 0d 7e 0f 81  |.|...}...~...~..|
00000030  0f 7f 0f 82 0d 7f 0d 82  0f 7f 0f 82 0f 7f 0f 83  |................|
00000040  0f 7f 0d 83 0f 7e 0d 81  0d 7e 0f 81 0f 7d 10 81  |.....~...~...}..|
00000050  10 7d 0f 80 0f 7d 0d 80  0b 7e 0b 80 0d 7e 0d 81  |.}...}...~...~..|
00000060  0d 7e 0d 81 0d 7e 0d 81  0d 7e 0d 81 0d 80 0d 81  |.~...~...~......|
00000070  0b 7e 0b 81 0d 7e 0d 81  0d 7d 10 83 10 7e 12 84  |.~...~...}...~..|
00000080  12 7e 0f 84 0f 7f 0d 82  0d 7e 0d 81 0d 7e 0d 81  |.~.......~...~..|
00000090  0f 7d 10 82 10 7c 12 84  10 7e 0f 84 10 7c 10 84  |.}...|...~...|..|
000000a0  10 7c 10 84 10 7c 12 84  12 7c 10 86 10 7d 12 88  |.|...|...|...}..|
000000b0  12 7d 12 87 12 7c 10 84  12 7b 12 84 13 7b 13 84  |.}...|...{...{..|
000000c0  13 7b 13 84 12 7d 12 87  12 7b 12 87 13 7b 13 87  |.{...}...{...{..|
000000d0  15 7a 15 87 15 79 15 87  18 77 1b 87 1f 73 20 87  |.z...y...w...s .|
000000e0  24 71 21 87 24 72 24 89  27 72 26 8a 28 72 23 8a  |$q!.$r$.'r&.(r#.|
000000f0  1f 74 1f 8c 1b 75 19 8e  20 77 1b 8e 1b 77 18 8c  |.t...u.. w...w..|
00000100  1c 77 13 89 1d 77 16 87  32 63 2e 8e 30 66 2e 8b  |.w...w..2c..0f..|
00000110  30 64 31 8b 31 63 32 8e  34 66 33 8f 34 68 35 8f  |0d1.1c2.4f3.4h5.|
00000120  34 65 37 8e 37 60 37 90  38 5e 39 8f 3a 5f 3b 8d  |4e7.7`7.8^9.:_;.|
00000130  3d 60 3f 8e 40 60 41 91  41 62 41 91 43 65 43 8f  |=`?.@`A.AbA.CeC.|
00000140  45 62 45 8e 44 5f 44 91  44 5e 44 92 46 5d 46 91  |EbE.D_D.D^D.F]F.|
00000150  48 5b 49 8e 48 5a 48 8a  49 5d 48 8a 4a 5f 4b 8b  |H[I.HZH.I]H.J_K.|
00000160  4b 5e 4c 89 4c 5e 4a 86  4b 62 4d 86 50 67 4c 88  |K^L.L^J.KbM.PgL.|
00000170  4e 6b 4d 89 4f 6c 51 8a  4f 68 4f 8d 4e 68 4c 8d  |NkM.OlQ.OhO.NhL.|
00000180  4e 6f 4b 89 50 74 52 84  52 71 4e 83 4d 6c 4d 83  |NoK.PtR.RqN.MlM.|
00000190  50 6c 4f 85 4e 72 4e 86  4d 74 4e 86 4d 73 4b 85  |PlO.NrN.MtN.MsK.|
000001a0  4b 73 4b 85 4c 70 4b 85  4a 6b 49 86 47 6b 44 87  |KsK.LpK.JkI.GkD.|
000001b0  44 6f 41 89 43 70 44 8a  44 6c 44 89 43 6c 00 fe  |DoA.CpD.DlD.Cl..|
000001c0  ff ff 07 fe ff ff 12 cc  a0 02 b1 62 a9 03 00 00  |...........b....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

### Post by brainfarth on 2012-05-22
I forgot to mention that this is an Acer Aspire 7736z laptop with a hidden recovery partition.

---

### Post by wilee-nilee on 2012-05-22
If you have a vista or w7 recovery or install disc for windows, boot it, get to the recovery terminal and run this command

```
bootrec.exe /fixmbr
```Here is a link on getting to that terminal, just run this command.

[FONT=Verdana, sans-serif][SIZE=1]http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html

This will only get the windows to boot, you might try one of the bootable AV cd downloads if you have problems with viri. Basically to get you in for a recovery, if you are infected. A fresh install of windows is what I would do if infected past using the safe mode.

Here is a link to bootable av's
[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)
[/SIZE][/FONT]

---

### Post by brainfarth on 2012-05-22
Thanks for the help. I was able to restore the windows bootup. Unfortunately the boot menu is gone. Which is fine for now since I'm going to back the system up and reinstall everything on a new ssd. But for future reference, how do you get into windows safe mode with a dual boot system?
 
edit: I used a windows 7 iso dvd I had laying around to get into rescue.

---

### Post by wilee-nilee on 2012-05-22
> **brainfarth said:**
> Thanks for the help. I was able to restore the windows bootup. Unfortunately the boot menu is gone. Which is fine for now since I'm going to back the system up and reinstall everything on a new ssd. But for future reference, how do you get into windows safe mode with a dual boot system?
 
edit: I used a windows 7 iso dvd I had laying around to get into rescue.

Should be the f8 prompt as soon as you choose windows from the grub menu.

So you are missing this from the sda3 partition the C.

**Boot/BCD**    I assume it was there as part of it still is.

This could possibly be fixed, it would mean either copying that from another partition, or the ISO or a moving the bootflag there and running a set of commands, not sure if this will fix the boot menu missing though.

---

