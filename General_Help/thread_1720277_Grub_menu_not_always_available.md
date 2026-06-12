---
title: "Grub menu not always available"
date: 2011-04-03
forum: General Help
---

### Post by jecook on 2011-04-03
I have just installed Ubuntu 10.10 Netbook Remix on my Win XP Acer Aspire 1. I created the Ubuntu Partition by resizing the C & D partitions and installed Ubuntu from a live USB Drive version.

When the computer starts up it does not always go to the GRUB menu.

If I have been running XP it tends to skip the GRUB menu unless I press the shift key, if i have done the shutdown from Ubuntu it will usually reboot to the GRUB menu. Is there a way to make the computer boot to the GRUB Menu everytime?

I have also noticed that when my external hard drive is not connected I cannot get the GRUB Menu even when I press the shift key when starting the PC. I don't understand why this is as both OSs are installed on partitions of the internal drive.

I have searched the forums for assistance but although I am sure that there have been lots of posts about installing GRUB I cannot come up with a search term that leads to a post that fits my problem and that explains the solution to someone used to windows terminology.

As a beginner with LINUX I would appreciate simple step by step instructions if someone can help with my GRUB problem as I would like to persevere and try to get to know LINUX well.

Jon

---

### Post by Hedgehog1 on 2011-04-03
We need to get a look at your partitions and see where you have placed your grub. Please be sure your external hard drive is attached (as I believe this is where you have installed it).

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

*p.s. The reason you do not see the grub menu sometimes is when the external drive is not attached, your PC is finding the next available drive and that happens to be the XP install with the non-grub MBR*.

---

### Post by jecook on 2011-04-03
Thanks for your help, you may be right looking at the attached results file, but I have no idea how to safely move the Grub loader to the correct disk.

I also note that I cannot see all the partitions on my external drive where there are 5 x 100Gb partitions, when I am in LInux I cannot mount the APOLLO Reports 1 and cannot see the Music partition. All the partitions on the external drive are NTFS as I normally use this disk with Win XP.

Jon

---

### Post by Quackers on 2011-04-03
Your boot script output in code tags, so others can see it :wink:
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

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
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1               2,048    16,779,263    16,777,216  12 Compaq diagnostics
/dev/sda2    *     16,779,264   148,344,209   131,564,946   7 HPFS/NTFS
/dev/sda3         148,344,210   271,434,239   123,090,030   7 HPFS/NTFS
/dev/sda4         271,437,822   312,580,095    41,142,274   5 Extended
/dev/sda5         271,437,824   308,387,839    36,950,016  83 Linux
/dev/sda6         308,389,888   312,580,095     4,190,208  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   195,639,569   195,639,507   7 HPFS/NTFS
/dev/sdb2         195,639,570   976,768,064   781,128,495   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sdb5         195,639,633   390,925,709   195,286,077   7 HPFS/NTFS
/dev/sdb6         390,925,773   586,211,849   195,286,077   7 HPFS/NTFS
/dev/sdb7         586,211,913   781,497,989   195,286,077   7 HPFS/NTFS
/dev/sdb8         781,498,053   976,768,064   195,270,012   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064    15,646,719    15,638,656   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       6d49a347-dcea-3e4e-9117-79dd55f75b10   ext2       casper-rw                     
/dev/sda1        D8444E9A444E7B70                       ntfs       PQSERVICE                     
/dev/sda2        A47AC1277AC0F758                       ntfs       ACER                          
/dev/sda3        01CBE628E0814680                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3d1fbb19-1047-436e-9376-bba4c94a25f5   ext4       Ubuntu                        
/dev/sda6        2e6459fd-75d2-4fd2-9bcf-3ab4e9001715   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1C5C6AFB5C6ACF58                       ntfs       APOLLO                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        4A22AB1422AB0453                       ntfs       APOLLO Music                  
/dev/sdb6        587CD2527CD22A90                       ntfs       APOLLO Reports 1              
/dev/sdb7        7AF6DC35F6DBEEFF                       ntfs       APOLLO Reports 2              
/dev/sdb8        30DE0128DE00E7C4                       ntfs       APOLLO Backups                
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        C5FC-6D44                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=3d1fbb19-1047-436e-9376-bba4c94a25f5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=3d1fbb19-1047-436e-9376-bba4c94a25f5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3d1fbb19-1047-436e-9376-bba4c94a25f5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3d1fbb19-1047-436e-9376-bba4c94a25f5 ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3d1fbb19-1047-436e-9376-bba4c94a25f5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d8444e9a444e7b70
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set a47ac1277ac0f758
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=3d1fbb19-1047-436e-9376-bba4c94a25f5 /               ext4    errors=remount-ro 0       1
/dev/sdb6       none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 145.5GB: boot/grub/core.img
 143.5GB: boot/grub/grub.cfg
 139.9GB: boot/initrd.img-2.6.35-22-generic
 140.0GB: boot/initrd.img-2.6.35-28-generic
 145.6GB: boot/vmlinuz-2.6.35-22-generic
 145.6GB: boot/vmlinuz-2.6.35-28-generic
 140.0GB: initrd.img
 139.9GB: initrd.img.old
 145.6GB: vmlinuz
 145.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 33 02 00 fe  |............3...|
000001d0  ff ff 05 fe ff ff 02 d0  33 02 00 f8 3f 00 00 00  |........3...?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 50 11  |.X.SYSLINUX..@P.|
00000010  02 00 00 00 00 f8 00 00  3f 00 80 00 80 1f 00 00  |........?.......|
00000020  80 a0 ee 00 78 07 00 00  00 00 00 00 02 00 00 00  |....x...........|
00000030  01 00 08 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 44 6d fc c5 20  20 20 20 20 20 20 20 20  |..)Dm..         |
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
00000110  c6 06 45 7d 00 66 b8 80  20 00 00 66 ba 00 00 00  |..E}.f.. ..f....|
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


```

Which hard drive is set to boot first in your bios please?
Are both sda and sdb internal drives?
You also appear to have a partition problem with sdb
```
Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   195,639,569   195,639,507   7 HPFS/NTFS
/dev/sdb2         195,639,570   976,768,064   781,128,495   f W95 Ext d (LBA)
[COLOR="Red"]Extended  partition  linking to another extended partition[/COLOR]
/dev/sdb5         195,639,633   390,925,709   195,286,077   7 HPFS/NTFS
/dev/sdb6         390,925,773   586,211,849   195,286,077   7 HPFS/NTFS
/dev/sdb7         586,211,913   781,497,989   195,286,077   7 HPFS/NTFS
/dev/sdb8         781,498,053   976,768,064   195,270,012   7 HPFS/NTFS

```

---

### Post by oldfred on 2011-04-03
Because you have grub's bootloader in the MBR of the external that is why you can only boot grub with the external plugged in.

You have a Acer boot loader in the MBR of the internal. I am not familiar with Acer, but it has to be a modified windows boot loader. Do you have any special functions on booting, maybe f keys? If so then installing grub may loose that special function.

I would backup MBR just in case that there is something special

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement")
Backup the MBR e.g. 
dd if=/dev/sda of=/acermbr.bin bs=446 count=1

Note that dd is a low level command that reads and writes directly to drive. Copy command exactly - best to copy & paste. 

I would also backup sda & sdb's partition tables:
sfdisk -d /dev/sda > sdaparts.txt
sfdisk -d /dev/sdb > sdbparts.txt

Fixparts - Repair broken partition tables
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
I think this program will fix your partition table error.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by techunit on 2011-04-03
It appears that when you installed Ubuntu it installed grub to the MBR of the external drive. You can either reinstall grub.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Subject number 13.

OR you can reinstall Ubuntu and in the installation process ensure you click manual partitioning and install over your old Ubuntu partition. In this step you will be given the opertunity to choose where to install grub.
it will likely be somthing like sda, however if I remember correctly it will tell you which you should use.

Hope this helps.

---

### Post by Hedgehog1 on 2011-04-03
> **jecook said:**
> Thanks for your help, you may be right looking at the attached results file, but I have no idea how to safely move the Grub loader to the correct disk.


Let's start by getting your PC to boot both OSs from the internal drive, and next we will turn off the boot flag on the external hard drive.

Please boot off the LiveCD/Live USB, select TRY, and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run these commands:

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Grub  dual boot menu is now installed on your internal drive.

Next, we want to get your external hard drive to stop being a boot drive.

To do this, we need to run gparted (**G**nome **PART**ion **ED**itor).  You will find it in the System >> Administration >> Gparted Partition Editor.

Select the 'sdb' device in the upper right hand corner, higlight the first partition, then right click for a menu:

[IMG]http://img855.imageshack.us/img855/6408/bootflaggparted.png[/IMG]

Select the 'Manage Flags', and then un-check the 'boot' flag.

You may have to unmount the partition for this operation; I am not sure.

Once these steps are both done, this will solve the booting issue.

***The Hedge***

:KS

p.s. The partitions that are not showing is a separate issue that I don't know how to solve off hand.  Hopefully other forum member sill now how to solve this.

---

### Post by techunit on 2011-04-03
I suppose that should work as well. best of luck getting your netbook running nice and cleanly. Because its a netbook I question why you don't just use Ubuntu though.

---

### Post by jecook on 2011-04-04
Thanks for all the replies, I will have to work my way through them all, and then reply Hedgehog1's suggestion to get both OS's booting from the internal drive sounds like the place to start but I need to read all these posts and digest them first. 

Thanks to Quackers for posting the entire text of the result file, I was not sure if that was what I was expected to do.

Quick answer to tech unit is that it came with XP, I use it for work with a lot of Windows based software - at 1.3kg the netbook beats humping a 3kg HP laptop, in and out of the office every day. However I decided it was about time to seriously checkout LINUX so I have the dual boot while I learn the ropes.

Jon

---

### Post by srs5694 on 2011-04-04
> **Quackers said:**
> You also appear to have a partition problem with sdb
```
Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   195,639,569   195,639,507   7 HPFS/NTFS
/dev/sdb2         195,639,570   976,768,064   781,128,495   f W95 Ext d (LBA)
[COLOR=Red]Extended  partition  linking to another extended partition[/COLOR]
/dev/sdb5         195,639,633   390,925,709   195,286,077   7 HPFS/NTFS
/dev/sdb6         390,925,773   586,211,849   195,286,077   7 HPFS/NTFS
/dev/sdb7         586,211,913   781,497,989   195,286,077   7 HPFS/NTFS
/dev/sdb8         781,498,053   976,768,064   195,270,012   7 HPFS/NTFS

```

[quote=oldfred]Fixparts - Repair broken partition tables
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
I think this program will fix your partition table error.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)[/quote]

I recommend trying the suggestions about (re-)installing GRUB before doing anything with FixParts. If adjusting GRUB fixes the problem, don't use FixParts. The reason is that I'm not sure the "extended partition linking to another extended partition" message is really an error message. I *think* I know what this message means, but I've not investigated it in any detail. If I'm right, it refers to an unusual way of writing logical partition data, but it appears that most utilities and OSes can handle it, so the saying "if it ain't broke, don't fix it" applies. If I'm right about all of this, FixParts *would* eliminate that message, but it wouldn't have any other beneficial effects, and there's always a chance that FixParts would mess up something else. Note that I'm not trying to bad-mouth FixParts -- I wrote it! -- but partition tables can be sensitive things, so you shouldn't mess with them unless it's necessary.

---

### Post by jecook on 2011-04-04
So far so good, followed Hedghog1's advice and that seems to have fixed the issue of the Grub Boot Menu.
The boot order was the thumb drive(sdc), then the ext usb drive (sdb) and then the internal drive (sda) of course with the Ext USB drive connected it would find the Grub Loader but when removed there was only the original Windows XP boot. Booting, at least, is fixed.

In the process of correcting the boot loader I seem to have recovered at least one of the missing partitions as I can now see 4 of the 5 partitions on the Ext USB. The one partition I cannot see is sdb6 (Reports 1) which will not mount and comes up with the following message:

> Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, none is already mounted on none
mount failedI can at least see my Music again which is in the sdb5 partition but if anyone has any ideas about the sdb6 partition I would be pleased to hear them (Do I need to start another thread for that?) but for the moment I think that I will follow the advice of srs5694 and save the use of FixParts until I'm sure I need to. Maybe now that I have fixed the MBR I only need to reboot from the internal drive without the external USB disk, and then re-connect the ext drive and let LINUX find the partitions again.

Will try that later.

Many thanks for all the assistance,
Jon

---

### Post by Hedgehog1 on 2011-04-04
> **jecook said:**
> So far so good, ***followed Hedghog1's advice and that seems to have fixed the issue of the Grub Boot Menu.***...Booting, at least, is fixed...

Jon,

I am pleased I did not lead you (completely) astray.  My goal is to do no harm (It's a hedgehog creed thing, you know).

One down...  A few to go...

***The Hedge***

:KS

---

### Post by jecook on 2011-04-04
So now to the next - but I think a new thread is best

Thanks

---

