---
title: "GRub Error"
date: 2010-04-12
forum: General Help
---

### Post by nbulchandani on 2010-04-12
HEllo ,
i had a grub error and reinstalled the grub...
now on rebooting
it comes with a shell as
sh:grub>
and no options of ubuntu  or windows..any ideas?
Thanks

---

### Post by prodigy_ on 2010-04-12
Boot from Ubuntu Live CD and run [this script](http://bootinfoscript.sourceforge.net/). Post the output here.

---

### Post by oleink on 2010-04-12
Did you delete prebundled software (like python 2.6 etc)?  That happened to me when i did that

---

### Post by nbulchandani on 2010-04-12
nah ...just reinstalled windows on the same place...trying the script

---

### Post by nbulchandani on 2010-04-12
this sourceforge link is very slow...any other way plz

---

### Post by nbulchandani on 2010-04-12
got the script posting d output

---

### Post by nbulchandani on 2010-04-12
the output is
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       240,974       240,912  de Dell Utility
/dev/sda2    *        241,664   102,641,663   102,400,000   7 HPFS/NTFS
/dev/sda3         102,641,664   150,372,351    47,730,688   7 HPFS/NTFS
/dev/sda4         150,384,526   625,139,711   474,755,186   f W95 Ext d (LBA)
/dev/sda5         205,043,712   415,207,423   210,163,712   7 HPFS/NTFS
/dev/sda6         415,209,472   625,139,711   209,930,240   7 HPFS/NTFS
/dev/sda7         150,384,528   156,376,709     5,992,182  82 Linux swap / Solaris
/dev/sda8         156,376,773   205,037,594    48,660,822  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            128     7,855,999     7,855,872   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D9-0806                              vfat       DellUtility                   
/dev/sda2        0A14B1BE14B1AD57                       ntfs                                     
/dev/sda3        9CD88714D886EC38                       ntfs       New Volume                    
/dev/sda5        542C93142C92EFEA                       ntfs       movies                        
/dev/sda6        8224AB4624AB3BD3                       ntfs       shahrukh                      
/dev/sda7        0bc74cba-8111-476e-92a7-2afc12329182   swap                                     
/dev/sda8        d66d3364-9f58-4b4d-94b0-d2cbc905872c   ext3                                     
/dev/sdb1        C4A9-E2A0                              vfat       NABS                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/NABS              vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda8/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d66d3364-9f58-4b4d-94b0-d2cbc905872c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d66d3364-9f58-4b4d-94b0-d2cbc905872c

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        d66d3364-9f58-4b4d-94b0-d2cbc905872c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=d66d3364-9f58-4b4d-94b0-d2cbc905872c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-17-generic
uuid        d66d3364-9f58-4b4d-94b0-d2cbc905872c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=d66d3364-9f58-4b4d-94b0-d2cbc905872c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=d66d3364-9f58-4b4d-94b0-d2cbc905872c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0bc74cba-8111-476e-92a7-2afc12329182 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 100.1GB: boot/grub/core.img
 100.1GB: boot/grub/menu.lst
 100.1GB: boot/grub/stage2
 100.1GB: boot/initrd.img-2.6.28-17-generic
 100.1GB: boot/initrd.img-2.6.31-20-generic
 100.1GB: boot/vmlinuz-2.6.28-17-generic
 100.1GB: boot/vmlinuz-2.6.31-20-generic
 100.1GB: initrd.img
 100.1GB: vmlinuz



I M waiting
please help fast
Thanks

---

### Post by prodigy_ on 2010-04-12
There's a mismatch between Grub versions. In your /dev/sda MBR you now have Grub2, but config files on /dev/sda8 are for legacy Grub.

Try [this HOWTO](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD) to reinstall Grub2 from Live CD. Don't forget **sudo update-grub** command in the end (it creates a new boot menu).

---

### Post by nbulchandani on 2010-04-12
tried the step 
which uses this at the end
sudo grub-install --root-directory=/mnt/ /dev/sdX

but still the same on reboot:(

---

### Post by ajgreeny on 2010-04-12
> **nbulchandani said:**
> tried the step 
which uses this at the end
sudo grub-install --root-directory=/mnt/ /dev/sdX

but still the same on reboot:(
I trust you didn't actually type "sudo grub-install --root-directory=/mnt/ /dev/sd[COLOR=Red]X[COLOR=Black]"[/COLOR] [COLOR=Black]did you, but put the real /dev/sda?[/COLOR][/COLOR]

---

### Post by prodigy_ on 2010-04-12
Are you sure you did everything right? In your case, the exact commands should be: ```
sudo mount /dev/sda8 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
sudo update-grub
```

If these commands don't give you any errors, **grub.cfg** file should appear in your new **/boot/grub** directory on /dev/sda8 (instead of **menu.lst**).

---

### Post by nbulchandani on 2010-04-12
the second one finishes without any error...
update-grub says
grub-probe:error:cannot find a device for /.
newaz trying 2 reboot

---

### Post by nbulchandani on 2010-04-12
the same screen after reboot:(
it actually is as
GNU GRUB version 1.97~beta4
[minimal BASH-like commands work....]
sh:grub>



well...to be honest.. i tried these commands sometime before on my own.have i done a mistake

---

### Post by prodigy_ on 2010-04-12
That's strange. Well, you can try to chroot into your Linux installation from Live CD:

```
sudo mount /dev/sda8 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
```
Then you'll be able take the upgrade route: ```
sudo apt-get install grub2
sudo upgrade-from-grub-legacy
```

---

### Post by nbulchandani on 2010-04-13
:(...this live cd terminal says 
could not resolve 'in.archive.ubuntu.com'
downloading above packages manually

---

### Post by nbulchandani on 2010-04-13
how to use sudo update-from-grub-legacy...
says unable to resolve host ubuntu
:(:(

---

