---
title: "Grub error 15"
date: 2011-05-07
forum: General Help
---

### Post by paul85 on 2011-05-07
I did an upgrade and now getting grub error 15 file not found on boot, memtest runs ok. any help would be appreciated.  system information is listed below:

Find /grub/stage1

	hd(1,0)


Menu.lst


title           Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic

root            (hd1,0)

kernel          /vmlinuz-2.6.24-28-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro quiet splash

initrd          /initrd.img-2.6.24-28-generic

quiet



title           Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)

root            (hd1,0)

kernel          /vmlinuz-2.6.24-28-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro single

initrd          /initrd.img-2.6.24-28-generic



title           Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic

root            (hd1,0)

kernel          /vmlinuz-2.6.24-24-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro quiet splash

initrd          /initrd.img-2.6.24-24-generic

quiet



title           Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)

root            (hd1,0)

kernel          /vmlinuz-2.6.24-24-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro single

initrd          /initrd.img-2.6.24-24-generic



title           Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic

root            (hd1,0)

kernel          /vmlinuz-2.6.24-23-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro quiet splash

initrd          /initrd.img-2.6.24-23-generic

quiet



title           Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)

root            (hd1,0)

kernel          /vmlinuz-2.6.24-23-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro single

initrd          /initrd.img-2.6.24-23-generic

                                                                                          
kernel          /vmlinuz-2.6.24-23-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro single

initrd          /initrd.img-2.6.24-23-generic



title           Ubuntu 8.04.4 LTS, kernel 2.6.24-22-generic

root            (hd1,0)

kernel          /vmlinuz-2.6.24-22-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro quiet splash

initrd          /initrd.img-2.6.24-22-generic

quiet



title           Ubuntu 8.04.4 LTS, kernel 2.6.24-22-generic (recovery mode)

root            (hd1,0)

kernel          /vmlinuz-2.6.24-22-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro single

initrd          /initrd.img-2.6.24-22-generic



title           Ubuntu 8.04.4 LTS, memtest86+

root            (hd1,0)

kernel          /memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title           Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title           Microsoft Windows XP Professional

root            (hd0,0)

#savedefault

#makeactive

chainloader     +1





Device map

(hd0)	/dev/sda

(hd1)	/dev/sdb


               Boot Info Script 0.55    dated February 15th, 2010                    

=========================== Boot Info Summary:============================

Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
in partition #1 for /grub/stage2 and /grub/menu.lst.
Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 6.06.1 LTS
    Boot files/dirs:   /etc/fstab

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000718f5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   125,837,144   125,837,082   7 HPFS/NTFS
/dev/sda2         125,837,145   251,674,289   125,837,145   b W95 FAT32
/dev/sda3         251,674,290   312,576,704    60,902,415  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000a135

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       208,844       208,782  83 Linux
/dev/sdb2             208,845    42,154,559    41,945,715  83 Linux
/dev/sdb3          42,154,560    84,100,274    41,945,715  83 Linux
/dev/sdb4          84,100,275   312,576,704   228,476,430   5 Extended
/dev/sdb5         311,532,480   312,576,704     1,044,225  82 Linux swap / Solaris
/dev/sdb6          84,100,401   126,045,989    41,945,589  83 Linux
/dev/sdb7         126,046,053   167,991,704    41,945,652  83 Linux
/dev/sdb8         167,991,768   209,937,419    41,945,652  83 Linux
/dev/sdb9         209,937,483   251,883,134    41,945,652  83 Linux
/dev/sdb10        251,883,198   272,847,959    20,964,762  83 Linux
/dev/sdb11        272,848,023   293,812,784    20,964,762  83 Linux
/dev/sdb12        293,812,848   311,516,414    17,703,567  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/cloop0                                             iso9660    KNOPPIX_FS                    
/dev/sda1        9C70C61570C5F5D4                       ntfs                                     
/dev/sda2        B44C-C27A                              vfat                                     
/dev/sda3        4d7d73c1-0a4b-4ee3-b584-d766b5a0a122   ext3                                     
/dev/sdb1        6eadcff1-3f7e-4c43-88c6-01652fbc361f   ext3                                     
/dev/sdb10       075757a8-d0ac-443b-b580-6bd514552cd3   ext3       /home                         
/dev/sdb11       1a302078-f33b-4dd8-adcc-eb7858cb1951   ext3       /home                         
/dev/sdb12       ff0645b7-9664-40f9-a998-4e2cc12f475a   ext3                                     
/dev/sdb2        7b99794c-382c-401c-bdba-1bb834789590   ext3       /                             
/dev/sdb3        61f3bcd4-2d71-4f31-bb17-0a354038278f   ext3                                     
/dev/sdb5        c949cb0c-695f-4a13-a034-b29c9cb89eca   swap                                     
/dev/sdb6        fba66d07-b467-4a29-9486-7b7894f651bf   ext3                                     
/dev/sdb7        c54ef932-6dd6-404b-b1d5-9b5444b5570f   ext3                                     
/dev/sdb8        e2463a54-b2fe-4853-b7ac-cc9b0881dc3a   ext3                                     
/dev/sdb9        199f9bec-6b4b-4d9e-8c85-4187bb4417c0   ext3                                     

================= "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw,relatime)
/dev/sr0         /mnt-system              iso9660    (ro,relatime)
/dev/cloop       /KNOPPIX                 iso9660    (ro,relatime)
/dev/sdb1        /media/sdb1              ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sdb2        /media/sdb2              ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sdb9        /media/sdb9              ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sdb8        /media/sdb8              ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sdb7        /media/sdb7              ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sdb6        /media/sdb6              ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sdb3        /media/sdb3              ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sdb12       /media/sdb12             ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sdb11       /media/sdb11             ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sdb10       /media/sdb10             ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sda3        /media/sda3              ext3       (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sda2        /media/sda2              vfat       (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0000,dmask=0000,allow_utime=0022,codepage=cp850,iocharset=iso8859-1,shortname=winnt,errors=remount-ro)
/dev/sda1        /media/sda1              fuseblk    (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000,allow_other,blksize=4096)


========================== sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


========================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122
 /            ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1 UUID=6eadcff1-3f7e-4c43-88c6-01652fbc361f
 /boot           ext3    defaults        0       2
# /dev/sdb10 UUID=075757a8-d0ac-443b-b580-6bd514552cd3
 /home           ext3    defaults        0       2
# /dev/sda1 UUID=9C70C61570C5F5D4
 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2 UUID=B44C-C27A
  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb11 UUID=1a302078-f33b-4dd8-adcc-eb7858cb1951
 /media/sdb11    ext3    defaults        0       2
# /dev/sdb12 UUID=ff0645b7-9664-40f9-a998-4e2cc12f475a
 /media/sdb12    ext3    defaults        0       2
# /dev/sdb2 UUID=7b99794c-382c-401c-bdba-1bb834789590
 /media/sdb2     ext3    defaults        0       2
# /dev/sdb3 UUID=61f3bcd4-2d71-4f31-bb17-0a354038278f
 /media/sdb3     ext3    defaults        0       2
# /dev/sdb6 UUID=fba66d07-b467-4a29-9486-7b7894f651bf
 /media/sdb6     ext3    defaults        0       2
# /dev/sdb7 UUID=c54ef932-6dd6-404b-b1d5-9b5444b5570f
 /media/sdb7     ext3    defaults        0       2
# /dev/sdb8 UUID=e2463a54-b2fe-4853-b7ac-cc9b0881dc3a
 /media/sdb8     ext3    defaults        0       2
# /dev/sdb9 UUID=199f9bec-6b4b-4d9e-8c85-4187bb4417c0
 /media/sdb9     ext3    defaults        0       2
# /dev/sdb5 UUID=c949cb0c-695f-4a13-a034-b29c9cb89eca none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
======================== sdb1/grub/menu.lst: =============================

# Splashimage line added by kubuntu-grub-splashimages package
#splashimage=(hd1,0)/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root		(hd1,0)
kernel		/vmlinuz-2.6.24-28-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro quiet splash
initrd		/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.24-28-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro single
initrd		/initrd.img-2.6.24-28-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root		(hd1,0)
kernel		/vmlinuz-2.6.24-24-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro quiet splash
initrd		/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.24-24-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro single
initrd		/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro quiet splash
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/vmlinuz-2.6.24-22-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro quiet splash
initrd		/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.24-22-generic root=UUID=4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ro single
initrd		/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd1,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
#savedefault
#makeactive
chainloader	+1


============== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: vmlinuz-2.6.24-24-generic
    .0GB: vmlinuz-2.6.24-28-generic

========================== sdb2/etc/fstab: ===============================

/etc/fstab: static file system information.

<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda10      /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/sda11      /media/sda11    ext3    defaults        0       2
/dev/sda12      /media/sda12    ext3    defaults        0       2
/dev/sda3       /media/sda3     ext3    defaults        0       2
/dev/sda6       /media/sda6     ext3    defaults        0       2
/dev/sda7       /media/sda7     ext3    defaults        0       2
/dev/sda8       /media/sda8     ext3    defaults        0       2
/dev/sda9       /media/sda9     ext3    defaults        0       2
/dev/sdb1       /media/sdb1     vfat    defaults        0       0
/dev/sdb2       /media/sdb2     ext3    defaults        0       2
/dev/sdb3       /media/sdb3     ext3    defaults        0       2
/dev/sdb5       /media/sdb5     ext3    defaults        0       2
/dev/sdb6       /media/sdb6     ext3    defaults        0       2
/dev/sdb7       /media/sdb7     ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

========================= StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

---

### Post by Hedgehog1 on 2011-05-08
Hi!

1) What version of Ubuntu were you upgrading to?

2) I am having a hard time figuring out your partition layout:

```
[B][COLOR="SeaGreen"]/dev/sda1 9C70C61570C5F5D4 ntfs [/COLOR]
/dev/sda2 B44C-C27A vfat 
[COLOR="Red"]/dev/sda3 4d7d73c1-0a4b-4ee3-b584-d766b5a0a122 ext3 
/dev/sdb1 6eadcff1-3f7e-4c43-88c6-01652fbc361f ext3[/COLOR] 
[COLOR="RoyalBlue"]/dev/sdb2 7b99794c-382c-401c-bdba-1bb834789590 ext3 / [/COLOR]
[COLOR="red"]/dev/sdb3 61f3bcd4-2d71-4f31-bb17-0a354038278f ext3 [/COLOR]
/dev/sdb5 c949cb0c-695f-4a13-a034-b29c9cb89eca swap 
[COLOR="red"]/dev/sdb6 fba66d07-b467-4a29-9486-7b7894f651bf ext3 
/dev/sdb7 c54ef932-6dd6-404b-b1d5-9b5444b5570f ext3 
/dev/sdb8 e2463a54-b2fe-4853-b7ac-cc9b0881dc3a ext3 
/dev/sdb9 199f9bec-6b4b-4d9e-8c85-4187bb4417c0 ext3[/COLOR]
[COLOR="RoyalBlue"]/dev/sdb10 075757a8-d0ac-443b-b580-6bd514552cd3 ext3 /home 
/dev/sdb11 1a302078-f33b-4dd8-adcc-eb7858cb1951 ext3 /home [/COLOR]
[COLOR="red"]/dev/sdb12 ff0645b7-9664-40f9-a998-4e2cc12f475a ext3[/COLOR][/B] 
```

The only partition that makes sense is the XP partition (/dev/sda1). Are these all in use in some way?

***The Hedge***

:KS

---

### Post by oldfred on 2011-05-08
Of late we have only  seen error 15 with grub2 conflicting with old grub legacy, but you are a long way from grub2.

[http://members.iinet.net.au/~herman546/p15.html#15]("http://members.iinet.net.au/%7Eherman546/p15.html#15")

You are booting from sdb1, but it is missing files.

.0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: vmlinuz-2.6.24-24-generic
    .0GB: vmlinuz-2.6.24-28-generic

You are missing the matching initrd files for the kernels your have. Not sure how they are missing. Do you have a liveCD of 8.04.4?

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Desktop supported until May 2011, server until April 2013.

Would you also go back and edit your post to use code tags around the boot script to make it easier to review. If you edit and use advanced you then get the full edit panel like a new post. Then you can highlight the boot script results you posted and then click the # which will add code tags around the highlighted area.

To go along with The Hedges post, I prefer to label my partitions just for my own sanity as when you get more than a few it is hard to keep track. I then often use that label as the mount so when mounted I know what is what and not just sdb5.

---

### Post by paul85 on 2011-05-08
Hedge

I origanally set up the system for FC 3, anticipating trying mutiple disto's,  when I moved to 6.04 I kept the partitions, some are empty. Any suggestions on how to simplify this?

Thanks

---

### Post by paul85 on 2011-05-09
oldfred,

This is what I am seeing through knoppix, the initd files appear to be in sda3.  During the upgrade could some of the files be moved or pointed to a different partition? 

/media/sdb1/vmlinuz-2.6.24-28-generic 1.9Mb
/media/sdb1/vmlinuz-2.6.24-24-generic 1.9Mb
/media/sdb1/System.map-2.6.24-28-generic 906k
/media/sdb1/System.map-2.6.24-24-generic 906k
/media/sdb1/memtest86+.bin 103k
/media/sdb1/config-2.6.24-28-generic 80k
/media/sdb1/config-2.6.24-24-generic 80k
/media/sdb1/abi-2.6.24-28-generic 423k
/media/sdb1/abi-2.6.24-24-generic 422k
/media/sdb1/lost+found
/media/sdb1/grub

/media/sdb1/grub/xfs_stage1_5 8k
/media/sdb1/grub/stage2 105k
/media/sdb1/grub/stage1 512b
/media/sdb1/grub/reiserfs_stage1_5 9k
/media/sdb1/grub/minix_stage1_5 6.8k
/media/sdb1/grub/menu.lst~ 6k
/media/sdb1/grub/menu.lst.071020204841 5k
/media/sdb1/grub/menu.lst 6k
/media/sdb1/grub/jfs_stage1_5 8k
/media/sdb1/grub/installed-version 16b
/media/sdb1/grub/fat_stage1_5 7k
/media/sdb1/grub/e2fs_stage1_5 7k
/media/sdb1/grub/device.map 30b
/media/sdb1/grub/default
/media/sdb1/grub/splashimages

sda3

knoppix@Microknoppix:/media/sda3$ ls -l
total 140
drwxr-xr-x   2 root root  4096 Oct 16  2008 Recycled
drwxr-xr-x   2 root root  4096 Oct  9  2010 bin
drwxr-xr-x   2 root root  4096 Nov  2  2006 boot
lrwxrwxrwx   1 root root    11 Nov  2  2006 cdrom -> media/cdrom
drwxr-xr-x   5 root root  4096 May 17  2008 dev
drwxr-xr-x 168 root root  8192 Dec 13 01:24 etc
drwxr-xr-x   2 root root  4096 Nov  2  2006 home
drwxr-xr-x   2 root root  4096 Oct 25  2006 initrd
lrwxrwxrwx   1 root root    33 Jun 16  2010 initrd.img -> boot/initrd.img-2.6.24-28-generic
lrwxrwxrwx   1 root root    33 Nov 25  2009 initrd.img.old -> boot/initrd.img-2.6.24-24-generic
drwxr-xr-x  19 root root  8192 Dec 12 23:09 lib
drwxr-xr-x   2 root root 49152 Nov  2  2006 lost+found
drwxr-xr-x  14 root root  4096 Dec 12 22:48 media
drwxr-xr-x   2 root root  4096 Oct 19  2006 mnt
drwxr-xr-x   4 root root  4096 May 20  2008 opt
drwxr-xr-x   2 root root  4096 Oct 19  2006 proc
drwxr-xr-x  41 root root  4096 Nov 25  2009 root
drwxr-xr-x   2 root root  8192 Dec 12 23:09 sbin
drwxr-xr-x   2 root root  4096 Oct 25  2006 srv
drwxr-xr-x   2 root root  4096 Oct 10  2006 sys
drwxrwxrwt  22 root root  8192 Dec 13 01:24 tmp
drwxr-xr-x  13 root root  4096 May 19  2008 usr
drwxr-xr-x  15 root root  4096 Oct 25  2006 var
lrwxrwxrwx   1 root root    30 Jun 16  2010 vmlinuz -> boot/vmlinuz-2.6.24-28-generic
lrwxrwxrwx   1 root root    30 Nov 25  2009 vmlinuz.old -> boot/vmlinuz-2.6.24-24-generic

---

### Post by oldfred on 2011-05-10
Your link in root show this:

initrd.img -> boot/initrd.img-2.6.24-28-generic

But you do not seem to be showing the initrd files? Everything else seems to be there, so it is not as if the folder was deleted. If you have copies on a LiveCd or backups you can copy them back into your system. Otherwise you may be able to chroot into your system from a liveCD and reinstall the kernels (which I think should update the initrd also).

I am not sure if there have been any changes to chroot. Most folders are the same. But you also have to mount both / & /boot.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
kansasnoob- full chroot one line version with &&----
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Older versions:
chroot to repair
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

sudo mount /dev/sda3 /mnt
sudo mount /dev/sdb1 /mnt/boot
for i in dev proc sys; do sudo mount --bind /$i /mnt/$i; done
sudo chroot  /mnt
sudo apt-get update 
sudo apt-get upgrade 
apt-get update
apt-get install linux-image-generic

---

### Post by paul85 on 2011-05-10
Thanks for the advice,I'll check for the initrd files,download a livecd and try the chroot suggestion.  I'll keep you updated,  it may be a few days due to work.

---

### Post by paul85 on 2011-05-14
Do files from the livecd have to be 8.04 or can I use the latest version I just downloaded>

---

