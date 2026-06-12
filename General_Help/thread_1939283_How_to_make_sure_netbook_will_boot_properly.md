---
title: "How to make sure netbook will boot properly?"
date: 2012-03-11
forum: General Help
---

### Post by sheptown on 2012-03-11
I have a Toshiba Netbook with 1 GB ram. It has Win7 starter on it.  I had successfully installed Ubuntu inside Windoze with Wubi a year or so ago. It ran fine and I was happy with it.  A couple of days ago, I decided to accept the various updates that were offered.  I got the message that to complete the update, I needed to reboot.  So I went ahead with that only to eventually get this message:

"Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/9C52D22B52D20A42 does not exist. Dropping to a shell!

BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) "

I did some googling about this, tried various things (including uninstalling the Ubuntu inside of Doze and then installing the current version  - but got same results -except for different number after 'by-uuid') and then decided maybe the way to go was to go ahead and just install Ubuntu as a separate system rather than inside Windoze.  The install appeared to go fine, but again, when I tried to boot I got the BusyBox - (initramfs) message.  Then I decided to try a different Linux - this time installing Linux Mint 12.  Same results.  Install seemed to go fine - but couldn't boot and again got the BusyBox - (initramfs) message.  

Again tried to boot the Ubuntu. I started typing stuff at the '(initramfs)' prompt, various commands which were given in 'help' and then just random letters and ctrl-c and esc - and whatever I could think of, not really expecting anything to do any good.  But then, all of a sudden, Ubuntu started to boot.  And it's running just fine. And now I'm afraid to shut it down.
[COLOR=DarkOrange]
**[COLOR=Black]SO - My question is, what do I need to do to make sure that it will boot properly the next time?[/COLOR]**[/COLOR]

I went to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and have pasted the RESULTS.txt file below.


```





============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 1083. But according to the info from fdisk, 
                       sda8 starts at sector 370219008.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 12 LXDE
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda14: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   179,910,447   176,836,400   7 NTFS / exFAT / HPFS
/dev/sda3         179,910,654   472,815,615   292,904,962   f W95 Extended (LBA)
/dev/sda5         242,243,647   244,348,649     2,105,003  82 Linux swap / Solaris
/dev/sda6         244,348,713   286,310,429    41,961,717  83 Linux
/dev/sda7         286,310,493   370,217,924    83,907,432  83 Linux
/dev/sda8         370,219,008   402,128,356    31,909,349   7 NTFS / exFAT / HPFS
/dev/sda9         179,910,656   239,583,231    59,672,576  83 Linux
/dev/sda10        239,585,280   242,227,199     2,641,920  82 Linux swap / Solaris
/dev/sda11        452,141,056   470,738,943    18,597,888  83 Linux
/dev/sda12        470,740,992   472,815,615     2,074,624  82 Linux swap / Solaris
/dev/sda13        402,128,896   450,056,191    47,927,296  83 Linux
/dev/sda14        450,058,240   452,132,863     2,074,624  82 Linux swap / Solaris
/dev/sda4         472,815,616   488,396,799    15,581,184  17 Hidden NTFS / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        7EECAC8FECAC42EF                       ntfs       System
/dev/sda10       b1401201-9e81-4bb7-b4c3-5eb9dd1f0c23   swap       
/dev/sda11       88037590-6d75-4b3f-b643-060e819d9ac7   ext4       
/dev/sda12       d499aaaf-e6eb-4858-bcc0-8ab2a6ab3c34   swap       
/dev/sda13       a6d7f43f-c73a-44b9-ab2f-46de74a87042   ext4       
/dev/sda14       05fee5fa-d43f-4d8a-9a52-4651480e0d66   swap       
/dev/sda2        9C52D22B52D20A42                       ntfs       TI103127W0E
/dev/sda4        4844F79B44F78A48                       ntfs       HDDRECOVERY
/dev/sda5        b7ca924a-2132-472d-ac81-783b0f295379   swap       
/dev/sda6        f500f62a-6d7c-4edf-965c-78a4bf113090   ext2       
/dev/sda7        cd8c147d-e9ec-4a2b-adbd-79d516b712ba   ext2       
/dev/sda8        1000D7CE00D7B8C4                       ntfs       New Volume
/dev/sda9        d6904402-b777-4211-80f0-bafbb8c60188   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda11       /media/88037590-6d75-4b3f-b643-060e819d9ac7 ext4       (rw,nosuid,nodev,commit=0,commit=0,commit=0,uhelper=udisks)
/dev/sda13       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/TI103127W0E       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
##  default             0
default         saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=649ca757-56cd-4634-be9e-fd9d8c81ec92 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=649ca757-56cd-4634-be9e-fd9d8c81ec92

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

###  title              Ubuntu 9.04, kernel 2.6.30.5-ep0
###  uuid               649ca757-56cd-4634-be9e-fd9d8c81ec92
###  kernel             /boot/vmlinuz-2.6.30.5-ep0 root=UUID=649ca757-56cd-4634-be9e-fd9d8c81ec92 ro quiet splash
###  initrd             /boot/initrd.img-2.6.30.5-ep0
###  quiet

title           Ubuntu 9.04, kernel 2.6.30.5-ep0
##  root (hd0,5)
uuid    f500f62a-6d7c-4edf-965c-78a4bf113090
### kernel              /boot/vmlinuz-2.6.30.5-ep0 root=/dev/sda6 ro quiet splash
kernel          /boot/vmlinuz-2.6.30.5-ep0 root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro quiet splash
initrd          /boot/initrd.img-2.6.30.5-ep0
quiet
savedefault

title           Ubuntu 9.04, kernel 2.6.30.5-ep0 (recovery mode)
uuid            f500f62a-6d7c-4edf-965c-78a4bf113090
kernel          /boot/vmlinuz-2.6.30.5-ep0 root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro  single
initrd          /boot/initrd.img-2.6.30.5-ep0

title           Ubuntu 9.04, memtest86+
uuid            f500f62a-6d7c-4edf-965c-78a4bf113090
kernel          /boot/memtest86+.bin
quiet

title           Ubuntu 9.04, == UNR == kernel 2.6.32
uuid            f500f62a-6d7c-4edf-965c-78a4bf113090
kernel          /boot/vmlinuz-2.6.32-02063202-generic root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
initrd          /boot/initrd.img-2.6.30.5-ep0
## quiet

title           Ubuntu 9.04, kernel 2.6.35 TEST Quietly
uuid            f500f62a-6d7c-4edf-965c-78a4bf113090
kernel          /boot/vmlinuz-2.6.35-rc3-ATOM root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
initrd          /boot/initrd.img-2.6.30.5-ep0
quiet

title           Ubuntu 9.04, kernel 2.6.35 TEST
uuid            f500f62a-6d7c-4edf-965c-78a4bf113090
kernel          /boot/vmlinuz-2.6.35-rc3-ATOM root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
initrd          /boot/initrd.img-2.6.30.5-ep0
## quiet

title           Ubuntu 9.04, kernel 2.6.34
uuid            f500f62a-6d7c-4edf-965c-78a4bf113090
kernel          /boot/vmlinuz-2.6.34-rc2-NETBOOK root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
initrd          /boot/initrd.img-2.6.30.5-ep0
quiet

title           Ubuntu 9.04, kernel 2.6.33
uuid            f500f62a-6d7c-4edf-965c-78a4bf113090
kernel          /boot/vmlinuz-2.6.33-NETBOOK root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
initrd          /boot/initrd.img-2.6.30.5-ep0
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title           Windows Vista (loader)
rootnoverify    (hd0,3)
savedefault
chainloader     +1


--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
##  set root='(hd0,msdos6)'
##  search --no-floppy --fs-uuid --set d5856335-4466-4a55-8bee-bc0cc6e50d9e
##  if loadfont /share/grub/unicode.pf2 ; then
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
if loadfont /grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'TESTME  Debian GNU/Linux, with Linux 2.6.39-rc3-ATOM' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    echo    'Loading Linux 2.6.39-rc3-ATOM-00082-g85f2e68-dirty ...'
    linux    /vmlinuz-2.6.39-rc3-ATOM-00082-g85f2e68-dirty root=/dev/sda5 ro  rootwait
}
menuentry 'Debian GNU/Linux, with Linux 2.6.39-rc3-ATOM (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    echo    'Loading Linux 2.6.39-rc3-ATOM-00082-g85f2e68-dirty ...'
    linux    /vmlinuz-2.6.39-rc3-ATOM-00082-g85f2e68-dirty root=/dev/sda5 ro single  rootwait
}
menuentry 'Debian GNU/Linux, with Linux 2.6.37-ATOM+' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    echo    'Loading Linux 2.6.37-ATOM+ ...'
    linux    /vmlinuz-2.6.37-ATOM+ root=/dev/sda5 ro  rootwait
}
menuentry 'Debian GNU/Linux, with Linux 2.6.37-ATOM+ (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    echo    'Loading Linux 2.6.37-ATOM+ ...'
    linux    /vmlinuz-2.6.37-ATOM+ root=/dev/sda5 ro single  rootwait
}
menuentry 'Debian GNU/Linux, with Linux 2.6.36-ATOM+' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    echo    'Loading Linux 2.6.36-ATOM+ ...'
    linux    /vmlinuz-2.6.36-ATOM+ root=/dev/sda5 ro  rootwait
}
menuentry 'Debian GNU/Linux, with Linux 2.6.36-ATOM+ (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    echo    'Loading Linux 2.6.36-ATOM+ ...'
    linux    /vmlinuz-2.6.36-ATOM+ root=/dev/sda5 ro single  rootwait
}
menuentry 'Debian GNU/Linux, with Linux 2.6.35-rc6-PIII+' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    echo    'Loading Linux 2.6.35-rc6-PIII+ ...'
    linux    /vmlinuz-2.6.35-rc6-PIII+ root=/dev/sda5 ro  rootwait
}
menuentry 'Debian GNU/Linux, with Linux 2.6.35-rc6-PIII+ (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    echo    'Loading Linux 2.6.35-rc6-PIII+ ...'
    linux    /vmlinuz-2.6.35-rc6-PIII+ root=/dev/sda5 ro single  rootwait
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86 ###
menuentry "Memory test (memtest86)" {
    linux16    /memtest86.bin
}
### END /etc/grub.d/20_memtest86 ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    multiboot    /memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa577aed-270e-4b8e-8be6-d0f47f645091
    multiboot    /memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 186248dd6248c16c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### ADDED by hand
menuentry "NetBSD fix me" {
    insmod part_msdos
    insmod ufs1
    set root='(hd0,msdos3)'
    #FiX  search --no-floppy --fs-uuid --set 186248dd6248c16c
    #FiX  drivemap -s (hd0) ${root}
    # GET A WORKING KERNEL
    multiboot /netbsd
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
### OLD   UUID=649ca757-56cd-4634-be9e-fd9d8c81ec92 /               ext2    noatime,errors=remount-ro 0       1
###  /dev/sda6 /               ext2    noatime,errors=remount-ro 0       1
###  /dev/sda7 /home               ext2    noatime,errors=remount-ro 0       1
UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 /               ext2    noatime,errors=remount-ro 0       1
UUID=cd8c147d-e9ec-4a2b-adbd-79d516b712ba /home               ext2    noatime,errors=remount-ro 0       1
# settings added by eeepc-tweaks
tmpfs        /tmp        tmpfs    defaults,noatime,mode=1777    0 0
##REAL FS  tmpfs        /var/tmp    tmpfs    defaults,noatime,mode=1777    0 0
##REAL FS  tmpfs        /var/log    tmpfs    defaults,noatime,mode=0755    0 0
UUID=b7ca924a-2132-472d-ac81-783b0f295379    none swap sw
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               2
               =                boot/initrd.img-2.6.30.5-ep0                   3
               =                boot/vmlinuz-2.6.30.5-ep0                      2
               =                boot/vmlinuz-2.6.32-02063202-generic           2
               =                boot/vmlinuz-2.6.33-NETBOOK                    2
               =                boot/vmlinuz-2.6.34-rc2-NETBOOK                2
               =                boot/vmlinuz-2.6.35-rc3-ATOM                   2
               =                boot/vmlinuz-2.6.35-rc3-PII                    2
               =                boot/vmlinuz-2.6.39-rc3-ATOM-00082-g85f2e68-dirty  2
               =                initrd.gz                                      3
               =                initrd.img                                     3
               =                vmlinuz                                        2

=========================== sda9/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd1,msdos9)'
search --no-floppy --fs-uuid --set d6904402-b777-4211-80f0-bafbb8c60188
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos9)'
search --no-floppy --fs-uuid --set d6904402-b777-4211-80f0-bafbb8c60188
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

## ADDED BY HAND 03.05.2011 to restore sanity and EZPZ with my newer kernel
menuentry "EZPZ - kernel 2.6.39-ATOM (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.39-rc3-ATOM-00082-g85f2e68-dirty root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro quiet splash
    initrd /boot/initrd.img-2.6.30.5-ep0
}
menuentry "EZPZ - kernel 2.6.39-ATOM Verbose booting (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.39-rc3-ATOM-00082-g85f2e68-dirty root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro splash
    initrd /boot/initrd.img-2.6.30.5-ep0
}
menuentry "EZPZ, kernel 2.6.39-ATOM (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.39-rc3-ATOM-00082-g85f2e68-dirty root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
    initrd /boot/initrd.img-2.6.30.5-ep0
}
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set d6904402-b777-4211-80f0-bafbb8c60188
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d6904402-b777-4211-80f0-bafbb8c60188 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set d6904402-b777-4211-80f0-bafbb8c60188
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d6904402-b777-4211-80f0-bafbb8c60188 ro single 
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
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set d6904402-b777-4211-80f0-bafbb8c60188
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set d6904402-b777-4211-80f0-bafbb8c60188
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 7eecac8fecac42ef
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 9c52d22b52d20a42
    chainloader +1
}
menuentry "Windows Vista OR NOT (loader) (on /dev/sdb4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set 4844f79b44f78a48
    chainloader +1
}
menuentry "EZPZ - kernel 2.6.30.5-ep0 (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.30.5-ep0 root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro quiet splash
    initrd /boot/initrd.img-2.6.30.5-ep0
}
menuentry "EZPZ, kernel 2.6.30.5-ep0 (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.30.5-ep0 root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
    initrd /boot/initrd.img-2.6.30.5-ep0
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, == UNR == kernel 2.6.32 (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.32-02063202-generic root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
    initrd /boot/initrd.img-2.6.30.5-ep0
}
menuentry "Ubuntu 9.04, kernel 2.6.35 TEST Quietly (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.35-rc3-ATOM root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
    initrd /boot/initrd.img-2.6.30.5-ep0
}
menuentry "Ubuntu 9.04, kernel 2.6.35 TEST (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.35-rc3-ATOM root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
    initrd /boot/initrd.img-2.6.30.5-ep0
}
menuentry "Ubuntu 9.04, kernel 2.6.34 (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.34-rc2-NETBOOK root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
    initrd /boot/initrd.img-2.6.30.5-ep0
}
menuentry "Ubuntu 9.04, kernel 2.6.33 (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.33-NETBOOK root=UUID=f500f62a-6d7c-4edf-965c-78a4bf113090 ro single
    initrd /boot/initrd.img-2.6.30.5-ep0
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
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=d6904402-b777-4211-80f0-bafbb8c60188 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb10 during installation
UUID=b1401201-9e81-4bb7-b4c3-5eb9dd1f0c23 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.35-22-generic              2
               =                boot/vmlinuz-2.6.35-22-generic                 1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========================== sda11/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set=root 88037590-6d75-4b3f-b643-060e819d9ac7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos11)'
  search --no-floppy --fs-uuid --set=root 88037590-6d75-4b3f-b643-060e819d9ac7
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Linux Mint 12 LXDE, 3.0.0-12-generic (/dev/sda11)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 88037590-6d75-4b3f-b643-060e819d9ac7
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=88037590-6d75-4b3f-b643-060e819d9ac7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Linux Mint 12 LXDE, 3.0.0-12-generic (/dev/sda11) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 88037590-6d75-4b3f-b643-060e819d9ac7
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=88037590-6d75-4b3f-b643-060e819d9ac7 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 88037590-6d75-4b3f-b643-060e819d9ac7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 88037590-6d75-4b3f-b643-060e819d9ac7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 7EECAC8FECAC42EF
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 9C52D22B52D20A42
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 4844F79B44F78A48
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.gz
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.img
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.img
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.30.5-ep0 root=/dev/sda6
    initrd /boot/initrd.img-2.6.30.5-ep0
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.32-02063202-generic root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.33-NETBOOK root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.34-rc2-NETBOOK root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.35-rc3-ATOM root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.35-rc3-PII root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.39-rc3-ATOM-00082-g85f2e68-dirty root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.gz
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.img
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root d6904402-b777-4211-80f0-bafbb8c60188
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d6904402-b777-4211-80f0-bafbb8c60188 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root d6904402-b777-4211-80f0-bafbb8c60188
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d6904402-b777-4211-80f0-bafbb8c60188 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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
--------------------------------------------------------------------------------

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=88037590-6d75-4b3f-b643-060e819d9ac7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=d499aaaf-e6eb-4858-bcc0-8ab2a6ab3c34 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========================== sda13/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos13)'
search --no-floppy --fs-uuid --set=root a6d7f43f-c73a-44b9-ab2f-46de74a87042
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos13)'
  search --no-floppy --fs-uuid --set=root a6d7f43f-c73a-44b9-ab2f-46de74a87042
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set=root a6d7f43f-c73a-44b9-ab2f-46de74a87042
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a6d7f43f-c73a-44b9-ab2f-46de74a87042 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set=root a6d7f43f-c73a-44b9-ab2f-46de74a87042
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a6d7f43f-c73a-44b9-ab2f-46de74a87042 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set=root a6d7f43f-c73a-44b9-ab2f-46de74a87042
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set=root a6d7f43f-c73a-44b9-ab2f-46de74a87042
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 7EECAC8FECAC42EF
    chainloader +1
}
menuentry "Linux Mint 12 LXDE, 3.0.0-12-generic (/dev/sda11) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 88037590-6d75-4b3f-b643-060e819d9ac7
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=88037590-6d75-4b3f-b643-060e819d9ac7 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Linux Mint 12 LXDE, 3.0.0-12-generic (/dev/sda11) -- recovery mode (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root 88037590-6d75-4b3f-b643-060e819d9ac7
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=88037590-6d75-4b3f-b643-060e819d9ac7 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 9C52D22B52D20A42
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 4844F79B44F78A48
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.gz
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.img
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.img
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.30.5-ep0 root=/dev/sda6
    initrd /boot/initrd.img-2.6.30.5-ep0
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.32-02063202-generic root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.33-NETBOOK root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.34-rc2-NETBOOK root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.35-rc3-ATOM root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.35-rc3-PII root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /boot/vmlinuz-2.6.39-rc3-ATOM-00082-g85f2e68-dirty root=/dev/sda6
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.gz
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.img
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f500f62a-6d7c-4edf-965c-78a4bf113090
    linux /vmlinuz root=/dev/sda6
    initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root d6904402-b777-4211-80f0-bafbb8c60188
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d6904402-b777-4211-80f0-bafbb8c60188 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root d6904402-b777-4211-80f0-bafbb8c60188
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d6904402-b777-4211-80f0-bafbb8c60188 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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
--------------------------------------------------------------------------------

=============================== sda13/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda13 during installation
UUID=a6d7f43f-c73a-44b9-ab2f-46de74a87042 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda14 during installation
UUID=05fee5fa-d43f-4d8a-9a52-4651480e0d66 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda13: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 41 20  b7 03 ab 1e 20 00 00 fe  |......A .... ...|
000001d0  ff ff 05 fe ff ff ec 3e  d7 03 34 49 80 02 00 00  |.......>..4I....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda5

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in

# Deteted a bunch more of these same lines


awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in







```

---

### Post by Frogs Hair on 2012-03-11
```

File system:       ext2
    Boot sector type:  -
    Boot sector info:  
   _ Operating System:  Ubuntu 9.04_
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

```

If You can run a newer version of Ubuntu backup your files and install a newer version . 9.04 is no longer supported.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by sheptown on 2012-03-11
> **Frogs Hair said:**
> ```

File system:       ext2
    Boot sector type:  -
    Boot sector info:  
   _ Operating System:  Ubuntu 9.04_
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

```If You can run a newer version of Ubuntu backup your files and install a newer version . 9.04 is no longer supported.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)


Yes, it may say that, but I just downloaded the newest version - 11.10 - and that is what I installed the other day.  I just now did:

lsb_release -a

and got Release 11.10  Codename: oneiric

I'm guessing the 9.04 quoted above is leftover from when I had an earlier Ubuntu installed within Windows, using Wubi.  Further into the copy of the RESULTS.txt that I pasted into the message can be seen:

sda13: _____________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

---

### Post by Frogs Hair on 2012-03-11
Take a look at the Wubi mega thread if you haven't already . [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by sheptown on 2012-03-11
> **Frogs Hair said:**
> Take a look at the Wubi mega thread if you haven't already . [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Thank you.  I have just taken a look at that thread.

Though I did initially have Wubi when I was earlier using the Ubuntu 9.04, I did uninstall the Ubuntu within the  Windows - and now see no sign of anything similar to what's pasted below and which the thread said "a Windows partition with a Wubi install would look like this." This leads me to think it is not a Wubi issue.

```

[COLOR=Red]sda3[/COLOR]: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows 7     Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr                         /ubuntu/winboot/wubildr.mbr /wubildr                         /ubuntu/winboot/wubildr /ubuntu/disks/root.disk                         /ubuntu/disks/swap.disk


```

---

