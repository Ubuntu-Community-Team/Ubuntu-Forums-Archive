---
title: "After Lucid install, can no longer boot from XP, missing file"
date: 2010-09-06
forum: General Help
---

### Post by lukashjanssen on 2010-09-06
I just installed Ubuntu 10.04. I'm dual-booting with Jaunty still as well as XP.
The problem is that I now cannot boot into XP. There wasn't a problem with this with Jaunty. I've read that Lucid rewrites the MBR and can mess us dual-booting machines. Sadly, I did not know this before upgrading. I did a fresh install from Live CD. I can access my files on the Windows partitions from both of the Ubuntu partitions, but I can't boot from XP itself.

---

### Post by drs305 on 2010-09-06
This should help you get your Windows back:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

It also works for 10.04.

---

### Post by lukashjanssen on 2010-09-06
I recently figured out that the reason why XP won't boot is because it cannot find the <Windows Boot>\system32\hal.dll file. There is a lot of info about this on the web, but I have no idea where to start or how to apply it to the Lucid install.

When I try to start the windows Recovery from GRUB it reaches a point where it says "Shutting down Windows to protect files" or something along those lines and then gives me the Technical reasons:

*** STOP: 0x00000024 (0x00190203, 0x82E2D0C8, 0xC0000102, 0x00000000)

Also, I got myself a Boot Info Script following this page: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897   c W95 FAT32 (LBA)
/dev/sda2    *     12,594,960   116,197,199   103,602,240   7 HPFS/NTFS
/dev/sda3         116,197,261   312,575,759   196,378,499   5 Extended
/dev/sda5         116,197,263   212,607,834    96,410,572  83 Linux
/dev/sda6         310,353,183   312,575,759     2,222,577  82 Linux swap / Solaris
/dev/sda7         212,609,024   308,131,839    95,522,816  83 Linux
/dev/sda8         308,133,888   310,351,871     2,217,984  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4295-037D                              vfat       PRESARIO_RP                   
/dev/sda2        09007DCC040D41B1                       ntfs       PRESARIO                      
/dev/sda5        09053764-477f-47e9-a34d-585fc9ea6513   ext3                                     
/dev/sda6        d9a528b0-6d54-4dba-b423-b799c6b52da1   swap                                     
/dev/sda7        78d89b64-5293-4e2c-bf81-906fb2d616d1   ext4                                     
/dev/sda8        9b1ad4cb-6f3c-4942-8a83-641a7c158302   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda2        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=09053764-477f-47e9-a34d-585fc9ea6513 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=09053764-477f-47e9-a34d-585fc9ea6513

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

title        Ubuntu 9.04, 2.6.28-19
uuid        09053764-477f-47e9-a34d-585fc9ea6513
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=09053764-477f-47e9-a34d-585fc9ea6513 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Microsoft Windows XP
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

title        Ubuntu 9.04, Recovery Mode
uuid        09053764-477f-47e9-a34d-585fc9ea6513
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=09053764-477f-47e9-a34d-585fc9ea6513 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, Memory Test
uuid        09053764-477f-47e9-a34d-585fc9ea6513
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title        Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
# title        Windows NT/2000/XP
# rootnoverify    (hd0,0)
# savedefault
# makeactive
# chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
# title        Microsoft Windows XP
# rootnoverify    (hd0,1)
# savedefault
# makeactive
# chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=09053764-477f-47e9-a34d-585fc9ea6513 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d9a528b0-6d54-4dba-b423-b799c6b52da1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# windows
/dev/sda2 /windows ntfs defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


  91.8GB: boot/grub/menu.lst
  91.7GB: boot/grub/stage2
  91.7GB: boot/initrd.img-2.6.28-11-generic
  91.7GB: boot/initrd.img-2.6.28-19-generic
  91.8GB: boot/vmlinuz-2.6.28-11-generic
  91.7GB: boot/vmlinuz-2.6.28-19-generic
  91.7GB: initrd.img
  91.7GB: initrd.img.old
  91.7GB: vmlinuz
  91.8GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 78d89b64-5293-4e2c-bf81-906fb2d616d1
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
search --no-floppy --fs-uuid --set 78d89b64-5293-4e2c-bf81-906fb2d616d1
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 78d89b64-5293-4e2c-bf81-906fb2d616d1
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=78d89b64-5293-4e2c-bf81-906fb2d616d1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 78d89b64-5293-4e2c-bf81-906fb2d616d1
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=78d89b64-5293-4e2c-bf81-906fb2d616d1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 78d89b64-5293-4e2c-bf81-906fb2d616d1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 78d89b64-5293-4e2c-bf81-906fb2d616d1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4295-037d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 09007dcc040d41b1
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04, 2.6.28-19 (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 09053764-477f-47e9-a34d-585fc9ea6513
    linux /boot/vmlinuz-2.6.28-19-generic root=UUID=09053764-477f-47e9-a34d-585fc9ea6513 ro quiet splash
    initrd /boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu 9.04, Recovery Mode (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 09053764-477f-47e9-a34d-585fc9ea6513
    linux /boot/vmlinuz-2.6.28-19-generic root=UUID=09053764-477f-47e9-a34d-585fc9ea6513 ro single
    initrd /boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu 9.04, Memory Test (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 09053764-477f-47e9-a34d-585fc9ea6513
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=78d89b64-5293-4e2c-bf81-906fb2d616d1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=9b1ad4cb-6f3c-4942-8a83-641a7c158302 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 151.9GB: boot/grub/core.img
 130.6GB: boot/grub/grub.cfg
 151.9GB: boot/initrd.img-2.6.32-21-generic
 151.9GB: boot/vmlinuz-2.6.32-21-generic
 151.9GB: initrd.img
 151.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by lukashjanssen on 2010-09-06
> **drs305 said:**
> This should help you get your Windows back:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

It also works for 10.04.

This didn't help for me because I do not have the Win XP disc.

---

### Post by lukashjanssen on 2010-09-07
bump

---

### Post by garvinrick4 on 2010-09-07
You have installed 10.04 with grub2 in sda7 so lets put grub2 in sda and then update-grub

I like to use labels when multiple installs so put in Live CD and boot it up 
Go into gparted and right click sda7 and label it lucid then apply it with green arrow.
These will put grub2 in the mbr.
```
sudo mkdir /media/lucid
``````
sudo mount /dev/sda7 /media/lucid
``````
sudo grub-install --recheck --root-directory=/media/lucid /dev/sda
``````
sudo umount /media/lucid
``````
sudo shutdown -r now
```Take out Cd and let it boot into lucid install. Open terminal
```
sudo update-grub
``````
sudo grub-mkconfig
```Should have all your installs in grub2 now. 

[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 

[GRUB 2 bootloader - Full tutorial]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459") 

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by wilee-nilee on 2010-09-07
> **lukashjanssen said:**
> This didn't help for me because I do not have the Win XP disc.

You do now.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

