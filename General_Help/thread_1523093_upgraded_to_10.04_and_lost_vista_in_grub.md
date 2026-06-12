---
title: "upgraded to 10.04 and lost vista in grub"
date: 2010-07-03
forum: General Help
---

### Post by Nomadjackalope on 2010-07-03
I am a linux noob and have been searching for a couple months to a fix for my problem but now I just need help.

I have two hard drives. One with vista and the other with ubuntu, storage space, and some other partition. I was dual booting windows and ubuntu jaunty jackalope then one day I decided it would be fun to upgrade to 10.04 so I did. When I tried loading windows from grub it just showed a blinking cursor forever. And while attempting to fix the problem by adding windows to the grub menu.lst file it dissapeared from the grub options. Help!

results for sudo fdisk -l

```
ben@ben-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x208196fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           11155       23211    96847852+   7  HPFS/NTFS
/dev/sdb2           23213       24321     8908042+   c  W95 FAT32 (LBA)
/dev/sdb3               1       11154    89594473+  83  Linux

Partition table entries are not in disk order
```

results for sudo update-grub

```
ben@ben-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

Thank you!!:D

---

### Post by Darkness Des on 2010-07-03
1: menu.lst does not exist anymore. In GRUB2, you have various little config files that compile into one big one when you run update-grub.
2: I need you to go ahead and post the output of the boot info script, located below.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Nomadjackalope on 2010-07-03
So I'm a real noob ha ha I don't want to waste your time but why is it

ben@ben-desktop:~$ sudo bash boot_info_script055.sh
[sudo] password for ben: 
bash: boot_info_script055.sh: No such file or directory
ben@ben-desktop:~$
 
am I doing something wrong? well apparently
I saved it to the desktop and then did that

---

### Post by Darkness Des on 2010-07-03
Close.
```

chmod +x boot_info_script055.sh
sudo ./boot_info_script055.sh

```./ means to use the file in the current directory, otherwise BASH will think it's a command.

EDIT:
I forgot to mention, post the contents of the results.txt file it generates here.

---

### Post by Nomadjackalope on 2010-07-03
Thank you!! I got it this time.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 272135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 272135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb3 and 
                       looks at sector 272135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         179,189,010   372,884,714   193,695,705   7 HPFS/NTFS
/dev/sdb2         372,900,780   390,716,864    17,816,085   c W95 FAT32 (LBA)
/dev/sdb3                  63   179,189,009   179,188,947  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8CB6354AB63535D4                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6666E90066E8D23B                       ntfs       HP_PAVILION                   
/dev/sdb2        4B6E-6BC0                              vfat       HP_RECOVERY                   
/dev/sdb3        bf3be40f-23e0-4a09-9ad7-db31608b1c67   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro)


================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sdb3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout        3

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
# kopt=root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bf3be40f-23e0-4a09-9ad7-db31608b1c67

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Chainload into GRUB 2
root        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/memtest86+.bin



### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows Vista Ultimate
root        (hd1,0)
makeactive
chainloader    +1

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
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
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb2)" {
    insmod fat
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 4b6e-6bc0
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   3.0GB: boot/grub/grub.cfg
    .3GB: boot/grub/menu.lst
   1.2GB: boot/initrd.img-2.6.31-21-generic
  30.1GB: boot/initrd.img-2.6.32-22-generic
    .7GB: boot/vmlinuz-2.6.31-21-generic
  15.0GB: boot/vmlinuz-2.6.32-22-generic
  30.1GB: initrd.img
   1.2GB: initrd.img.old
  15.0GB: vmlinuz
    .7GB: vmlinuz.old
```

---

### Post by Darkness Des on 2010-07-03
Thanks, that helps alot. Is Vista installed in /dev/sdb2? Or at least, the boot loader?

---

### Post by Nomadjackalope on 2010-07-03
I don't think so. I installed vista on the Disk /dev/sda before I put the second hard drive in my computer. so unless while I have been trying to fix this problem I have somehow moved the boot loader then it shouldn't be there.

---

### Post by Darkness Des on 2010-07-03
Hmmm.... It looks to me like some of the Windows Configuration files are there. I don't know how, but I do know how to fix it. Go ahead and run
```

sudo aptitude install testdisk

```
```

sudo testdisk

```

Select your log file preference, and browse through the menus and restore the MBR of /dev/sdb2 and you should be good to go.

---

### Post by last1home on 2010-07-03
Go Synaptic Package Manager>type GRUB in Search>.locate GRUB-PC which should already  be installed.>Right click on it and mark for Re-Installation>Apply and maybe Bob's yer uncle

---

### Post by Nomadjackalope on 2010-07-03
Ok so the test disk thing felt like it was working but I couldn't see grub on the menu. I installed grub-pc because it wasn't installed so I was feeling good and restarted and tried to boot to vista and there was the blinking cursor again. so thank you for helping me fix the mistakes I created trying to fix it but now it's back to that blinking cursor...
?

---

### Post by Mark Phelps on 2010-07-03
Looks like you have two physical drives with Vista installed on the first one.

As a test, I would disconnect the second drive and confirm that Vista still boots OK with only the first drive connected.  That will at least narrow down the problem to being one with GRUB, not with Vista as well.

---

### Post by Nomadjackalope on 2010-07-04
I have disabled the second drive through bios and tried booting up but nothing happens. I'll look into this more. I haven't tried physically unplugging the second one and booting w/o vista cd but when I do it just has the last cursor of the "Do you want to boot from the cd_ _ _ _" thing keep blinking.

I don't remember if I said that I had tried bootrec /fixmbr and bootrec /fixboot... just more info for you.

---

### Post by Nomadjackalope on 2010-07-05
When I tried using just the 1st disk that I though was the windows hard drive. when it booted up all I got was this doesn't exist and a mac address. then it said grub something with a ">" 
I guess that means grub is on there too? I don't know how this all works...

---

### Post by wilee-nilee on 2010-07-05
Run the bootscript again, it has been several days and some fixes have been run. Testdisk probably was the answer but the corresponding page and instructions were not included.

---

### Post by Nomadjackalope on 2010-07-06
I tried it again I don't know if it's any different but I used the download in your sig thing below your post.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 272135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 272135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb3 and 
                       looks at sector 272135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         179,189,010   372,884,714   193,695,705   7 HPFS/NTFS
/dev/sdb2         372,900,780   390,716,864    17,816,085   c W95 FAT32 (LBA)
/dev/sdb3                  63   179,189,009   179,188,947  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8CB6354AB63535D4                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6666E90066E8D23B                       ntfs       HP_PAVILION                   
/dev/sdb2        4B6E-6BC0                              vfat       HP_RECOVERY                   
/dev/sdb3        bf3be40f-23e0-4a09-9ad7-db31608b1c67   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro)


================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sdb3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout        3

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
# kopt=root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bf3be40f-23e0-4a09-9ad7-db31608b1c67

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Chainload into GRUB 2
root        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        bf3be40f-23e0-4a09-9ad7-db31608b1c67
kernel        /boot/memtest86+.bin



### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows Vista Ultimate
root        (hd1,0)
makeactive
chainloader    +1

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
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
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bf3be40f-23e0-4a09-9ad7-db31608b1c67
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb2)" {
    insmod fat
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 4b6e-6bc0
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=bf3be40f-23e0-4a09-9ad7-db31608b1c67 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   3.0GB: boot/grub/grub.cfg
    .3GB: boot/grub/menu.lst
   1.2GB: boot/initrd.img-2.6.31-21-generic
  30.1GB: boot/initrd.img-2.6.32-22-generic
    .7GB: boot/vmlinuz-2.6.31-21-generic
  15.0GB: boot/vmlinuz-2.6.32-22-generic
  30.1GB: initrd.img
   1.2GB: initrd.img.old
  15.0GB: vmlinuz
    .7GB: vmlinuz.old

```

---

### Post by wilee-nilee on 2010-07-06
sda1 which appears to be Vista looks okay as far as I can tell it is marked active.

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info: **Grub 2 is installed in the boot sector of sdb2 and **
                       looks at sector 272135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

This though is hard to say grub should not be in this it shows a XP boot file setup, use this testdisk link to remove it. There is also grub files in sd1 but those can be removed manually or with testdisk.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You also haven't run the last exspunge of the grub-legacy files, that is part of the upgrade to grub2. Here is a link to where you should find information pertinent.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

Fix the sdb boot and put it 1st in being read in bios.

---

### Post by Nomadjackalope on 2010-07-06
Ok I think I got it all except vista still has that cursor, it's not running. I had to fixboot for vista when doing the testdisk. I used completely remove grub legacy in synaptic to get rid of it. I changed the sdb to boot 1st and it all seemed to be ok.

I hope I'm not wasting your time with an issue of vista being corrupted or something. Thank you for helping me so far. :D I appreciate a lot.

---

### Post by wilee-nilee on 2010-07-06
> **Nomadjackalope said:**
> Ok I think I got it all except vista still has that cursor, it's not running. I had to fixboot for vista when doing the testdisk. I used completely remove grub legacy in synaptic to get rid of it. I changed the sdb to boot 1st and it all seemed to be ok.

I hope I'm not wasting your time with an issue of vista being corrupted or something. Thank you for helping me so far. :D I appreciate a lot.

Removing grub-legacy from synaptic doesn't remove the grub files. You should read the grub2 link upgrading to grub2 portion if this makes sense in that you did a manual upgrade or through update manager. There is a final command to exspunge grub-legacy.

As far as Vista if it's not booting with a straight boot from it's partition by choosing it with a boot from key prompt, what happens if you just boot that HD.

To be honest your doing some things that are not suggested so I am not even sure you have cleared the grub from the former XP sdb2 partition.

Here is a link to a good tutorial about grub2, the OP has a couple of other grub threads if you look in their thread list.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

