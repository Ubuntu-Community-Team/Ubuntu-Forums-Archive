---
title: "Point grub to windows?"
date: 2011-02-13
forum: General Help
---

### Post by krepperk on 2011-02-13
I have had win 7 and xp installed but since I didn't use xp I wanted to remove that partition in order to clean up my partitions. This caused the computer to stop from booting into windows and it displayed the "bootmgr is missing" messege. So now I can only boot into ubuntu 10.10 and i need windows since I'm a musician and ubuntu doesn't support my soundcard.
I've been searching the forum to try and get help with my problem but nothing has worked.
This is the output from boot info script, I have added the windows7 entry in grub but it doesn't work. I know it's a bit of a mess but I really need help.
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 1370. But according to the info from fdisk, 
                       sdb8 starts at sector 502353920.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 62. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    19,531,775    19,529,728  82 Linux swap / Solaris
/dev/sda2          19,533,822   136,718,335   117,184,514   5 Extended
/dev/sda5          19,533,824   136,718,335   117,184,512  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,939,880,879 1,939,880,817   5 Extended
/dev/sdb5                 126    40,965,749    40,965,624   7 HPFS/NTFS
/dev/sdb6          40,965,813   143,690,215   102,724,403  83 Linux
/dev/sdb7         143,797,878   502,352,549   358,554,672   7 HPFS/NTFS
/dev/sdb8         502,353,920   624,715,775   122,361,856   7 HPFS/NTFS
/dev/sdb9         624,719,718   636,848,729    12,129,012  82 Linux swap / Solaris
/dev/sdb10        636,848,793 1,187,348,084   550,499,292   7 HPFS/NTFS
/dev/sdb11      1,271,480,553 1,939,880,879   668,400,327   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8005 MB, 8005787648 bytes
32 heads, 63 sectors/track, 7756 cylinders, total 15636304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    15,636,095    15,636,033   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2493d5ee-eca5-4e54-82b4-0613ee8d22d9   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c6845d6e-6cca-4c9b-94de-177660c17554   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb10       62029D6352AA2E6A                       ntfs       Gris                          
/dev/sdb11       2B61B42F31334A1B                       ntfs       Hest                          
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        D070F14370F130B8                       ntfs                                     
/dev/sdb6        128844ba-cbfa-4076-ab31-e56c7e2d21c7   ext3                                     
/dev/sdb7        6C3854DE3854A8BA                       ntfs       FÃ¥r                          
/dev/sdb8        40D87431D8742776                       ntfs                                     
/dev/sdb9        1b10b5da-543b-42e1-a354-546f46e54a21   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        4D50-46B4                              vfat       J[N&#710;w&#8240;ýª                   
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdd1        /media/sdd1              vfat       (rw)
/dev/sdb8        /media/40D87431D8742776  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=c6845d6e-6cca-4c9b-94de-177660c17554 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=c6845d6e-6cca-4c9b-94de-177660c17554 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c6845d6e-6cca-4c9b-94de-177660c17554 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c6845d6e-6cca-4c9b-94de-177660c17554 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (on /dev/sdc6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 128844ba-cbfa-4076-ab31-e56c7e2d21c7
	linux /boot/vmlinuz-2.6.30.9 root=UUID=128844ba-cbfa-4076-ab31-e56c7e2d21c7 ro quiet splash
	initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (recovery mode) (on /dev/sdc6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 128844ba-cbfa-4076-ab31-e56c7e2d21c7
	linux /boot/vmlinuz-2.6.30.9 root=UUID=128844ba-cbfa-4076-ab31-e56c7e2d21c7 ro single
	initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sdc6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 128844ba-cbfa-4076-ab31-e56c7e2d21c7
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=c6845d6e-6cca-4c9b-94de-177660c17554 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=c6845d6e-6cca-4c9b-94de-177660c17554 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c6845d6e-6cca-4c9b-94de-177660c17554 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c6845d6e-6cca-4c9b-94de-177660c17554 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set c6845d6e-6cca-4c9b-94de-177660c17554
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (on /dev/sdc6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 128844ba-cbfa-4076-ab31-e56c7e2d21c7
	linux /boot/vmlinuz-2.6.30.9 root=UUID=128844ba-cbfa-4076-ab31-e56c7e2d21c7 ro quiet splash
	initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (recovery mode) (on /dev/sdc6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 128844ba-cbfa-4076-ab31-e56c7e2d21c7
	linux /boot/vmlinuz-2.6.30.9 root=UUID=128844ba-cbfa-4076-ab31-e56c7e2d21c7 ro single
	initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sdc6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 128844ba-cbfa-4076-ab31-e56c7e2d21c7
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###

menuentry "windows7" {
set root=' (hd2,msdos8)'
chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda5 during installation
UUID=c6845d6e-6cca-4c9b-94de-177660c17554  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda1 during installation
UUID=2493d5ee-eca5-4e54-82b4-0613ee8d22d9  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1     vfat  defaults                  0  0  
/dev/sdd1                                  /media/sdd1     vfat  defaults                  0  0  

=================== sda5: Location of files loaded by Grub: ===================


  18.7GB: boot/grub/core.img
  27.8GB: boot/grub/grub.cfg
  11.3GB: boot/initrd.img-2.6.35-22-generic
  16.9GB: boot/initrd.img-2.6.35-25-generic
  18.7GB: boot/vmlinuz-2.6.35-22-generic
  18.7GB: boot/vmlinuz-2.6.35-25-generic
  16.9GB: initrd.img
  11.3GB: initrd.img.old
  18.7GB: vmlinuz
  18.7GB: vmlinuz.old

=========================== sdb6/boot/grub/menu.lst: ===========================

splashimage=128844ba-cbfa-4076-ab31-e56c7e2d21c7/boot/grub/splash.xpm.gz

title		Ubuntu 8.10, kernel 2.6.30.9
uuid		128844ba-cbfa-4076-ab31-e56c7e2d21c7
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=128844ba-cbfa-4076-ab31-e56c7e2d21c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.30.9
quiet

title		Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid		128844ba-cbfa-4076-ab31-e56c7e2d21c7
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=128844ba-cbfa-4076-ab31-e56c7e2d21c7 ro  single
initrd		/boot/initrd.img-2.6.30.9

title		Ubuntu 8.10, memtest86+
uuid		128844ba-cbfa-4076-ab31-e56c7e2d21c7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional x64 Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb6/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=128844ba-cbfa-4076-ab31-e56c7e2d21c7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb8
UUID=1b10b5da-543b-42e1-a354-546f46e54a21 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  30.9GB: boot/grub/menu.lst
  30.9GB: boot/grub/stage2
  31.1GB: boot/initrd.img-2.6.30.9
  31.0GB: boot/vmlinuz-2.6.30.9
  31.1GB: initrd.img
  31.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  00 8b 96 28 b8 00 00 8b  06 8d 4d f8 51 8b 4a 04  |...(......M.Q.J.|
00000010  8b 90 94 00 00 00 68 00  00 0f 00 57 51 8b ce ff  |......h....WQ...|
00000020  d2 85 c0 0f 8c a8 00 00  00 8b 4d fc 8b 55 f8 8b  |..........M..U..|
00000030  06 51 8b 4d f4 52 8b 90  80 00 00 00 51 8b ce ff  |.Q.M.R......Q...|
00000040  d2 85 c0 0f 8c 88 00 00  00 8b 06 53 8d 4d fc 51  |...........S.M.Q|
00000050  8b 8e 28 b8 00 00 8d 55  f4 52 8b 51 04 8b 0c ba  |..(....U.R.Q....|
00000060  8b 90 90 00 00 00 8d 1c  bd 00 00 00 00 51 8b ce  |.............Q..|
00000070  ff d2 85 c0 7c 5a 8b 96  28 b8 00 00 8b 06 8d 4d  |....|Z..(......M|
00000080  f8 51 8b 4a 04 8b 90 94  00 00 00 68 00 00 0f 00  |.Q.J.......h....|
00000090  03 cb 57 51 8b ce ff d2  85 c0 7c 34 8b 4d fc 8b  |..WQ......|4.M..|
000000a0  55 f8 8b 06 51 8b 4d f4  52 8b 90 80 00 00 00 51  |U...Q.M.R......Q|
000000b0  8b ce ff d2 85 c0 7c 18  8b 06 8b 50 78 8b ce ff  |......|....Px...|
000000c0  d2 85 c0 7c 0b e8 16 6e  00 00 85 c0 7c 02 33 c0  |...|...n....|.3.|
000000d0  5b 5f 5e 8b e5 5d c3 cc  cc cc cc cc cc cc cc cc  |[_^..]..........|
000000e0  8b ff 55 8b ec 83 ec 08  56 6a 28 8b f0 e8 ee 0a  |..U.....Vj(.....|
000000f0  00 00 85 c0 7c 67 8b 06  8d 4d fc 51 8b 8e 28 b8  |....|g...M.Q..(.|
00000100  00 00 8d 55 f8 52 8b 51  04 8b 0a 8b 90 90 00 00  |...U.R.Q........|
00000110  00 51 8b ce ff d2 85 c0  7c 43 0f b6 55 08 8b 4d  |.Q......|C..U..M|
00000120  fc 8b 06 8b 80 80 00 00  00 f7 da 1b d2 51 81 e2  |.............Q..|
00000130  00 00 00 0d 0b 55 f8 68  00 00 e4 00 52 8b ce ff  |.....U.h....R...|
00000140  d0 85 c0 7c 18 8b 16 8b  42 78 8b ce ff d0 85 c0  |...|....Bx......|
00000150  7c 0b e8 89 6d 00 00 85  c0 7c 02 33 c0 5e 8b e5  ||...m....|.3.^..|
00000160  5d c2 04 00 cc cc cc cc  cc cc cc cc cc cc cc cc  |]...............|
00000170  8b ff 56 6a 2a 8b f0 e8  64 0a 00 00 85 c0 7c 18  |..Vj*...d.....|.|
00000180  8b 06 8b 50 78 8b ce ff  d2 85 c0 7c 0b e8 4e 6d  |...Px......|..Nm|
00000190  00 00 85 c0 7c 02 33 c0  5e c3 cc cc cc cc cc cc  |....|.3.^.......|
000001a0  8b ff 56 6a 2b 8b f0 e8  34 0a 00 00 85 c0 7c 18  |..Vj+...4.....|.|
000001b0  8b 06 8b 50 78 8b ce ff  d2 85 c0 7c 0b e8 00 fe  |...Px......|....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 18 fc 06 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2011-02-13
Windows has to boot from a primary partition, yours is in sda5 a logical. Your boot files were in the XP partition. Windows moves all the boot files from second installs whether in primary or logical partitions to the first install with the boot flag as that is the only bootable partition with windows. If it was XP there would be workarounds, but I do not know of any with Vista/7. You can restall windows or create a small 100MB primary NTFS boot partition for windows to use to boot. And I do not think the repairs are then automatic as windows does not recognize the install in the logical without an install in the primary.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You generally should not make all the partitions on a drive logical inside the extended. You could delete sda1 and reinstall a swap partition somewhere else, but will have to edit fstab with the new UUID. But it would be best to have windows all on one drive.

---

### Post by krepperk on 2011-02-14
Thank's for your help, have read the the multibooters page, very informative.

---

