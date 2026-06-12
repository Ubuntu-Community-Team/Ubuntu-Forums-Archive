---
title: "After re-installing grub, system seems to have backslid to a previous state"
date: 2011-02-27
forum: General Help
---

### Post by Nicezia on 2011-02-27
after i reinstalled grub on my 10.10 installation via my 10.04 liveCD my system seems to have backslid to a state before i upgraded to 10.10.

files that have been on my system for years gone in the wink of an eye... 

how could this have happened?

---

### Post by sikander3786 on 2011-02-27
It shouldn't have happened anyway. Are you sure there aren't multiple Ubuntu installs on your HDD?

Can you please boot Ubuntu and post the output of bootinfoscript as per instruction here to let us take a look at your boot and partition setup.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

### Post by Nicezia on 2011-02-27
this is the results i got.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on boot drive #2 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf
 => Windows is installed in the MBR of /dev/sdg
 => Syslinux is installed in the MBR of /dev/sdh

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

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    62,912,511    62,705,664   7 HPFS/NTFS
/dev/sda3          62,914,381   117,226,304    54,311,924   f W95 Ext d (LBA)
/dev/sda5          62,914,383    83,885,759    20,971,377   7 HPFS/NTFS
/dev/sda6          83,891,493    91,891,799     8,000,307  82 Linux swap / Solaris
/dev/sda7          91,891,863   117,226,304    25,334,442  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   234,441,646   234,441,584   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 251.0 GB, 250999111168 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490232639 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   490,223,474   490,223,412  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63   976,773,166   976,773,104   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 4051 MB, 4051697152 bytes
255 heads, 63 sectors/track, 492 cylinders, total 7913471 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             63     7,913,470     7,913,408   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3680C15D80C123E9                       ntfs       System Reserved               
/dev/sda2        E8A8E3E9A8E3B3EA                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        6CC8F582C8F54ABA                       ntfs       10GB_NTFS                     
/dev/sda6        d1e07ee9-9265-4263-a722-3916771642f4   swap                                     
/dev/sda7        304d2425-01f8-4495-ad3e-4a06f7bc3bf0   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        db449cb4-4a38-4c6d-959e-d215e7bed2e1   ext4       233GB_1                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2958A57970A33B11                       ntfs       700GB                         
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        6490940D9093E438                       ntfs       111GB                         
/dev/sdd: PTTYPE="dos" 
/dev/sde1        164452ca-cd35-425b-938b-c41f17dbf261   ext4       233GB_2                       
/dev/sde: PTTYPE="dos" 
/dev/sdf1        938e6aa8-c534-4eac-8b24-55670e84c8da   ext4       465GB_2                       
/dev/sdf: PTTYPE="dos" 
/dev/sdg1        5f090f88-4b64-4e61-92b2-ee2038c51c1f   ext4       465GB_1                       
/dev/sdg: PTTYPE="dos" 
/dev/sdh1        08EA-608B                              vfat       TECHNUTS                      
/dev/sdh: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda5        /media/10GB_NTFS         fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/111GB             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=512,default_permissions)
/dev/sdb1        /media/233GB_1           ext4       (rw,nosuid,nodev,noatime)
/dev/sde1        /media/233GB_2           ext4       (rw,nosuid,nodev,noatime)
/dev/sdg1        /media/465GB_1           ext4       (rw,nosuid,nodev,noatime)
/dev/sdf1        /media/465GB_2           ext4       (rw,nosuid,nodev,noatime)
/dev/sdc1        /media/700GB             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdh1        /media/TECHNUTS          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/Windows           fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/E8A8E3E9A8E3B3EA  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=304d2425-01f8-4495-ad3e-4a06f7bc3bf0

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

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-28-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic (recovery mode)
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro  single
initrd		/boot/initrd.img-2.6.32-28-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-27-generic
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-27-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-27-generic (recovery mode)
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro  single
initrd		/boot/initrd.img-2.6.32-27-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-24-generic
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-22-generic
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.28-11-generic
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Chainload into GRUB 2
root		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/grub/core.img

title		Ubuntu 10.04.2 LTS, memtest86+
uuid		304d2425-01f8-4495-ad3e-4a06f7bc3bf0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
chainloader	+1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdb7 :
UUID=304d2425-01f8-4495-ad3e-4a06f7bc3bf0	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb5 :
UUID=6CC8F582C8F54ABA				/media/10GB_NTFS		ntfs-3g		defaults,user,locale=en_US.UTF-8,umask=000	0	0
UUID=6490940D9093E438				/media/111GB			ntfs-3g		defaults,user,locale=en_US.UTF-8,umask=000	0	0
UUID=db449cb4-4a38-4c6d-959e-d215e7bed2e1	/media/233GB_1			ext4		rw,user,auto,exec,noatime         		0	0
UUID=164452ca-cd35-425b-938b-c41f17dbf261 	/media/233GB_2 			ext4 		rw,user,auto,exec,noatime         		0       0
UUID=5f090f88-4b64-4e61-92b2-ee2038c51c1f	/media/465GB_1			ext4		rw,user,auto,exec,noatime			0	0
UUID=938e6aa8-c534-4eac-8b24-55670e84c8da	/media/465GB_2 			ext4 		rw,user,auto,exec,noatime         		0       0
UUID=3680C15D80C123E9				/media/Windows			ntfs-3g		defaults,user,locale=en_US.UTF-8,umask=000	0	0
UUID=2958A57970A33B11				/media/700GB			ntfs-3g		defaults,user,locale=en_US.UTF-8,umask=000	0	0
#Entry for /dev/sdb6 :
UUID=d1e07ee9-9265-4263-a722-3916771642f4	none	swap	sw	0	0
/dev/scd1	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0



=================== sda7: Location of files loaded by Grub: ===================


  55.4GB: boot/grub/core.img
  55.0GB: boot/grub/menu.lst
  55.3GB: boot/grub/stage2
  55.1GB: boot/initrd.img-2.6.28-11-generic
  55.2GB: boot/initrd.img-2.6.31-22-generic
  55.0GB: boot/initrd.img-2.6.32-24-generic
  55.9GB: boot/initrd.img-2.6.32-27-generic
  56.6GB: boot/initrd.img-2.6.32-28-generic
  55.1GB: boot/vmlinuz-2.6.28-11-generic
  54.9GB: boot/vmlinuz-2.6.31-22-generic
  55.1GB: boot/vmlinuz-2.6.32-24-generic
  55.7GB: boot/vmlinuz-2.6.32-27-generic
  55.7GB: boot/vmlinuz-2.6.32-28-generic
  56.6GB: initrd.img
  55.9GB: initrd.img.old
  55.7GB: vmlinuz
  55.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  9e 72 c3 c5 82 af 5b 8f  7f 5e 5d b3 3b b1 e1 fc  |.r....[..^].;...|
00000010  11 da e8 f6 55 ef 8f 74  1d f5 f1 c2 29 b5 1c db  |....U..t....)...|
00000020  f4 51 97 c5 80 07 de 0f  6a 9e ce 65 7e b5 7d 72  |.Q......j..e~.}r|
00000030  f5 2a 3c 8e cb 76 ab b4  4c 2f c2 81 9f 9e 8a 12  |.*<..v..L/......|
00000040  d4 f4 a9 fd f9 13 3c 76  8d d3 7f 12 7d 42 9f 72  |......<v....}B.r|
00000050  70 7a ee d8 a6 bf 22 97  57 3b a1 9b 1e e3 eb ea  |pz....".W;......|
00000060  91 2c e2 2c 3a ca 63 1c  7a c8 b5 4a 33 96 31 39  |.,.,:.c.z..J3.19|
00000070  22 fd 1f b3 ac 88 4c 99  b1 3e db 0b 55 76 90 85  |".....L..>..Uv..|
00000080  b7 c3 b5 7c 8d 8b b5 30  5c 1b f6 40 f7 d6 d2 f5  |...|...0\..@....|
00000090  71 16 86 fd 70 d0 e3 39  ce d1 1c 44 42 d3 d3 30  |q...p..9...DB..0|
000000a0  ee 11 bd 1d 86 51 4f 98  30 b1 cf 67 7d de 0b e3  |.....QO.0..g}...|
000000b0  48 cf 12 7b d2 a6 9e 31  1e 31 b2 4b 46 4a 2e fa  |H..{...1.1.KFJ..|
000000c0  89 9e 91 b5 cf 13 ae 0b  58 7b 2e a5 49 04 59 8b  |........X{..I.Y.|
000000d0  5c 62 3a 5e a8 33 61 fa  49 2f 34 a9 50 f8 de 62  |\b:^.3a.I/4.P..b|
000000e0  30 a6 ef ed 45 44 c9 3a  e1 39 57 a1 a5 6c 14 46  |0...ED.:.9W..l.F|
000000f0  44 6f 1d 8c c2 5e 54 d3  5e 31 14 a3 7e 44 34 9f  |Do...^T.^1..~D4.|
00000100  8c a2 24 8e 4a a5 55 c2  87 11 f0 3e 6f 35 db 40  |..$.J.U....>o5.@|
00000110  b2 56 7f 46 fa 7c d3 52  87 4b bd d6 e8 58 2c e4  |.V.F.|.R.K...X,.|
00000120  b5 46 e3 71 4a 6b 7b ad  03 4a d6 e2 aa f3 e8 ed  |.F.qJk{..J......|
00000130  04 6e db 0d e2 3d fc a6  9f 26 e2 4f 1d 0b 5c 1d  |.n...=...&.O..\.|
00000140  ac 72 35 e9 a6 a7 18 68  ea fd f1 a6 9b 22 7a 42  |.r5....h....."zB|
00000150  ad 7f 46 3a d6 7e be e1  be 77 d3 ce 62 b6 d4 cd  |..F:.~...w..b...|
00000160  e7 b0 fd 39 16 a3 d9 f1  55 6e 37 24 04 f6 09 ad  |...9....Un7$....|
00000170  8d 64 97 dc 29 30 40 46  5f 05 9e b8 65 5d 3f 3c  |.d..)0@F_...e]?<|
00000180  6f b7 9f 1f 0a e5 24 df  77 32 f7 ce 75 11 39 bc  |o.....$.w2..u.9.|
00000190  82 d3 fe 1d 3f 6e fb 6a  f3 64 ae 08 fd 7f ab 8b  |....?n.j.d......|
000001a0  f5 6f 54 97 bb ed 2d 50  da 0f 4b 31 39 1b 1f 21  |.oT...-P..K19..!|
000001b0  6b 7c 19 e7 e5 74 1b db  5b 0d 1b 17 6d ef 00 ef  |k|...t..[...m...|
000001c0  ff ff 07 ef ff ff 02 00  00 00 71 ff 3f 01 00 fe  |..........q.?...|
000001d0  ff ff 05 fe ff ff 99 15  40 01 72 13 7a 00 00 00  |........@.r.z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by sikander3786 on 2011-02-27
Only a single Ubuntu install is there. Check under System > Administration > System Monitor and see which Ubuntu release it lists.

And where were your personal files stored previously? On the same partition or some other one?

---

### Post by Nicezia on 2011-02-27
its listed as 10.04 (lucid)

the kernel is listed as 2.6.32-28

---

### Post by Nicezia on 2011-02-27
luckily all my REALLY important files are kept on drives other than my installation drive, what i'm really worried about is i finally had my system set up like i wanted it (and had seriously tweaked it to a personal peak performance) been comfy with it for several months. But i decided to update my hdd install of windows to windows7 (which i was previously running in a VM) and then i restore grub, and as i boot into Ubuntu, i immediately realized something was wrong (theme was wrong, sound scheme background) went back to edit the XBMC skin i was working on, and ... its not installed!!

its no biggie, but i would like to know what happened... its almost like i did a equivalent to a *shivers* "Windows System Restore"

---

### Post by sikander3786 on 2011-02-27
Yes that sounds strange. Luckily, all your data is safe.

I would also want to find the answer to what happened when you re-installed Grub.

Most of the Ubuntu users are waiting for a 'System Restore' like app in Ubuntu. Is it already there and you discovered it :-P

I hope some-one else can jump in and make note of some important log files that can help diagnose the happenings here.

---

