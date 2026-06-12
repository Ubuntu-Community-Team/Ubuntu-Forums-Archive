---
title: "Grub/MBR problems -- system won't boot"
date: 2011-04-18
forum: General Help
---

### Post by Quiver on 2011-04-18
I am stuck at the GRUB> prompt. 
Which is an improvement from being stuck at the GRUB Rescue> prompt.

I've looked at many other threads by people with a similar problem, but what works for them seems not to work for me.

Here is the RESULTS.txt from the boot_info_script:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    58,521,147    58,519,100   7 HPFS/NTFS
/dev/sda2          58,521,598   467,382,271   408,860,674   5 Extended
/dev/sda5         138,178,560   372,553,559   234,375,000  83 Linux
/dev/sda6         372,553,728   457,687,039    85,133,312  83 Linux
/dev/sda7         457,689,088   461,418,495     3,729,408  82 Linux swap / Solaris
/dev/sda8         461,428,736   467,382,271     5,953,536  82 Linux swap / Solaris
/dev/sda3         467,382,272   488,353,791    20,971,520   b W95 FAT32
/dev/sda4         488,353,792   488,392,064        38,273  1b Hidden W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,935,999     7,935,938   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b64a7490-0fd4-45cb-a3d2-bb1a7cadef07   ext3                                     
/dev/sda1        029EAFED9EAFD785                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        86F4-D40A                              vfat                                     
/dev/sda5        3dcba3f5-ba88-4bef-af18-90d365f363fa   ext4       majstudio                     
/dev/sda6        04b40181-c355-4cff-ad6a-86e3d4730160   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4F97-85EE                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /win                     ext4       (rw)
/dev/sda5        /lin                     ext4       (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod fat
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 86f4-d40a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=ed1c6a67-674f-4b14-ac3e-b0e1f9cf7164 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
#UUID=4486e6e8-046a-46e1-aa91-d7c4d9ebca73 none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0

=================== sda5: Location of files loaded by Grub: ===================


 168.7GB: boot/grub/grub.cfg
 169.6GB: boot/grub/stage2
 169.7GB: boot/initrd.img-2.6.32-21-generic
 169.8GB: boot/initrd.img-2.6.32-22-generic
 170.0GB: boot/initrd.img-2.6.32-23-generic
  75.0GB: boot/initrd.img-2.6.32-24-generic
 168.4GB: boot/initrd.img-2.6.32-25-generic
  72.9GB: boot/initrd.img-2.6.32-27-generic
  97.4GB: boot/initrd.img-2.6.32-28-generic
 169.6GB: boot/vmlinuz-2.6.32-21-generic
 169.6GB: boot/vmlinuz-2.6.32-22-generic
 169.9GB: boot/vmlinuz-2.6.32-23-generic
 169.9GB: boot/vmlinuz-2.6.32-24-generic
 170.0GB: boot/vmlinuz-2.6.32-25-generic
 170.0GB: boot/vmlinuz-2.6.32-27-generic
 171.7GB: boot/vmlinuz-2.6.32-28-generic
  97.4GB: initrd.img
  72.9GB: initrd.img.old
 171.7GB: vmlinuz
 170.0GB: vmlinuz.old

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=04b40181-c355-4cff-ad6a-86e3d4730160 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4486e6e8-046a-46e1-aa91-d7c4d9ebca73 none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 210.2GB: boot/initrd.img-2.6.32-21-generic
 210.2GB: boot/vmlinuz-2.6.32-21-generic
 210.2GB: initrd.img
 210.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  54 ad 43 79 45 9a 75 be  31 c1 a1 17 57 f4 93 06  |T.CyE.u.1...W...|
00000010  fd a4 a2 4b 3e 3a bd 17  57 f4 93 06 5d a7 2f 57  |...K>:..W...]./W|
00000020  b2 8a 84 11 57 f4 37 0d  fa 9b 8a 9e a9 f5 d3 7b  |....W.7........{|
00000030  71 45 7f d3 a0 bf 99 28  81 da 4a 71 a5 28 42 58  |qE.....(..Jq.(BX|
00000040  8c d0 41 58 06 ac 1b b0  62 84 65 a2 04 f1 52 fc  |..AX....b.e...R.|
00000050  65 58 26 7a 61 8e d1 5b  f4 40 aa ee a2 27 c2 1e  |eX&za..[.@...'..|
00000060  08 fb 20 d6 13 94 12 9c  ed 83 b3 bd 29 2c 11 7d  |.. .........),.}|
00000070  71 ae 1f 52 f4 c7 d9 22  60 fd 81 f5 a3 b0 48 0c  |q..R..."`.....H.|
00000080  c2 6c a5 4c 0c c4 7f 00  d2 0f 40 fa 81 c0 07 21  |.l.L......@....!|
00000090  e7 20 31 4c 0c 16 c3 c5  10 31 42 0c 15 23 c5 19  |. 1L.....1B..#..|
000000a0  80 83 81 0d 46 6c 08 61  23 90 62 38 8e 91 80 23  |....Fl.a#.b8...#|
000000b0  81 95 8b 33 c5 58 31 4a  8c 46 38 06 e1 28 84 c3  |...3.X1J.F8..(..|
000000c0  81 0d 01 36 06 e1 70 a4  18 82 14 63 11 4e 14 e3  |...6..p....c.N..|
000000d0  c4 24 31 5e 4c 16 13 00  c7 00 1b 83 d8 38 c2 26  |.$1^L........8.&|
000000e0  21 ed 44 1c 93 01 27 03  9b 26 a6 88 e9 62 2a 4a  |!.D...'..&...b*J|
000000f0  9a 82 d2 a7 e2 3f 05 67  86 21 f5 60 84 d3 10 4e  |.....?.g.!.`...N|
00000100  c7 7f 1a e8 33 70 a6 02  d4 19 38 5b 81 ff 0c 48  |....3p....8[...H|
00000110  55 01 49 67 88 59 62 26  fe c3 71 8c 44 7c 08 8e  |U.Ig.Yb&..q.D|..|
00000120  33 70 8c 05 5e 0e 39 5d  48 5a 09 09 5c 94 5a 89  |3p..^.9]HZ..\.Z.|
00000130  bf 8b 52 2b 21 89 2b aa  44 04 ff 89 38 26 23 3e  |..R+!.+.D...8&#>|
00000140  0e c7 04 1c d3 81 4f 13  35 22 2a e2 a2 1a 67 a3  |......O.5"*...g.|
00000150  22 86 b0 1a e1 6c c4 62  24 7d 0d e2 71 fc 65 38  |"....l.b$}..q.e8|
00000160  5a 9c 85 73 67 23 c5 1c  9c 1d 06 6c 0e b0 b3 29  |Z..sg#.....l...)|
00000170  1c 26 e6 22 45 2d d2 25  90 ba 16 32 26 40 99 4b  |.&."E-.%...2&@.K|
00000180  61 ad 38 07 4e b2 50 cc  13 f3 11 2e 40 38 0f e1  |a.8.N.P.....@8..|
00000190  22 60 8b 81 2d 40 b8 08  29 16 23 c5 42 0a 17 89  |"`..-@..).#.B...|
000001a0  25 c8 77 2e ea 77 1e 62  4b 11 3b 17 e1 79 28 63  |%.w..w.bK.;..y(c|
000001b0  29 b4 b2 14 b1 e5 e2 7c  b1 42 5c 20 56 8a 00 fe  |)......|.B\ V...|
000001c0  ff ff 83 fe ff ff 02 78  bf 04 58 47 f8 0d 00 fe  |.......x..XG....|
000001d0  ff ff 05 fe ff ff 5a bf  b7 12 a8 08 13 05 00 00  |......Z.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda4

00000000  55 aa 03 e9 7a 00 93 00  00 00 00 00 00 00 00 00  |U...z...........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  ff ff 00 00 00 9b cf 00  |................|
00000030  ff ff 00 00 00 93 cf 00  ff ff 00 00 00 9a 0f 00  |................|
00000040  ff ff 00 00 00 92 0f 00  27 00 20 00 00 00 00 00  |........'. .....|
00000050  ff ff 00 00 00 00 00 00  10 00 44 65 76 69 63 65  |..........Device|
00000060  56 4d 20 52 6f 6d 20 4c  6f 61 64 65 72 00 00 00  |VM Rom Loader...|
00000070  01 31 31 2f 32 32 2f 32  30 30 37 00 00 00 00 00  |.11/22/2007.....|
00000080  0e 58 2e a3 42 02 68 00  00 1f 68 00 00 07 57 2e  |.X..B.h...h...W.|
00000090  8d 3e 00 06 2e 80 7d 20  03 75 17 9c 60 b8 03 00  |.>....} .u..`...|
000000a0  cd 10 61 9d 2e 8d 3e 8c  03 e8 fd 02 b4 00 50 cd  |..a...>.......P.|
000000b0  16 58 5f b8 03 00 c1 e0  09 89 c3 0e 07 26 66 8b  |.X_..........&f.|
000000c0  47 0c 66 85 c0 74 05 2e  66 a3 56 00 fa 66 31 c0  |G.f..t..f.V..f1.|
000000d0  8c c8 66 c1 e0 04 2e 66  01 06 4a 00 fb 2e 66 a3  |..f....f..J...f.|
000000e0  3a 00 b0 9a 2e a2 3d 00  66 50 e8 25 03 66 58 66  |:.....=.fP.%.fXf|
000000f0  50 66 51 1e c8 0c 00 00  0e 1f 66 31 c0 3e a1 06  |PfQ.......f1.>..|
00000100  00 66 c1 e0 09 66 2d 03  00 00 00 66 50 2e 66 a1  |.f...f-....fP.f.|
00000110  56 00 66 50 66 31 c0 66  31 c9 b9 00 06 8c c8 66  |V.fPf1.f1......f|
00000120  c1 e0 04 66 01 c8 66 50  e8 cb 01 c9 1f 66 59 66  |...f..fP.....fYf|
00000130  58 fa 2e 0f 01 16 48 00  0f 20 c0 0c 01 0f 22 c0  |X.....H.. ....".|
00000140  2e 66 8b 36 56 00 66 67  66 67 8b 06 66 3d eb 3e  |.f.6V.fgfg..f=.>|
00000150  45 54 74 14 0f 20 c0 24  fe 0f 22 c0 57 2e 8d 3e  |ETt.. .$..".W..>|
00000160  5a 03 e8 44 02 5f cd 18  0f 20 c0 24 fe 0f 22 c0  |Z..D._... .$..".|
00000170  06 53 8c cb 8e c3 bb 00  06 e8 e0 00 5b 07 c8 0c  |.S..........[...|
00000180  00 00 66 b8 00 02 00 00  66 50 2e 66 a1 56 00 66  |..f.....fP.f.V.f|
00000190  50 66 31 c0 66 31 c9 b9  00 06 8c c8 66 c1 e0 04  |Pf1.f1......f...|
000001a0  66 01 c8 66 50 e8 4e 01  c9 2e 66 8b 36 56 00 66  |f..fP.N...f.6V.f|
000001b0  89 e0 66 50 16 66 29 db  bb 48 00 66 29 c9 8c c9  |..fP.f)..H.f)...|
000001c0  66 c1 e1 04 66 01 d9 66  51 66 29 c0 66 29 c9 b8  |f...f..fQf).f)..|
000001d0  08 00 66 50 b8 14 02 8c  c9 66 c1 e1 04 66 01 c1  |..fP.....f...f..|
000001e0  66 51 66 29 c0 89 e0 66  29 c9 8c d1 66 c1 e1 04  |fQf)...f)...f...|
000001f0  66 01 c1 fa 2e 0f 01 16  48 00 0f 20 c0 0c 01 0f  |f.......H.. ....|
00000200

---

### Post by kiyop on 2011-04-18
grub2 was formerly installed, but you might have been installed grub legacy to MBR.
So, now, you dropped into Grub legacy command line perhaps.
And you have 2 ubuntu installed in /dev/sda5 and /dev/sda6, don't you?

At "grub>" prompt, 
```
grub> root (hd0,4)
grub> kernel /boot/vmlinuz-2.6.32-28-generic root=/dev/sda5 ro acpi_osi=Linux
grub> initrd /boot/initrd.img-2.6.32-28-generic
grub> boot
```If Ubuntu 10.04.2 on /dev/sda5 boots well, execute in terminal:
```
sudo apt-get update
sudo apt-get install --reinstall grub-pc
sudo grub-mkdevicemap
sudo grub-install /dev/sda
sudo update-grub
```

---

### Post by Quiver on 2011-04-19
> If Ubuntu 10.04.2 on /dev/sda5 boots well, execute in terminal:
Code:

sudo apt-get update
sudo apt-get install --reinstall grub-pc
sudo grub-mkdevicemap
sudo grub-install /dev/sda
sudo update-grub





I have a problem when I try the second command. I am asked if I want to install grub2 on sda, my hard drive, or on sdb, my jump drive. I choose sda and doesn't work.

```
ubuntu@ubuntu:~$ sudo apt-get install --reinstall grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 354 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up grub-pc (1.98+20100804-5ubuntu3) ...
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

[1]+  Stopped                 sudo apt-get install --reinstall grub-pc



```

When I try to mount /dev I am told that it is not a block device.

---

### Post by Quiver on 2011-04-19
> grub2 was formerly installed, but you might have been installed grub legacy to MBR.
So, now, you dropped into Grub legacy command line perhaps.
And you have 2 ubuntu installed in /dev/sda5 and /dev/sda6, don't you?

  Yeah, I thought that I had grub legacy, so when I had trouble I tried to reinstall grub.  Later, I also tried installing Lilo.

   And yes, I was trying out ubuntu 10.10 and installed it on /dev/sda6

---

### Post by wilee-nilee on 2011-04-19
I'm reposting the script in its easier to read format here as well.
```
RESULTS.txt from the boot_info_script:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    58,521,147    58,519,100   7 HPFS/NTFS
/dev/sda2          58,521,598   467,382,271   408,860,674   5 Extended
/dev/sda5         138,178,560   372,553,559   234,375,000  83 Linux
/dev/sda6         372,553,728   457,687,039    85,133,312  83 Linux
/dev/sda7         457,689,088   461,418,495     3,729,408  82 Linux swap / Solaris
/dev/sda8         461,428,736   467,382,271     5,953,536  82 Linux swap / Solaris
/dev/sda3         467,382,272   488,353,791    20,971,520   b W95 FAT32
/dev/sda4         488,353,792   488,392,064        38,273  1b Hidden W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,935,999     7,935,938   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b64a7490-0fd4-45cb-a3d2-bb1a7cadef07   ext3                                     
/dev/sda1        029EAFED9EAFD785                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        86F4-D40A                              vfat                                     
/dev/sda5        3dcba3f5-ba88-4bef-af18-90d365f363fa   ext4       majstudio                     
/dev/sda6        04b40181-c355-4cff-ad6a-86e3d4730160   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4F97-85EE                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /win                     ext4       (rw)
/dev/sda5        /lin                     ext4       (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro   quiet acpi_osi=Linux
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3dcba3f5-ba88-4bef-af18-90d365f363fa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod fat
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 86f4-d40a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3dcba3f5-ba88-4bef-af18-90d365f363fa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=ed1c6a67-674f-4b14-ac3e-b0e1f9cf7164 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
#UUID=4486e6e8-046a-46e1-aa91-d7c4d9ebca73 none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0

=================== sda5: Location of files loaded by Grub: ===================


 168.7GB: boot/grub/grub.cfg
 169.6GB: boot/grub/stage2
 169.7GB: boot/initrd.img-2.6.32-21-generic
 169.8GB: boot/initrd.img-2.6.32-22-generic
 170.0GB: boot/initrd.img-2.6.32-23-generic
  75.0GB: boot/initrd.img-2.6.32-24-generic
 168.4GB: boot/initrd.img-2.6.32-25-generic
  72.9GB: boot/initrd.img-2.6.32-27-generic
  97.4GB: boot/initrd.img-2.6.32-28-generic
 169.6GB: boot/vmlinuz-2.6.32-21-generic
 169.6GB: boot/vmlinuz-2.6.32-22-generic
 169.9GB: boot/vmlinuz-2.6.32-23-generic
 169.9GB: boot/vmlinuz-2.6.32-24-generic
 170.0GB: boot/vmlinuz-2.6.32-25-generic
 170.0GB: boot/vmlinuz-2.6.32-27-generic
 171.7GB: boot/vmlinuz-2.6.32-28-generic
  97.4GB: initrd.img
  72.9GB: initrd.img.old
 171.7GB: vmlinuz
 170.0GB: vmlinuz.old

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=04b40181-c355-4cff-ad6a-86e3d4730160 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4486e6e8-046a-46e1-aa91-d7c4d9ebca73 none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 210.2GB: boot/initrd.img-2.6.32-21-generic
 210.2GB: boot/vmlinuz-2.6.32-21-generic
 210.2GB: initrd.img
 210.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  54 ad 43 79 45 9a 75 be  31 c1 a1 17 57 f4 93 06  |T.CyE.u.1...W...|
00000010  fd a4 a2 4b 3e 3a bd 17  57 f4 93 06 5d a7 2f 57  |...K>:..W...]./W|
00000020  b2 8a 84 11 57 f4 37 0d  fa 9b 8a 9e a9 f5 d3 7b  |....W.7........{|
00000030  71 45 7f d3 a0 bf 99 28  81 da 4a 71 a5 28 42 58  |qE.....(..Jq.(BX|
00000040  8c d0 41 58 06 ac 1b b0  62 84 65 a2 04 f1 52 fc  |..AX....b.e...R.|
00000050  65 58 26 7a 61 8e d1 5b  f4 40 aa ee a2 27 c2 1e  |eX&za..[.@...'..|
00000060  08 fb 20 d6 13 94 12 9c  ed 83 b3 bd 29 2c 11 7d  |.. .........),.}|
00000070  71 ae 1f 52 f4 c7 d9 22  60 fd 81 f5 a3 b0 48 0c  |q..R..."`.....H.|
00000080  c2 6c a5 4c 0c c4 7f 00  d2 0f 40 fa 81 c0 07 21  |.l.L......@....!|
00000090  e7 20 31 4c 0c 16 c3 c5  10 31 42 0c 15 23 c5 19  |. 1L.....1B..#..|
000000a0  80 83 81 0d 46 6c 08 61  23 90 62 38 8e 91 80 23  |....Fl.a#.b8...#|
000000b0  81 95 8b 33 c5 58 31 4a  8c 46 38 06 e1 28 84 c3  |...3.X1J.F8..(..|
000000c0  81 0d 01 36 06 e1 70 a4  18 82 14 63 11 4e 14 e3  |...6..p....c.N..|
000000d0  c4 24 31 5e 4c 16 13 00  c7 00 1b 83 d8 38 c2 26  |.$1^L........8.&|
000000e0  21 ed 44 1c 93 01 27 03  9b 26 a6 88 e9 62 2a 4a  |!.D...'..&...b*J|
000000f0  9a 82 d2 a7 e2 3f 05 67  86 21 f5 60 84 d3 10 4e  |.....?.g.!.`...N|
00000100  c7 7f 1a e8 33 70 a6 02  d4 19 38 5b 81 ff 0c 48  |....3p....8[...H|
00000110  55 01 49 67 88 59 62 26  fe c3 71 8c 44 7c 08 8e  |U.Ig.Yb&..q.D|..|
00000120  33 70 8c 05 5e 0e 39 5d  48 5a 09 09 5c 94 5a 89  |3p..^.9]HZ..\.Z.|
00000130  bf 8b 52 2b 21 89 2b aa  44 04 ff 89 38 26 23 3e  |..R+!.+.D...8&#>|
00000140  0e c7 04 1c d3 81 4f 13  35 22 2a e2 a2 1a 67 a3  |......O.5"*...g.|
00000150  22 86 b0 1a e1 6c c4 62  24 7d 0d e2 71 fc 65 38  |"....l.b$}..q.e8|
00000160  5a 9c 85 73 67 23 c5 1c  9c 1d 06 6c 0e b0 b3 29  |Z..sg#.....l...)|
00000170  1c 26 e6 22 45 2d d2 25  90 ba 16 32 26 40 99 4b  |.&."E-.%...2&@.K|
00000180  61 ad 38 07 4e b2 50 cc  13 f3 11 2e 40 38 0f e1  |a.8.N.P.....@8..|
00000190  22 60 8b 81 2d 40 b8 08  29 16 23 c5 42 0a 17 89  |"`..-@..).#.B...|
000001a0  25 c8 77 2e ea 77 1e 62  4b 11 3b 17 e1 79 28 63  |%.w..w.bK.;..y(c|
000001b0  29 b4 b2 14 b1 e5 e2 7c  b1 42 5c 20 56 8a 00 fe  |)......|.B\ V...|
000001c0  ff ff 83 fe ff ff 02 78  bf 04 58 47 f8 0d 00 fe  |.......x..XG....|
000001d0  ff ff 05 fe ff ff 5a bf  b7 12 a8 08 13 05 00 00  |......Z.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda4

00000000  55 aa 03 e9 7a 00 93 00  00 00 00 00 00 00 00 00  |U...z...........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  ff ff 00 00 00 9b cf 00  |................|
00000030  ff ff 00 00 00 93 cf 00  ff ff 00 00 00 9a 0f 00  |................|
00000040  ff ff 00 00 00 92 0f 00  27 00 20 00 00 00 00 00  |........'. .....|
00000050  ff ff 00 00 00 00 00 00  10 00 44 65 76 69 63 65  |..........Device|
00000060  56 4d 20 52 6f 6d 20 4c  6f 61 64 65 72 00 00 00  |VM Rom Loader...|
00000070  01 31 31 2f 32 32 2f 32  30 30 37 00 00 00 00 00  |.11/22/2007.....|
00000080  0e 58 2e a3 42 02 68 00  00 1f 68 00 00 07 57 2e  |.X..B.h...h...W.|
00000090  8d 3e 00 06 2e 80 7d 20  03 75 17 9c 60 b8 03 00  |.>....} .u..`...|
000000a0  cd 10 61 9d 2e 8d 3e 8c  03 e8 fd 02 b4 00 50 cd  |..a...>.......P.|
000000b0  16 58 5f b8 03 00 c1 e0  09 89 c3 0e 07 26 66 8b  |.X_..........&f.|
000000c0  47 0c 66 85 c0 74 05 2e  66 a3 56 00 fa 66 31 c0  |G.f..t..f.V..f1.|
000000d0  8c c8 66 c1 e0 04 2e 66  01 06 4a 00 fb 2e 66 a3  |..f....f..J...f.|
000000e0  3a 00 b0 9a 2e a2 3d 00  66 50 e8 25 03 66 58 66  |:.....=.fP.%.fXf|
000000f0  50 66 51 1e c8 0c 00 00  0e 1f 66 31 c0 3e a1 06  |PfQ.......f1.>..|
00000100  00 66 c1 e0 09 66 2d 03  00 00 00 66 50 2e 66 a1  |.f...f-....fP.f.|
00000110  56 00 66 50 66 31 c0 66  31 c9 b9 00 06 8c c8 66  |V.fPf1.f1......f|
00000120  c1 e0 04 66 01 c8 66 50  e8 cb 01 c9 1f 66 59 66  |...f..fP.....fYf|
00000130  58 fa 2e 0f 01 16 48 00  0f 20 c0 0c 01 0f 22 c0  |X.....H.. ....".|
00000140  2e 66 8b 36 56 00 66 67  66 67 8b 06 66 3d eb 3e  |.f.6V.fgfg..f=.>|
00000150  45 54 74 14 0f 20 c0 24  fe 0f 22 c0 57 2e 8d 3e  |ETt.. .$..".W..>|
00000160  5a 03 e8 44 02 5f cd 18  0f 20 c0 24 fe 0f 22 c0  |Z..D._... .$..".|
00000170  06 53 8c cb 8e c3 bb 00  06 e8 e0 00 5b 07 c8 0c  |.S..........[...|
00000180  00 00 66 b8 00 02 00 00  66 50 2e 66 a1 56 00 66  |..f.....fP.f.V.f|
00000190  50 66 31 c0 66 31 c9 b9  00 06 8c c8 66 c1 e0 04  |Pf1.f1......f...|
000001a0  66 01 c8 66 50 e8 4e 01  c9 2e 66 8b 36 56 00 66  |f..fP.N...f.6V.f|
000001b0  89 e0 66 50 16 66 29 db  bb 48 00 66 29 c9 8c c9  |..fP.f)..H.f)...|
000001c0  66 c1 e1 04 66 01 d9 66  51 66 29 c0 66 29 c9 b8  |f...f..fQf).f)..|
000001d0  08 00 66 50 b8 14 02 8c  c9 66 c1 e1 04 66 01 c1  |..fP.....f...f..|
000001e0  66 51 66 29 c0 89 e0 66  29 c9 8c d1 66 c1 e1 04  |fQf)...f)...f...|
000001f0  66 01 c1 fa 2e 0f 01 16  48 00 0f 20 c0 0c 01 0f  |f.......H.. ....|
00000200[/QUOTE]


```

I would download supergrub2 or one of the supergrub discs use it to boot to the sda5 partition once there in the terminal run these commands.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

```
sudo apt-get purge grub grub-pc grub-common
```
the reinstall grub2 with
```
sudo apt-get install grub-pc grub-common
```
choose the mbr=sda for where grub2 is put then run at the end.
```
sudo update-grub
```

Or from a live Ubuntu cd equal to the sda5 install lucid, and follow this link.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)```

```

---

### Post by Quiver on 2011-04-19
Whoops, I didn't read kiyop's post correctly and tried reinstalling grub before booting sda5. #-o

Once I followed the directions completely... it worked!!  :D

Thank you, thank you, thank you!!

Grub still doesn't list my other ubuntu partition, or my windows partition.
Might supergrub2 fix this?

---

### Post by wilee-nilee on 2011-04-19
> **Quiver said:**
> Whoops, I didn't read kiyop's post correctly and tried reinstalling grub before booting sda5. #-o

Once I followed the directions completely... it worked!!  :D

Thank you, thank you, thank you!!

Grub still doesn't list my other ubuntu partition, or my windows partition.
Might supergrub2 fix this?

I knew kiyop's original post should work basically, have you run in the installs terminal, 
sudo update-grub

You might identify exactly what is supposed to be on the HD, there are missing files that would normally show for a windows install for example a Vista or W7 install would look like this, the highlighted.
sd??: __________________________________________________ ________
File system: ntfs
Boot sector type: Windows Vista
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: [B]Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe[/B]

It never hurts to run the script again as well put it in code tags, to look like my repost, if you do by clicking on the **(#)** in the opened reply panel and paste all the text between.

---

### Post by kiyop on 2011-04-20
[color=gray]> **Quiver said:**
> Grub still doesn't list my other ubuntu partition, or my windows partition.
Might supergrub2 fix this?
Other OS'es in other partition is searched and added in /boot/grub/grub.cfg by the script os-prober called by /etc/grub.d/30_os-prober in Grub2.
30_os-prober cannot work if /etc/default/grub contains a line:
"GRUB_DISABLE_OS_PROBER=true"
(if not commented out -- i.e. without preceding "#")
and/or if /etc/grub.d/30_os-prober does not have executable permission (x).

Please check by
```
grep GRUB_DISABLE_OS_PROBER /etc/default/grub
```and
```
ls -la /etc/grub.d/30_os-prober
```[/color]

Edit:
Neglect the above.
Excuse me.
I was not noticed that the result of boot info script has:
> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod fat
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 86f4-d40a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###


30_os-prober definitely worked and wilee-nilee's advice is better.

---

