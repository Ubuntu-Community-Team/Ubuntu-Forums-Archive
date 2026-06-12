---
title: "Where is my Windows stuff?"
date: 2011-08-04
forum: General Help
---

### Post by Meninspex on 2011-08-04
I just installed Ubuntu 11.04.  I ticked the box to install alongside Windows 7 but now my PC just boots straight into Ubuntu.  How do I get to my Windows system, please tell me I haven't lost it, my wife will go mad.

I'm a very inexperienced Linux user so please keep it simple,  And please, please help

---

### Post by jerome1232 on 2011-08-04
Can you post the output of fdisk and mount from a terminal? ctrl+shift+c to copy out of a terminal, ctrl+v to paste into firefox. You can press alt+f2 then type gnome-terminal to launch a terminal.

Make sure to put [noparse]```

```[/noparse] tags around the output to make it readable.

```
sudo fdisk -l
mount
```

---

### Post by Meninspex on 2011-08-04
Sorry, I said I was inexperienced, I don't even know how to find the terminal with this Unity thing.

---

### Post by jerome1232 on 2011-08-04
Which is why I told you how to launch it ;)

Alt+F2, gnome-terminal, enter.

---

### Post by Swagman on 2011-08-04
Just press ctrl + alt + t to open a terminal

---

### Post by Meninspex on 2011-08-04
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

bev@bev-M61P-S3:~$ fdisk -1
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

bev@bev-M61P-S3:~$ 

Is this what you asked for?

---

### Post by jerome1232 on 2011-08-04
Just copy and paste it from my code block, less typing for you :)

it's actually a lower case letter l not the number 1, I know they look the same on this font /shrug.

---

### Post by Meninspex on 2011-08-04
Try again

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x84b584b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x604209d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       20835   167353172    7  HPFS/NTFS
/dev/sdb2           20835       38914   145217537    5  Extended
/dev/sdb5           20835       38400   141089792   83  Linux
/dev/sdb6           38400       38914     4126720   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc79174c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
bev@bev-M61P-S3:~$

---

### Post by .... on 2011-08-04
You hold down shift when your system first starts to access the grub menu...

---

### Post by Meninspex on 2011-08-05
First off thanks to all who are trying to help me.  Sorry if I disappear for a while - other stuff to do.

Tried holding down the shift key during loading.  The words "Grub loading" appear at the end of the loading text but the Grub loader does not appear and the PC then goes straight into Ubuntu.  All the Windows folders and files are there on the disk, what I was expecting was the Windows boot loader to come up first.

---

### Post by MartyBuntu on 2011-08-05
> **Meninspex said:**
> First off thanks to all who are trying to help me.  Sorry if I disappear for a while - other stuff to do.

Tried holding down the shift key during loading.  The words "Grub loading" appear at the end of the loading text but the Grub loader does not appear and the PC then goes straight into Ubuntu.  All the Windows folders and files are there on the disk, what I was expecting was the Windows boot loader to come up first.


When you boot into Ubuntu, go to the software center and install **startupmanager**. It's a graphical tool for configuring GRUB and allowing you the choice of which OS you'd like to be the default.
It's fairly straightforward.

---

### Post by coffeecat on 2011-08-05
@Meninspex, although your output of fdisk shows a number of NTFS partitions, one of which has a boot flag, we ought to check to be sure that one of them is your Windows C: partition and that it still has Windows boot files in its boot sector. We also need to see whether or not some grub files have strayed into your Windows C: partition boot sector, because this is a common reason for Windows not showing up in the grub menu.

Boot up Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there. Then post the contents of your RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. I emphasise this point. You were asked to post the output of fdisk between between [noparse]```
 and 
```[/noparse] tags, but you didn't. You can use the message toolbar [img]http://ubuntuforums.org/images/editor/code.gif[/img] button for this for convenience. But however you do it, please use code tags. Your output will be difficult to read without.

The boot script output will give us an overview of your system and hopefully show why Windows is not showing in your grub menu and what can be done about it.

---

### Post by Meninspex on 2011-08-05
Thanks for the help guys &/or gals.  My brain has had its allotted three score years and ten so its a bit time-worn.  I've finally spotted where the problem lies tho I'm buggerred if I know how to fix it.

I have two HDDs (C & D in Windows) and Windows is on C:,  but I've installed Ubuntu on D: (which is partitioned of course).  What I can't figure out is why the machine now boots from the D drive when it previously booted from the C.

---

### Post by nothingspecial on 2011-08-05
Head over to Wilmslow, through the airport tunnel, straight over the roundabout, through Hale Barns and turn right for Timperley.

Bring your computer and plenty of beer :P :popcorn:

Just kidding.

The computer boots from your D drive because it now uses grub2 which is capable of booting windows and linux. The windows bootloader will not boot linux.

Unfortunately, as is the often the case with these things, something has gone awry. The script coffeecat asked you to run will have all the relevant information in it's output, to allow someone to fix this for you, so follow the instructions in his post.

---

### Post by coffeecat on 2011-08-05
> **Meninspex said:**
> What I can't figure out is why the machine now boots from the D drive when it previously booted from the C.

Maybe a BIOS setting, or maybe the grub bootloader is in what you call your C: drive, but the grub menu doesn't have Windows for one reason or another. The one reason or another is why we need to see the output of the boot script.

**EDIT**: sorry, I should have explained better. Some grub code gets installed to the mbr of the boot disk, probably sda or what you call "C:". But most is in the /boot folder of your Ubuntu root partition, which in your case is on sdb (what you call D: ). That's quite workable. Your system is not booting from "D:". Grub, as a bootloader is far more sophisticated and complex than anything Windows has. So let's see the boot script output! :wink:

---

### Post by Meninspex on 2011-08-05
Hope I've got it right this time     


           ```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 5249ada1-44f4-4b0c-880f-362f301cb24f root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   334,706,406   334,706,344   7 NTFS / exFAT / HPFS
/dev/sdd2         334,706,686   625,141,759   290,435,074   5 Extended
/dev/sdd5         334,706,688   616,886,271   282,179,584  83 Linux
/dev/sdd6         616,888,320   625,141,759     8,253,440  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        68C4ECF3C4ECC482                       ntfs       
/dev/sdb1        0CA044AAA0449BD8                       ntfs       Buffalo
/dev/sdd1        7EB091EEB091ACE1                       ntfs       Data Store
/dev/sdd5        5249ada1-44f4-4b0c-880f-362f301cb24f   ext4       
/dev/sdd6        4d0ffe0d-4fbe-41aa-8e8b-da2d6e2e4f1e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/Buffalo           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/Data Store        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd5        /                        ext4       (rw,errors=remount-ro,commit=0)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: =====================

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
# kopt=root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 11.04, kernel 2.6.38-10-generic-pae
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.38-10-generic-pae

title        Ubuntu 11.04, kernel 2.6.38-10-generic-pae (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.38-10-generic-pae

title        Ubuntu 11.04, kernel 2.6.38-10-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.38-10-generic

title        Ubuntu 11.04, kernel 2.6.38-10-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.38-10-generic

title        Ubuntu 11.04, kernel 2.6.35-30-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.35-30-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.35-30-generic

title        Ubuntu 11.04, kernel 2.6.35-30-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.35-30-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.35-30-generic

title        Ubuntu 11.04, kernel 2.6.32-25-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 11.04, kernel 2.6.32-25-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 11.04, kernel 2.6.31-17-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 11.04, kernel 2.6.31-17-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 11.04, kernel 2.6.28-16-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 11.04, kernel 2.6.28-16-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 11.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
chainloader    +1

--------------------------------------------------------------------------------

======================== sda1/ubuntu/winboot/menu.lst: =========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt
--------------------------------------------------------------------------------

================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=c:\wubildr.mbr 
[operating systems] 
c:\wubildr.mbr="Ubuntu"  
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ubuntu/disks/boot/grub/menu.lst                1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-16-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.31-17-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.32-25-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.35-30-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.38-10-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.38-10-generic-pae  1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-16-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.31-17-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.32-25-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.35-30-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.38-10-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.38-10-generic-pae  1

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=========================== sdd5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=5249ada1-44f4-4b0c-880f-362f301cb24f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
    echo    'Loading Linux 2.6.38-10-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=5249ada1-44f4-4b0c-880f-362f301cb24f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 68C4ECF3C4ECC482
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
--------------------------------------------------------------------------------

=============================== sdd5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=5249ada1-44f4-4b0c-880f-362f301cb24f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4d0ffe0d-4fbe-41aa-8e8b-da2d6e2e4f1e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdd5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 199.754840851 = 214.485127168  boot/grub/core.img                             1
 199.797168732 = 214.530576384  boot/grub/grub.cfg                             1
 161.385940552 = 173.286834176  boot/initrd.img-2.6.38-10-generic-pae          1
 160.417423248 = 172.246896640  boot/vmlinuz-2.6.38-10-generic-pae             2
 161.385940552 = 173.286834176  initrd.img                                     1
 160.417423248 = 172.246896640  vmlinuz                                        2

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Basher101 on 2011-08-05
Could you post your configuration of your Grub? Press Alt+F2 and type "gedit /etc/default/grub" (without the quotations) and paste it here

---

### Post by Meninspex on 2011-08-05
When I run that command I get zero result

---

### Post by Meninspex on 2011-08-05
Got to go for tonight.  Will be back.

---

### Post by Meninspex on 2011-08-06
Is this copy of the Grub file text of any use/help?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by coffeecat on 2011-08-06
@Meninspex, sorry for the delay getting back to you - also had things to do.

The boot script reveals a considerably more complex setup than I had anticipated and reveals something you didn't tell us about - not that it makes any difference to your problem. A few comments:

First - in your earlier fdisk output, your three hard drives are designated as follows:

sda - 160GB
sdb - 320GB
sdc - 500GB

But in your boot script they appear as:

sda - 160GB
sdb - 500GB
sdd - 320GB

Did you run both fdisk and the boot script from your new Ubuntu installation or did you use a live CD for one or both? And did you change any BIOS settings between running the two, and/or did you change the SATA cable layout inside the case between the two? If you didn't, don't worry too much about it because some BIOSs change drive designations seemingly at random, but this is an incongruity which I'd like to clear up, if only because it confuses things. 

Next - you have a wubi installation of Ubuntu 11.04 inside the Windows C: partition. Not only that, you have had it there since 2009 - it started life as Jaunty/9.04. Out of interest, was it working while you were still able to access it? That is, before you installed Ubuntu to its own partition. Also - I see that your Windows 7 was upgraded from XP.

Next - the system is not booting from what you call your "D:" drive, as you thought. Grub is installed to the mbr of the sda drive and looks to partition UUID=5249ada1-44f4-4b0c-880f-362f301cb24f, which is your Ubuntu partition. That is all as it should be.

Next - you have an entry in your Ubuntu grub.cfg file for Windows 7 on sda1. Which is good. However, you say that the system boots straight into Ubuntu and you do not get to see the grub menu. My guess is that the timeout is wrong and that Basher101's suggestion to have a look at /etc/default/grub is the way to go now.

Two suggestions:

You tried holding down the shift key earlier, but that didn't help. The timing of pressing the shift key is very precise. You need to repeatedly tap shift as soon as you see the BIOS splash and keep tapping until the grub menu appears. If it does, you will see the Windows menu entry.

But that's only a temporary workaround. Let's look at /etc/default/grub. Open a Nautilus (file browser) window. Click on "File System" in the left pane. Open the /etc folder, now the "default" folder. Double-click on the grub file. It will open read-only in gedit. Copy and paste the contents into your next post. Don't forget to paste it between [noparse]```
 and 
```[/noparse] tags.

**EDIT**: OK, it took me so long to type this post that I didn't see that you had posted the contents of /etc/default/grub while I was typing. I'll get back to you.

---

### Post by Meninspex on 2011-08-06
Coffeecat, thanks for your time and effort even though I don't technically understand everything that you say!

In answer to some of your questions:-

I haven't altered anything in the BIOS since starting this thread.

The 500GB drive is a Buffalo USB drive.

I ran all the scripts from my new Ubuntu installation (but am doing this on a Windows laptop -will need to go back to my desktop machine if any more scripts are required)

I had/have Ubuntu 10 alongside W7 and it was working OK but I wanted to try Natty.  I tried to upgrade but it failed to load properly so thats when I did the fresh install and buggered it all up!

---

### Post by coffeecat on 2011-08-06
I don't think you've done anything wrong at all! Upgrades to wubi installations (those inside the Windows partition) do often go wrong. It might be repairable but now that you have Ubuntu on its own partition, it's sensible to concentrate on that. Wubi is only really ever meant to be a temporary way of running Ubuntu.

Thanks for confirming that you haven't altered anything in the BIOS. We can assume that your BIOS is one of those that has a cavalier attitude to determining the drive order.

Anyway - the important thing, your /etc/default/grub file. I must admit that I'm scratching my head over this one. It appears to be OK and the grub menu *should* be showing. (The grub menu will have a working Windows entry so out priority is to get the thing showing for you.) I'll do a bit of digging around and post back later, but in the meantime, try the repeatedly tapping the shift key trick that I described. See if that gives you the grub menu. When I say repeatedly, I mean quickly but decisively. The time frame for getting the shift key depressed is very short. Just keeping the key down won't do.

If you can't get the grub menu showing with the shift key, try the ESC key. The shift key is the correct one for grub2, which is what you've got, and ESC was used with the older legacy grub. However, ESC will work with grub 2 (even if not documented) so try that as well if you need to.

---

### Post by Meninspex on 2011-08-06
Tried the rapid pressing of Shift and Esc but neither produces the Grub.

---

### Post by coffeecat on 2011-08-06
In your /etc/default/grub file, this is the bit that's perplexing me:

> **Meninspex said:**
> 

```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

You see that '#' (hash) symbol at the beginning of the second line that I've included in the quote? According to [this link](https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29), that's correct - that should reveal the grub menu. But according to the [official grub manual](http://www.gnu.org/software/grub/manual/grub.html#Simple-configuration) I'm not so sure. What I can say is that the equivalent part of my /etc/default/grub file is:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

No # at the beginning of the line and I do see the grub menu.

This is what I suggest - but no guarantees. Boot into Ubuntu and open a terminal. Now:

```
gksudo gedit /etc/default/grub
```

If you get an error message or an empty text editor, you've made a typo. Be careful now - you have a system file open in a text editor with root writing privileges. Remove the hash (#) symbol at the beginning of that line so it looks like mine. Save the file and close the text editor. Now, while still in the terminal:

```
sudo update-grub
```

The system may ask you for your password again, but this time you won't see any visual feedback as you type it in. Don't worry - it is going in. You should get a few lines of feedback as update-grub runs and then you'll be returned to the terminal prompt. Now close the terminal and reboot. Do you see the grub menu?

---

### Post by Meninspex on 2011-08-06
Did all that but no change, still boots straight into Ubuntu.  Checked the Grub file with text editor and the hash has been removed.

---

### Post by coffeecat on 2011-08-06
> **Meninspex said:**
> Did all that but no change

Yes, I feared that might be the case. I tried my /etc/default/grub with and without the hash symbol in that line, and I get the grub menu with both. Which makes little sense.

I'm going to pm a couple of people to get a couple more opinions. I do have one more idea, but I think it would be a good idea to get a fresh look from someone first in case I've missed something. Hang in there! You are not forgotten. At least your Windows partition is there. The problem is that the grub menu is not behaving the way it should.

---

### Post by Quackers on 2011-08-06
Hello Meninspex,
can you please open up a terminal and run ```
sudo update-grub
``` and post (copy/paste) the output in your next post please?.

---

### Post by avihebbar on 2011-08-06
Try updating grub. It may fix your problem.
On the terminal

sudo update-grub

This usually fixed the problems i have seen.Any error messages you get please let me know.

---

### Post by linfidel on 2011-08-06
This probably will be less than helpful, but I'll try anyway...

I don't remember the details, but I seem to remember a problem somewhere when 2 drives are used - something like one piece of the boot process is assuming /boot is on sda, but a configuration is putting it on sdb.

I think I may have posted somewhere about this, so I'll look and get back if I can find it.

I have one system with an old windows installation on sda, and linux on sdb, and I installed grub on sdb.  This worked well, with the benefit that I can remove the 2nd drive completely, or just switch the BIOS boot order, and the Windows drive will boot like it used to.  After being so clever, though, now I haven't run that windows os for months, and may never run it again - I just created a virtual drive for windows when I need to run it for something.

I'll look for more details on the problem now.

---

### Post by Meninspex on 2011-08-06
```
bev@bev-M61P-S3:~$ sudo update-grub
[sudo] password for bev: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-10-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
bev@bev-M61P-S3:~$ 

```

---

### Post by Quackers on 2011-08-06
Ok, thanks for that. That looks normal :-)
Will you reboot now and see if the grub menu appears please?

---

### Post by Meninspex on 2011-08-06
Nope!  Still going straight in to Ubuntu.

---

### Post by jerome1232 on 2011-08-06
You're still not getting the grub selection menu? Are you sure the bios is set to boot /dev/sda?

I'm completely mystified (glad to see some more knowledgeable guys picked this thread back up)

---

### Post by coffeecat on 2011-08-06
OK - another idea.

First put /etc/default/grub back the way it was originally. From a terminal:

```
gksudo gedit /etc/default/grub
```

And put a # back at the beginning of this line:

```
#GRUB_HIDDEN_TIMEOUT=0
```

Save the file and close gedit, but don't run update-grub yet. Now:

```
gksudo gedit /etc/grub.d/40_custom
```

This should yield a file which has only:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```

Edit it so that it looks like this:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7 on /dev/sda1 - custom entry" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 68C4ECF3C4ECC482
    chainloader +1
}
```

You can copy and paste from this post. Yes, that stanza is borrowed from your grub.cfg file and *should* be superfluous, but I have entries in my 40_custom file and I can see my grub menu, so I'm clutching at straws here.

Save the edited 40_custom file and close gedit. Now:

```
sudo update-grub
```

Don't forget that last one - very important - it has to be repeated each time you edit a grub configuration file. Now reboot and tell us what happens.

---

### Post by coffeecat on 2011-08-06
> **jerome1232 said:**
> Are you sure the bios is set to boot /dev/sda?

I'm *hoping* we can assume that. :) Grub is installed in the mbr of sda and looks to the Ubuntu partition, so grub seems to be working the way it should, with the exception of refusing to show the menu. If the BIOS was set to boot from one of the other drives, nothing would boot at all - see the mbr information in the boot script output. The windows code in the mbr of sdd is presumably left over from when that drive had a Windows partition on it - there is no Windows OS partition on it now - just a NTFS partition without an OS and the Ubuntu partitions.

---

### Post by Quackers on 2011-08-06
I'm wondering if the wubi system update broke something in Windows.
Is that likely coffeecat?
Maybe a Windows repair then a grub purge/re-install may be necessary?

---

### Post by coffeecat on 2011-08-06
Interesting thought. However, os-prober is obviously seeing the Windows partition - the output of update-grub says so - and we have a Windows entry in the grub menu. It's just that the grub menu refuses to report for duty. I'm baffled. Tbh, I'd prefer to get the grub menu visible to see if Windows is still bootable before trying to repair the Windows partition, but I really don't know.

---

### Post by Quackers on 2011-08-06
It's a conundrum.
We are after the same thing in that we want Windows booting again first :-)
The benefit to purging and re-installing grub once Windows is booting is that all of grub's files will be returned to default values - ie any changes made reversed.
It may come to that, I'm afraid.

---

### Post by coffeecat on 2011-08-06
@Quackers, I'm sure you're right. Let's see what comes of my slightly off-the-wall 40_custom suggestion and then take it from there.

---

### Post by Quackers on 2011-08-06
Yes, that could be an eye-opener :-) I can't see any reason why that shouldn't work. Let's see what grub thinks :-)

---

### Post by Meninspex on 2011-08-06
Added the 40_CUSTOM file and guess what?  Still straight into Ubuntu.  Thoughts are turning to reformat and reinstall.  

  Its our wedding anniversary and I'm going for a glass of bubbly.  Back soon.

---

### Post by Quackers on 2011-08-06
That's a bit drastic, methinks!
There may be more professional help on its way :wink:
Happy anniversary :-)

---

### Post by drs305 on 2011-08-06
Late to the thread, with no definite answers as yet.

From your running Ubuntu OS, please type:
> mount
Look for the line  that includes " ... on / type ext4". Does it start with **/dev/sdd5** ?

Also please run "grub-install -v" to verify the grub version being used.

Next, run the following to make sure the grub.cfg file is updated:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Next, unless you have a reason not to, try installing Grub2 to the MBR of sdd and change your BIOS to boot from sdd (320GB drive) first:
```
sudo grub-install /dev/sdd
``` 

As far as getting the GRUB menu to display, if you are trying ESC you press the key repeatedly. If you want to use the SHIFT key, you should just hold it down continuously during the early part of the boot process to get the menu to appear. *However*, in this case your grub.cfg file doesn't include the keystatus check; that is why it isn't working.

If it still doesn't display, we can try a 'dirty' fix: Start the boot, then press CTRL-ALT-DEL to interrupt the boot (after the G2 menu disappers but before the Ubuntu splash screen appears). This should force G2 to display the menu when it reboots.

If none of this gets the menu to display we can manually try editing the files.

---

### Post by Meninspex on 2011-08-07
Back, a bit late - a bit too much bubbly.

In response to drs305 - before I try any of that I need to talk about my BIOS.

It is an Award BIOS and the only HDD options it offers for Boot Device(s) are HDD and USB-HDD.  I can't fathom out how I get it to differentiate between the various hard drives.

---

### Post by Rubi1200 on 2011-08-07
Hi,
coffeecat asked me to offer some ideas, and even though you are getting excellent advice already, I want o confirm some things which may be relevant to the problem:

1. is the Wubi install working and have you used it recently?

2. do you have the Windows recovery/installation disk?

If yes, use this link to boot the computer and drop to a command prompt. Then type in bcedit and take a look at what the default operating system is set to and very important the timout.
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

Use Option Two and choose the command prompt from the menu then just type in bcedit and look for the information I asked about.

Thanks.

---

### Post by Meninspex on 2011-08-07
[QUOTELook for the line  that includes " ... on / type ext4". Does it start with /dev/sdd5 ?][/QUOTE]

No it starts with **/dev/sdb5**    Is the "b instead of d" significant?

---

### Post by Meninspex on 2011-08-07
Also, in re Grub version
```
grub-install (GRUB) 1.99~rc1-13ubuntu3
```

---

### Post by coffeecat on 2011-08-07
> **Meninspex said:**
> 
No it starts with **/dev/sdb5**    Is the "b instead of d" significant?

Yes and no. Back in post #21 I mentioned that your 320GB drive appeared firstly as sdb and then as sdd. This is probably down to your BIOS. Some BIOS's seem to detect hard drives in different orders at different times, leading to kernel device names (sdb, sdd) being different at different times. I think we can assume that your sdb5 is sdd5 wearing a different hat today since of your three physical hard drives, only one - the one that has appeared as sdb or sdd so far - has a #5 partition.

---

### Post by Meninspex on 2011-08-07
> **Rubi1200 said:**
> Hi,
coffeecat asked me to offer some ideas, and even though you are getting excellent advice already, I want o confirm some things which may be relevant to the problem:

1. is the Wubi install working and have you used it recently?

2. do you have the Windows recovery/installation disk?

If yes, use this link to boot the computer and drop to a command prompt. Then type in bcedit and take a look at what the default operating system is set to and very important the timout.
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

Use Option Two and choose the command prompt from the menu then just type in bcedit and look for the information I asked about.

Thanks.
Yes, Wubi was working before I tried to upgrade to Natty.
The Windows disk gave the following ( I didn't know how to take a screenshot)
X: \Sources>bcedit
'bcedit' is not recognised as an internal or external command, operable program or batch file

---

### Post by westie457 on 2011-08-07
Hello a new set of eyes looking at this issue.

So some thoughts on this.

Grub has installed correctly to sda and bypasses any reference to Windows Bootloader. Is that correct?

So Grub not seeing Windows naturally assumes that Windows does not exist and boots straight into Ubuntu. Could this be caused by the USB drive (possibly with remnants of previous Windows installation) being plugged in at the time the pc is turned on. Simple to check - remove the USB drive from the computer. What happens?

Hopefully the Grub menu shows. If not power off and disconnect the second internal hard drive. Restart and in theory Windows should start, however in all probability you will get a blank screen with a flashing cursor.

The above is open for discussion as they are only ideas to track down the problem.

---

### Post by Meninspex on 2011-08-07
> **westie457 said:**
> Hello a new set of eyes looking at this issue.

So some thoughts on this.

Grub has installed correctly to sda and bypasses any reference to Windows Bootloader. Is that correct?

So Grub not seeing Windows naturally assumes that Windows does not exist and boots straight into Ubuntu. Could this be caused by the USB drive (possibly with remnants of previous Windows installation) being plugged in at the time the pc is turned on. Simple to check - remove the USB drive from the computer. What happens?

Hopefully the Grub menu shows. If not power off and disconnect the second internal hard drive. Restart and in theory Windows should start, however in all probability you will get a blank screen with a flashing cursor.

The above is open for discussion as they are only ideas to track down the problem.

Have tried unplugging the USB drive - makes no difference.  As for disconnecting the second drive, all my data is on it so Windows on its own would be no use.

---

### Post by niko123456 on 2011-08-07
this may be a dumb question.. but have you taken the CD with Ubuntu on it out of the drive?

---

### Post by Meninspex on 2011-08-07
> **niko123456 said:**
> this may be a dumb question.. but have you taken the CD with Ubuntu on it out of the drive?

I'll try not to be too offended.  Yes I have taken it out.

---

### Post by niko123456 on 2011-08-07
> **Meninspex said:**
> I'll try not to be too offended.  Yes I have taken it out.

haha! sorry. 

personally I just don't understand how on earth you managed to unlock the secret feature of grub which doesn't present you with any menu whatsoever, but instead boots straight into ubuntu. the menu is an integral part of the boot process. even if it is using a hidden menu, pressing any key should bring it up. edit: bzzt. never knew that menu is skipped when Ubuntu is the sole OS.

---

### Post by westie457 on 2011-08-07
> **Meninspex said:**
> Have tried unplugging the USB drive - makes no difference.  As for disconnecting the second drive, all my data is on it so Windows on its own would be no use.

Understood about the USB drive, for now that is out of the problem.

I was just wondering if the drive with Windows will boot properly if Grub is not in control or if you will get a blank screen with the flashing cursor if Grub is in control. Either way it will tell us something and we might be able to come up with an elegant (read simple) solution for you.

---

### Post by coffeecat on 2011-08-07
@Meninspex, can I draw your attention back to drs305's post at #44? drs305 almost certainly knows more about grub than any of us in this thread. Have you tried everything in that post yet? In particular the "dirty" fix with ctrl-alt-del? That's a new one on me and it sounds as though it might get the grub menu showing, at least temporarily.

And also - drs305's last comment. If you've tried everything in that post and the menu is still not showing you need to say so, so that drs305 can suggest some manual edits to the grub configuration files.

---

### Post by Meninspex on 2011-08-07
> **coffeecat said:**
> @Meninspex, can I draw your attention back to drs305's post at #44? drs305 almost certainly knows more about grub than any of us in this thread. Have you tried everything in that post yet? In particular the "dirty" fix with ctrl-alt-del? That's a new one on me and it sounds as though it might get the grub menu showing, at least temporarily.

And also - drs305's last comment. If you've tried everything in that post and the menu is still not showing you need to say so, so that drs305 can suggest some manual edits to the grub configuration files.


@coffecat, as I said in my post at#45 I don't know how to make my BIOS distinguish between the various HDDs.  If you or somebody else can show me how I will try to do as drs305 asked.

---

### Post by jerome1232 on 2011-08-07
> **Meninspex said:**
> @coffecat, as I said in my post at#45 I don't know how to make my BIOS distinguish between the various HDDs.  If you or somebody else can show me how I will try to do as drs305 asked.

Some BIOS's can't, you said yours only gave the option of HDD or USB Drive etc... so I assume your's will only boot the first hard disk. I'm not sure how much we can help you on that bios, they are all different.

---

### Post by coffeecat on 2011-08-07
> **Meninspex said:**
> @coffecat, as I said in my post at#45 I don't know how to make my BIOS distinguish between the various HDDs.  If you or somebody else can show me how I will try to do as drs305 asked.

You can try the "dirty" fix with ctrl-alt-del without trying to change the boot order first. However...

> **Meninspex said:**
> It is an Award BIOS and the only HDD options it offers for Boot Device(s) are HDD and USB-HDD.  I can't fathom out how I get it to differentiate between the various hard drives.

Sometimes there is a different category in the BIOS apart from boot device. Have a look and see if there is something for hard drives, and select that. It might show all three of your hard drives and then you would be able to put them in a different order. When you go back to the boot device category, it will probably show for HD whichever you set as first in the other category. Sorry that's a bit vague, but BIOSs vary a lot as jerome1232 says.

---

### Post by Meninspex on 2011-08-07
Thanks for that guys, I will try it tomorrow but must leave for now.

---

### Post by drs305 on 2011-08-07
I'm on a business trip and just haven't been able to check in as often as normal. Since it may be a while before I get back on, I'll explain some of my previous post since the helpers may get some ideas.

As far as the CTRL-ALT-DEL, when Grub2 boots, it records a 'recordfail' to /boot/grub/grubenv. Once Ubuntu completes a successful boot, the 'recordfail' is removed. If you interrupt the boot, the grubenv file should still contain the 'recordfail' designation. Grub2 should then see this the next time it boots and display the menu.

The other thing I was trying to accomplish was to confirm it really is the sdd5 Grub that is controlling the boot. Since the grub.cfg file looks like it should display the menu, I wanted to confirm the boot isn't being controlled by something else. I noted that 11.04 is also installed in Wubi and I even considered the possibility that the MBR was actually passing control to the Wubi grub menu. It's a bit of a stretch, but I've seen stranger things. That was the reason for asking to check "mount".

---

### Post by linfidel on 2011-08-07
> **Meninspex said:**
> Back, a bit late - a bit too much bubbly.

In response to drs305 - before I try any of that I need to talk about my BIOS.

It is an Award BIOS and the only HDD options it offers for Boot Device(s) are HDD and USB-HDD.  I can't fathom out how I get it to differentiate between the various hard drives.
There may be more than one place to set the boot options.  There is often one which might set which device boots first (HDD, network, CD, floppy, ...) and another that sets which the order of devices within that category.  I forget, but one is usually called "boot priority" and another may be "boot device".

---

### Post by JASONFUSARO on 2011-08-07
Sorry to interrupt, do you think that adjusting the key rate might allow the ESC or SHIFT key to be recognized? I have to tap mine very quickly in succession to get mine to work.


Just a thought?



EDIT*****

What about setting [COLOR="Red"]GRUB_DEFAULT='Windows 7 on /dev/sda1 - custom entry'[/COLOR]  since the actual position in the menu is not known?


EDIT*******

How about trying grub-emu, if it is not installed install it apt-get install grub-emu see output screenshot

---

### Post by Meninspex on 2011-08-08
Addendum

Have at last sussed how to change the boot drive in the BIOS.  It was cunningly concealed under the heading "Hard Disk Boot Priority"            

Everybody is allowed an off day - I'm just allowed several  :confused:

---

### Post by JASONFUSARO on 2011-08-08
Hi,

Did you give grub-emu a try? Which I placed in the post prior to your recent post? It pulls up the grub menu you should be seeing.

Run it and post it please, curious about the output.

---

### Post by Meninspex on 2011-08-08
Can you give me the exact Terminal command as I can't seem to make it work?

---

### Post by JASONFUSARO on 2011-08-08
> **Meninspex said:**
> Can you give me the exact Terminal command as I can't seem to make it work?


Sorry I was viewing other posts, I will focus on this since your back


Which terminal command are we taliking about?


If it is grub-emu

just type it, if it is not installed it will tell you how to install it and just select that line copy and paste it on the current command line and hit enter


If your taliking Default that has to be added to etc/grub/default or modified I should say

---

### Post by JASONFUSARO on 2011-08-08
GRUB_DEFAULT='Windows 7 on /dev/sda1 - custom entry' 


This would be by modifying etc/grub/default

GRUB_DEFAULT=     can be numeric or alpha as is in your boot_info_script.sh output



EDIT**************


I removed it and reinstalled so you can see output


```


metapsychiatrist@metapsychiatrist-ML6720 ~/Desktop $ [COLOR="Red"]sudo apt-get install grub-emu[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 lib32ncurses5 nspluginwrapper ia32-libs libc6-i386 lib32gcc1 lib32asound2 lib32ncursesw5 lib32z1 lib32stdc++6 lib32v4l-0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  grub-emu
0 upgraded, 1 newly installed, 0 to remove and 134 not upgraded.
Need to get 0 B/3,306 kB of archives.
After this operation, 10.8 MB of additional disk space will be used.
Selecting previously deselected package grub-emu.
(Reading database ... 155389 files and directories currently installed.)
Unpacking grub-emu (from .../grub-emu_1.99~rc1-13ubuntu3-1mint1_amd64.deb) ...
Processing triggers for man-db ...
Setting up grub-emu (1.99~rc1-13ubuntu3-1mint1) ...



```


then type        grub-emu

---

### Post by Meninspex on 2011-08-08
My apologies **drs305 **have done this post once already but it seems to have got lost.


> **drs305 said:**
> Late to the thread, with no definite answers as yet.

From your running Ubuntu OS, please type:

Look for the line  that includes " ... on / type ext4". Does it start with **/dev/sdd5** ?

Also please run "grub-install -v" to verify the grub version being used.

Next, run the following to make sure the grub.cfg file is updated:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```Next, unless you have a reason not to, try installing Grub2 to the MBR of sdd and change your BIOS to boot from sdd (320GB drive) first:
```
sudo grub-install /dev/sdd
```As far as getting the GRUB menu to display, if you are trying ESC you press the key repeatedly. If you want to use the SHIFT key, you should just hold it down continuously during the early part of the boot process to get the menu to appear. *However*, in this case your grub.cfg file doesn't include the keystatus check; that is why it isn't working.

If it still doesn't display, we can try a 'dirty' fix: Start the boot, then press CTRL-ALT-DEL to interrupt the boot (after the G2 menu disappers but before the Ubuntu splash screen appears). This should force G2 to display the menu when it reboots.

If none of this gets the menu to display we can manually try editing the files.

"mount"    -    see my post #47
"grub-install -v"   -  see #48
"grub.cfg"    -   updated
"sudo grub-install /dev/sdd   -
> bev@bev-M61P-S3:~$ sudo grub-install /dev/sdd
[sudo] password for bev: 
/usr/sbin/grub-probe: error: cannot stat `/dev/sdd'.
bev@bev-M61P-S3:~$ CTRL-ALT-DEL  -  stops the boot process but then restarts and boots into Ubuntu with no sign of menu

Have looked at the disk setup with GParted and is as follows (again can't get the screenshot to work):-

/dev/sda1          ntfs                  150GB
/dev/sdb1          ntfs                   160GB
/dev/sdb2          extended          138GB
/dev/sdb5          ext4                  134GB
/dev/sdb6          linux-swap            4GB
Is the reason for the above error in the above nomenclature?

---

### Post by JASONFUSARO on 2011-08-08
> **Meninspex said:**
> Can you give me the exact Terminal command as I can't seem to make it work?



I thought this question was directed to me but your last post seems on the contrary.



If it was my first post is #66

---

### Post by drs305 on 2011-08-08
> **Meninspex said:**
> My apologies **drs305 **have done this post once already but it seems to have got lost.

Is the reason for the above error in the above nomenclature?

Yes, the grub-install didn't work since the computer is now seeing the partition as sd**b**5

You can try running it again as:
```
sudo grub-install /dev/sdb
sudo update-grub
```
And I think you found how to get the BIOS to boot sdb first, so make sure it does.

If this doesn't work, and since we can't seem to see what's wrong with your current Grub files, I would recommend purging and reinstalling G2. Since you have a working Ubuntu, it's not a difficult process. You just have to make sure you have an Internet connection. 

Purging is required because 'reinstalling' doesn't replace corrupted files or those deleted by the user. So we will remove Grub2 then reinstall it.

In the second command, you will be warned that you are removing the bootloader and your system may become unbootable. You will correct this in the next step.

```
sudo apt-get update # Confirm your Internet is working
sudo apt-get purge grub-common # Removes grub-common, grub-pc and grub-gfxpayload-lists if installed
sudo apt-get install grub-pc # Reinstalls Grub 2 (grub-pc, grub-common ...)

```

When you run the third command, it will ask if you want to add any kernel options. Normally you wouldn't. TAB to OK and press ENTER. Next, it will ask where to install G2. Press the spacebar for **sdb** to place an asterisk by it. Do not select any partition. TAB to OK, press ENTER and it will install Grub 2.

Watch the terminal to make sure it runs "update-grub" and look to see if it finds Windows. Reboot and see what happens. If it boots sdb and found Windows, it *should* pause at the Grub menu for 10 seconds to allow you make a selection.

If it still doesn't work, please rerun the boot info script and post the new RESULTS.txt

---

### Post by Meninspex on 2011-08-08
[FONT=monospace]Reply to [/FONT]**drs**305.  Thanks for all that stuff.
Still get the error message for "sudo grub-install /dev/sdb"
Have to leave it for now.  Will try the rest of your suggestions tomorrow and report back.

You'll have to remind me, what is the boot info script?

---

### Post by Meninspex on 2011-08-08
> **JASONFUSARO said:**
> I thought this question was directed to me but your last post seems on the contrary.



If it was my first post is #66

It was directed at you, sorry I didn't make myself clear.  The other post was for drs305

Will be back online hopefully tomorrow pm

---

### Post by drs305 on 2011-08-08
> **Meninspex said:**
> [FONT=monospace]Reply to [/FONT]**drs**305.  Thanks for all that stuff.
Still get the error message for "sudo grub-install /dev/sdb"
Have to leave it for now.  Will try the rest of your suggestions tomorrow and report back.

You'll have to remind me, what is the boot info script?

The boot info script was what was requested in Post #12 and to which you replied in #16.

When you tried to install grub do you now get the error:
> error: cannot stat `/dev/sdb'
(Earlier the error was for sdd)
In any event the device should be the one listed by the "mount" command which contains "/ ". But only use the device (i.e. sdb, sdd, etc) and not the partition (sdb5, sdd5,...)

---

### Post by JASONFUSARO on 2011-08-08
> **Meninspex said:**
> Can you give me the exact Terminal command as I can't seem to make it work?


If you want to try grub-emu:

If when you enter:

grub-emu

and nothing happens

then install it by entering:

```

sudo apt-get install grub-emu

```

then enter:

grub-emu

and you should get the grub menu running in emulation [COLOR="Blue"](see screenshot)[/COLOR]

====================================================================================

If you want to try editing default grub and putting this as opposed to numeric menu item location then edit your default grub file: 

located in etc/default folder


make the following highlighted change in the file

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

[COLOR="Red"]##################GRUB_DEFAULT=0
GRUB_DEFAULT='Windows 7 (loader) (on /dev/sda1)'[/COLOR]
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=60


```

which is listed in your boot_info_script post #16


```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "[COLOR="Red"]Windows 7 (loader) (on /dev/sda1)[/COLOR]" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 68C4ECF3C4ECC482
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```

---

### Post by Meninspex on 2011-08-09
> **drs305 said:**
> the boot info script was what was requested in post #12 and to which you replied in #16.

When you tried to install grub do you now get the error:

(earlier the error was for sdd)
in any event the device should be the one listed by the "mount" command which contains "/ ". But only use the device (i.e. Sdb, sdd, etc) and not the partition (sdb5, sdd5,...)

Yes, still get the error "cannot stat /dev/sdb"

Did the purge and reinstall and all went without problem but it has made no difference, still booting straight into Ubuntu.  This Boot Script seems to show I have Grub on both sda &sdb even though I just specified **sdb**

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 5249ada1-44f4-4b0c-880f-362f301cb24f root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   334,706,406   334,706,344   7 NTFS / exFAT / HPFS
/dev/sdb2         334,706,686   625,141,759   290,435,074   5 Extended
/dev/sdb5         334,706,688   616,886,271   282,179,584  83 Linux
/dev/sdb6         616,888,320   625,141,759     8,253,440  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        68C4ECF3C4ECC482                       ntfs       
/dev/sdb1        7EB091EEB091ACE1                       ntfs       Data Store
/dev/sdb5        5249ada1-44f4-4b0c-880f-362f301cb24f   ext4       
/dev/sdb6        4d0ffe0d-4fbe-41aa-8e8b-da2d6e2e4f1e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: =====================

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
# kopt=root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 11.04, kernel 2.6.38-10-generic-pae
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.38-10-generic-pae

title        Ubuntu 11.04, kernel 2.6.38-10-generic-pae (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.38-10-generic-pae

title        Ubuntu 11.04, kernel 2.6.38-10-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.38-10-generic

title        Ubuntu 11.04, kernel 2.6.38-10-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.38-10-generic

title        Ubuntu 11.04, kernel 2.6.35-30-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.35-30-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.35-30-generic

title        Ubuntu 11.04, kernel 2.6.35-30-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.35-30-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.35-30-generic

title        Ubuntu 11.04, kernel 2.6.32-25-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 11.04, kernel 2.6.32-25-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 11.04, kernel 2.6.31-17-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 11.04, kernel 2.6.31-17-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 11.04, kernel 2.6.28-16-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 11.04, kernel 2.6.28-16-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=68C4ECF3C4ECC482 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 11.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
chainloader    +1

--------------------------------------------------------------------------------

======================== sda1/ubuntu/winboot/menu.lst: =========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt
--------------------------------------------------------------------------------

================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=c:\wubildr.mbr 
[operating systems] 
c:\wubildr.mbr="Ubuntu"  
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ubuntu/disks/boot/grub/menu.lst                1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-16-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.31-17-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.32-25-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.35-30-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.38-10-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.38-10-generic-pae  1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-16-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.31-17-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.32-25-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.35-30-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.38-10-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.38-10-generic-pae  1

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=5249ada1-44f4-4b0c-880f-362f301cb24f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
    echo    'Loading Linux 2.6.38-10-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=5249ada1-44f4-4b0c-880f-362f301cb24f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 5249ada1-44f4-4b0c-880f-362f301cb24f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 68C4ECF3C4ECC482
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
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=5249ada1-44f4-4b0c-880f-362f301cb24f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4d0ffe0d-4fbe-41aa-8e8b-da2d6e2e4f1e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 205.750923157 = 220.923371520  boot/grub/core.img                             1
 207.776973724 = 223.098826752  boot/grub/grub.cfg                             1
 161.385940552 = 173.286834176  boot/initrd.img-2.6.38-10-generic-pae          1
 160.417423248 = 172.246896640  boot/vmlinuz-2.6.38-10-generic-pae             2
 161.385940552 = 173.286834176  initrd.img                                     1
 160.417423248 = 172.246896640  vmlinuz                                        2

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
```Another oddity:-  Yesterday after using the GParted disk I removed the disk but forgot to reset the BIOS to boot from HDD (all 3 boot devices were set to CD ROM) but the PC still rebooted quite happily straight into Ubuntu - is there a ghost in my machine?

---

### Post by drs305 on 2011-08-09
> **Meninspex said:**
> Yes, still get the error "cannot stat /dev/sdb"

Did the purge and reinstall and all went without problem but it has made no difference, still booting straight into Ubuntu.  This Boot Script seems to show I have Grub on both sda &sdb even though I just specified **sdb**

Another oddity:-  Yesterday after using the GParted disk I removed the disk but forgot to reset the BIOS to boot from HDD (all 3 boot devices were set to CD ROM) but the PC still rebooted quite happily straight into Ubuntu - is there a ghost in my machine?

When you install or reinstall Grub 2, it doesn't *erase* Grub 2 from other MBRs if it resides there. So if G2 was already on sda, when you install on sdb the sda MBR is not altered. That is one of the reasons the BIOS boot order must be changed to boot the desired MBR first.

BIOS sets the boot order, but if the first device is not bootable the BIOS will move on to the next device. Most BIOS are set up by default to boot the CD first *if found*. If the BIOS detects no CD, it moves on to the next device. So if you had all three boot options set to CD that is unnecessary and potentially a problem. Your BIOS obviously reverted to a hard disk after no finding a CD. Or a ghost did it....

The next thing to try to display the menu is to change the timeout to -1, which should force the menu to show. To do this, we will edit the grub.cfg file. Normally we don't edit this file directly but we can for testing. Just make sure you do NOT run "update-grub" afterward, since it would erase the change.

Open grub.cfg for editing (at line [noparse]58)[/noparse]:
```
gksu gedit +58 /boot/grub/grub.cfg
```

Change the timeout to -1 in both sections:
> 
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
[s]  set timeout=10[/s]
  set timeout=**-1**
fi
### END /etc/grub.d/00_header ###
Save the file and reboot. Do not run "sudo update-grub"

This should force Grub 2 to display the menu whether it thinks there is another OS or not. If the menu still doesn't display about the only thing I can think of is that your system still isn't using the grub.cfg file we think it is.

---

### Post by Meninspex on 2011-08-09
> **drs305 said:**
> When you install or reinstall Grub 2, it doesn't *erase* Grub 2 from other MBRs if it resides there. So if G2 was already on sda, when you install on sdb the sda MBR is not altered. That is one of the reasons the BIOS boot order must be changed to boot the desired MBR first.

BIOS sets the boot order, but if the first device is not bootable the BIOS will move on to the next device. Most BIOS are set up by default to boot the CD first *if found*. If the BIOS detects no CD, it moves on to the next device. So if you had all three boot options set to CD that is unnecessary and potentially a problem. Your BIOS obviously reverted to a hard disk after no finding a CD. Or a ghost did it....

The next thing to try to display the menu is to change the timeout to -1, which should force the menu to show. To do this, we will edit the grub.cfg file. Normally we don't edit this file directly but we can for testing. Just make sure you do NOT run "update-grub" afterward, since it would erase the change.

Open grub.cfg for editing (at line [noparse]58)[/noparse]:
```
gksu gedit +58 /boot/grub/grub.cfg
```Change the timeout to -1 in both sections:

Save the file and reboot. Do not run "sudo update"

This should force Grub 2 to display the menu whether it thinks there is another OS or not. If the menu still doesn't display about the only thing I can think of is that your system still isn't using the grub.cfg file we think it is.

Carried out the above and after trying to boot its just hanging at a black screen (after the POST)

EDIT  Pressed the down arrow and enter and it opened Ubuntu

---

### Post by drs305 on 2011-08-09
> **Meninspex said:**
> Carried out the above and after trying to boot its just hanging at a black screen (after the POST)

EDIT  Pressed the down arrow and enter and it opened Ubuntu

This may be giving us a clue ... 

Previously, when you booted did it seem to take a while before Ubuntu started booting? If so, what happened above may explain why you never see a choice. If for some reason G2 cannot render the menu, and it was aware of Windows, the screen would be blank and after 10 seconds boot the default entry. To the user, it would appear like there is no menu.

If you haven't reverted  the timeout change to grub.cfg, you could try this experiment. Boot to the black screen, then press the DN arrow 4 times, then press ENTER. If the menu is present but not visible, it should attempt to boot Windows.

Note: If you wish to remove the change to grub.cfg, just run "sudo update-grub" and the timeout will revert to 10 seconds.

---

### Post by Meninspex on 2011-08-09
[B]#drs305

[/B]Hooray and huzzah,  That has produced Windows.  Now I just need to be able to see the menu but in the meantime:-

What are options 2 & 3?
Can I reset the order so that Windows is the first option - this will keep my wife off my back.

---

### Post by drs305 on 2011-08-09
> **Meninspex said:**
> [B]#drs305

[/B]Hooray and huzzah,  That has produced Windows.  Now I just need to be able to see the menu but in the meantime:-

What are options 2 & 3?
Can I reset the order so that Windows is the first option - this will keep my wife off my back.

Yes, we can set it up to boot Windows first. I'm on a business trip and will see what I can deduce about the video when I return home.

For now, we will can change a few things so it's more convenient.

I highly recommend Grub Customizer for making changes. It's a great GUI tool and the link is in my signature line. For now though, I'd recommend continuing to doing things from the command line since your Grub still isn't acting normally.

To answer the options question: If you look at grub.cfg, you will see lines starting with 'menuentry'. You can also see them easier by running this command:
```
grep "menuentry" /boot/grub/grub.cfg
```
Each "menuentry" is a choice on the Grub menu. Grub 2 counts the first 'menuentry' as 0, the second as 1, etc.
So in your case, 0 is Ubuntu, 1 is the Ubuntu recovery mode, 2 and 3 are memory tests, and 4 is Windows.

We can set Windows (4) as the default via the /etc/default/grub file:
```
gksu gedit /etc/default/grub
```
Change the applicable line to:
> GRUB_DEFAULT=**4**
or even better since it doesn't matter what number it is on the menu. For simplicity and to make sure this will work, using the number might be easier initially for testing:
> GRUB_DEFAULT=**"Windows 7 (loader) (on /dev/sda1)"**
Also for now, since the screen is blank, you might as well shorten the timeout to less than 10 seconds. Choose whatever value you wish to use. 
> GRUB_TIMEOUT=10

Save the file, then run:
```
sudo update-grub
```
This will update the file, and will also restore automatic booting after the delay you specify above. (If you don't want to let it boot automatically, make the value -1).

I'll get back to the menu visibility issue when time permits.

---

### Post by Meninspex on 2011-08-09
**#drs305**
Many thanks for that, have now got Windows as default.  I await your return.

---

### Post by drs305 on 2011-08-09
There are a couple of options for trying to repair the video.

The easiest is to turn off the graphics mode entirely. I think this will work but you'll just have to try it. Open /etc/default/grub as you have done previously. Then uncomment the following line to enable the console so it looks like this:
> 
GRUB_TERMINAL=console

Save the file, run "sudo update-grub" and reboot.

If you now see the menu, you can try to restore the graphics mode if desired. While the menu is displayed, press 'c' to get to the grub command prompt. Type:```

set pager=1
vbeinfo
```
This should show the resolutions available to your monitor *and*
 Grub 2. You will probably see at least 640x480 and probably 800x600 and 1024x768. Note the ones you want to try.

After booting go back into /etc/default/grub, *return the # symbol to the GRUB_TERMINAL=console line*, and uncomment:
> GRUB_GFXMODE=640x480
Use that resolution or try other combinations you found earlier. Save the file, update grub and see if the graphical mode will work. For the default bootloader, the principal advantage in having the graphics is that you can control the font size. There are lots of other things it would let you do, but they fall into the 'eye candy' category.

---

### Post by Meninspex on 2011-08-10
> **drs305 said:**
> There are a couple of options for trying to repair the video.

The easiest is to turn off the graphics mode entirely. I think this will work but you'll just have to try it. Open /etc/default/grub as you have done previously. Then uncomment the following line to enable the console so it looks like this:

Save the file, run "sudo update-grub" and reboot.

If you now see the menu, you can try to restore the graphics mode if desired. While the menu is displayed, press 'c' to get to the grub command prompt. Type:```

set pager=1
vbeinfo
```This should show the resolutions available to your monitor *and*
 Grub 2. You will probably see at least 640x480 and probably 800x600 and 1024x768. Note the ones you want to try.

After booting go back into /etc/default/grub, *return the # symbol to the GRUB_TERMINAL=console line*, and uncomment:

Use that resolution or try other combinations you found earlier. Save the file, update grub and see if the graphical mode will work. For the default bootloader, the principal advantage in having the graphics is that you can control the font size. There are lots of other things it would let you do, but they fall into the 'eye candy' category.

All went fine until I got to the Grub Command line - it didn't like "set pager-1".
I tried "vbeinfo" on its own and that returned something like 150 resolution options.

Carried out the remainder of the instructions and changed resolution to 1024 x 768, which is small enough for my poor eyesight, updated and rebooted.

Everything is now just as I want it.  It only remains for me to offer my heartfelt thanks to @drs305, @coffeecat and all the other people who offered help.  I'm still blindingly ignorant about Linux but I know a damned sight more than I did when this started all those posts ago.

Meninspex:D

---

### Post by drs305 on 2011-08-10
> **Meninspex said:**
> All went fine until I got to the Grub Command line - it didn't like "set pager-1".
For the record, the command includes an 'equal' sign, not a "-". But it's not a critical command; it just limits screen output to one page at a time for easier viewing.

> 
Carried out the remainder of the instructions and changed resolution to 1024 x 768, which is small enough for my poor eyesight, updated and rebooted.


I'm just curious as to which method you ended up using. Since you mention resolutions, I assume you were able to keep the graphics mode with a specified resolution (# on the 'console' line). Or did you end up with the console line uncommented?

In any event, this was an interesting problem. I wish I could tell you why G2 failed in the first place...

If you feel the issue is resolved you can mark the thread 'SOLVED' via the 'Thread Tools' link at the top right of the first post.

Happy Ubuntu-ing !

---

