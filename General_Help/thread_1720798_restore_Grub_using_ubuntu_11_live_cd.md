---
title: "restore Grub using ubuntu 11 live cd"
date: 2011-04-03
forum: General Help
---

### Post by schorli on 2011-04-03
My main operating system is Win7 and i had a ubuntu 10.10 as secondary on my notebook, but it never really worked (screen was almost, but not 100% black, impossible to work on. It did work however if i used an external monitor, then i got a perfect image on both displays --but that might get it's own topic in some time).
So i thought that Ubuntu 11 might fix this issue, deleted the linux partition in windows and started the live version of Ubuntu11 - same problem. 
But now, when I try to boot windows I get the error "couldn't load file system" and get to the "grub recover" menu. 
I don't have the windows dvds with me, so i hope to fix this using the live cd.

I already looked for solutions, but I don't get very far.

For example i tried to fallow this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
but ```
 find /boot/grub/stage1
``` gives me an Error 15: File not found


I feel lost :(

btw, sorry for the 6th grub problem of the day

---

### Post by techunit on 2011-04-03
Arg another wonderful grub problem! ](*,)

take a look at this and see if this helps.

Without Windows CD
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

With Windows CD
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

Good Luck.

---

### Post by wilee-nilee on 2011-04-03
Here is a download of a small recovery ISO for W7, burn it and follow these directions to slip in the MS bootloader.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

ms-sys is a older method lilo is a better alternative, amongst others.

---

### Post by coffeecat on 2011-04-03
> **techunit said:**
> Without Windows CD
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)


Unfortunately, ms-sys was removed from the Ubuntu repositories from the 8.04 release because of licensing issues.

@schorli, if you want to repair the Windows mbr with an Ubuntu live CD, the last post in this thread gives you three alternatives to the disappeared ms-sys:

[http://ubuntuforums.org/showthread.php?t=868342](http://ubuntuforums.org/showthread.php?t=868342)

It also gives more background on the removal of ms-sys.

---

### Post by techunit on 2011-04-03
> **coffeecat said:**
> Unfortunately, ms-sys was removed from the Ubuntu repositories from the 8.04 release because of licensing issues.

@schorli, if you want to repair the Windows mbr with an Ubuntu live CD, the last post in this thread gives you three alternatives to the disappeared ms-sys:

[http://ubuntuforums.org/showthread.php?t=868342](http://ubuntuforums.org/showthread.php?t=868342)

It also gives more background on the removal of ms-sys.
Thank you. I am going to bookmark Wilee-Nilee's urls for future reference.

---

### Post by schorli on 2011-04-03
thx coffecat, I was just fighting with the ms-sys.


I didn't see the similar thread "win7 boot loader broken" before, but just to make sure i uploaded my results of the bootscript.

&#8364;: Thanks! You guys are awesome :D


For the record, these 2 lines were all i needed:

```
sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
```

---

### Post by coffeecat on 2011-04-04
I'm glad the lilo fix worked for you

I'll repost your RESULTS.txt so that it is easily readable because there are some oddities in it.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    30,411,044    30,410,982  27 Hidden HPFS/NTFS
/dev/sda2          30,411,045    37,752,749     7,341,705  12 Compaq diagnostics
/dev/sda3    *     37,752,750    37,961,594       208,845   7 HPFS/NTFS
/dev/sda4          37,961,656 1,250,260,991 1,212,299,336   f W95 Ext d (LBA)
/dev/sda5          37,961,658 1,188,818,624 1,150,856,967   7 HPFS/NTFS
/dev/sda6       1,247,414,272 1,250,260,991     2,846,720  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     7,843,839     7,835,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5C902352902331C6                       ntfs       PQSERVICE                     
/dev/sda2        220823E80823B9A5                       ntfs       ARCADE                        
/dev/sda3        D8A4241AA423FA20                       ntfs       SYSTEM RESERVED               
/dev/sda4: PTTYPE="dos" 
/dev/sda5        66C42582C4255619                       ntfs       Acer                          
/dev/sda6        b321e66f-bc1a-4975-ba0d-51450e6bfee3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AA8D-36ED                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Acer              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 56 04  |.X.SYSLINUX...V.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 00 00  |........?.... ..|
00000020  00 90 77 00 d5 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ed 36 8d aa 4e  4f 20 4e 41 4d 45 20 20  |..).6..NO NAME  |
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
00000110  c6 06 45 7d 00 66 b8 08  40 00 00 66 ba 00 00 00  |..E}.f..@..f....|
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
```You must have run the bootscript before you installed lilo to the mbr, because it is showing grub in the mbr, and rather oddly pointing to sda6, your Linux swap partition which is your only Linux partition. Your partitions are (approx sizes):

sda1 - primary - 15.6GB - hidden recovery partition (I guess)
sda2 - primary - 3.8GB - Compaq diagnostics
sda3 - primary - 106MB - Windows 7 boot partition
sda4 - extended partition, containing:
sda5 - logical - 589GB - Windows C: partition
sda6 - logical - 1.5GB - Linux swap partition.

It's unusual to have a Windows C: partition as a logical partition, but since it boots from the primary partition sda3, this is OK. I guess Compaq must have set it up that way.

What I don't understand is how you come to have a Linux swap partition with no other Linux partitions. Whatever, if you need any further help, just post back. :)

---

