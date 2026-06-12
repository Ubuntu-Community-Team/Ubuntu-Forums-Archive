---
title: "How to configure GRUB2 from Live cd installed on a drive with no  linux"
date: 2010-11-14
forum: General Help
---

### Post by chasigor on 2010-11-14
I've got an error during ubuntu installation from USB stick now and killed grub.  Now i've reinstalled it on the linux partition without working ubuntu but formatted and with a part of files on it. 

How to configure GRUB2 from ubuntu live CD cause i need to at least load my Windows now?

---

### Post by lmarmisa on 2010-11-14
What version of Windows do you use?.

---

### Post by chasigor on 2010-11-14
XP
but I would like to repair grub not windows loader.

---

### Post by Quackers on 2010-11-14
Please boot from your Ubuntu live cd/usb and select "try Ubuntu" then go to the site below and download the boot script to your DESKTOP then open a terminal and run the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by chasigor on 2010-11-14
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    25,173,854    25,173,792   7 HPFS/NTFS
/dev/sda2          25,174,014   234,491,903   209,317,890   f W95 Ext d (LBA)
/dev/sda5          30,716,343   223,271,369   192,555,027   7 HPFS/NTFS
/dev/sda6          25,174,016    30,713,855     5,539,840  82 Linux swap / Solaris
/dev/sda7         223,272,960   234,491,903    11,218,944  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,646,719    15,638,656   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       308ccec3-9d41-d544-9ea7-344f15962f8f   ext2       casper-rw                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        9ADCAA4FDCAA258B                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        B440328440324D7C                       ntfs       DISK                          
/dev/sda6        74149def-7c52-4f46-bfa1-7694a08580fd   swap                                     
/dev/sda7        7d3f2af5-daea-41d4-92de-e91e69d49533   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C1A8-458B                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7        /mnt                     ext4       (rw)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
    .8GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: vmlinuz

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 114.5GB: boot/grub/core.img
 115.1GB: boot/vmlinuz-2.6.35-22-generic
 115.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2e 3f 41 56 43 52 65 63  6f 72 64 65 72 43 6f 6d  |.?AVCRecorderCom|
00000010  62 6f 62 6f 78 40 40 00  08 df 08 10 00 00 00 00  |bobox@@.........|
00000020  2e 3f 41 56 3f 24 43 43  6f 6d 43 6f 43 6c 61 73  |.?AV?$CComCoClas|
00000030  73 40 56 43 52 65 63 6f  72 64 65 72 43 6f 6d 62  |s@VCRecorderComb|
00000040  6f 62 6f 78 40 40 24 31  3f 43 4c 53 49 44 5f 52  |obox@@$1?CLSID_R|
00000050  65 63 6f 72 64 65 72 43  6f 6d 62 6f 62 6f 78 40  |ecorderCombobox@|
00000060  40 33 55 5f 47 55 49 44  40 40 42 40 41 54 4c 40  |@3U_GUID@@B@ATL@|
00000070  40 00 00 00 00 00 00 00  08 df 08 10 00 00 00 00  |@...............|
00000080  2e 3f 41 56 3f 24 49 4e  45 52 4f 5f 53 43 53 49  |.?AV?$INERO_SCSI|
00000090  5f 44 45 56 49 43 45 5f  49 4e 46 4f 5f 49 6d 70  |_DEVICE_INFO_Imp|
000000a0  6c 40 56 43 52 65 63 6f  72 64 65 72 43 6f 6d 62  |l@VCRecorderComb|
000000b0  6f 62 6f 78 40 40 40 40  00 00 00 00 08 df 08 10  |obox@@@@........|
000000c0  00 00 00 00 2e 3f 41 55  49 52 65 63 6f 72 64 65  |.....?AUIRecorde|
000000d0  72 43 6f 6d 62 6f 62 6f  78 33 40 40 00 00 00 00  |rCombobox3@@....|
000000e0  08 df 08 10 00 00 00 00  2e 3f 41 55 49 52 65 63  |.........?AUIRec|
000000f0  6f 72 64 65 72 43 6f 6d  62 6f 62 6f 78 32 40 40  |orderCombobox2@@|
00000100  00 00 00 00 08 df 08 10  00 00 00 00 2e 3f 41 55  |.............?AU|
00000110  49 52 65 63 6f 72 64 65  72 43 6f 6d 62 6f 62 6f  |IRecorderCombobo|
00000120  78 40 40 00 08 df 08 10  00 00 00 00 2e 3f 41 56  |x@@..........?AV|
00000130  3f 24 49 43 68 69 6c 64  57 69 6e 64 6f 77 49 6d  |?$IChildWindowIm|
00000140  70 6c 40 56 43 52 65 63  6f 72 64 65 72 43 6f 6d  |pl@VCRecorderCom|
00000150  62 6f 62 6f 78 40 40 40  40 00 00 00 08 df 08 10  |bobox@@@@.......|
00000160  00 00 00 00 2e 3f 41 55  49 43 68 69 6c 64 57 69  |.....?AUIChildWi|
00000170  6e 64 6f 77 40 40 00 00  08 df 08 10 00 00 00 00  |ndow@@..........|
00000180  2e 3f 41 56 3f 24 43 44  65 76 69 63 65 49 6e 66  |.?AV?$CDeviceInf|
00000190  6f 73 49 6d 70 6c 40 56  43 52 65 63 6f 72 64 65  |osImpl@VCRecorde|
000001a0  72 43 6f 6d 62 6f 62 6f  78 40 40 40 40 00 00 00  |rCombobox@@@@...|
000001b0  08 df 08 10 00 00 00 00  2e 3f 41 56 3f 24 00 fe  |.........?AV?$..|
000001c0  ff ff 07 fe ff ff b9 91  54 00 13 28 7a 0b 00 fe  |........T..(z...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 88 54 00 00 00  |............T...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 30 00  |.X.SYSLINUX..@0.|
00000010  02 00 00 00 00 f8 00 00  3f 00 80 00 80 1f 00 00  |........?.......|
00000020  80 a0 ee 00 78 07 00 00  00 00 00 00 02 00 00 00  |....x...........|
00000030  01 00 08 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 8b 45 a8 c1 4b  49 4e 47 53 54 4f 4e 20  |..).E..KINGSTON |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 60 50 69 00  66 ba 00 00 00 00 bb 00  |}.f.`Pi.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by lmarmisa on 2010-11-14
Boot your system from an Ubuntu LiveCD, open a terminal and type these commands:

```

sudo bash
mount /dev/sda7 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda
exit
exit

```

---

### Post by Quackers on 2010-11-14
According to the boot script info you have 2 Ubuntu 10.10 installations. The first is on sda1 which is a NTFS partition, which is no good for Ubuntu.
The second is on sda7, which is an ext4 formatted partition.
Neither the sda1 or the sda7 partitions have all the necessary boot files for Ubuntu to boot (/boot/grub/grub.cfg is missing on both partitions).
I don't see a Windows operating system installed at all.
To fix Ubuntu I would recommend booting from the Ubuntu live cd and mounting the sda7 partition and re-installing grub to sda, using the guide written by drs305 below.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by chasigor on 2010-11-14
windows is still on sda1

---

