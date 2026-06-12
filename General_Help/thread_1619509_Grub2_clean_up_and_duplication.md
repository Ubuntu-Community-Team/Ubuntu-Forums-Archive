---
title: "Grub2 clean up and duplication"
date: 2010-11-11
forum: General Help
---

### Post by The standard username on 2010-11-11
Hello,
this is my first post here .

I have two issues related to grub2

I upgraded recently from ubuntu 8 to 10.04  and upgraded grub 0.98 to 1.98  .

1-How to prevent Grub from detecting one of Windows installations?  or how does grub detect Windows.     I have 2 hdds,  they were backup of each other. but no more, I deleted one Windows by deleting most of the files so therefore I don't need it to be present in Grub 2 menu.    How do I delete this?  any suggestion? 

2-For some reason grub2 only work correctly from sdb ,  even though I chose to install grub2 to sda too, but it seems grub is trying to find grub files on the same hard disk instead of on sdb, therefore it goes into grub rescue mode with error "file not found" .    I set my computer to boot from sdb for now.  but I would like to learn how to make sda's grub work.  before it used to work with grub 0.98.



I'm kind of new to Linux, so please provide more explanation of what to do (;
Thanks!

---

### Post by wilee-nilee on 2010-11-11
Lets have a look at the whole setup with all the hardrives plugged in, click on the bootscript link in my signature. Follow the instructions, come back to the thread open a reply and click on the # in the reply panel you will see codetags like in my sig, paste the text in between them.

---

### Post by The standard username on 2010-11-11
Thanks for the fast response.  

I did what you suggested and pasted the result between code tags

sorry for the clutter , these hard disks were backups of each other, the modified entries you see in windows boot ini is by me to solve another issue.


```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #4 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sdb4 already mounted or sdb4 busy

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 56.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sda2         268,414,020   567,174,824   298,760,805   7 HPFS/NTFS
/dev/sda3         567,174,825   772,180,289   205,005,465   7 HPFS/NTFS
/dev/sda4         889,374,465   976,768,064    87,393,600  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sdb2         268,414,020   567,174,824   298,760,805   7 HPFS/NTFS
/dev/sdb3         567,174,825   772,180,289   205,005,465   7 HPFS/NTFS
/dev/sdb4         889,374,465   976,768,064    87,393,600  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4009 MB, 4009754624 bytes
51 heads, 56 sectors/track, 2742 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             56     7,831,551     7,831,496   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        22F48CF8F48CD009                       ntfs                                     
/dev/sda2        C694A12D94A12143                       ntfs       D Town                        
/dev/sda3        CE18E25118E2385B                       ntfs       E Town                        
/dev/sda4        e7562bed-434d-4a0c-aa29-1af385378986   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        22F48CF8F48CD009                       ntfs                                     
/dev/sdb2        C694A12D94A12143                       ntfs       D Town                        
/dev/sdb3        CE18E25118E2385B                       ntfs       E Town                        
/dev/sdb4        e7562bed-434d-4a0c-aa29-1af385378986   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3CB00312B002D1F6                       ntfs       Town 80                       
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        84BE-2329                              vfat                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /media/22F48CF8F48CD009  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/D Town            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT /NOEXECUTE=OPTIN 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition 2" /FASTDETECT /NOEXECUTE=OPTIN 

=========================== sda4/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e7562bed-434d-4a0c-aa29-1af385378986 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Chainload into GRUB 2
root        (hd0,3)
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=e7562bed-434d-4a0c-aa29-1af385378986 ro quiet splash
initrd        /boot/initrd.img-2.6.32-25-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=e7562bed-434d-4a0c-aa29-1af385378986 ro single
initrd        /boot/initrd.img-2.6.32-25-generic

#title        Ubuntu 10.04.1 LTS, kernel 2.6.24-19-generic
#root        (hd0,3)
#kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=e7562bed-434d-4a0c-#aa29-1af385378986 ro quiet splash
#initrd        /boot/initrd.img-2.6.24-19-generic
#quiet

#title        Ubuntu 10.04.1 LTS, kernel 2.6.24-19-generic (recovery mode)
#root        (hd0,3)
#kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=e7562bed-434d-4a0c-#aa29-1af385378986 ro single
#initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 10.04.1 LTS, memtest86+
root        (hd0,3)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST





=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set e7562bed-434d-4a0c-aa29-1af385378986
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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set e7562bed-434d-4a0c-aa29-1af385378986
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set e7562bed-434d-4a0c-aa29-1af385378986
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=e7562bed-434d-4a0c-aa29-1af385378986 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set e7562bed-434d-4a0c-aa29-1af385378986
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=e7562bed-434d-4a0c-aa29-1af385378986 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set e7562bed-434d-4a0c-aa29-1af385378986
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set e7562bed-434d-4a0c-aa29-1af385378986
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 22f48cf8f48cd009
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 22f48cf8f48cd009
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

========================== sda4/boot/grub/grub.conf: ==========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e7562bed-434d-4a0c-aa29-1af385378986 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=e7562bed-434d-4a0c-aa29-1af385378986 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=e7562bed-434d-4a0c-aa29-1af385378986 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,3)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST





=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=e7562bed-434d-4a0c-aa29-1af385378986 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 463.8GB: boot/grub/core.img
 463.9GB: boot/grub/grub.cfg
 463.8GB: boot/grub/grub.conf
 463.9GB: boot/grub/menu.lst
 463.9GB: boot/initrd.img-2.6.32-25-generic
 463.8GB: boot/vmlinuz-2.6.32-25-generic
 463.9GB: initrd.img
 463.8GB: vmlinuz

================================ sdb1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition 2" /FASTDETECT /NOEXECUTE=OPTIN 
```

---

### Post by wilee-nilee on 2010-11-11
So you have a couple of problems all fixable I think. First you need to understand that grub works best when in the MBR of the HD it is actually in=sda this is just how it is. And the HD should be first to be read in the bios.

You also have a mixture of grub-legacy and grub2.
```
sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   **/boot/grub/menu.lst /boot/grub/grub.cfg **
                       /boot/grub/grub.conf /etc/fstab /boot/grub/core.img



```

Take a look at the Chroot part of this thread to get some type of grub in there after purging the mixture. Personally grub2 is the future, I'm not sure how you feel.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If you look at this thread and the drs305's signature links you will find a plethora of great tutorials.

It also looks like two W7 installs is this the case? 

So this is information really at this point. You might hang a bit to see what others say as you have a setup that is well at the least a lot of text to decipher and I want you up and running.;)

---

### Post by The standard username on 2010-11-11
Thanks for the help. I ll take a look at the links and will post back later. but just to clarify.

I used to have windows 7 RC.  but I removed it too as it probably expired anyway.  both hard disks had the same installations because one was backup of the other. but not on Raid, so not exact copy.  just I copied the first hard to second.   this happened when I wanted to try windows 7 Beta, then again when installed Windows 7 RC.     in anyway. now there is only windows that's Windows XP.  , the rest are all left overs. boots .

I thought I already copied grub2 to mbr.  correct me if I'm wrong.    I don't want to use the old grub.  and I also want to clean up this mess.  I only need one Windows XP and one Ubuntu.

You can safely ignore information about sdd . only sdb and sda matter. the rest are nothing. also windows on the first partition , so sda2,3, sdb2,3 don't matter.     Windows XP on sdb1  linux on sdb4 too. 


For now in relation to issue 1, is there a simple way to delete windows in a way that prevent grub from detecting it?  

thanks

Edit:

yes that mixture of boot is on sda4,  this is an old linux installation,  I need to get rid of it.   is that why grub2 when installed on sda trying to load files from sda not sdb? is there a way to force grub to load files from the second hard disk, or not possible? 
the current linux installed on sdb4

---

### Post by wilee-nilee on 2010-11-11
So here is the deal I have a terrible headache right now and can't really concentrate well enough to really give you definitive help that I would feel was in your best interests, because your #1 here, no matter what anybody else says;)

So about this time a few regulars flow onto the forum, (if your out there now post) so I'm going to get some dinner and a chill a bit, then I will take a look at the thread and see whats up.

Be really concise about your setup, we don't care about your intentions, just the facts,;) for me it is difficult to follow a description when I get the intentions and why somebody does something that really isn't relevant. Your problem isn't real complex but with the mixture of all this it does make it a challenge for me personally.

Be back shortly within a couple of hours.:)

---

### Post by The standard username on 2010-11-12
> **wilee-nilee said:**
> So here is the deal I have a terrible headache right now and can't really concentrate well enough to really give you definitive help that I would feel was in your best interests, because your #1 here, no matter what anybody else says;)

So about this time a few regulars flow onto the forum, (if your out there now post) so I'm going to get some dinner and a chill a bit, then I will take a look at the thread and see whats up.

Be really concise about your setup, we don't care about your intentions, just the facts,;) for me it is difficult to follow a description when I get the intentions and why somebody does something that really isn't relevant. Your problem isn't real complex but with the mixture of all this it does make it a challenge for me personally.

Be back shortly within a couple of hours.:)


Thanks a lot, I appreciate your help.     I mentioned my *intentions* and what I did, only to provide background for the problem in case it matters for the solution. sorry to make my posts long. 

Please take your time. it is not an urgent. I'm able to boot both systems.  I just want to learn and clean up the clutter.     I use Windows most of the time but I would love to switch my work at least to Ubuntu. but first i need to understand more. 

I also made a workaround to hide one windows installation in 30_os_probe  I added lines to check if it matches the /dev/sda1 then it doesn't display the OS.   and it worked. but this is a quirky solution


Feel free to reply anytime /anyday you like,  or if anyone can help thanks!

---

### Post by wilee-nilee on 2010-11-12
sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sdb4 already mounted or sdb4 busy

This is the OS you said is working but shows no pertinent stuff, are you sure that it is this that is booting. To be honest I see no evidence that Ubuntu should boot at all from the script. Strange things happen though, so it is hard to decipher this altogether.

As far as clean up goes just move what you can't loose to a new partition an ntfs one for dual usage, and delete the rest that are not a working OS. Partition it how you want. I would be concerned with my setup if I had a booting OS from a partition that shows nothing but the partition type=ext3 Even if mounted the bootscript should show whats there.

---

### Post by The standard username on 2010-11-12
> **wilee-nilee said:**
> sdb4: _________________________________________________________________________

    ...are you sure that it is this that is booting. To be honest I see no evidence that Ubuntu should boot at all from the script. Strange things happen though, so it is hard to decipher this altogether.



No, I'm not very sure. I'm confused now too.  I don't understand what exactly happening,  menu.cfg sets (hd1,4) as root when loading linux   isn't that sdb?   

so would you please confirm to me if I understand this correctly.

hd0  means sda, right? always,   which means the first master hdd on sata controller? 
and hd1 means sdb , the second hard disk on the controller? 

I can't move much files, because the hard disks almost full.  so no much space left to move. but I want to prevent grub from detecting one of the OSes. perhaps by renaming a folder.   or deleting a file?  if you know how grub detects windows exactly, please let me know

I ll try to unplug one hard to see what exactly happening.    will post back hours later.

---

### Post by drs305 on 2010-11-12
I'd also recommend just purging all versions of grub and then reinstalling just Grub2.

If you ran the boot info script after a normal boot your default Ubuntu is on sda4. You can purge/reinstall without having to use the chroot procedure - just make sure you have a working Internet connection when you do it.

From a normally-booted Ubuntu:
Check to ensure you are using sda4 as root. sda4 should be mounted as "/":
```
mount | grep " / "
```
Purge grub, grub-pc (Grub 2):
You will be warned that you are removing the bootloader. Tab to OK and ENTER.
```
sudo apt-get purge grub
sudo apt-get purge grub-common  # Will uninstall grub-pc and grub-common

```
Install Grub2 (grub-common and grub-pc packages will be installed):
```
sudo apt-get install grub-pc
```
You will given the choice to add options to the kernel line. Unless you know of special options you previously had to include, tab to OK and press ENTER.
When given the option to set the MBR info, select "sda". Do not select "sda4".
You should see "update-grub" running at the end of the process. If you don't, manually run:
```
sudo update-grub
```

The unwanted Windows option will probably reappear. If so, exclude that partition as you did before. Yes it's a hack...

---

### Post by The standard username on 2010-11-13
Thanks for the detailed reply. 

I followed the procedure but here is what I found out.

the most recent linux that I'm using right now is on sdb4  not sda4.   sda4 however have ubuntu too but an older one.    regardless I continued to follow the procedure, but unsuprisingly the result was same as before. perhaps that grub2 on sda is trying to get files from the same sda hard disk which is the older linux that does not have grub2 files. 

so , is there a way to either: 1-easily transfer sdb4 linux to sda4.   or 2-force grub on sda to chain to grub on sdb.

also I don't know exactly why linux on sdb4 can't see the files on linux sda4.is there a way to make linux see the other linux, so that maybe I can transfer files?  

One more, do you think the duplicate UUID of the hard disk partitions can be a problem here?  Now, all hard disk 2 partitions UUIDs matches their counterpart in hard 1

thanks a lot for all the great help.

---

### Post by drs305 on 2010-11-13
Yes, you will need to change the UUIDs of each partition of the second drive so they don't match the ones on the other drive.

You can use the following command to change a partition's UUID. However, don't change the UUIDs until you have developed a plan on how you are going to get Grub 2 on the installation you desire. If you change the UUID on a system partition, it may not boot either because the Grub directory is no longer identified or the /etc/fstab file identifying / is incorrect.
```
sudo tune2fs -U random /dev/sdXY  # Example: sudo tune2fs -U random /dev/sda5
```

One method to get Grub2 installed on your newest partition would be to chroot into it. Since we don't know how old your old install is, you could do it from the LiveCD of the version you intend to use. Here are instructions on how to use "chroot" to install Grub2:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

There are other methods since you have at least one working Grub2 installation, but the above procedure will work for just about any type of setup you currently have. Additionally, if you use the LiveCD you can change all the UUIDs of your new Ubuntu's drive *before* you install Grub2.

As far as seeing files from another Linux partition, the other partition  may already be mounted - look in Nautilus's Places side bar or check to see what is mounted under /media.

If not, all you need to do is mount the partition  and then point your file browser to it. If you are running sda4 and want to see the files on sdb4, you would:
```
sudo mkdir /mnt/temp
sudo mount /dev/sdb4 /mnt/temp
gksu nautilus /mnt/temp
```
You would be running the browser as root, so file permissions and ownership may need to be changed.

If you need further clarification, it would be best to run the boot info script found below and post the contents of the RESULTS.txt the script generates.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by The standard username on 2010-11-13
thanks,

it seems it is mostly a UUID issue,  after I changed uuid of sda4,  now booting work from sda and I can boot to linux on sdb4 fine and I can also see the other linux files from places (;  thanks a lot.

However,   (sorry, I still have issues)

  (by the way my older linux on sda4 although old but  upgraded by mistake to 10.04, long story) so both 10.04

but now grub 2 writes the wrong UUID for that  sda4 linux.    although it says found 10.04 linux on sda4, instead of the new UUID , it writes the older UUID or the same UUID of sdb4.  

I tried sudo grub-mkconfig   and sudo update-grub    no avail
also I tried reconfigure grub-pc

===========================
So issue left:

 How to make grub writes the correct UUID.  or  use /dev/sda for other linux.


================


Never mind,  I went into the sda linux and uninstalled the old package left over of 8.04,  and installed grub2 there but without installation on mbr or anything.   then went back to sdb4 and did update-grub  and now uuid of sda is correct.

thanks a lot for the wonderful help.

---

