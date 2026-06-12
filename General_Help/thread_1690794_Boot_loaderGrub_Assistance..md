---
title: "Boot loader/Grub Assistance."
date: 2011-02-19
forum: General Help
---

### Post by gstla on 2011-02-19
Wish I had posted here earlier, but I stubbornly wanted to try and fix  my problem, turns out I only made it worse =(.  I'm really loving Ubuntu  otherwise, and I think it's worth the trouble to get it running as a  dual boot.  If all else fails I'll just go pure Ubuntu ; ) since I can  run Microsoft Office (need it for my IT class) in PlayOnLinux/Wine, or  CrossOver. 

Some background:  I've been using Wubi-Ubuntu for several months.  I saw  that I could get StarCraft II working with PlayOnLinux (and I did  earlier, before checking my broken windows partition).  (I needed more  HDD space, so I decided to make around a 108 GB Ubuntu Partition).  I  shrunk my C: drive down approximately the 108 GB and then created a new  partition & distributed the space through the Ubuntu Installer. 

So I did some research, and managed to make it so that I can't run  anything other than a live-CD.  I think when I ran "bootsect /nt60 C: /  mbr" in an attempt to make it so that Windows 7 would boot again I  overwrote the Grub Bootloader or got rid of it somehow.  The problem  probably lies in some context of Cylanders in the Windows 7 system. 

That being said, I saw another similar thread earlier.  But... I guess I  should give some context first.  I divided my C: Drive (297 GB) into 2  Partitions (C:smile: (Windows) and (G:smile:  (Ubuntu).  I was pretty happy that I managed to partition and boot up  Ubuntu, but I realised I made a mistake somewhere as Windows 7 would  freeze/get stuck on the "Windows Key" - screen. 

So, I ran the boot_info_script055.sh (put it on my desktop) so I could  copy & paste the command to give the results.txt file... which I'm  posting below.  I don't particularly have any way to backup files, and I  should probably mention that I CAN access my windows 7 files while on  this live CD. 




```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   414,091,439   413,884,592  82 Linux swap / Solaris
/dev/sda3         414,091,501   625,142,284   211,050,784   f W95 Ext d (LBA)
/dev/sda5         414,091,503   625,142,284   211,050,782  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DE4E709A4E706D61                       ntfs       System Reserved               
/dev/sda2        821E07CA1E07B667                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        966d65b9-63db-4b02-b9d2-9f553ded0d5d   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/966d65b9-63db-4b02-b9d2-9f553ded0d5d ext2       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 966d65b9-63db-4b02-b9d2-9f553ded0d5d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 966d65b9-63db-4b02-b9d2-9f553ded0d5d
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 966d65b9-63db-4b02-b9d2-9f553ded0d5d
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=966d65b9-63db-4b02-b9d2-9f553ded0d5d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 966d65b9-63db-4b02-b9d2-9f553ded0d5d
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=966d65b9-63db-4b02-b9d2-9f553ded0d5d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 966d65b9-63db-4b02-b9d2-9f553ded0d5d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=966d65b9-63db-4b02-b9d2-9f553ded0d5d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 966d65b9-63db-4b02-b9d2-9f553ded0d5d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=966d65b9-63db-4b02-b9d2-9f553ded0d5d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 966d65b9-63db-4b02-b9d2-9f553ded0d5d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 966d65b9-63db-4b02-b9d2-9f553ded0d5d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de4e709a4e706d61
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
/dev/sda5       /               ext2    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 306.4GB: boot/grub/core.img
 306.4GB: boot/grub/grub.cfg
 306.2GB: boot/initrd.img-2.6.35-22-generic
 306.2GB: boot/initrd.img-2.6.35-25-generic
 306.3GB: boot/vmlinuz-2.6.35-22-generic
 306.3GB: boot/vmlinuz-2.6.35-25-generic
 306.2GB: initrd.img
 306.2GB: initrd.img.old
 306.3GB: vmlinuz
 306.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  47 44 63 10 f0 f8 be 4a  06 23 b9 c6 35 73 3f 2f  |GDc....J.#..5s?/|
00000010  19 13 83 a1 73 ac 23 e2  5c 70 cd e1 68 1f 95 e2  |....s.#.\p..h...|
00000020  13 01 25 17 b6 a1 3a 38  91 8a c5 9d d5 01 c3 6b  |..%...:8.......k|
00000030  c1 a3 94 b3 63 35 a7 82  64 98 e0 0a ed df 47 a2  |....c5..d.....G.|
00000040  01 e5 ee d8 23 99 ed ed  b3 75 72 38 06 68 96 ac  |....#....ur8.h..|
00000050  bc 98 d4 68 be 79 b5 68  bf 65 ff d5 b2 ec 53 0e  |...h.y.h.e....S.|
00000060  71 ca d8 e8 3a 18 3f 75  7f 5c fa 42 0c bb 95 d1  |q...:.?u.\.B....|
00000070  82 00 8f 30 e7 79 aa cd  05 af 93 02 7a 8f 39 01  |...0.y......z.9.|
00000080  fd 89 e5 50 40 89 20 73  93 25 19 3a f3 a1 e7 d7  |...P@. s.%.:....|
00000090  61 09 65 cd a6 ac 86 94  a8 68 43 4d 95 6f 7c 02  |a.e......hCM.o|.|
000000a0  ad 16 32 aa 06 26 b8 5a  65 16 8a 8b f3 e2 69 e1  |..2..&.Ze.....i.|
000000b0  1a a2 42 85 ef 7d 17 5b  0b 57 4c 6a 47 36 79 44  |..B..}.[.WLjG6yD|
000000c0  66 56 d7 55 ec ec 44 71  3a 59 da ce cc e8 62 88  |fV.U..Dq:Y....b.|
000000d0  ab 8e 7a c2 43 6b c1 f1  6e 1c 27 d0 6c 6e e2 13  |..z.Ck..n.'.ln..|
000000e0  a7 7c e6 55 a4 0f 7f bb  79 82 35 80 3a dd a8 95  |.|.U....y.5.:...|
000000f0  9a 68 f3 64 7b ad 74 b6  8a 18 44 8a b7 59 32 88  |.h.d{.t...D..Y2.|
00000100  72 54 15 6d 6f 24 80 85  86 a3 c1 dd e9 c3 57 1e  |rT.mo$........W.|
00000110  31 0d f3 4b b3 75 9e ed  a9 6c 4a a0 39 fd 01 88  |1..K.u...lJ.9...|
00000120  d0 da 4b 0a 61 c9 12 50  59 dc 11 5a 90 72 7a d9  |..K.a..PY..Z.rz.|
00000130  eb a3 17 48 87 8b d3 21  46 3a ad 03 df dd fd 1c  |...H...!F:......|
00000140  59 82 fb 89 ec 31 f0 05  e6 51 59 27 f5 95 8d 40  |Y....1...QY'...@|
00000150  76 98 df 6a 4c 4c 61 88  65 a4 fc 73 35 4e c1 ef  |v..jLLa.e..s5N..|
00000160  1b c9 47 a6 c9 00 28 b8  19 4c ab 23 0e 43 01 02  |..G...(..L.#.C..|
00000170  ee 07 e9 86 2a 9e 07 71  04 24 de 6f 06 11 9e dc  |....*..q.$.o....|
00000180  21 35 5d 82 44 76 10 5f  7f ed 9f af cf a7 23 09  |!5].Dv._......#.|
00000190  83 c2 9f 46 e0 9d ca 8a  f8 79 a3 0c 2e df 3b 8e  |...F.....y....;.|
000001a0  5b c4 63 5d 17 4b 45 3b  8f b1 e5 9e 05 5e 59 bc  |[.c].KE;.....^Y.|
000001b0  df 38 70 32 4f de b4 04  c2 9f 13 4d 2c 60 00 fe  |.8p2O......M,`..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 1e 61 94 0c 00 00  |...........a....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200 
```Edit: but that doesn't mean I've given up. :razz:.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) working through this bit, just got through the last with a successful

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/966d65b9-63db-4b02-b9d2-9f553ded0d5d /dev/sda5
Probing devices to guess BIOS drives. This may take a long time.
Installing GRUB to /dev/sda5 as (hd0,4)...
Installation finished. No error reported.
This is the contents of the device map /media/966d65b9-63db-4b02-b9d2-9f553ded0d5d/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda 
```rebooted... didn't work.  Windows Boot Loader  loaded up again listing only the Windows 7 OS that won't boot up.  I was  aiming for > 
Reboot, making sure to boot to your hard drive and  not to the live CD.  Grub should be installed and both Ubuntu and Windows  should have been  automatically detected and listed in the menu. 
The  Master Boot Record will execute Grub as the initial boot-loader.  The  Windows boot-loader is contained within the Windows partition and  will  then be chainloaded by the Grub boot-loader.  Any ideas  where I went wrong? 

If at all possible, getting Grub back / being able to boot my ubuntu would be ideal.
Going to try Rescatux 0.22.. xD
(Wait... I'm using a LiveCD, and my brother took my flash drive for a school project ><)

---

### Post by Rubi1200 on 2011-02-19
If I've followed your post correctly, you just installed GRUB to the Ubuntu partition.

GRUB needs to be installed to the MBR of the drive, not the partition.

You can do one of two things now; either post the boot script again for us to see what the current situation is or reinstall GRUB, but this time to the MBR of sda.

---

### Post by gstla on 2011-02-19
> **Rubi1200 said:**
> If I've followed your post correctly, you just installed GRUB to the Ubuntu partition.

GRUB needs to be installed to the MBR of the drive, not the partition.

You can do one of two things now; either post the boot script again for us to see what the current situation is or reinstall GRUB, but this time to the MBR of sda.

Program-Hardware logic is really hard to follow if you're not versed in it very well.  I went ahead and re-installed Ubuntu (formatted the 108GB old partition) and now I have Grub back w/ the Windows 7 in it that won't boot.  

I'll make another log soon.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 598509967 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   414,091,439   413,884,592  82 Linux swap / Solaris
/dev/sda3         414,091,501   625,142,284   211,050,784   f W95 Ext d (LBA)
/dev/sda5         414,091,503   625,142,284   211,050,782  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DE4E709A4E706D61                       ntfs       System Reserved               
/dev/sda2        821E07CA1E07B667                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        362026f9-50dd-4e34-884b-fe01b933cd91   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext2       (rw,errors=remount-ro)
/dev/sda2        /media/821E07CA1E07B667  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=362026f9-50dd-4e34-884b-fe01b933cd91 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=362026f9-50dd-4e34-884b-fe01b933cd91 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=362026f9-50dd-4e34-884b-fe01b933cd91 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=362026f9-50dd-4e34-884b-fe01b933cd91 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de4e709a4e706d61
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
# / was on /dev/sda5 during installation
UUID=362026f9-50dd-4e34-884b-fe01b933cd91 /               ext2    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 295.4GB: boot/grub/core.img
 295.3GB: boot/grub/grub.cfg
 295.2GB: boot/initrd.img-2.6.35-22-generic
 295.2GB: boot/initrd.img-2.6.35-25-generic
 295.3GB: boot/vmlinuz-2.6.35-22-generic
 295.3GB: boot/vmlinuz-2.6.35-25-generic
 295.2GB: initrd.img
 295.2GB: initrd.img.old
 295.3GB: vmlinuz
 295.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  47 44 63 10 f0 f8 be 4a  06 23 b9 c6 35 73 3f 2f  |GDc....J.#..5s?/|
00000010  19 13 83 a1 73 ac 23 e2  5c 70 cd e1 68 1f 95 e2  |....s.#.\p..h...|
00000020  13 01 25 17 b6 a1 3a 38  91 8a c5 9d d5 01 c3 6b  |..%...:8.......k|
00000030  c1 a3 94 b3 63 35 a7 82  64 98 e0 0a ed df 47 a2  |....c5..d.....G.|
00000040  01 e5 ee d8 23 99 ed ed  b3 75 72 38 06 68 96 ac  |....#....ur8.h..|
00000050  bc 98 d4 68 be 79 b5 68  bf 65 ff d5 b2 ec 53 0e  |...h.y.h.e....S.|
00000060  71 ca d8 e8 3a 18 3f 75  7f 5c fa 42 0c bb 95 d1  |q...:.?u.\.B....|
00000070  82 00 8f 30 e7 79 aa cd  05 af 93 02 7a 8f 39 01  |...0.y......z.9.|
00000080  fd 89 e5 50 40 89 20 73  93 25 19 3a f3 a1 e7 d7  |...P@. s.%.:....|
00000090  61 09 65 cd a6 ac 86 94  a8 68 43 4d 95 6f 7c 02  |a.e......hCM.o|.|
000000a0  ad 16 32 aa 06 26 b8 5a  65 16 8a 8b f3 e2 69 e1  |..2..&.Ze.....i.|
000000b0  1a a2 42 85 ef 7d 17 5b  0b 57 4c 6a 47 36 79 44  |..B..}.[.WLjG6yD|
000000c0  66 56 d7 55 ec ec 44 71  3a 59 da ce cc e8 62 88  |fV.U..Dq:Y....b.|
000000d0  ab 8e 7a c2 43 6b c1 f1  6e 1c 27 d0 6c 6e e2 13  |..z.Ck..n.'.ln..|
000000e0  a7 7c e6 55 a4 0f 7f bb  79 82 35 80 3a dd a8 95  |.|.U....y.5.:...|
000000f0  9a 68 f3 64 7b ad 74 b6  8a 18 44 8a b7 59 32 88  |.h.d{.t...D..Y2.|
00000100  72 54 15 6d 6f 24 80 85  86 a3 c1 dd e9 c3 57 1e  |rT.mo$........W.|
00000110  31 0d f3 4b b3 75 9e ed  a9 6c 4a a0 39 fd 01 88  |1..K.u...lJ.9...|
00000120  d0 da 4b 0a 61 c9 12 50  59 dc 11 5a 90 72 7a d9  |..K.a..PY..Z.rz.|
00000130  eb a3 17 48 87 8b d3 21  46 3a ad 03 df dd fd 1c  |...H...!F:......|
00000140  59 82 fb 89 ec 31 f0 05  e6 51 59 27 f5 95 8d 40  |Y....1...QY'...@|
00000150  76 98 df 6a 4c 4c 61 88  65 a4 fc 73 35 4e c1 ef  |v..jLLa.e..s5N..|
00000160  1b c9 47 a6 c9 00 28 b8  19 4c ab 23 0e 43 01 02  |..G...(..L.#.C..|
00000170  ee 07 e9 86 2a 9e 07 71  04 24 de 6f 06 11 9e dc  |....*..q.$.o....|
00000180  21 35 5d 82 44 76 10 5f  7f ed 9f af cf a7 23 09  |!5].Dv._......#.|
00000190  83 c2 9f 46 e0 9d ca 8a  f8 79 a3 0c 2e df 3b 8e  |...F.....y....;.|
000001a0  5b c4 63 5d 17 4b 45 3b  8f b1 e5 9e 05 5e 59 bc  |[.c].KE;.....^Y.|
000001b0  df 38 70 32 4f de b4 04  c2 9f 13 4d 2c 60 00 fe  |.8p2O......M,`..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 1e 61 94 0c 00 00  |...........a....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200 
```

---

### Post by Rubi1200 on 2011-02-19
Is Windows booting now? Sorry, wasn't clear to me from what you wrote.

And Ubuntu? Because you seem to have vestiges of legacy-GRUB in the boot sector of sda5 even though this was a reinstall???

---

### Post by gstla on 2011-02-19
> **Rubi1200 said:**
> Is Windows booting now? Sorry, wasn't clear to me from what you wrote.

And Ubuntu? Because you seem to have vestiges of legacy-GRUB in the boot sector of sda5 even though this was a reinstall???

I don't believe that windows is bootable now (I'll check).  When I first installed Ubuntu, I set things up to the best of my ability, then checked Windows.  Windows boots up to the red, green, yellow and blue Windows Logo, then freezes at that screen. Yep, I think it may have something to do with when I resized the windows partition.  I did it with Easeus Partition maker, I remember something about Cylindrical Bounds(?) but I didn't see an option for it.  

Right now, I'd just like to figure out how to get Windows back, so I can dual-boot..  Ubuntu is much more responsive than Windows 7, in my opinion, but I'd still like the primary OS to be usable. 

In the Ubuntu Installer I selected the 108GB partition, checked format, added the /, the Ex2 File type, and installed.  Vestiges? Remnants? is that what those .old files are? No need to apologise, if anything was unclear, then it's my fault.  The boot loader said that Windows was @ /dev/sda1

---

### Post by Rubi1200 on 2011-02-19
Check to see if Windows is booting first.

Why are you using ext2? The default for Ubuntu from 9.10 onwards is ext4.

If Ubuntu boots normally and the only problem is Windows we can sort that out.

But if Windows starts and then freezes at the logo that is not a GRUB or Ubuntu issue but a Windows problem.

Once GRUB hands over control to the Windows kernel, it is Windows all the way so to speak.

---

### Post by gstla on 2011-02-19
> **Rubi1200 said:**
> Check to see if Windows is booting first.

Why are you using ext2? The default for Ubuntu from 9.10 onwards is ext4.

If Ubuntu boots normally and the only problem is Windows we can sort that out.

But if Windows starts and then freezes at the logo that is not a GRUB or Ubuntu issue but a Windows problem.

Once GRUB hands over control to the Windows kernel, it is Windows all the way so to speak.

Well, I originally wanted to use NTFS, but I wasn't thinking and the installer suggested ext2, so that's what I went with.  Would it be worth formatting again to switch file-systems later down the road?

Ubuntu boots up fine now.  The simplest solution & most effective was for me to elect to re-configure all my settings w/ a reformat & reinstall of Ubuntu.  

Yeah, I suspect I botched some part of the partitioning process in Windows 7 when I shrunk the Windows Partition & created the Ubuntu partition.  

Opening up the Systems > Administration > Disk Utility at the moment.  

212 GB NTFS / Usage: File System / Partition Type - Linux Swap(?) (0x82) / Device : /dev/sda2 

Under Edit Partition, it's not listed as bootable either(not checked).  (Hopefully I don't have a 212 GB swap file... that would be embarrassing..) but with my luck...

---

### Post by Rubi1200 on 2011-02-19
Do you have the Windows installation/recovery CD?

Please also post the output of the boot script again.

 > I suspect I botched some part of the partitioning process in Windows 7  when I shrunk the Windows Partition & created the Ubuntu partition.   In general, Windows does not like it when its partitions are shrunk by tools other than its own built-in tools. So, for example, if you did that with GParted etc. it could be unhappy.

If you have the Windows CD, I recommend you run chkdsk on the Windows partition:
[http://kb.wisc.edu/page.php?id=6565](http://kb.wisc.edu/page.php?id=6565)
I recommend using chkdsk /f (you may need to run it a few times if there are many errors reported)

---

### Post by gstla on 2011-02-19
> **Rubi1200 said:**
> Do you have the Windows installation/recovery CD?

Please also post the output of the boot script again.

 In general, Windows does not like it when its partitions are shrunk by tools other than its own built-in tools. So, for example, if you did that with GParted etc. it could be unhappy.

If you have the Windows CD, I recommend you run chkdsk on the Windows partition:
[http://kb.wisc.edu/page.php?id=6565](http://kb.wisc.edu/page.php?id=6565)
I recommend using chkdsk /f

There's a small recovery partition for this laptop.  When I tap F8 at bootup I can get into advanced boot options and launch things like a startup repair (hasn't been able to fix anything yet), a command prompt, or a system restore  

I do have my Home Premium 7 x64 disc, but it doesn't seem to have this sort of capability, I'll try the chkdsk /f command in the F8-Recovery shortly. 

[http://www.partition-tool.com/easeus-partition-manager/](http://www.partition-tool.com/easeus-partition-manager/)
I used this partition manager, I did not use gparted, I wanted to take care of it within Windows.

edit: tried a chkdsk /f @ the recovery-panel
Type = NTFS
cannot lock current drive
cannot run d checking because its write protected.

another log for you. (Thank you...) 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 598509967 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   414,091,439   413,884,592  82 Linux swap / Solaris
/dev/sda3         414,091,501   625,142,284   211,050,784   f W95 Ext d (LBA)
/dev/sda5         414,091,503   625,142,284   211,050,782  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DE4E709A4E706D61                       ntfs       System Reserved               
/dev/sda2        821E07CA1E07B667                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        362026f9-50dd-4e34-884b-fe01b933cd91   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext2       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=362026f9-50dd-4e34-884b-fe01b933cd91 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=362026f9-50dd-4e34-884b-fe01b933cd91 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=362026f9-50dd-4e34-884b-fe01b933cd91 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=362026f9-50dd-4e34-884b-fe01b933cd91 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 362026f9-50dd-4e34-884b-fe01b933cd91
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de4e709a4e706d61
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
# / was on /dev/sda5 during installation
UUID=362026f9-50dd-4e34-884b-fe01b933cd91 /               ext2    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 295.4GB: boot/grub/core.img
 295.3GB: boot/grub/grub.cfg
 295.2GB: boot/initrd.img-2.6.35-22-generic
 295.2GB: boot/initrd.img-2.6.35-25-generic
 295.3GB: boot/vmlinuz-2.6.35-22-generic
 295.3GB: boot/vmlinuz-2.6.35-25-generic
 295.2GB: initrd.img
 295.2GB: initrd.img.old
 295.3GB: vmlinuz
 295.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  47 44 63 10 f0 f8 be 4a  06 23 b9 c6 35 73 3f 2f  |GDc....J.#..5s?/|
00000010  19 13 83 a1 73 ac 23 e2  5c 70 cd e1 68 1f 95 e2  |....s.#.\p..h...|
00000020  13 01 25 17 b6 a1 3a 38  91 8a c5 9d d5 01 c3 6b  |..%...:8.......k|
00000030  c1 a3 94 b3 63 35 a7 82  64 98 e0 0a ed df 47 a2  |....c5..d.....G.|
00000040  01 e5 ee d8 23 99 ed ed  b3 75 72 38 06 68 96 ac  |....#....ur8.h..|
00000050  bc 98 d4 68 be 79 b5 68  bf 65 ff d5 b2 ec 53 0e  |...h.y.h.e....S.|
00000060  71 ca d8 e8 3a 18 3f 75  7f 5c fa 42 0c bb 95 d1  |q...:.?u.\.B....|
00000070  82 00 8f 30 e7 79 aa cd  05 af 93 02 7a 8f 39 01  |...0.y......z.9.|
00000080  fd 89 e5 50 40 89 20 73  93 25 19 3a f3 a1 e7 d7  |...P@. s.%.:....|
00000090  61 09 65 cd a6 ac 86 94  a8 68 43 4d 95 6f 7c 02  |a.e......hCM.o|.|
000000a0  ad 16 32 aa 06 26 b8 5a  65 16 8a 8b f3 e2 69 e1  |..2..&.Ze.....i.|
000000b0  1a a2 42 85 ef 7d 17 5b  0b 57 4c 6a 47 36 79 44  |..B..}.[.WLjG6yD|
000000c0  66 56 d7 55 ec ec 44 71  3a 59 da ce cc e8 62 88  |fV.U..Dq:Y....b.|
000000d0  ab 8e 7a c2 43 6b c1 f1  6e 1c 27 d0 6c 6e e2 13  |..z.Ck..n.'.ln..|
000000e0  a7 7c e6 55 a4 0f 7f bb  79 82 35 80 3a dd a8 95  |.|.U....y.5.:...|
000000f0  9a 68 f3 64 7b ad 74 b6  8a 18 44 8a b7 59 32 88  |.h.d{.t...D..Y2.|
00000100  72 54 15 6d 6f 24 80 85  86 a3 c1 dd e9 c3 57 1e  |rT.mo$........W.|
00000110  31 0d f3 4b b3 75 9e ed  a9 6c 4a a0 39 fd 01 88  |1..K.u...lJ.9...|
00000120  d0 da 4b 0a 61 c9 12 50  59 dc 11 5a 90 72 7a d9  |..K.a..PY..Z.rz.|
00000130  eb a3 17 48 87 8b d3 21  46 3a ad 03 df dd fd 1c  |...H...!F:......|
00000140  59 82 fb 89 ec 31 f0 05  e6 51 59 27 f5 95 8d 40  |Y....1...QY'...@|
00000150  76 98 df 6a 4c 4c 61 88  65 a4 fc 73 35 4e c1 ef  |v..jLLa.e..s5N..|
00000160  1b c9 47 a6 c9 00 28 b8  19 4c ab 23 0e 43 01 02  |..G...(..L.#.C..|
00000170  ee 07 e9 86 2a 9e 07 71  04 24 de 6f 06 11 9e dc  |....*..q.$.o....|
00000180  21 35 5d 82 44 76 10 5f  7f ed 9f af cf a7 23 09  |!5].Dv._......#.|
00000190  83 c2 9f 46 e0 9d ca 8a  f8 79 a3 0c 2e df 3b 8e  |...F.....y....;.|
000001a0  5b c4 63 5d 17 4b 45 3b  8f b1 e5 9e 05 5e 59 bc  |[.c].KE;.....^Y.|
000001b0  df 38 70 32 4f de b4 04  c2 9f 13 4d 2c 60 00 fe  |.8p2O......M,`..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 1e 61 94 0c 00 00  |...........a....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200 
```

---

### Post by Rubi1200 on 2011-02-19
You should definitely try and run chkdsk.

In future, please don't use third party partitioning tools for this kind of thing.

Windows 7 has the built-in Disk Management utility which will do the job without creating problems (usually).

---

### Post by gstla on 2011-02-19
> **Rubi1200 said:**
> You should definitely try and run chkdsk.

In future, please don't use third party partitioning tools for this kind of thing.

Windows 7 has the built-in Disk Management utility which will do the job without creating problems (usually).

chkdsk said that it couldn't lock the current drive and that it couldn't run disc checking b/c the drive was write protected.  Okay, if I manage to get back into windows I'll never use a 3rd party partitioning manager again.

---

### Post by Quackers on 2011-02-19
I would suggest re-installing Ubuntu to an ext4 partition leaving the bootloader to install at its default settings.
At the moment you have grub 2 installed to the mbr of the drive and parts of grub legacy (a previous version of grub) in the sda5 partition. I would imagine you used an old guide at some time to repair grub.
When re-installed and booting ok, you should run ```
sudo update-grub
``` in the terminal, and watch as grub.cfg is run, to make sure the Windows Loader is picked up.
At that point you can try booting from the Windows installation disc, pressing R when required to, giving you access to the recovery console. At this point you can select the command prompt option and run 
```
chkdsk C: /r
```
and keep running that until no errors are found. Hopefully Windows will then boot from the grub menu.

---

### Post by gstla on 2011-02-19
Okay, I just ran "Sudo update-grub"
Got the following code / terminal
```
@GST-M15x:~$ sudo update-grub
[sudo] password for brian: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done 
```

I do have my dell-alienware M15x recovery disc, but I've never accessed the recovery from it (if such a thing is possible).  Usually, when I boot up that disc it just goes straight to the windows installer.  After I choose to boot from the M15x recovery-disc (windows re-installation disc) should I just tap R?

As I said in a prior post, there's a small recovery-partition available (maybe 200 MB), where if I tap F8 while booting, it'll load me into the advanced boot options and Windows-Repair; where I have a host of options ranging from a command prompt, system restore, back-up images, & so on.

---

### Post by Rubi1200 on 2011-02-19
Have you tried booting Windows from the GRUB menu now that it seems to have added it?

I would give that a go first. If it works, you are back in business. If not, we can try other options.

---

### Post by gstla on 2011-02-19
Well, the thing is even **originally**, when I installed Ubuntu, Windows 7 showed up on the GRUB-Bootloader.  It **will/would not**, however, load up past the windows, blue, yellow, red & green logo. 

When I've been running chkdsk as you guys told me to I've been doing it from the small recovery partition that's "system reserved" on my partition, you might be able to see it on the boot info logs. 

Anyhow, I ran "chkdsk C: /r" and it ran, but in my experience it's supposed to take a considerable amount of time; this chkdsk ran in like 15 seconds, and re-affirmed that the disk is in fact clean. However, a peculiar thing that happened was that I received a message that said "Failed to transfer logged message event - Log Status 50" or something similar. (Log Status 50, for sure). 

I don't think there's anything wrong with my disc as a whole, are there other reasons why windows wouldn't be able to boot? What should my Disk Utility say about the windows partition sda2? 

I'll upload a screen-shot of my Disk Utility page so you can see what I'm looking at.  
[http://img716.imageshack.us/f/screenshotdlg.png/](http://img716.imageshack.us/f/screenshotdlg.png/)

If we can't get windows back to booting normally, then I'd like to know how to properly reformat so that I can give Windows the 108 GB partition and Ubuntu the 212 GB partition.

---

### Post by gstla on 2011-02-19
I just went ahead and deleted both partitions and reformatted back to Windows 7.  My data wasn't very important, mostly multimedia that I can garner from my two brothers and their desktops.

I also installed EasyBCD and downloaded the Windows 7 repair disc (it's legal, and from the EasyBCD maker themselves, sponsored by Microsoft).  So that'll come in handy for future problems.

For now I'm just working on getting my Windows Partition back up to speed, installing commonly used programs; that sort of thing.  An Ubuntu installation will come sometime this weekend or on Monday, perhaps, but for now I'm just glad to have a working Windows again.

---

