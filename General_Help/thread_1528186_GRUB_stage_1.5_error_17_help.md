---
title: "GRUB stage 1.5 error 17 help"
date: 2010-07-10
forum: General Help
---

### Post by snwbrdrjake on 2010-07-10
ok so i jut installed ubuntu from an old live cd, i had to upgrade it twice to get it currant, and i also have a win 7 os on my box.  Now when I try to boot I only get as far as the grub loading screen where an error 17 pops up, google says thats because it can't boot the selected boot partition but i cant even select my windows partition. im on the old live disk right now, any ideas?

Here's a screenshot of a sudo fdisk -l command
            [http://imgur.com/dL6uv](http://imgur.com/dL6uv)

---

### Post by krishnandu.sarkar on 2010-07-10
This may not solve your problem. But run this command in terminal : sudo apt-get update-grub

---

### Post by snwbrdrjake on 2010-07-10
> **krishnandu.sarkar said:**
> This may not solve your problem. But run this command in terminal : sudo apt-get update-grub
it says E: Invalid operation update-grub

---

### Post by WorMzy on 2010-07-10
That command should be 'sudo apt-get **install** update grub', but I don't think that will help. You need to modify your menu.lst, or, if using grub2, you need to 'update-grub' so that it detects the correct partitions.

Can you download and run the boot info script from [here]("http://sourceforge.net/projects/bootinfoscript/"), then post the output here, please.

---

### Post by snwbrdrjake on 2010-07-10
> **WorMzy said:**
> That command should be 'sudo apt-get **install** update grub', but I don't think that will help. You need to modify your menu.lst, or, if using grub2, you need to 'update-grub' so that it detects the correct partitions.

Can you download and run the boot info script from [here]("http://sourceforge.net/projects/bootinfoscript/"), then post the output here, please.
terminal says "E: Couldn't find package update-grub, and as for the script, i downloaded it, but how do I run it?

---

### Post by WorMzy on 2010-07-10
There's a link to the instructions on the page I linked, but here's a direct link: [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by snwbrdrjake on 2010-07-10
> **WorMzy said:**
> There's a link to the instructions on the page I linked, but here's a direct link: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
thanks, im new to ubuntu by the way, hah. heres the info.
             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd3392d9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   419,432,447   419,225,600   7 HPFS/NTFS
/dev/sda3         419,432,448   503,830,887    84,398,440   7 HPFS/NTFS
/dev/sda4         503,846,595 1,948,298,939 1,444,452,345   f W95 Ext d (LBA)
/dev/sda5         503,846,721 1,546,159,859 1,042,313,139  83 Linux
/dev/sda6       1,546,159,923 1,564,249,049    18,089,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        70446FF5446FBC8A                       ntfs       System Reserved               
/dev/sda2        0266711966710EA3                       ntfs                                     
/dev/sda3        6E50D24D50D21BA1                       ntfs       Files                         
/dev/sda5        91b3a904-6a34-4be2-a1ab-79eec0ef5501   ext3                                     
/dev/sda6        93f43631-9fd2-4b9e-8842-2ede7f09c3c3   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/Files             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)


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
color cyan/blue white/blue

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
# kopt=root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=91b3a904-6a34-4be2-a1ab-79eec0ef5501

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
# defoptions=splash vga=799 quiet

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid        91b3a904-6a34-4be2-a1ab-79eec0ef5501
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro splash vga=799 quiet 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        91b3a904-6a34-4be2-a1ab-79eec0ef5501
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic
uuid        91b3a904-6a34-4be2-a1ab-79eec0ef5501
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro splash vga=799 quiet 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        91b3a904-6a34-4be2-a1ab-79eec0ef5501
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid        91b3a904-6a34-4be2-a1ab-79eec0ef5501
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro splash vga=799 quiet 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid        91b3a904-6a34-4be2-a1ab-79eec0ef5501
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        91b3a904-6a34-4be2-a1ab-79eec0ef5501
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=93f43631-9fd2-4b9e-8842-2ede7f09c3c3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 750.2GB: boot/grub/menu.lst
 750.1GB: boot/grub/stage2
 750.2GB: boot/initrd.img-2.6.28-11-generic
 750.1GB: boot/initrd.img-2.6.31-22-generic
 750.2GB: boot/initrd.img-2.6.32-23-generic
 750.1GB: boot/vmlinuz-2.6.28-11-generic
 750.2GB: boot/vmlinuz-2.6.31-22-generic
 750.1GB: boot/vmlinuz-2.6.32-23-generic
 750.2GB: initrd.img
 750.1GB: initrd.img.old
 750.1GB: vmlinuz
 750.2GB: vmlinuz.old

---

### Post by ajgreeny on 2010-07-10
The obvious problem that I see is shown in this statement at the top of your RESULTS.txt file:-
```
=> Grub 0.97 is installed in the MBR of /dev/sda and looks on the  same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
```Unfortunately partition #6 is your swap, not the ubuntu OS partition, so something has obviously gone wrong at some point, which is also borne out by the /etc/fstab file which shows:-
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name  devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#[COLOR=Red] / was on /dev/sda6 during installation[/COLOR]
UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 /               ext3     relatime,errors=remount-ro 0       1
# [COLOR=Red]swap was on /dev/sda7 during installation[/COLOR]
UUID=93f43631-9fd2-4b9e-8842-2ede7f09c3c3 none            swap    sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0        0
```
You appear to have lost a partition and the ones left behind are apparently mapped wrongly, though the UUIDs appear to be correct.

Can you have a quick look at the device.map file with ```
cat /boot/grub/device.map
``` and post what it says.  I doubt it will help, but it's worth a try.

---

### Post by snwbrdrjake on 2010-07-10
> **ajgreeny said:**
> The obvious problem that I see is shown in this statement at the top of your RESULTS.txt file:-
```
=> Grub 0.97 is installed in the MBR of /dev/sda and looks on the  same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
```Unfortunately partition #6 is your swap, not the ubuntu OS partition, so something has obviously gone wrong at some point, which is also borne out by the /etc/fstab file which shows:-
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name  devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#[COLOR=Red] / was on /dev/sda6 during installation[/COLOR]
UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 /               ext3     relatime,errors=remount-ro 0       1
# [COLOR=Red]swap was on /dev/sda7 during installation[/COLOR]
UUID=93f43631-9fd2-4b9e-8842-2ede7f09c3c3 none            swap    sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0        0
```You appear to have lost a partition and the ones left behind are apparently mapped wrongly, though the UUIDs appear to be correct.

Can you have a quick look at the device.map file with ```
cat /boot/grub/device.map
``` and post what it says.  I doubt it will help, but it's worth a try.
the command says no such file or directory, im on an old live cd if that matters

---

### Post by WorMzy on 2010-07-10
Okay, I think the problem is that grub seems to be looking at your swap partition for your boot files, which aren't there (obviously, swap is just used to store program data that gets ousted from RAM, similar to a paging file in Windows)

All I can suggest is reinstalling grub to the MBR:
Boot into the liveCD (use your Karmic CD, or previous version*)
Open a terminal and write:
```
grub
```
followed by
```
find /boot/grub/stage1
```
I believe it should find it on hd0,4; but if it finds it on a different partition, then change the next commands accordingly
```
root (hd0,4)
```
and finally
```
setup (hd0)
```
followed by```
quit
```

And reboot.

*the reason for this is you're using grub legacy, 10.04 ships with grub2 (which isn't backwards compatible), so I'm led to believe you upgraded from a previous install.

(I guess I took longer writing this than I thought.)

---

### Post by snwbrdrjake on 2010-07-10
> **snwbrdrjake said:**
> the command says no such file or directory, im on an old live cd if that matters
wait, no i got th4e directorys mixed up, here the data

[LIST=1]
[*]           Boot Info Script 0.55    dated February 15th, 2010                    
[*] 
[*]============================= Boot Info Summary: ==============================
[*] 
[*] => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
[*]    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
[*] 
[*]sda1: _________________________________________________________________________
[*] 
[*]    File system:       ntfs
[*]    Boot sector type:  Windows Vista/7
[*]    Boot sector info:  No errors found in the Boot Parameter Block.
[*]    Operating System:  
[*]    Boot files/dirs:   /bootmgr /Boot/BCD
[*] 
[*]sda2: _________________________________________________________________________
[*] 
[*]    File system:       ntfs
[*]    Boot sector type:  Windows Vista/7
[*]    Boot sector info:  No errors found in the Boot Parameter Block.
[*]    Operating System:  Windows 7
[*]    Boot files/dirs:   /Windows/System32/winload.exe
[*] 
[*]sda3: _________________________________________________________________________
[*] 
[*]    File system:       ntfs
[*]    Boot sector type:  Windows Vista/7
[*]    Boot sector info:  No errors found in the Boot Parameter Block.
[*]    Operating System:  
[*]    Boot files/dirs:   
[*] 
[*]sda4: _________________________________________________________________________
[*] 
[*]    File system:       Extended Partition
[*]    Boot sector type:  -
[*]    Boot sector info:  
[*] 
[*]sda5: _________________________________________________________________________
[*] 
[*]    File system:       ext3
[*]    Boot sector type:  -
[*]    Boot sector info:  
[*]    Operating System:  Ubuntu 10.04 LTS
[*]    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
[*] 
[*]sda6: _________________________________________________________________________
[*] 
[*]    File system:       swap
[*]    Boot sector type:  -
[*]    Boot sector info:  
[*] 
[*]=========================== Drive/Partition Info: =============================
[*] 
[*]Drive: sda ___________________ _____________________________________________________
[*] 
[*]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
[*]255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
[*]Units = sectors of 1 * 512 = 512 bytes
[*]Disk identifier: 0xbd3392d9
[*] 
[*]Partition  Boot         Start           End          Size  Id System
[*] 
[*]/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
[*]/dev/sda2             206,848   419,432,447   419,225,600   7 HPFS/NTFS
[*]/dev/sda3         419,432,448   503,830,887    84,398,440   7 HPFS/NTFS
[*]/dev/sda4         503,846,595 1,948,298,939 1,444,452,345   f W95 Ext d (LBA)
[*]/dev/sda5         503,846,721 1,546,159,859 1,042,313,139  83 Linux
[*]/dev/sda6       1,546,159,923 1,564,249,049    18,089,127  82 Linux swap / Solaris
[*] 
[*] 
[*]blkid -c /dev/null: ____________________________________________________________
[*] 
[*]Device           UUID                                   TYPE       LABEL                         
[*] 
[*]/dev/loop0                                              squashfs                                 
[*]/dev/sda1        70446FF5446FBC8A                       ntfs       System Reserved               
[*]/dev/sda2        0266711966710EA3                       ntfs                                     
[*]/dev/sda3        6E50D24D50D21BA1                       ntfs       Files                         
[*]/dev/sda5        91b3a904-6a34-4be2-a1ab-79eec0ef5501   ext3                                     
[*]/dev/sda6        93f43631-9fd2-4b9e-8842-2ede7f09c3c3   swap                                     
[*] 
[*]============================ "mount | grep ^/dev  output: ===========================
[*] 
[*]Device           Mount_Point              Type       Options
[*] 
[*]rootfs           /                        rootfs     (rw)
[*]/dev/sr0         /cdrom                   iso9660    (ro,noatime)
[*]/dev/loop0       /rofs                    squashfs   (ro,noatime)
[*]/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
[*]/dev/sda3        /media/Files             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
[*]/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
[*]/dev/sda5        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)
[*] 
[*] 
[*]=========================== sda5/boot/grub/menu.lst: ===========================
[*] 
[*]# menu.lst - See: grub(8), info grub, update-grub(8)
[*]#            grub-install(8), grub-floppy(8),
[*]#            grub-md5-crypt, /usr/share/doc/grub
[*]#            and /usr/share/doc/grub-doc/.
[*] 
[*]## default num
[*]# Set the default entry to the entry number NUM. Numbering starts from 0, and
[*]# the entry number 0 is the default if the command is not used.
[*]#
[*]# You can specify 'saved' instead of a number. In this case, the default entry
[*]# is the entry saved with the command 'savedefault'.
[*]# WARNING: If you are using dmraid do not use 'savedefault' or your
[*]# array will desync and will not let you boot your system.
[*]default         0
[*] 
[*]## timeout sec
[*]# Set a timeout, in SEC seconds, before automatically booting the default entry
[*]# (normally the first entry defined).
[*]timeout         10
[*] 
[*]## hiddenmenu
[*]# Hides the menu by default (press ESC to see the menu)
[*]#hiddenmenu
[*] 
[*]# Pretty colours
[*]color cyan/blue white/blue
[*] 
[*]## password ['--md5'] passwd
[*]# If used in the first section of a menu file, disable all interactive editing
[*]# control (menu entry editor and command-line)  and entries protected by the
[*]# command 'lock'
[*]# e.g. password topsecret
[*]## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
[*]# password topsecret
[*] 
[*]#
[*]# examples
[*]#
[*]# title         Windows 95/98/NT/2000
[*]# root          (hd0,0)
[*]# makeactive
[*]# chainloader   +1
[*]#
[*]# title         Linux
[*]# root          (hd0,1)
[*]# kernel        /vmlinuz root=/dev/hda2 ro
[*]#
[*] 
[*]#
[*]# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[*] 
[*]### BEGIN AUTOMAGIC KERNELS LIST
[*]## lines between the AUTOMAGIC KERNELS LIST markers will be modified
[*]## by the debian update-grub script except for the default options below
[*] 
[*]## DO NOT UNCOMMENT THEM, Just edit them to your needs
[*] 
[*]## ## Start Default Options ##
[*]## default kernel options
[*]## default kernel options for automagic boot options
[*]## If you want special options for specific kernels use kopt_x_y_z
[*]## where x.y.z is kernel version. Minor versions can be omitted.
[*]## e.g. kopt=root=/dev/hda1 ro
[*]##      kopt_2_6_8=root=/dev/hdc1 ro
[*]##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[*]# kopt=root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro
[*] 
[*]## default grub root device
[*]## e.g. groot=(hd0,0)
[*]# groot=91b3a904-6a34-4be2-a1ab-79eec0ef5501
[*] 
[*]## should update-grub create alternative automagic boot options
[*]## e.g. alternative=true
[*]##      alternative=false
[*]# alternative=true
[*] 
[*]## should update-grub lock alternative automagic boot options
[*]## e.g. lockalternative=true
[*]##      lockalternative=false
[*]# lockalternative=false
[*] 
[*]## additional options to use with the default boot option, but not with the
[*]## alternatives
[*]## e.g. defoptions=vga=791 resume=/dev/hda5
[*]# defoptions=splash vga=799 quiet
[*] 
[*]## should update-grub lock old automagic boot options
[*]## e.g. lockold=false
[*]##      lockold=true
[*]# lockold=false
[*] 
[*]## Xen hypervisor options to use with the default Xen boot option
[*]# xenhopt=
[*] 
[*]## Xen Linux kernel options to use with the default Xen boot option
[*]# xenkopt=console=tty0
[*] 
[*]## altoption boot targets option
[*]## multiple altoptions lines are allowed
[*]## e.g. altoptions=(extra menu suffix) extra boot options
[*]##      altoptions=(recovery) single
[*]# altoptions=(recovery mode) single
[*] 
[*]## controls how many kernels should be put into the menu.lst
[*]## only counts the first occurence of a kernel, not the
[*]## alternative kernel options
[*]## e.g. howmany=all
[*]##      howmany=7
[*]# howmany=all
[*] 
[*]## specify if running in Xen domU or have grub detect automatically
[*]## update-grub will ignore non-xen kernels when running in domU and vice versa
[*]## e.g. indomU=detect
[*]##      indomU=true
[*]##      indomU=false
[*]# indomU=detect
[*] 
[*]## should update-grub create memtest86 boot option
[*]## e.g. memtest86=true
[*]##      memtest86=false
[*]# memtest86=true
[*] 
[*]## should update-grub adjust the value of the default booted system
[*]## can be true or false
[*]# updatedefaultentry=false
[*] 
[*]## should update-grub add savedefault to the default options
[*]## can be true or false
[*]# savedefault=false
[*] 
[*]## ## End Default Options ##
[*] 
[*]title           Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
[*]uuid            91b3a904-6a34-4be2-a1ab-79eec0ef5501
[*]kernel          /boot/vmlinuz-2.6.32-23-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro splash vga=799 quiet 
[*]initrd          /boot/initrd.img-2.6.32-23-generic
[*]quiet
[*] 
[*]title           Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
[*]uuid            91b3a904-6a34-4be2-a1ab-79eec0ef5501
[*]kernel          /boot/vmlinuz-2.6.32-23-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro  single
[*]initrd          /boot/initrd.img-2.6.32-23-generic
[*] 
[*]title           Ubuntu 10.04 LTS, kernel 2.6.31-22-generic
[*]uuid            91b3a904-6a34-4be2-a1ab-79eec0ef5501
[*]kernel          /boot/vmlinuz-2.6.31-22-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro splash vga=799 quiet 
[*]initrd          /boot/initrd.img-2.6.31-22-generic
[*]quiet
[*] 
[*]title           Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode)
[*]uuid            91b3a904-6a34-4be2-a1ab-79eec0ef5501
[*]kernel          /boot/vmlinuz-2.6.31-22-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro  single
[*]initrd          /boot/initrd.img-2.6.31-22-generic
[*] 
[*]title           Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
[*]uuid            91b3a904-6a34-4be2-a1ab-79eec0ef5501
[*]kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro splash vga=799 quiet 
[*]initrd          /boot/initrd.img-2.6.28-11-generic
[*]quiet
[*] 
[*]title           Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
[*]uuid            91b3a904-6a34-4be2-a1ab-79eec0ef5501
[*]kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 ro  single
[*]initrd          /boot/initrd.img-2.6.28-11-generic
[*] 
[*]title           Ubuntu 10.04 LTS, memtest86+
[*]uuid            91b3a904-6a34-4be2-a1ab-79eec0ef5501
[*]kernel          /boot/memtest86+.bin
[*]quiet
[*] 
[*]### END DEBIAN AUTOMAGIC KERNELS LIST
[*] 
[*]# This is a divider, added to separate the menu items below from the Debian
[*]# ones.
[*]title           Other operating systems:
[*]root
[*] 
[*] 
[*]# This entry automatically added by the Debian installer for a non-linux OS
[*]# on /dev/sda1
[*]title           Windows Vista (loader)
[*]rootnoverify    (hd0,0)
[*]savedefault
[*]makeactive
[*]chainloader     +1
[*] 
[*] 
[*]=============================== sda5/etc/fstab: ===============================
[*] 
[*]# /etc/fstab: static file system information.
[*]#
[*]# Use 'vol_id --uuid' to print the universally unique identifier for a
[*]# device; this may be used with UUID= as a more robust way to name devices
[*]# that works even if disks are added and removed. See fstab(5).
[*]#
[*]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
[*]proc            /proc           proc    defaults        0       0
[*]# / was on /dev/sda6 during installation
[*]UUID=91b3a904-6a34-4be2-a1ab-79eec0ef5501 /               ext3    relatime,errors=remount-ro 0       1
[*]# swap was on /dev/sda7 during installation
[*]UUID=93f43631-9fd2-4b9e-8842-2ede7f09c3c3 none            swap    sw              0       0
[*]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[*] 
[*]=================== sda5: Location of files loaded by Grub: ===================
[*] 
[*] 
[*] 750.2GB: boot/grub/menu.lst
[*] 750.1GB: boot/grub/stage2
[*] 750.2GB: boot/initrd.img-2.6.28-11-generic
[*] 750.1GB: boot/initrd.img-2.6.31-22-generic
[*] 750.2GB: boot/initrd.img-2.6.32-23-generic
[*] 750.1GB: boot/vmlinuz-2.6.28-11-generic
[*] 750.2GB: boot/vmlinuz-2.6.31-22-generic
[*] 750.1GB: boot/vmlinuz-2.6.32-23-generic
[*] 750.2GB: initrd.img
[*] 750.1GB: initrd.img.old
[*] 750.1GB: vmlinuz
[*] 750.2GB: vmlinuz.old
[/LIST]

---

### Post by snwbrdrjake on 2010-07-10
> **WorMzy said:**
> Okay, I think the problem is that grub seems to be looking at your swap partition for your boot files, which aren't there (obviously, swap is just used to store program data that gets ousted from RAM, similar to a paging file in Windows)

All I can suggest is reinstalling grub to the MBR:
Boot into the liveCD (use your Karmic CD, or previous version*)
Open a terminal and write:
```
grub
```followed by
```
find /boot/grub/stage1
```I believe it should find it on hd0,4; but if it finds it on a different partition, then change the next commands accordingly
```
root (hd0,4)
```and finally
```
setup (hd0)
```followed by```
quit
```And reboot.

*the reason for this is you're using grub legacy, 10.04 ships with grub2 (which isn't backwards compatible), so I'm led to believe you upgraded from a previous install.

(I guess I took longer writing this than I thought.)
thank you so mutch! my compy is saved!

---

### Post by WorMzy on 2010-07-10
Glad to see it worked. :)

---

### Post by snwbrdrjake on 2010-07-10
> **WorMzy said:**
> Glad to see it worked. :)
wait no, when i try find /boot/grub/stage 1 i get an error 15, file not found

---

### Post by dino99 on 2010-07-10
> **snwbrdrjake said:**
> wait no, when i try find /boot/grub/stage 1 i get an error 15, file not found

you are using Lucid and it only work with so called grub2 (ie grub-pc and grub-common, check synaptic)

so remove menu.lst because its not compatible with grub2, and into a console:

sudo grub-mkconfig
sudo update-grub

---

### Post by WorMzy on 2010-07-10
Dino, using grub2 may be a valid solution, but Lucid will work with either grub legacy or grub2.

snwbrdjake, that's a little worrying. Can you quit out of grub, mount your Ubuntu partition with
```
sudo mount -t ext3 /dev/sda5 /mnt
```
then post the output of the following command
```
ls -l /mnt/boot/grub
```

---

