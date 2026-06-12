---
title: "Dual boot Vista/Ubuntu worked but now grub rescue&gt;"
date: 2010-09-03
forum: General Help
---

### Post by dooper on 2010-09-03
Hi all...

I have a Toshiba A210-12U lappy which has dual core AMD turion 64 processor.

It is running windows Vista.

A couple of weeks ago i installed the latest Ubuntu 10. ? LTS as a duel boot with the grub loader and it worked fine and all was well.

I could choose at bootup and both systems worked fine.

Today i rebooted my lappy and got..

error-unknown filesystem
grub rescue>

I am now running on Ubuntu via a USB pendrive.

I dont have any rescue CD for my vista as the OS was preloaded into a rescue/restart type hidden partition on my HD as from new.

I'd like to get back to my dual boot working system if poss...

What can i do ?

Thanks

Jo


EDIT
I've downloaded and run the boot info script as suggested elsewhere and the output is as follows...


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

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

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   175,783,229   172,709,182   7 HPFS/NTFS
/dev/sda3         175,783,230   197,723,443    21,940,214   7 HPFS/NTFS
/dev/sda4         197,724,159   234,436,544    36,712,386   f W95 Ext d (LBA)
/dev/sda5         197,724,160   217,579,519    19,855,360  83 Linux
/dev/sda6         217,581,568   218,562,559       980,992  82 Linux swap / Solaris
/dev/sda7         218,564,388   230,870,114    12,305,727   7 HPFS/NTFS
/dev/sda8         230,870,178   234,436,544     3,566,367  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4126 MB, 4126146560 bytes
16 heads, 32 sectors/track, 15740 cylinders, total 8058880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     8,058,879     8,058,848   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        70F0DCBDF0DC8B2C                       ntfs       WinRE                         
/dev/sda2        E4DCE083DCE0517A                       ntfs       Vista                         
/dev/sda3        5EA0E4E8A0E4C81B                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        654573ae-bf5a-4922-85ec-d6308edfa5bb   ext4                                     
/dev/sda6        38f65b56-b27b-4763-a1a5-c49eb402031e   swap                                     
/dev/sda7        01CB46C7F24D0080                       ntfs                                     
/dev/sda8        3328d126-5c87-4c9d-8a6f-85d371acd351   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E1EC-90E0                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 654573ae-bf5a-4922-85ec-d6308edfa5bb
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 654573ae-bf5a-4922-85ec-d6308edfa5bb
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 654573ae-bf5a-4922-85ec-d6308edfa5bb
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=654573ae-bf5a-4922-85ec-d6308edfa5bb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 654573ae-bf5a-4922-85ec-d6308edfa5bb
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=654573ae-bf5a-4922-85ec-d6308edfa5bb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 654573ae-bf5a-4922-85ec-d6308edfa5bb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 654573ae-bf5a-4922-85ec-d6308edfa5bb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4dce083dce0517a
	drivemap -s (hd0) ${root}
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
# / was on /dev/sda7 during installation
UUID=654573ae-bf5a-4922-85ec-d6308edfa5bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=38f65b56-b27b-4763-a1a5-c49eb402031e none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 108.0GB: boot/grub/core.img
 104.3GB: boot/grub/grub.cfg
 108.0GB: boot/initrd.img-2.6.32-24-generic
 108.0GB: boot/vmlinuz-2.6.32-24-generic
 108.0GB: initrd.img
 108.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 44 4f 4b 30 32  2e 30 32 00 02 08 20 00  |.X.DOK02.02... .|
00000010  02 00 00 00 00 f8 00 00  20 00 10 00 20 00 00 00  |........ ... ...|
00000020  e0 f7 7a 00 af 1e 00 00  00 00 00 00 02 00 00 00  |..z.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 e0 90 ec e1 00  00 00 00 00 00 00 00 00  |..).............|
00000050  00 00 46 41 54 33 32 20  20 20 fa fc 31 c0 8e d0  |..FAT32   ..1...|
00000060  bc b4 7b 8e c0 b9 08 00  89 e7 f3 a5 8e d8 bb 78  |..{............x|
00000070  00 0f b4 37 0f a0 56 88  16 a1 4c 20 d2 78 15 b1  |...7..V...L .x..|
00000080  06 89 3f 89 47 02 64 f3  a5 8a 0e 18 7c 88 4d f8  |..?.G.d.....|.M.|
00000090  cd 13 eb 27 f6 45 f0 7f  75 08 66 8b 45 f8 66 a3  |...'.E..u.f.E.f.|
000000a0  1c 7c b4 08 cd 13 72 13  20 e4 75 0f c1 ea 08 42  |.|....r. .u....B|
000000b0  89 16 1a 7c 83 e1 3f 89  0e 18 7c fb bb aa 55 b4  |...|..?...|...U.|
000000c0  41 8a 16 a1 4c cd 13 72  10 81 fb 55 aa 75 0a f6  |A...L..r...U.u..|
000000d0  c1 01 74 05 c6 06 ff 7c  00 66 a1 f8 7d bb 00 7e  |..t....|.f..}..~|
000000e0  e8 10 00 66 81 3e 24 7e  09 99 4b 78 0f 85 c3 00  |...f.>$~..Kx....|
000000f0  e9 3d 02 bd 01 00 66 03  06 1c 7c 66 31 d2 eb 4f  |.=....f...|f1..O|
00000100  55 e8 d5 00 66 0f b7 fd  b9 10 00 66 52 66 50 06  |U...f......fRfP.|
00000110  53 57 6a 10 89 e6 66 60  8a 16 a1 4c 1e 16 1f b4  |SWj...f`...L....|
00000120  42 cd 13 1f 66 61 8d 64  10 72 10 5d 66 01 f8 29  |B...fa.d.r.]f..)|
00000130  fd c1 e7 09 01 fb 21 ed  75 c6 c3 66 60 31 c0 8a  |......!.u..f`1..|
00000140  16 a1 4c cd 13 66 61 e2  c2 c6 06 ff 7c 4f 5d 66  |..L..fa.....|O]f|
00000150  52 66 50 55 53 66 0f b7  36 18 7c 66 0f b7 3e 1a  |RfPUSf..6.|f..>.|
00000160  7c 66 f7 f6 31 c9 87 ca  66 f7 f7 e8 6b 00 29 ce  ||f..1...f...k.).|
00000170  39 f5 76 02 89 f5 c0 e4  06 41 08 e1 88 c5 88 d6  |9.v......A......|
00000180  8a 16 a1 4c 95 b4 02 bd  10 00 66 60 cd 13 66 61  |...L......f`..fa|
00000190  72 17 66 0f b6 c8 c1 e0  09 5b 01 c3 5d 66 58 66  |r.f......[..]fXf|
000001a0  5a 66 01 c8 29 cd 75 a7  c3 4d 75 de 95 d1 2e fc  |Zf..).u..Mu.....|
000001b0  7d 75 df 31 f6 8e d6 bc  b0 7b 8e de 66 8f 06 78  |}u.1.....{..f..x|
000001c0  00 be e4 7d ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |...}. .t........|
000001d0  eb f2 98 cd 16 cd 19 eb  fe 3b 2e fc 7d 76 04 8b  |.........;..}v..|
000001e0  2e fc 7d c3 42 6f 6f 74  20 65 72 72 6f 72 0d 0a  |..}.Boot error..|
000001f0  00 00 00 00 00 00 00 00  ee 01 19 00 7f 00 55 aa  |..............U.|
00000200
.

---

### Post by oldfred on 2010-09-03
Did you use windows to add or change partitions. Your Ubuntu shows it is in sda5 but the grub.cfg and fstab show the original install was sda7. And the grub in the MBR says it is trying to boot form sda7 but you do not have grub in sda7 but sda5.

You should just reinstall grub2 to the MBR of sda.

Install MBR from LiveCD (or USB), Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Once you  have rebooted into your install.

sudo update-grub

---

### Post by dooper on 2010-09-03
Fred...you are a Guru....

problem now seems fixed.

I am no Linux expert and have dabbled in the past but decided on the latest Ubuntu.

I installed the dual boot the other week but my lappy is usually powered up 24/7 so the issue didnt flag until today for some reason.

I think i went wrong by first trying to rejig and clear space on my drive for the proposed ubuntu install.

However when i went to install,the option given was to install/run windows/ubuntu side by side or similar??

Anyway,it didnt get installed in the space i had so carefully cleared using some 3rd party windows software.

I guess thats where all the issues were created and i had a feeling that the system was looking in the wrong place..

Thanks for the help Fred.. )

---

