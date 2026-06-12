---
title: "Master Boot Record damaged in Windows partition"
date: 2010-07-01
forum: General Help
---

### Post by vincentertainment on 2010-07-01
Thanks in advance for any help. 
Windows' Master Boot Record seems to be damaged on my dual-boot.
Here are the details.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => HP/Gateway is installed in the MBR of /dev/sdk
 => Windows is installed in the MBR of /dev/sdl

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 9817679 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 9721135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdk1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdk2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdl1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdl2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdl5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdl5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   303,917,669   303,917,607  83 Linux
/dev/sda2         303,917,670   312,576,704     8,659,035   5 Extended
/dev/sda5         303,917,733   312,576,704     8,658,972  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    15,133,229    15,133,167   b W95 FAT32
/dev/sdb2    *     15,133,230   312,560,639   297,427,410   7 HPFS/NTFS


Drive: sdk ___________________ _____________________________________________________

Disk /dev/sdk: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdk1                  63    15,133,229    15,133,167   b W95 FAT32
/dev/sdk2    *     15,133,230   312,560,639   297,427,410   7 HPFS/NTFS


Drive: sdl ___________________ _____________________________________________________

Disk /dev/sdl: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdl1          18,619,398    39,102,209    20,482,812   c W95 FAT32 (LBA)
/dev/sdl2              16,065    18,619,334    18,603,270   f W95 Ext d (LBA)
/dev/sdl5              16,128    18,619,334    18,603,207   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        705d06e4-5d5a-45a1-aee9-8f89d8a37ec7   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        678152f3-b6d4-40ef-b7ad-b19a9fee1d18   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0C56-6A4E                              vfat       HP_RECOVERY                   
/dev/sdb2        00F070A2F0709F98                       ntfs       HP_PAVILION                   
/dev/sdb: PTTYPE="dos" 
/dev/sdk1        0C56-6A4E                              vfat       HP_RECOVERY                   
/dev/sdk2        B20C7A690C7A290D                       ntfs       HP_PAVILION                   
/dev/sdk: PTTYPE="dos" 
/dev/sdl1        2469-0874                              vfat                                     
/dev/sdl2: PTTYPE="dos" 
/dev/sdl5        E8646E21646DF2AC                       ntfs                                     
/dev/sdl: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found
error: /dev/sdj: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdl1        /media/2469-0874         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdl5        /media/E8646E21646DF2AC  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdk2        /media/HP_PAVILION_      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/HP_PAVILION__     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=705d06e4-5d5a-45a1-aee9-8f89d8a37ec7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=705d06e4-5d5a-45a1-aee9-8f89d8a37ec7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=705d06e4-5d5a-45a1-aee9-8f89d8a37ec7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=705d06e4-5d5a-45a1-aee9-8f89d8a37ec7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod fat
    set root='(/dev/sdb,1)'
    search --no-floppy --fs-uuid --set 0c56-6a4e
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sdb2)" {
    insmod ntfs
    set root='(/dev/sdb,2)'
    search --no-floppy --fs-uuid --set 00f070a2f0709f98
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=705d06e4-5d5a-45a1-aee9-8f89d8a37ec7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=678152f3-b6d4-40ef-b7ad-b19a9fee1d18 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.9GB: boot/grub/core.img
   4.9GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.31-14-generic
   1.0GB: boot/initrd.img-2.6.32-22-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: boot/vmlinuz-2.6.32-22-generic
   1.0GB: initrd.img
    .9GB: initrd.img.old
    .8GB: vmlinuz
    .5GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sdk1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sdk2/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg sdh sdi sdj

---

### Post by Seanlol on 2010-07-01
Get a Windows disc and do a repair, first. See if that helps.

---

### Post by wilee-nilee on 2010-07-01
sdb2: __________________________________________________ _______________________

File system: ntfs
[B]Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sdb2 [/B]and
looks at sector 9721135 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

It appears that grub2 got installed to this partition which appears to be the boot partition, and the main OS. It looks to be XP, this link will direct you to a download and fix that should leave grub in place in the MBR sdb, and should allow for you to boot both OS.
If you need a link to a XP dusc though post that I can give you a legit download link.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

It looks as well that Grub2 in the mbr may be loaded to look at sdb1, so if you run this fix and still can't boot in post, it may be that the Ubuntu partition needs to be mounted along with loading the mbr again.

Edit: I guess also it helps to know what the sdk partitions are, it has a boot sdk1 and a sdk2 that looks like a ms media center or another XP install. I'm not familiar with what the media center would show in the bootscript.

It would also be helpful if you need more assistance if you give us more information as to actually how the computer boots or doesn't. work.

---

### Post by vincentertainment on 2010-07-02
Thanks for the feedback. I followed the instructions from Wilee-Nilee's link and that made progress.
Windows and Ubuntu both boot up now.
When I first boot up, I initially get an error that says Master Boot Record Error. Press a key.
Once I press a key, Grub 2 loads up and I'm good to go from there.
Any suggestions on getting rid of this error?
Here is my updated Boot Info Script results since the changes.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdk

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 9817679 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdk1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdk2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdk5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdk5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   303,917,669   303,917,607  83 Linux
/dev/sda2         303,917,670   312,576,704     8,659,035   5 Extended
/dev/sda5         303,917,733   312,576,704     8,658,972  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    15,133,229    15,133,167   b W95 FAT32
/dev/sdb2    *     15,133,230   312,560,639   297,427,410   7 HPFS/NTFS


Drive: sdk ___________________ _____________________________________________________

Disk /dev/sdk: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdk1          18,619,398    39,102,209    20,482,812   c W95 FAT32 (LBA)
/dev/sdk2              16,065    18,619,334    18,603,270   f W95 Ext d (LBA)
/dev/sdk5              16,128    18,619,334    18,603,207   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        705d06e4-5d5a-45a1-aee9-8f89d8a37ec7   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        678152f3-b6d4-40ef-b7ad-b19a9fee1d18   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0C56-6A4E                              vfat       HP_RECOVERY                   
/dev/sdb2        00F070A2F0709F98                       ntfs       WINDOWS_XP                    
/dev/sdb: PTTYPE="dos" 
/dev/sdk1        2469-0874                              vfat                                     
/dev/sdk2: PTTYPE="dos" 
/dev/sdk5        E8646E21646DF2AC                       ntfs                                     
/dev/sdk: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found
error: /dev/sdj: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdk5        /media/E8646E21646DF2AC  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdk1        /media/2469-0874         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=705d06e4-5d5a-45a1-aee9-8f89d8a37ec7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=705d06e4-5d5a-45a1-aee9-8f89d8a37ec7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=705d06e4-5d5a-45a1-aee9-8f89d8a37ec7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=705d06e4-5d5a-45a1-aee9-8f89d8a37ec7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 705d06e4-5d5a-45a1-aee9-8f89d8a37ec7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod fat
    set root='(/dev/sdb,1)'
    search --no-floppy --fs-uuid --set 0c56-6a4e
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sdb2)" {
    insmod ntfs
    set root='(/dev/sdb,2)'
    search --no-floppy --fs-uuid --set 00f070a2f0709f98
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=705d06e4-5d5a-45a1-aee9-8f89d8a37ec7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=678152f3-b6d4-40ef-b7ad-b19a9fee1d18 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.9GB: boot/grub/core.img
   5.3GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.31-14-generic
   1.0GB: boot/initrd.img-2.6.32-22-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: boot/vmlinuz-2.6.32-22-generic
   1.0GB: initrd.img
    .9GB: initrd.img.old
    .8GB: vmlinuz
    .5GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg sdh sdi sdj


```

---

### Post by wilee-nilee on 2010-07-02
I think for the fix on this error another more experienced forum member would be appropriate here. I think it may be a mixture of things with Grub2 being in the mbr of sdb and it pointed at sdb1 when Ubuntu is in sda1.

I want to error on the side of caution here, since you can boot both OS as of now except for the error at boot. There is also a HP bootloader showing in the mbr of sda so I'm just not sure of the overall fix.

At the least run in the Ubuntu terminal, and let us know if this changes things.
```
sudo update-grub
```

This set of multiple bootloaders is a little confusing three different types in 3 HD.

> HP/Gateway is installed in the MBR of /dev/sda
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
partition #1 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdk

---

### Post by drs305 on 2010-07-02
Your linux install is on your sda drive and but Grub2 isn't set up quite correctly. It's installed on *sdb* (which is ok) but also looks at a non-linux partition (sdb1) initially. To clean things up a bit, I recommend installing G2 in the sda MBR. It will probably eliminate the MBR error and may even speed up the boot a bit.

To do this, run:
```
sudo dpkg-reconfigure grub-pc
```

It will first display your kernel options - just press TAB to highlight the "OK" and press ENTER.

Then there will be a page of explanations - again TAB to "OK" and press ENTER.

Next is where you will make the change. Highlight "sda" (NOT sda1) and press the SPACE BAR. This should place an asterisk (*) next to *sda*. This will setup your system to install G2 to the *sda* MBR. 

Finally, highlight any other device with an asterisk and press the SPACE BAR to remove it. 

When only *sda* has an asterisk, tab to "OK" and press ENTER.

This should clean things up. If Grub2 doesn't see your Windows install after reboot (which is rare on normal setups), run "sudo update-grub".

Tip:
When pasting large amounts of text in a post, it is good to place it within "code" tags to provide a more user-friendly formatting. You do this by clicking on the "#" symbol in the post's menu. It will generate [noparse]```

```[/noparse] tags. Insert the text between the two tags.

I've taken the liberty of doing so with your previous post so you can compare the results between posts #1 and #4..

---

