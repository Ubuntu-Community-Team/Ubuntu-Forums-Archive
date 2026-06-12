---
title: "MBR destroyed?"
date: 2011-04-18
forum: General Help
---

### Post by ZShock on 2011-04-18
Hello, I'd like to ask for some help for this little mess I've made; so far I've tried like everything but nothing seems to work. Hopefully some of you can help me u-u

**Go to the bold text if you don't wanna read all that fail history.**

So, this is WHERE the problem has started.

I got this netbook, and it came with two operating systems: XP and a Linux Distro called Pixart. Well, I deleted this last one since it completely sucked (I couldn't access to some admin parameters.) After that, I was supossed to install Ubuntu in his last version (I think 10.10?) But after doing some research and realizing this computer's skills, I picked Ubuntu Netbook Remix.

NEXT, I made a partition and filled it with oh-so-sweet ubuntu nbook remix, but I had to execute it from GRUB with another command, else it'd crash. This command was intel_idle.max_cstate=0. Once inside the OS I modified GRUB so it could execute itself everytime the GRUB menu was shown, and this is were the problems started.

Ubuntu worked great, but it booted automatically, without even givin' me the chance to run XP. Soon I realized that the problem was that command, so what I did was to remove that line from GRUB once again. After that, GRUB alone would execute, there was no Windows boot to run ):

After uninstalling Ubuntu Netbook remix, I started to try 'n fix Windows. I found out that I could run it thru a boot disk, such as Hiren's Boot. Once inside, I just fixed boot.ini and master boot records (I can't remember how.) Decided to install Ubuntu, I ran that soft called Wubi to put it from Windows, to see if this time GRUB would recognise my first OS, but something went wrong again and Windows stopped showing up, from everywhere.

[B]So this is what has been happening lately:
I ran every way possible to fix the mbr from the hdd, but FDISK (so far I couldn't find a way to execute it.) This included every tool possible in Hiren's Boot and Super Grub Disk with no success, getting several errors.

Not found NTDLR.
Not found OS.
Blank screen with cursor...

I've used some programs to check the partition files, and I was able to check the file system, watching all my files in perfect state but with no chance of booting the OS. Oh, and when I try to boot from any of the options in Hiren's Boot, I get "cannot mount drive", or when it tries to run Windows commands 

I think that something's wrong with the MRB, but I'm quite ****** up now, since not even these rescue disks will find my partition...[/B]

I truly don't know what to do at this point, seeing all I've tried, so I put like my trust in you Ubuntu Forums xD Thanks.

Edit: for some reason these DOS programs don't find the HDD, yet with Rescatux I can see my files perfectly. PS: Isn't there any way to rebuild the windows mbr from zero, with no imperfections?

---

### Post by debd on 2011-04-18
check this thread:  [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by ZShock on 2011-04-18
I got into the Live CD struggling with some commands, but I'm there after all. Now, I have a problem when mounting drives, since it's like it doesn't detect any drives, the only one there is the usb drive I'm using to run the Live CD.

Edit: nevermind it was sda1 and I was using sdb1; I'll keep going from here. And btw thanks for the link.

---

### Post by coffeecat on 2011-04-18
This:

> **ZShock said:**
> [B]
Not found NTDLR.[/B]

... is not a problem with the MBR. It is a problem with the boot sector of your Windows C: partition. There are one or more boot files missing. That is quite a different matter from an MBR problem. You can re-install grub or re-install the Windows mbr for ever and that will not fix the problem.

So that we can see exactly what is on your system you need to boot up into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script as described there and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for legibility.

---

### Post by ZShock on 2011-04-18
Hmm... that's a lotta code but here it is:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr /grub/core.img 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: tipo de sistema de ficheros '' desconocido

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst /grldr /grub/core.img

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: tipo de sistema de ficheros '' desconocido
mount: tipo de sistema de ficheros '' desconocido

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   312,576,704   107,780,085   f W95 Ext d (LBA)
/dev/sda5         204,796,683   312,576,704   107,780,022   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 8011 MB, 8011120640 bytes
247 cabezas, 62 sectores/pista, 1021 cilindros, 15646720 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    15,631,244    15,631,182   b W95 FAT32
/dev/sdc2          15,631,245    15,631,307            63  21 Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BAC040F1C040B583                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        34C82FEFC82FAE54                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        C655-77F9                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1        /mnt/pendrive            vfat       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=signature(c8c0c8b)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
signature(c8c0c8b)disk(0)rdisk(0)partition(1)\WINDOWS="1" 1
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/core.img

================================ sdc1/menu.lst: ================================

#timeout 15
default /default

title Boot From Hard Drive (Windows Vista/7 or Xp)\n
find --set-root --ignore-floppies --ignore-cd /bootmgr || find --set-root --ignore-floppies --ignore-cd /ntldr || rootnoverify (hd0) && chainloader +1 && boot
map () (hd0) && map (hd0) () && map --rehook
find --set-root --ignore-floppies --ignore-cd /bootmgr || find --set-root --ignore-floppies --ignore-cd /ntldr
chainloader /bootmgr || chainloader /ntldr

title \n
root

title Dos Programs\nRun Dos Programs
find --set-root /HBCD/memdisk
kernel /HBCD/memdisk
initrd /HBCD/boot.gz

title Mini Windows Xp\nRun Antivirus and other windows programs
# example password: test 
# password --md5 $1$gNe0$KZPOE8wNbTNSKOzrajuoB0
find --set-root /HBCD/XPLOADER.BIN
chainloader /HBCD/XPLOADER.BIN

title Mini Linux\nRecovery Is Possible Linux (Min RAM 350MB)
find --set-root /HBCD/linux
kernel /HBCD/linux xlogin keymap=us xkeymap=us xdriver=fbdev root=/dev/ram0 rw vga=791
initrd /HBCD/riplinux.gz

title \n
root

title Windows Memory Diagnostic\n
find --set-root /HBCD/memdisk
kernel /HBCD/memdisk
initrd /HBCD/wmemtest.gz

title MemTest86+\n
find --set-root /HBCD/memtest.gz
map --mem /HBCD/memtest.gz (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)
map --floppies=1
boot

title Offline NT/2000/XP/Vista/7 Password Changer\nWindows Password Reset
find --set-root /HBCD/chntpw
kernel /HBCD/chntpw vga=1
initrd /HBCD/chntpw.gz

title Kon-Boot\nWindows (any/blank password) and Linux (kon-usr) Login Without a Password
find --set-root /HBCD/memdisk
kernel /HBCD/memdisk
initrd /HBCD/konboot.gz

title Seagate DiscWizard (Powered by Acronis Trueimage)\nPress ALT+T+O+K to skip Error
find --set-root /HBCD/SeagatDW
kernel /HBCD/SeagatDW vga=788 ramdisk_size=32768 acpi=off quiet noapic mbrcrcs on
initrd /HBCD/SeagatDW.gz

title PLoP Boot Manager\n
find --set-root /HBCD/plpbt.bin
kernel /HBCD/plpbt.bin

title Smart Boot Manager 3.7.1\n
find --set-root /HBCD/memdisk
kernel /HBCD/memdisk
initrd /HBCD/smartbm.gz

title Fix "NTLDR is Missing"\n
find --set-root /HBCD/memdisk
kernel /HBCD/memdisk
initrd /HBCD/ntldr.gz

title Darik's Boot and Nuke (Hard Disk Eraser)\n
find --set-root /HBCD/dban.gz
kernel /HBCD/memdisk
initrd /HBCD/dban.gz

title Custom Menu...  (Use HBCDCustomizer to add your files)\n
find --set-root /HBCD/menu-custom.lst
configfile /HBCD/menu-custom.lst

title More...\n
root

title Dos Programs (Alternative Boot Method)\nUsing Grub4Dos map
find --set-root /HBCD/boot.gz
map --mem /HBCD/boot.gz (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)
map --floppies=1
boot


title Mini Linux 640x480\nRecovery Is Possible Linux
find --set-root /HBCD/riplinux.gz
kernel /HBCD/linux xlogin keymap=us xkeymap=us root=/dev/ram0 rw vga=normal video=640x480
initrd /HBCD/riplinux.gz

title Linux Console\nRecovery Is Possible Linux
find --set-root /HBCD/linux
kernel /HBCD/linux root=/dev/ram0 rw vga=normal
initrd /HBCD/riplinux.gz

title Boot HDD 1 MBR\n
rootnoverify (hd0)
chainloader +1
title Boot HDD 1 Partition 1\n
rootnoverify (hd0,0)
chainloader +1
title Boot HDD 1 Partition 2\n
rootnoverify (hd0,1)
chainloader +1
title Boot HDD 1 Partition 3\n
rootnoverify (hd0,2)
chainloader +1
title Boot HDD 1 Partition 4\n
rootnoverify (hd0,3)
chainloader +1
title Boot HDD 2 MBR\n
rootnoverify (hd1)
chainloader +1
title Boot HDD 2 Partition 1\n
rootnoverify (hd1,0)
chainloader +1
title Boot HDD 2 Partition 2\n
rootnoverify (hd1,1)
chainloader +1
title Boot HDD 2 Partition 3\n
rootnoverify (hd1,2)
chainloader +1
title Boot HDD 2 Partition 4\n
rootnoverify (hd1,3)
chainloader +1
title Boot HDD 3 MBR\n
rootnoverify (hd2)
chainloader +1
title Boot HDD 3 Partition 1\n
rootnoverify (hd2,0)
chainloader +1
title Boot HDD 3 Partition 2\n
rootnoverify (hd2,1)
chainloader +1

title More...\n
root

title Boot HDD 3 Partition 3\n
rootnoverify (hd2,2)
chainloader +1
title Boot HDD 3 Partition 4\n
rootnoverify (hd2,3)
chainloader +1

title Boot Windows XP (NTLDR) from Hard Drive\n
find --set-root --ignore-floppies --ignore-cd /ntldr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /ntldr
chainloader /ntldr
savedefault

title Boot Windows Vista/7 (BOOTMGR) from Hard Drive\n
find --set-root --ignore-floppies --ignore-cd /bootmgr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /bootmgr
chainloader /bootmgr
savedefault

title Chainload isolinux.bin\n
find --set-root /HBCD/isolinux.bin
chainloader /HBCD/isolinux.bin

title Custom Menu...  (Use HBCDCustomizer to add your files)\n
find --set-root /HBCD/menu-custom.lst
configfile /HBCD/menu-custom.lst

title ...Back\n
root




=================== sdc1: Location of files loaded by Grub: ===================


    nfGB: grub/core.img
    nfGB: menu.lst
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 fe 08  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  4e 83 ee 00 81 3b 00 00  00 00 00 00 02 00 00 00  |N....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f9 77 55 c6 4e  4f 20 4e 41 4d 45 20 20  |..).wU.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 00  80 20 00 66 ba 00 00 00  |..E}.f... .f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  7e 7b d4 37 21 91 5b f7  33 14 79 4e 95 98 c4 a4  |~{.7!.[.3.yN....|
00000010  c9 e3 4a 35 56 29 4d 4c  af be 9e 00 6c 76 07 14  |..J5V)ML....lv..|
00000020  f8 cd 0d ff 03 ac cd fe  03 18 b8 89 6e ba c5 3d  |............n..=|
00000030  c4 f6 7f 43 95 2e b9 da  57 65 9a f5 f3 98 af 12  |...C....We......|
00000040  61 e9 16 95 59 ee 4e ff  7e 55 d6 b2 00 13 14 5d  |a...Y.N.~U.....]|
00000050  17 13 6f 5b ef 73 9b 51  88 a0 7d 30 50 ef 45 83  |..o[.s.Q..}0P.E.|
00000060  d0 6a a4 7e 4d a6 5d 04  93 e6 cf dc e3 01 0f c2  |.j.~M.].........|
00000070  4a a4 b7 1a 03 50 6a ea  1b 6c 4d 8c 32 63 77 13  |J....Pj..lM.2cw.|
00000080  3d 5c 8f c1 e1 fa a1 19  77 db b2 32 51 28 41 1e  |=\......w..2Q(A.|
00000090  a9 65 c8 a6 7d 26 68 8d  74 4e 56 92 f4 26 1f dc  |.e..}&h.tNV..&..|
000000a0  f7 e4 55 c1 f5 fb 6e 60  4e 97 4d d3 b1 5b a5 34  |..U...n`N.M..[.4|
000000b0  b7 7e c1 e8 23 76 6b af  61 bb 7e a3 79 31 4d ea  |.~..#vk.a.~.y1M.|
000000c0  8a e1 3c d6 12 d6 c7 fd  fa ba 94 dd 79 f4 8a 5c  |..<.........y..\|
000000d0  27 27 69 ba 22 7f 8b 5a  f0 4c 23 d5 8c 07 88 9d  |''i."..Z.L#.....|
000000e0  3c 09 15 3b 5b 21 94 d2  0e 66 83 b6 d8 f5 8d e9  |<..;[!...f......|
000000f0  72 44 b5 dc 0c 29 78 d1  10 b5 65 37 1b 4d 30 56  |rD...)x...e7.M0V|
00000100  72 6f 55 22 2b 01 89 af  01 6c d5 22 e0 60 ac a8  |roU"+....l.".`..|
00000110  02 4b dc 15 32 93 d7 c9  f2 d9 ba b2 cb 97 e4 33  |.K..2..........3|
00000120  5c d8 43 a4 10 8f bd 42  14 97 69 aa 4c f5 e9 8e  |\.C....B..i.L...|
00000130  da 2b 5d cb f4 79 3a 05  71 89 49 6f b9 cb 4a 64  |.+]..y:.q.Io..Jd|
00000140  e8 21 59 87 11 92 10 47  2a c7 e8 ea 0a 7b 3b c3  |.!Y....G*....{;.|
00000150  d0 9e ea b0 9a 4c 84 eb  e5 4a 0b 61 72 b1 2c ad  |.....L...J.ar.,.|
00000160  8b 4d f1 53 db 6d 69 0f  f6 2f 18 ad ea 4e cf 22  |.M.S.mi../...N."|
00000170  b4 25 52 11 07 43 d3 c6  e8 a3 0b be 29 c5 45 7f  |.%R..C......).E.|
00000180  78 bf 22 81 a3 6d 14 8b  16 5b ee 58 93 7e d1 99  |x."..m...[.X.~..|
00000190  ac ff e6 ad d3 4b 47 c6  3c bf c9 46 b4 0e 2a 83  |.....KG.<..F..*.|
000001a0  48 72 44 0b 1c f3 61 d4  3b 2c 65 71 7b ed 61 84  |HrD...a.;,eq{.a.|
000001b0  ba 95 04 65 91 ff 65 2f  c7 2a 12 1a 87 71 e0 1e  |...e..e/.*...q..|
000001c0  de 3a e6 9c d4 6c 1e 01  49 6b 27 63 21 79 c3 0b  |.:...l..Ik'c!y..|
000001d0  2f 55 a6 4e 1b a5 24 47  88 ab 1d 33 5a 79 86 fb  |/U.N..$G...3Zy..|
000001e0  31 98 14 7b 87 9a 9c c5  78 3c db 14 09 03 25 ce  |1..{....x<....%.|
000001f0  72 f2 c9 56 4a 45 62 22  ea 74 2e 45 50 d3 37 cc  |r..VJEb".t.EP.7.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script055.sh: línea 1704: /usr/bin/wc: Error de entrada/salida
boot_info_script055.sh: línea 1704: [: -gt: se esperaba un operador unario

```

My first partition is the one containing Windows XP, and the second one is deleted I think; both were (are) under NTFS.

---

### Post by coffeecat on 2011-04-18
YOU seem to have a Wubi installation - which you didn't mention - which puts a whole different perspective on the situation. I can see countless problems in your boot script, as follows:

You have grub 2 installed to the mbr. For wubi you do need a Windows mbr - that needs fixing.

You have grub 2 files (/grub/core.img and /boot/grub/core.img) in your sda1 (which would appear to be your Windows boot and/or C: partition). They have no business being there and are probably interfering with the Windows boot files. You do, in fact, have /ntldr so the error message you got about a missing ntldr was probably because of confusion caused by the grub files.

Despite having grub 2 in sda, you have a legacy grub menu.lst in sdc1 - which is a FAT32 partition! I don't know whether that's a leftover from some previous installation, but it is the most extraordinary menu.lst I've seen, referencing an interesting variety of boot loading utilities.

There may be other problems but, if so, I've missed them; I'm feeling suddenly very unwell and need to log off. I will, however, pm someone who knows more about wubi than I and hopefully he will be able to help you.

---

### Post by ZShock on 2011-04-18
Such mess I've done :D
Thanks for your help.

Edit (once again: ) I think that FAT32 with GRUB inside is the USB drive I've been using to mount the Live CD and every tool I've been trying in my hdd.

---

### Post by kiyop on 2011-04-18
Can you mount /dev/sda1 by booting with Ubuntu Live CD?

If not, testdisk may solve the problem. But I think you can mount.

If you can mount, install lilo (with -M option) to MBR (and fixboot) may solve the problem.

Remove USB drive and boot with Ubuntu Live CD with internet cable connected, open terminal and type:
```
sudo apt-get update
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```If you do not have Ubuntu Live CD, with Live USB drive, you can do similar thing.

After the above operation, shutdown and remove Live CD (and/or Live USB) and restart.

Do you have Windows XP install CD?

---

### Post by ZShock on 2011-04-18
I've followed the listed steps, yet when booting the HDD, it keeps saying "Operating System not found."
Thanks for your help U-U

---

### Post by kiyop on 2011-04-18
Thanks for your report.

I could not expect what you reported, judging from the result of boot info script.

Boot with Live Ubuntu (USB? CD?) and open terminal and type,
```
sudo dd if=/dev/sda1 bs=512 count=1 2>/dev/null|hd
```and copy the result and paste to "Reply" and submit.

---

### Post by ZShock on 2011-04-18
Typing from my Ubuntu Live USB Disk (omg :D) Welcome, and thank you for your quick reply. Here is what I got:
```
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  8c f2 34 0c 00 00 00 00  |..........4.....|
00000030  00 00 0c 00 00 00 00 00  10 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  83 b5 40 c0 f1 40 c0 ba  |..........@..@..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
```

---

### Post by dragonfly41 on 2011-04-18
clue:   "NTLDR is missing"

[http://support.microsoft.com/kb/318728](http://support.microsoft.com/kb/318728)

---

### Post by ZShock on 2011-04-18
Once again, I've done as shown, replacing NTLDR and NTDETECT.COM from an XP disk, but the answer is the same: "Operating System not found."

Thanks for your help dragonfly41.

---

### Post by dandnsmith on 2011-04-18
> clue: "NTLDR is missing"

That's a mistaken assumption from what is displayed. That message string is a normal part of the boot block for Windows.

My mind isn't functioning well enough to really analyse the data offered at present - might try it later.

---

### Post by kiyop on 2011-04-18
Thanks for reporting.

Excuse my asking again and again.

Boot with Live Ubuntu and type at terminal:
```
sudo dd if=/dev/sda bs=512 count=1 2>/dev/null|hd
```and submit the result.

---

### Post by ZShock on 2011-04-18
Woot, it seems to me that it changed from the last time! Here is the new code...
```
00000000  fa eb 31 12 00 00 4c 49  4c 4f 16 08 10 00 01 00  |..1...LILO......|
00000010  00 7c 00 00 00 00 00 00  00 00 00 00 5e ac 08 c0  |.|..........^...|
00000020  74 09 b4 0e bb 07 00 cd  10 eb f2 b9 13 00 b4 86  |t...............|
00000030  cd 15 cd 18 31 c0 8e d0  bc 00 7c fb 89 e1 06 53  |....1.....|....S|
00000040  56 52 89 ce fc 8e d8 8e  c0 bf 00 06 b9 00 01 f3  |VR..............|
00000050  a5 ea 56 06 00 00 60 b8  00 12 b3 36 cd 10 61 66  |..V...`....6..af|
00000060  8b 3e b8 07 66 09 ff 74  1b b4 08 b2 80 cd 13 0f  |.>..f..t........|
00000070  b6 ca 92 ba 80 00 e8 9a  00 66 3b 3e b8 7d 74 04  |.........f;>.}t.|
00000080  42 e2 f3 92 be be 07 b9  04 00 f6 04 80 89 f5 78  |B..............x|
00000090  33 83 c6 10 e2 f4 e8 83  ff 4e 6f 20 70 61 72 74  |3........No part|
000000a0  69 74 69 6f 6e 20 61 63  74 69 76 65 0d 0a 00 f6  |ition active....|
000000b0  04 80 79 10 e8 65 ff 49  6e 76 61 6c 69 64 20 50  |..y..e.Invalid P|
000000c0  54 0d 0a 00 83 c6 10 e2  e6 89 ee 66 8b 44 08 66  |T..........f.D.f|
000000d0  a3 14 06 e8 3d 00 81 3e  fe 7d 55 aa 75 11 31 c0  |....=..>.}U.u.1.|
000000e0  58 3c fe 75 06 88 d4 5e  5b 07 92 ff 2e 10 06 e8  |X<.u...^[.......|
000000f0  2a ff 4e 6f 20 62 6f 6f  74 20 73 69 67 6e 61 74  |*.No boot signat|
00000100  75 72 65 20 69 6e 20 70  61 72 74 69 74 69 6f 6e  |ure in partition|
00000110  0d 0a 00 60 bd 0c 00 be  0c 06 bb aa 55 b4 41 cd  |...`........U.A.|
00000120  13 72 0f 81 fb 55 aa 75  09 f6 c1 01 74 04 b4 42  |.r...U.u....t..B|
00000130  eb 3f 52 b4 08 cd 13 72  43 51 c0 e9 06 86 e9 89  |.?R....rCQ......|
00000140  cf 59 c1 ea 08 92 40 83  e1 3f f7 e1 93 a1 14 06  |.Y....@..?......|
00000150  8b 16 16 06 39 da 73 22  f7 f3 39 f8 77 1c c0 e4  |....9.s"..9.w...|
00000160  06 86 e0 92 f6 f1 08 e2  89 d1 41 5a 88 c6 b8 01  |..........AZ....|
00000170  02 c4 5c 04 cd 13 72 05  61 c3 b4 40 5a 4d 74 06  |..\...r.a..@ZMt.|
00000180  30 e4 cd 13 eb 91 e8 93  fe 44 69 73 6b 20 72 65  |0........Disk re|
00000190  61 64 20 65 72 72 6f 72  0d 0a 00 00 00 00 00 00  |ad error........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 44 63  8b 0c 8c 0c 00 00 80 01  |......Dc........|
000001c0  01 00 07 fe ff ff 3f 00  00 00 8d f2 34 0c 00 00  |......?.....4...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Rubi1200 on 2011-04-18
Fellow user coffeecat asked me to help out so I will add some comments of a more general nature.

If you have a Wubi install, you **cannot** have GRUB in the MBR. Wubi uses a program called grub4dos to boot the virtual file-system from within the host. It does so by using the Windows bootloader.

Here is what I suggest:

use the LiveCD to remove _only_ the following files from sda1:
> /wubildr /grub/core.img /boot/grub/core.imgThen, still on the LiveCD, run the commands again given by kiyop to install lilo to the MBR, in post #8.

Let's see where that gets us before proceeding with anything else.

EDIT: more information. your Wubi install is also damaged, but we can fix that after Windows is booting again. And, the wubildr file on sda1 also needs a file that is currently on sda5. Therefore, make a copy of the wubildr file from sda1 before removing it just in case we need that file again later.

---

### Post by ZShock on 2011-04-18
Ookay Rubi1200, thanks for your help. In my rush, I couldn't save that last file you told me too, but everything else has been done. Anyways, I still keep getting that damn error: "Operative System not found."

---

### Post by kiyop on 2011-04-18
Thanks Rubi1200.
Thanks ZShock for reporting the result.

I will check the result.

Please make sure that your internal HDD is in boot order of BIOS. To configure and look BIOS setting, press F2, DEL, or some key at boot time.

---

### Post by ZShock on 2011-04-18
> **kiyop said:**
> Thanks Rubi1200.
Thanks ZShock for reporting the result.

I will check the result.

Please make sure that your internal HDD is in boot order of BIOS. To configure and look BIOS setting, press F2, DEL, or some key at boot time.
Yep, everything's in order.

---

### Post by kiyop on 2011-04-18
Thanks for reply, ZShock.

> **ZShock said:**
> ```
...
000001b0  00 00 00 00 00 00 44 63  8b 0c 8c 0c 00 00 80 01  |......Dc........|
000001c0  01 00 07 fe ff ff 3f 00  00 00 8d f2 34 0c 00 00  |......?.....4...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```
There is no information on /dev/sda2, although boot info script and fdisk tells the information on /dev/sda2.

I will dig more.

GPT? no...?

---

### Post by ZShock on 2011-04-18
Oh, sorry. Didn't I tell you? I deleted the second partition...

---

### Post by Rubi1200 on 2011-04-18
I think it would be useful if you run the boot info script again and post the results with these changes.

Can we assume you do not have the Windows XP installation CD?

---

### Post by dandnsmith on 2011-04-18
This is really gong to be fun - I see from the sda first block that he followed earlier advice and installed LILO.
The target is moving!!

---

### Post by kiyop on 2011-04-18
Oh! You deleted /dev/sda2!

Please run boot info script again as Rubi1200 suggested.
Do you have Windows XP install CD?

There seems no problem on the code in 0x54-0x1ff in /dev/sda2 PBR reported at [#11](http://ubuntuforums.org/showthread.php?p=10690608#post10690608).

---

### Post by ZShock on 2011-04-18
Sorry for the late asnwer guys, I fell asleep! Yes I have a boot CD (actually A USB drive with the same work) and my sda drive doesn't exist anymore.

---

### Post by kiyop on 2011-04-18
> **ZShock said:**
> Sorry for the late asnwer guys, I fell asleep! Yes I have a boot CD (actually A USB drive with the same work) and my sda drive doesn't exist anymore.
?????

Why do you think your sda drive does not exist?

---

### Post by ZShock on 2011-04-18
> **kiyop said:**
> ?????

Why do you think your sda drive does not exist?
*sda2; there.

---

### Post by ZShock on 2011-04-18
I have a Win XP disk, but I cannot run it in the computer since I have no disk drive; anyways if you're asking me to get into the recovery console I've been there already. Will now post another boot log.

---

### Post by ZShock on 2011-04-18
Alright, here is the new code. It seems to be way shorter, maybe because my usb drive is not listed, since I did not unplug and plug it again. I think it is more readable now. Anyway, here it is.
```

                Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.

```
Notice I have deleted the second partition and created a new NTFS volume (just because I do not like unused space.) At the moment I am getting the annoying not operating system found message, any help appreciated.

---

### Post by kiyop on 2011-04-18
If you can use Windows (XP) Recovery Console (via USB pendrive?), I suggest you to execute "fixmbr".

Refer to:
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

If your problem is not solved, execute "fixboot".

---

### Post by ZShock on 2011-04-19
> **kiyop said:**
> If you can use Windows (XP) Recovery Console (via USB pendrive?), I suggest you to execute "fixmbr".

Refer to:
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

If your problem is not solved, execute "fixboot".

Thanks for your help, kiyop. I tried that before lotsa times, and I think that wouldn't have worked. I've accidentally destroyed my partitions, so I installed Ubuntu 10.10 on the whole hdd. But, guess what, not operating system message's still there, I cannot boot the system in any way.

Kinda frustrating, does this mean that the HDD is failing? Because I can access my files thru mounting the sda inside o' Ubuntu. The bad thing is that I cannot access to the hard drive through DOS programs of rescue disks but Linux based systems; say GParted, Rescatux, Ubuntu Live CD...

Any clue on this?

Edit: I've found out what was wrong, and it was the BIOS. See I'm using a Phoenix BIOS in my netbook laptop, and I saw, everytime I went into the boot menu, that there was an exclamation mark next to my hard drive. I thought it was nothing, but WOW, that exclamation mark ended to mean that the device was disabled for booting! Dammit! I've lost so much data... Anyways, the answer's there for those who had the same problem: I guess the previous solutions could even work.

Oh, and in order to remove this question mark, all I had to do was to press shift + F1 while selecting the drive.

Thanks to everyone who've helped me all along this thread, it's been a nice experience, and I hope to come around more often to see what's up

---

### Post by Rubi1200 on 2011-04-19
I am glad you eventually got things sorted out.

Good luck and enjoy :)

---

### Post by kiyop on 2011-04-19
Congratulations!

> **kiyop said:**
> Please make sure that your internal HDD is in boot order of BIOS. To configure and look BIOS setting, press F2, DEL, or some key at boot time.

I should have concluded that "Operating System not found." is given by BIOS without passing control to MBR. I wonder if some kind of boot loader gives such message.

---

### Post by ZShock on 2011-04-19
What I've learn of all this, is: never, **ever**, do a Wubi install. If you want Linux, then go ahead and make a partition, it'll bring less or none problems.

---

