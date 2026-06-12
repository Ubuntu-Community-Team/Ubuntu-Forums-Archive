---
title: "Fix boot loader"
date: 2010-08-18
forum: General Help
---

### Post by xissburg on 2010-08-18
Hey, [this]("http://ubuntuforums.org/showthread.php?t=1553115") [bug]("https://bugs.launchpad.net/ubuntu/+bug/609815") affected me a few days ago and I couldn't boot again. I got to boot in Windows 7 again after using the Windows 7 Recovery disc, but I still can't boot in Windows XP nor Ubuntu (installed through Wubi).  [bcbc]("https://launchpad.net/%7Ebcbc") told  me to start a thread here and post the results of running  boot_info_script so that someone would try to help me get the other OSes  booting again. I ran it in Live Ubuntu from a pendrive and here it goes

```
                Boot Info Script 0.55    dated February 15th, 2010                     

============================= Boot Info Summary:  ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2:  _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5  starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr  /wubildr

sda6:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6  starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr  /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda6/Wubi:  _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1:  _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   625,121,279   461,274,345   f W95 Ext d  (LBA)
/dev/sda5         163,846,998   327,693,869   163,846,872   7 HPFS/NTFS
/dev/sda6         327,693,933   625,121,279   297,427,347   7 HPFS/NTFS


Drive: sdb ___________________  _____________________________________________________

Disk /dev/sdb: 4127 MB, 4127195136 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8060928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     8,060,927     8,060,865   c W95 FAT32  (LBA)


blkid -c /dev/null:  ____________________________________________________________

Device           UUID                                   TYPE       LABEL                          

/dev/loop0                                              squashfs                                  
/dev/loop1       1702221f-6b2a-43c3-bc1b-91ad61dac9ce   ext4                                      
/dev/sda1        44E87E5AE87E49E6                       ntfs                                      
/dev/sda2: PTTYPE="dos" 
/dev/sda5        589CE6A29CE67A40                       ntfs                                      
/dev/sda6        F804D07404D0377A                       ntfs                                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B4B3-6B34                              vfat        XISSBURG                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini:  ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP  Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc  =======================

Unknown BootLoader  on sda2

00000000  2e 29 6f 60 a4 d5 27 33  8b f3 63 f3 7b 8c ba 92   |.)o`..'3..c.{...|
00000010  08 58 ac ce 15 bf b5 fe  ed 68 44 26 54 70 cd 6b   |.X.......hD&Tp.k|
00000020  7a 36 0e d4 01 f5 0d 06  54 29 da 58 be 9e 0e d8   |z6......T).X....|
00000030  e8 45 7a 50 d1 a8 80 86  35 84 6c ec 6d 5f 07 3a   |.EzP....5.l.m_.:|
00000040  7a 19 12 ea 0a 1b 36 16  4c 22 18 15 21 c5 54 d1   |z.....6.L"..!.T.|
00000050  21 bd b2 79 a5 d4 a1 9d  79 ce 54 45 fb 15 dd 03   |!..y....y.TE....|
00000060  fb 32 c1 1a 71 85 b9 d2  fb 1e ca e8 61 e7 6d 35   |.2..q.......a.m5|
00000070  d8 34 57 08 d5 3c 4f 1c  fb 74 2e c4 0a 8c dd 56   |.4W..<O..t.....V|
00000080  ce b1 bf 47 da d0 6b 29  76 3e c6 c7 a8 1c e0 4e   |...G..k)v>.....N|
00000090  2b da 5a f8 fd eb 3b 7f  48 59 ba 1e 8c a2 23 a9   |+.Z...;.HY....#.|
000000a0  81 a2 28 9b 80 48 8c 29  32 ba b8 71 bd ce b8 84   |..(..H.)2..q....|
000000b0  f2 4a 81 68 59 14 a1 fc  72 da 59 bb 04 29 1b f0   |.J.hY...r.Y..)..|
000000c0  6b 92 14 30 f7 10 e7 20  5b e8 d8 38 73 e0 8d bd  |k..0...  [..8s...|
000000d0  b5 5f 6d 2f dd 84 c9 85  fb 6c d8 72 41 bd 0c cb   |._m/.....l.rA...|
000000e0  32 96 d2 79 d6 ae 69 4d  45 53 0e 65 16 57 c0 15   |2..y..iMES.e.W..|
000000f0  80 43 01 11 36 38 08 8e  70 0c 48 22 80 20 d8 a2   |.C..68..p.H". ..|
00000100  47 60 d1 b2 2e 5c 53 06  f5 68 14 1a 97 e3 76 b6   |G`...\S..h....v.|
00000110  b9 f4 4d 3d 0a 18 04 91  d6 03 74 34 8e 5f 4d 69   |..M=......t4._Mi|
00000120  c4 13 2f 9e 9a 73 cd a8  06 77 23 a1 05 27 43 57   |../..s...w#..'CW|
00000130  09 c8 71 74 40 e7 57 df  16 66 ae 45 7c 89 f4 25   |..qt@.W..f.E|..%|
00000140  0b 7e 76 31 9d 39 71 03  39 75 9c c0 8a 41 3d fe   |.~v1.9q.9u...A=.|
00000150  31 2d c7 06 3b e3 eb f0  33 bb 50 8c b9 4e 0c 9d   |1-..;...3.P..N..|
00000160  b8 b9 67 0e fe 01 05 ac  63 2b 5a 5b fa c6 d6 ea   |..g.....c+Z[....|
00000170  47 a5 22 48 53 84 c6 8f  e3 08 c2 44 9d 33 09 9b   |G."HS......D.3..|
00000180  8c 36 97 6f a2 3b 25 29  c2 97 5b 8a 72 ab 59 be   |.6.o.;%)..[.r.Y.|
00000190  32 f7 5e c2 4d 5e 37 ca  e4 63 2f 10 52 a0 35 b0   |2.^.M^7..c/.R.5.|
000001a0  a0 80 c1 dd d3 bf 3d fb  c2 af c1 a5 da ba 90 26   |......=........&|
000001b0  1f a4 ac 17 a3 27 16 71  d2 43 cd 63 77 fc 00 fe   |.....'.q.C.cw...|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 d8 1a c4 09 00 fe   |......?.........|
000001d0  ff ff 05 fe ff ff 17 1b  c4 09 d2 61 ba 11 00 00   |...........a....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa   |..............U.|
00000200


```Thanks in advance.

---

### Post by JBAlaska on 2010-08-18
Have you tried using your windows 7 install disk or a recovery disk to repair your windows MBR?

1-Insert Win 7 installation DVD and boot from DVD drive. While in some older systems you may have to change boot order through system BIOS, most newer systems allow booting from DVD without changing boot order by simply clicking on any key when prompted to doing so.

2-Choose your default "Language", "Time", and "keyboard Input" on the first window and click next.

3-You're now presented with 3 choices. Click on "Repair Your Computer" to gain access to the System Recovery window. Now choose "Command Prompt" in order to run the desired utility which is called "bootsect.exe". Bootsect is located inside the boot folder so change your directory to boot. 

Now run "bootsect /nt60 C:\" if you had Win 7 initially installed in the C partition. Alternatively, you can run "bootsect /nt60 SYS" or "bootsect /nt60 ALL" to repair the system partition or all partitions. Eject the DVD, and restart computer. Your computer should now boot Win 7 again.

---

### Post by bcbc on 2010-08-18
Try this to get Windows XP to show: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) (run bootrec.exe /scanos)

Regarding wubi, well first you probably need to get XP booting. Second it looks like there are problems mounting the root.disk. So you might need to run fsck on it. 

Let's see if you can get XP loaded and then worry about root.disk. I advise to take backups if there is critical data in root.disk (before trying to recover it).

---

### Post by NUboon2Age on 2010-08-22
Any progress Xiss burg?

---

### Post by xissburg on 2010-08-23
I've been busy lately :3 .  

@JBAlaska: I already got to boot in Win7 (since I created this thread)
@bcbc: I'll try that when I find some free time

Thanks

---

### Post by NUboon2Age on 2010-08-29
btw, this is [https://bugs.launchpad.net/ubuntu/+bug/609815](https://bugs.launchpad.net/ubuntu/+bug/609815) .  Any news Xiss burg?

---

