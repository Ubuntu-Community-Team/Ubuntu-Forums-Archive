---
title: "Partition table issues"
date: 2010-09-07
forum: General Help
---

### Post by themostunoriginalname on 2010-09-07
Currently, I have this setup

Intel C2D e6300
6GB RAM
GTX 275
OCZ ModXStream 500W
Seagate 7200.9 500GB
Seagate 7200.8 320GB

The 320GB drive has been running 40GB for Ubuntu 9.10, 40GB for Windows 7, and the rest for random space stuff for windows 7. It has been working fine for a while, but suddenly, I get this message when grub is loading:

Grub Loading
Error: No Such partition
grub rescue>

I have been looking around, but I quite get any of the solutions to work. Here are some information you guys may find useful. I booted up a live version of Ubuntu 10.04 and did fdisk -l. Here's what I get

ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x3c8b of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x002da1b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25496       38913   107772645+   f  W95 Ext'd (LBA)
/dev/sda5   ?      241960      459876  1750408791   bd  Unknown

Disk /dev/sdb: 999 MB, 999817216 bytes
31 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 1922 * 512 = 984064 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5f70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1016      976345    b  W95 FAT32


Then, I tried this:

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda2
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda5


Any idea how to fix this?
Thank you in advance.

---

### Post by garvinrick4 on 2010-09-07
Download this script to DESKTOP then run the code I give you. Will give text file on desktop. Post in this thread you started. Copy and paste whole file and then highlight all of it and hit the # sign in upper right will be easier to read. Here is site and command.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 

```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by themostunoriginalname on 2010-09-07
Also, I forgot to mention that I unplugged my 500GB drive.

Anyway, below is the RESULTS.txt file

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   409,593,239   409,593,177   7 HPFS/NTFS
/dev/sda2         409,592,054   625,137,344   215,545,291   f W95 Ext d (LBA)
Invalid MBR Signature found
/dev/sda5     ? 3,887,079,541 7,387,897,122 3,500,817,582  bd Unknown
/dev/sda6     ? 2,244,550,315 6,336,174,901 4,091,624,587  7f Unknown

/dev/sda1 overlaps with /dev/sda2
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2
/dev/sda5 overlaps with /dev/sda6
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda2

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 999 MB, 999817216 bytes
31 heads, 62 sectors/track, 1016 cylinders, total 1952768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     1,952,751     1,952,690   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        01CAE1DD7C9C23B0                       ntfs       Extra space                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        785C-7FB1                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  59 37 7c bd 1c 82 44 3e  39 bf 7a 3f 0d 9e b3 bd  |Y7|...D>9.z?....|
00000010  08 79 1d 3e d9 f4 7b 3f  3c 69 7c bd 9f 27 03 3e  |.y.>..{?<i|..'.>|
00000020  a3 66 7d 3f 53 10 93 3d  a5 55 e0 bc 2c 3e 7f 3f  |.f}?S..=.U..,>.?|
00000030  dd a4 e0 bd c8 20 1d 3e  a6 67 7b 3f 33 fe c8 bd  |..... .>.g{?3...|
00000040  9b a4 93 3d 46 18 7e 3f  87 f0 9f 3a 3e ea e0 bc  |...=F.~?...:>...|
00000050  3f e7 7f 3f 7f 42 40 bd  45 d3 8b 3c 35 ae 7f 3f  |?..?.B@.E..<5..?|
00000060  89 5c d0 bd e1 96 93 3d  a7 00 7e 3f 2e 33 ce bd  |.\.....=..~?.3..|
00000070  36 bf 46 3d 64 65 7e 3f  ba 22 8e bd 5c a4 8b 3c  |6.F=de~?."..\..<|
00000080  6f 58 7f 3f a7 6a 33 bc  23 38 a3 bd 99 2b 7f 3f  |oX.?.j3.#8...+.?|
00000090  e9 94 0d be e9 d7 45 3d  53 3d 7d 3f c7 02 93 bd  |......E=S=}?....|
000000a0  4a fa 1c bd aa 26 7f 3f  e7 16 f9 bc 52 27 a3 bd  |J....&.?....R'..|
000000b0  4f 11 7f 3f 7a a3 0b be  08 fd 82 3d 59 14 7d 3f  |O..?z......=Y.}?|
000000c0  0e 4f 0e bd e7 49 1d bd  11 a8 7f 3f 23 ef a7 bd  |.O...I.....?#...|
000000d0  9c 6c 5d 3d 26 c3 7e 3f  d6 cb bc bd 19 a9 83 3d  |.l]=&.~?.......=|
000000e0  ca 60 7e 3f 69 56 85 bd  e6 71 33 3d e6 35 7f 3f  |.`~?iV...q3=.5.?|
000000f0  ed 54 9a bd 6d 8a 5d 3d  73 e5 7e 3f cb 0f 13 bd  |.T..m.]=s.~?....|
00000100  80 95 8b 3d 41 3d 7f 3f  d7 cd 3d bc 7b d0 33 3d  |...=A=.?..=.{.3=|
00000110  6b bc 7f 3f fc a9 d6 3c  fc 2e 4a 3d 94 99 7f 3f  |k..?...<..J=...?|
00000120  4f 6f ef 3b 99 ab 8b 3d  aa 65 7f 3f 00 00 00 80  |Oo.;...=.e.?....|
00000130  7c 13 72 3d 72 8d 7f 3f  17 cc 1f 3c 4d 3e 4a 3d  ||.r=r..?...<M>J=|
00000140  f1 ac 7f 3f d6 69 80 3d  4a 1d 13 3d ad 54 7f 3f  |...?.i.=J..=.T.?|
00000150  c2 16 22 3d f2 e2 71 3d  33 5a 7f 3f ed b7 1f 3c  |.."=..q=3Z.?...<|
00000160  e3 93 6f 3d ae 8c 7f 3f  54 58 04 3d d6 53 13 3d  |..o=...?TX.=.S.=|
00000170  5a b3 7f 3f 4e 3a 4f 3d  56 d4 01 bc 03 aa 7f 3f  |Z..?N:O=V......?|
00000180  d9 c2 81 bc 1b 8f 6f 3d  95 87 7f 3f a2 fb 3d 3c  |......o=...?..=<|
00000190  f2 fa db 3b 1e fa 7f 3f  53 eb d6 3c 7f f3 01 bc  |...;...?S..<....|
000001a0  61 e7 7f 3f 91 c7 65 3c  4a d6 29 3d 30 c1 7f 3f  |a..?..e<J.)=0..?|
000001b0  ed c1 47 3d b7 bb db 3b  8b b0 7f 3f 25 54 22 3d  |..G=...;...?%T"=|
000001c0  b8 cc bd 3c e8 ba 7f 3f  46 cf ae 3c aa d0 29 3d  |...<...?F..<..)=|
000001d0  b8 b8 7f 3f dc c0 b5 3d  5f 6d 8b 3c e1 f3 7e 3f  |...?...=_m.<..~?|
000001e0  42 5f a9 3d 59 4c bd 3c  f1 0d 7f 3f f0 05 6f bd  |B_.=YL.<...?..o.|
000001f0  d4 ac 8c 3d 44 f5 7e 3f  82 f6 db bb f6 f9 8b 3c  |...=D.~?.......<|
00000200

Unknown BootLoader  on sda5


Unknown BootLoader  on sda6



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory

---

### Post by john newbuntu on 2010-09-07
There clearly seems to be problems with the partition table on sda (320GB).  Your linux partitions are not being identified and the logical partition sda5 has overshot the extended partition sda2 ! Looks to me like it is time to make a full backup of your disk using say ddrescue (or some other data recovery tool) and trying to fix the partition table using testdisk.
[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

There could be other ways to fix this too.  Someone who has done this before can chip in here.

---

### Post by themostunoriginalname on 2010-09-07
I downloaded testdisk and chose the option to analyze the disk. This is what I see:

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 25495 254 63  409593177 [Extra space]
L HPFS - NTFS          25496   1  1 36576 254 63  178016202
L Linux Swap           36578   1  1 36820 254 63    3903732
P Linux                36821   0  1 38912 254 63   33607980


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue



The strange thing is that [Extra space] is not a bootable partition. The one below it though is probably bootable partition. Any idea how I can proceed with this and how I can fix this?

---

### Post by john newbuntu on 2010-09-07
You might have to perform a deeper search to locate the partitions.  If I am right, what you are seeing here is a quick search.  Hit enter and you will find an option for the deeper one.  You should hopefully see an Extended partition once the scan is done.  I wish you had an older fdisk output to cross verify what testdisk says.

---

### Post by themostunoriginalname on 2010-09-08
Did a deeper search and wrote it.

Now, here's the output for fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3fbb692b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       36821    90968062+   f  W95 Ext'd (LBA)
/dev/sda3           36822       38913    16803990   83  Linux
/dev/sda5           25497       36577    89008101    7  HPFS/NTFS
/dev/sda6           36579       36821     1951866   82  Linux swap / Solaris


I can mount back a 91GB partition and >200GB partition. I am unable to mount back the last partition. I don't remember having a 91GB partition. I remember it being around 40GB. I also did not remember having 17GB partition for the Linux drive either. Also, my mbr is messed up. Any ideas?

---

### Post by john newbuntu on 2010-09-08
Nothing glaringly stands out of the fdisk output to me although I am unable to correlate it with your findings.

When you say that the MBR is messed up, I assume that you are not able to boot into Ubuntu possibly because a part of GRUB2 being messed up.  Re-install grub2 to the MBR from a liveCD following section 13 from this post by drs305: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Also, since you have rewritten your partition table, just to be safe(I could be paranoid here), run a  'chkdsk' command on your NTFS partitions from the win boot CD and an 'e2fsck' command from Ubuntu liveCD on  /dev/sda3.

---

