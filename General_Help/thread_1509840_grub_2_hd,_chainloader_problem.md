---
title: "grub 2 hd, chainloader problem"
date: 2010-06-14
forum: General Help
---

### Post by mebinte on 2010-06-14
[SIZE=3]hey guys, 
A while back i installed ubuntu on a partition of my second HD (storage 1tb HD), Grub replaced windows bootloader and now, if i remove my 2hd from my computer, i cant access windows 7 on my 1st HD as well. I would like to reinstall windows 7 bootloader to the main hd and have ubuntu as an option (linking to the 2nd hd)

ATM i dont mind uninstallling Ubuntu (so i can reinstall a fresh 10.04 xD)

I tried easybcd to resintall windows bootloader but it only ends up modifying a bootloader in a bootloader(once i click win& in grub, then it takes me to win7 bootloader). Having 2Hd is probably confusing the program. 

Also, i dont understand the chain loader stuff. I used to see the entries under grub (menu.lst) and startup manager, including win7, but now its only 1 entry. ill try to gave as much info as possible below

[/SIZE]     [SIZE=3]sudo fdisk -l 
[/SIZE]```
[SIZE=3]Disk /dev/sda: 500.1 GB, 500107862016 bytes 
 [/SIZE][SIZE=3]255 heads, 63 sectors/track, 60801 cylinders 
 [/SIZE][SIZE=3]Units = cylinders of 16065 * 512 = 8225280 bytes 
 [/SIZE][SIZE=3]Disk identifier: 0x6d5f2042 
 
    [/SIZE][SIZE=3]Device Boot      Start         End      Blocks   Id  System 
 [/SIZE][SIZE=3]/dev/sda1               1          13      102400    7  HPFS/NTFS 
 [/SIZE][SIZE=3]Partition 1 does not end on cylinder boundary. 
 [/SIZE][SIZE=3]/dev/sda2   *          13       34421   276376576    7  HPFS/NTFS 
 [/SIZE][SIZE=3]Partition 2 does not end on cylinder boundary. 
 [/SIZE][SIZE=3]/dev/sda3           34421       60801   211901440    7  HPFS/NTFS 
 [/SIZE][SIZE=3]Partition 3 does not end on cylinder boundary. 
 
 [/SIZE][SIZE=3]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes 
 [/SIZE][SIZE=3]255 heads, 63 sectors/track, 121601 cylinders 
 [/SIZE][SIZE=3]Units = cylinders of 16065 * 512 = 8225280 bytes 
 [/SIZE][SIZE=3]Disk identifier: 0xb6434e34 
 
    [/SIZE][SIZE=3]Device Boot      Start         End      Blocks   Id  System 
 [/SIZE][SIZE=3]/dev/sdb1               1      109062   876039491    7  HPFS/NTFS 
 [/SIZE][SIZE=3]/dev/sdb2          109063      112989    31543627+   5  Extended 
 [/SIZE][SIZE=3]/dev/sdb3          112990      121601    69175296    7  HPFS/NTFS 
 [/SIZE][SIZE=3]/dev/sdb5          109063      112822    30202168+  83  Linux 
 [/SIZE][SIZE=3]/dev/sdb6          112823      112989     1341396   82  Linux swap / Solaris 
 [/SIZE]
```[FONT=Arial][SIZE=3]After sudo update-grub[/SIZE][/FONT][SIZE=3]
[/SIZE]```
[FONT=Arial][SIZE=3]
[/SIZE][/FONT] [SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]Searching for GRUB installation directory ... found: /boot/grub[/SIZE][/FONT][SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]
[/SIZE][/FONT] [SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]Searching for default file ... found: /boot/grub/default[/SIZE][/FONT][SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]
[/SIZE][/FONT] [SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst[/SIZE][/FONT][SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]
[/SIZE][/FONT] [SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]Searching for splash image ... none found, skipping ...[/SIZE][/FONT][SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]
[/SIZE][/FONT] [SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]Found kernel: /boot/vmlinuz-2.6.31-20-generic[/SIZE][/FONT][SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]
[/SIZE][/FONT] [SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]Found kernel: /boot/vmlinuz-2.6.31-17-generic[/SIZE][/FONT][SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]
[/SIZE][/FONT] [SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]Found GRUB 2: /boot/grub/core.img[/SIZE][/FONT][SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]
[/SIZE][/FONT] [SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]Found kernel: /boot/memtest86+.bin[/SIZE][/FONT][SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]
[/SIZE][/FONT] [SIZE=3]
 [/SIZE][FONT=Arial][SIZE=3]Updating /boot/grub/menu.lst ... done[/SIZE][/FONT][SIZE=3]
 

 [/SIZE]
```[FONT=Arial][SIZE=3]gksudo gedit /boot/grub/menu.lst[/SIZE][/FONT][SIZE=3]

```
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
#timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
...........
## ## End Default Options ##

[B]title        Ubuntu 9.10, kernel 2.6.32-22-generic
uuid        da333e2b-951d-49ba-ab98-4f354452479d
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=da333e2b-951d-49ba-ab98-4f354452479d ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic

title        Chainload into GRUB 2
root        da333e2b-951d-49ba-ab98-4f354452479d
kernel        /boot/grub/core.img[/B]

### END DEBIAN AUTOMAGIC KERNELS LIST
```[/SIZE]

---

### Post by mebinte on 2010-06-14
Current Grub Bootloader when i start computer

Ubuntu 2.631-17gen [COLOR=Red]->starts ubuntu[/COLOR]
""(recovermode)
Ubuntu 2.631-14gen [COLOR=Red]->does not work[/COLOR]
""(recovermode)
Memtest (memtest 86+)
"" ("", serial console 115200 )
windows 7 (loader) (on dev/sda1)[COLOR=Red] -> goes to win7bootloader[/COLOR]
windows 7 (loader) (on dev/sda 2)[COLOR=Red]->Starts win7[/COLOR]
windows vista (loader) (on /dev/sdb1)[COLOR=Red]->dont know why it is here, goes to diskerror (Press Ctrl+Alt+Del to restart)[/COLOR]

Also, under startupmanager, i cant make win7 on dev/sda 2 defult since it does not show on drop down (only shows 1st +chainloader). none of the options understartupmanager actually work like hide memtest or hide old entries

---

### Post by oldfred on 2010-06-14
I would just install grub2 to sdb and reinstall windows boot loader to sda and set sdb to boot in BIOS.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

You can use windows repairs fixMBR to restore the windows boot or from Ubuntu:
sudo  apt-get install lilo
sudo lilo -M /dev/sda mbr
per kansasnoob Note: If I use Lilo to restore a Windows MBR using my "installed" Ubuntu I always like to remove the package "lilo" when done just to prevent some later "conflict" with grub updates, this of course is as easy as "sudo apt-get remove lilo".

---

### Post by mebinte on 2010-06-14
did some, research on how to post grub. before i try ur method, can u read below to see if it will still work/still most efficient?

Results .txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=da333e2b-951d-49ba-ab98-4f354452479d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #1815177216 on boot drive #1
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #1815177216 on boot drive #1
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6d5f2042

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2    *        206,848   552,959,999   552,753,152   7 HPFS/NTFS
/dev/sda3         552,962,048   976,764,927   423,802,880   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb6434e34

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,752,081,029 1,752,078,982   7 HPFS/NTFS
/dev/sdb2       1,752,081,030 1,815,168,284    63,087,255   5 Extended
/dev/sdb5       1,752,081,093 1,812,485,429    60,404,337  83 Linux
/dev/sdb6       1,812,485,493 1,815,168,284     2,682,792  82 Linux swap / Solaris
/dev/sdb3       1,815,169,024 1,953,519,615   138,350,592   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6886D10286D0D224                       ntfs       System Reserved               
/dev/sda2        123EE88B3EE86965                       ntfs                                     
/dev/sda3        7042814242810DD2                       ntfs       download                      
/dev/sdb1        AC2A960C2A95D424                       ntfs       storage                       
/dev/sdb3        20BE63B8BE63855E                       ntfs       STORE2                        
/dev/sdb5        da333e2b-951d-49ba-ab98-4f354452479d   ext4                                     
/dev/sdb6        d1add834-2781-425c-802b-609547d831ee   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/123EE88B3EE86965  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(3)\windows 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\windows="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/menu.lst: ===========================

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
#timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=da333e2b-951d-49ba-ab98-4f354452479d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=da333e2b-951d-49ba-ab98-4f354452479d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.32-22-generic
uuid        da333e2b-951d-49ba-ab98-4f354452479d
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=da333e2b-951d-49ba-ab98-4f354452479d ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic

title        Chainload into GRUB 2
root        da333e2b-951d-49ba-ab98-4f354452479d
kernel        /boot/grub/core.img

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set da333e2b-951d-49ba-ab98-4f354452479d
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set da333e2b-951d-49ba-ab98-4f354452479d
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=da333e2b-951d-49ba-ab98-4f354452479d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set da333e2b-951d-49ba-ab98-4f354452479d
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=da333e2b-951d-49ba-ab98-4f354452479d ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set da333e2b-951d-49ba-ab98-4f354452479d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=da333e2b-951d-49ba-ab98-4f354452479d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set da333e2b-951d-49ba-ab98-4f354452479d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=da333e2b-951d-49ba-ab98-4f354452479d ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6886d10286d0d224
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 123ee88b3ee86965
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set ac2a960c2a95d424
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=da333e2b-951d-49ba-ab98-4f354452479d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=d1add834-2781-425c-802b-609547d831ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 901.2GB: boot/grub/core.img
 901.3GB: boot/grub/grub.cfg
 901.0GB: boot/grub/menu.lst
 898.1GB: boot/initrd.img-2.6.31-17-generic
 898.6GB: boot/initrd.img-2.6.32-22-generic
 897.9GB: boot/vmlinuz-2.6.31-17-generic
 898.6GB: boot/vmlinuz-2.6.32-22-generic
 898.6GB: initrd.img
 898.6GB: vmlinuz
```

---

### Post by oldfred on 2010-06-14
I do not know about your easyBCD. You have it installed in the windows partitions sda1 & sda2, sdb1 has this file from grub4dos - /grldr. And your have menu.lst from grub legacy in sdb5.

    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #1815177216 on boot drive #1


With all these boot loaders they are conflicting with each other.

You probalby can use test disk to recover the windows boot sectors unles easyBCD has instructions on how to uninstall.

Fix for most, a few have other issues, you also need to run on both sda1 & sda2:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

From your Ubuntu liveCD you can reinstall grub2 to sdb.

sudo mkdir /mnt/sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

If you set sdb to boot in BIOS and remove the menu.lst in /boot/grub you should be able to get into Ubuntu. If not we may have to totally uninstall grub legacy and reinstall grub2.

If the testdisk repair does not work you have to run fixboot from windows. Slightly different for XP and vista/7
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by mebinte on 2010-06-14
i was using vistaboot pro and accidently added some loader into hd 2
from what i know when i boot into windows 7
sda2=windows 7
sda1=system reserved (100mb) this is where win 7 boot loader is
i need to only get rid of vista/win7loaders on sdb1&sdb3...ill try test disk on those 2. can i also remove the loader from sda1 and put it into my win7 HD (sda2)?

---

### Post by mebinte on 2010-06-14
k, i did
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo apt-get remove lilo

it rebooted right into my win7 :p. i tried selecting sdb at bios on startup and it also booted into win7 (mbr on each hd that boots into win7)
since i coulnt boot into ubuntu, i deleted the volumes from disk management and then made 2 partitions for it when i reinstall 10.04
i want to get this right this time around; how do i reinstall 10.04lts on drive J and grub on sdb aswell. is there an option to make sure grub installs on sdb?
should i disconnect my sda and then install ubuntu on the 1tb partition?
[IMG]http://i706.photobucket.com/albums/ww63/SogeSoga/u2.jpg[/IMG]

---

### Post by mebinte on 2010-06-14
bump

---

### Post by oldfred on 2010-06-14
Unless you install wubi you cannot install to NTFS partitions and you either have to delete them or at least reformat them.

The important thing with multiple drives is the advanced button that lets you choose which drive to install grub to. Just install to sdb, often the default is to the boot drive which is sda. After installing grub to sdb, go into BIOS and change boot to sdb -1000GB drive. Windows seems to show them reversed. Disk 0 is the 1000GB drive. Not sure why.

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by mebinte on 2010-06-16
k thnks man, i got it to work :guitar:

---

