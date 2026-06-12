---
title: "Grub has gone crazy - random errors 16 and 18"
date: 2010-08-18
forum: General Help
---

### Post by Starlight on 2010-08-18
Hi!

Because I have Windows and two different Linux distributions installed, I have two GRUBs on my system. The first one that starts when I boot the computer is Linux Mint's GRUB. It can run Mint, Windows, or Kubuntu's GRUB, which in turn can run Kubuntu. Right now I mostly use Kubuntu, but I haven't changed the setup of the GRUBs because it worked. Until yesterday, when Mint's GRUB worked well, but Kubuntu's GRUB gave me an error while trying to run Kubuntu. I restarted the computer a few times, and it happened every time. Sometimes the errors I got were 16 and sometimes 18. Occasionally, even the first GRUB had errors. 

I thought that maybe something's wrong with my hard disk, so I booted from a Kubuntu Live CD and did a fsck, which showed no errors at all (except that it's rather suspicious, because it checked the partition instantly, is it supposed to work like that?).  Then, I reinstalled Kubuntu's GRUB and rebooted the computer. This time, everything went well! I even rebooted it later once, and didn't get any errors.

Today, I got up and wanted to use the computer, and it gave me the same errors again. :O I rebooted a few times, and it was just like before. Then, I booted from the Live CD, there I didn't start the system, but I picked "boot from hard drive" and it miraculously worked. This is weird. What could possibly cause these errors? I haven't even installed or updated anything recently.

---

### Post by coffeecat on 2010-08-18
Some thoughts.

You refer to grub errors 16 and 18, which suggests you have legacy grub, not grub 2. This means that your Mint and Kubuntu versions will be based on Ubuntu 9.04 or earlier. Am I correct? Or did you start with a pre-9.10 version of either/both and do a dist-upgrade? Ubuntu 9.10 and later (and Kubuntu and Mint derivatives) came with grub 2, but you retain legacy grub if you upgrade from an earlier version.

Anyway, from [legacy grub manual]("http://www.gnu.org/software/grub/manual/legacy/"):

> 16 : Inconsistent filesystem structure
This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.and

> 18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).Since you are getting these errors inconsistently and at different times, and since fsck was OK, I suspect you may have a failing hard drive, rather than a problem with the filesystems themselves.

But  some information would be useful. It's not clear from your post whether you're using one grub to boot directly into the other Linux OS, or whether you're chainloading. Have a look [here]("http://bootinfoscript.sourceforge.net/"). Download and run the boot_info_script and post the contents of the RESULTS.txt here. Also, post the contents of /boot/grub/menu.lst from both Mint and Kubuntu.

---

### Post by Starlight on 2010-08-18
Thanks for the reply! Yes, both are legacy grubs. The first one is Mint's grub, and it can run Mint, Windows loader, and Kubuntu's grub (but not Kubuntu directly). Kubuntu's grub is for loading Kubuntu, but it still has the option to load the Windows loader.

And yes, these are exactly the errors I got. 

Here's the RESULTS.txt file, you can ignore all the sdb stuff, it's an old hard disk from another computer, it's only connected because I didn't want to lose some stuff there. And there's a huge mess on sda :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 82790240 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 7 Gloria - Main 
                       Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004799e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    14,683,409    14,683,347   b W95 FAT32
/dev/sda2          14,683,410    77,593,949    62,910,540   7 HPFS/NTFS
/dev/sda3          77,593,950    79,698,464     2,104,515  82 Linux swap / Solaris
/dev/sda4          79,698,465   312,576,704   232,878,240   5 Extended
/dev/sda5          79,698,528   111,153,734    31,455,207  83 Linux
/dev/sda6         111,153,798   270,406,079   159,252,282   b W95 FAT32
/dev/sda7         270,406,143   306,712,979    36,306,837  83 Linux
/dev/sda8         306,713,043   312,576,704     5,863,662  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12c412c3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    66,043,214    66,043,152   f W95 Ext d (LBA)
/dev/sdb5                 126     2,827,439     2,827,314  83 Linux
/dev/sdb6          16,450,623    66,043,214    49,592,592   b W95 FAT32
/dev/sdb7           2,827,503     3,196,934       369,432  82 Linux swap / Solaris
/dev/sdb8           3,196,998     4,160,834       963,837  83 Linux
/dev/sdb2          66,043,215    78,156,224    12,113,010  83 Linux
/dev/sdb4    *      4,160,835    16,450,559    12,289,725   b W95 FAT32

/dev/sdb1 overlaps with /dev/sdb4

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        408C-EA93                              vfat       &#65533;PNG
                        
/dev/sda2        D2008B2A008B149F                       ntfs                                     
/dev/sda3        302d06aa-d7bf-4b9b-b5fb-335d751cef3d   swap                                     
/dev/sda5        1a959b97-58c1-4df7-979d-d9a269312fa4   ext4                                     
/dev/sda6        9B37-D5C0                              vfat       GIGANT                        
/dev/sda7        be0127bc-fc7b-4433-85be-10f9549aa161   ext4                                     
/dev/sda8        3e4aa468-8df2-49ac-a51b-cd47f52ef0fc   swap                                     
/dev/sdb2        e2461f9a-a236-4de8-9940-e91ef82c030a   ext3                                     
/dev/sdb4        4645-1AF2                              vfat                                     
/dev/sdb6        17FD-2061                              vfat       DUZY GIK                      
/dev/sdb7        b10d537c-91eb-4e32-9bce-fe41abf8414a   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sdb4        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
/dev/sdb6        /media/DUZY GIK          vfat       (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
/dev/sda2        /media/disk-1            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7        /media/disk-2            ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb2        /media/disk-3            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda1        /media/?PNG             vfat       (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
/dev/sr1         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=piotrek)
/dev/sda6        /media/GIGANT            vfat       (rw,utf8,umask=007,gid=46)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

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
# kopt=root=UUID=1a959b97-58c1-4df7-979d-d9a269312fa4 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=1a959b97-58c1-4df7-979d-d9a269312fa4

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

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		1a959b97-58c1-4df7-979d-d9a269312fa4
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=1a959b97-58c1-4df7-979d-d9a269312fa4 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		1a959b97-58c1-4df7-979d-d9a269312fa4
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=1a959b97-58c1-4df7-979d-d9a269312fa4 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, memtest86+
uuid		1a959b97-58c1-4df7-979d-d9a269312fa4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1


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
UUID=1a959b97-58c1-4df7-979d-d9a269312fa4 /               ext4    relatime,errors=remount-ro 0       1
# /media/GIGANT was on /dev/sda6 during installation
UUID=9B37-D5C0  /media/GIGANT   vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda3 during installation
UUID=302d06aa-d7bf-4b9b-b5fb-335d751cef3d none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=3e4aa468-8df2-49ac-a51b-cd47f52ef0fc none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  54.9GB: boot/grub/menu.lst
  42.3GB: boot/grub/stage2
  47.3GB: boot/initrd.img-2.6.31-21-generic
  42.1GB: boot/vmlinuz-2.6.31-21-generic
  47.3GB: initrd.img
  42.1GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
##      altoptions=(single-user) single
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

title		Linux Mint 7 Gloria, kernel 2.6.28-13-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-13-generic root=/dev/sda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Linux Mint 7 Gloria, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-13-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Linux Mint 7 Gloria, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Kubuntu
root		(hd0,4)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Failsafe -- openSUSE 11.1 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-MAXTOR_STM3160815AS_6RA36BLA-part5 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a nopat 
initrd		/boot/initrd-2.6.27.7-9-default
savedefault
boot





=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=be0127bc-fc7b-4433-85be-10f9549aa161 /               ext4    relatime,errors=remount-ro 0       1
# /media/GIGANT was on /dev/sda6 during installation
UUID=9B37-D5C0  /media/GIGANT   vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda3 during installation
UUID=302d06aa-d7bf-4b9b-b5fb-335d751cef3d none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=3e4aa468-8df2-49ac-a51b-cd47f52ef0fc none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 140.5GB: boot/grub/menu.lst
 139.0GB: boot/grub/stage2
 139.6GB: boot/initrd.img-2.6.28-11-generic
 139.5GB: boot/initrd.img-2.6.28-13-generic
 140.3GB: boot/vmlinuz-2.6.28-11-generic
 139.4GB: boot/vmlinuz-2.6.28-13-generic
 139.5GB: initrd.img
 139.6GB: initrd.img.old
 139.4GB: vmlinuz
 140.3GB: vmlinuz.old

=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e2461f9a-a236-4de8-9940-e91ef82c030a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=e2461f9a-a236-4de8-9940-e91ef82c030a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=e2461f9a-a236-4de8-9940-e91ef82c030a ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=e2461f9a-a236-4de8-9940-e91ef82c030a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda4 -- converted during upgrade to edgy
UUID=4645-1AF2 /media/hda4 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=17FD-2061 /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hdb1       /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3 -- converted during upgrade to edgy
UUID=05eff86d-13d4-43ca-aa36-7f00649929c1 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
=================== sdb2: Location of files loaded by Grub: ===================


  36.6GB: boot/grub/menu.lst
  36.7GB: boot/grub/stage2
  37.5GB: boot/initrd.img-2.6.17-11-386.bak
  38.0GB: boot/initrd.img-2.6.20-16-386
  37.0GB: boot/initrd.img-2.6.20-16-386.bak
  36.7GB: boot/vmlinuz-2.6.20-16-386
  38.0GB: initrd.img
  36.7GB: vmlinuz

================================ sdb4/boot.ini: ================================

[boot loader]
timeout = 30
default = multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS = "Microsoft Windows XP Professional" /fastdetect
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb5

00000000  6d 65 72 5f 72 65 63 5f  74 00 69 6f 70 72 69 6f  |mer_rec_t.ioprio|
00000010  00 74 61 73 6b 5f 69 6f  5f 61 63 63 6f 75 6e 74  |.task_io_account|
00000020  69 6e 67 00 67 70 6c 5f  63 72 63 73 00 6b 65 65  |ing.gpl_crcs.kee|
00000030  70 5f 63 61 70 61 62 69  6c 69 74 69 65 73 00 73  |p_capabilities.s|
00000040  65 74 5f 69 6f 70 6c 5f  6d 61 73 6b 00 69 5f 75  |et_iopl_mask.i_u|
00000050  69 64 00 76 6d 5f 66 6c  61 67 73 00 67 65 74 5f  |id.vm_flags.get_|
00000060  78 73 74 61 74 65 00 6b  73 77 61 70 64 5f 6d 61  |xstate.kswapd_ma|
00000070  78 5f 6f 72 64 65 72 00  67 65 74 5f 77 61 6c 6c  |x_order.get_wall|
00000080  63 6c 6f 63 6b 00 61 72  67 30 00 61 72 67 31 00  |clock.arg0.arg1.|
00000090  61 72 67 32 00 70 67 70  72 6f 74 00 67 65 74 5f  |arg2.pgprot.get_|
000000a0  69 6e 66 6f 00 73 69 76  61 6c 5f 70 74 72 00 66  |info.sival_ptr.f|
000000b0  69 72 73 74 5f 74 69 6d  65 5f 73 6c 69 63 65 00  |irst_time_slice.|
000000c0  5f 5f 5f 65 61 78 00 6b  73 77 61 70 64 00 6d 6d  |___eax.kswapd.mm|
000000d0  5f 73 65 67 6d 65 6e 74  5f 74 00 64 5f 66 69 65  |_segment_t.d_fie|
000000e0  6c 64 6d 61 73 6b 00 73  73 69 7a 65 5f 74 00 61  |ldmask.ssize_t.a|
000000f0  72 67 73 00 5f 5f 63 61  63 68 65 6c 69 6e 65 5f  |rgs.__cacheline_|
00000100  66 69 6c 6c 65 72 00 5f  5f 6d 61 70 00 5f 5f 75  |filler.__map.__u|
00000110  33 32 00 5f 5f 5f 65 62  78 00 63 70 75 6d 61 73  |32.___ebx.cpumas|
00000120  6b 5f 74 00 72 61 77 5f  70 72 69 6f 5f 74 72 65  |k_t.raw_prio_tre|
00000130  65 5f 6e 6f 64 65 00 6e  6f 64 65 5f 73 70 61 6e  |e_node.node_span|
00000140  6e 65 64 5f 70 61 67 65  73 00 62 64 5f 70 61 72  |ned_pages.bd_par|
00000150  74 00 6e 75 6d 5f 75 6e  75 73 65 64 5f 67 70 6c  |t.num_unused_gpl|
00000160  5f 73 79 6d 73 00 68 6c  69 73 74 5f 68 65 61 64  |_syms.hlist_head|
00000170  00 61 63 71 75 69 72 65  5f 64 71 75 6f 74 00 78  |.acquire_dquot.x|
00000180  38 36 5f 6d 61 73 6b 00  72 74 5f 6d 75 74 65 78  |86_mask.rt_mutex|
00000190  5f 77 61 69 74 65 72 00  64 71 5f 66 6c 61 67 73  |_waiter.dq_flags|
000001a0  00 73 61 76 65 64 5f 6e  61 6d 65 73 00 6b 69 5f  |.saved_names.ki_|
000001b0  6c 65 66 74 00 5f 5f 5f  65 63 78 00 69 5f 61 6c  |left.___ecx.i_al|
000001c0  6c 6f 63 5f 73 65 6d 00  71 69 64 5f 74 00 64 72  |loc_sem.qid_t.dr|
000001d0  6f 70 5f 69 6e 6f 64 65  00 75 6d 61 73 6b 00 77  |op_inode.umask.w|
000001e0  6f 72 6b 5f 66 75 6e 63  5f 74 00 70 74 72 61 63  |ork_func_t.ptrac|
000001f0  65 00 70 61 72 61 76 69  72 74 5f 65 6e 61 62 6c  |e.paravirt_enabl|
00000200

Unknown BootLoader  on sdb7

00000000  60 00 61 00 62 00 63 00  64 00 65 00 66 00 67 00  |`.a.b.c.d.e.f.g.|
00000010  68 00 69 00 6a 00 6b 00  6c 00 6d 00 6e 00 6f 00  |h.i.j.k.l.m.n.o.|
00000020  70 00 71 00 72 00 73 00  74 00 75 00 76 00 77 00  |p.q.r.s.t.u.v.w.|
00000030  78 00 79 00 7a 00 7b 00  7c 00 7d 00 7e 00 7f 00  |x.y.z.{.|.}.~...|
00000040  c7 00 fc 00 e9 00 e2 00  e4 00 6f 01 07 01 e7 00  |..........o.....|
00000050  42 01 eb 00 50 01 51 01  ee 00 79 01 c4 00 06 01  |B...P.Q...y.....|
00000060  c9 00 39 01 3a 01 f4 00  f6 00 3d 01 3e 01 5a 01  |..9.:.....=.>.Z.|
00000070  5b 01 d6 00 dc 00 64 01  65 01 41 01 d7 00 0d 01  |[.....d.e.A.....|
00000080  e1 00 ed 00 f3 00 fa 00  04 01 05 01 7d 01 7e 01  |............}.~.|
00000090  18 01 19 01 ac 00 7a 01  0c 01 5f 01 ab 00 bb 00  |......z..._.....|
000000a0  91 25 92 25 93 25 02 25  24 25 c1 00 c2 00 1a 01  |.%.%.%.%$%......|
000000b0  5e 01 63 25 51 25 57 25  5d 25 7b 01 7c 01 10 25  |^.c%Q%W%]%{.|..%|
000000c0  14 25 34 25 2c 25 1c 25  00 25 3c 25 02 01 03 01  |.%4%,%.%.%<%....|
000000d0  5a 25 54 25 69 25 66 25  60 25 50 25 6c 25 a4 00  |Z%T%i%f%`%P%l%..|
000000e0  11 01 10 01 0e 01 cb 00  0f 01 47 01 cd 00 ce 00  |..........G.....|
000000f0  1b 01 18 25 0c 25 88 25  84 25 62 01 6e 01 80 25  |...%.%.%.%b.n..%|
00000100  d3 00 df 00 d4 00 43 01  44 01 48 01 60 01 61 01  |......C.D.H.`.a.|
00000110  54 01 da 00 55 01 70 01  fd 00 dd 00 63 01 b4 00  |T...U.p.....c...|
00000120  ad 00 dd 02 db 02 c7 02  d8 02 a7 00 f7 00 b8 00  |................|
00000130  b0 00 a8 00 d9 02 71 01  58 01 59 01 a0 25 a0 00  |......q.X.Y..%..|
00000140  00 01 02 03 04 05 06 07  08 09 0a 0b 0c 0d 0e 0f  |................|
00000150  10 11 12 13 14 15 16 17  18 19 1a 1b 1c 1d 1e 1f  |................|
00000160  20 21 22 23 24 25 26 27  28 29 2a 2b 2c 2d 2e 2f  | !"#$%&'()*+,-./|
00000170  30 31 32 33 34 35 36 37  38 39 3a 3b 3c 3d 3e 3f  |0123456789:;<=>?|
00000180  40 41 42 43 44 45 46 47  48 49 4a 4b 4c 4d 4e 4f  |@ABCDEFGHIJKLMNO|
00000190  50 51 52 53 54 55 56 57  58 59 5a 5b 5c 5d 5e 5f  |PQRSTUVWXYZ[\]^_|
000001a0  60 61 62 63 64 65 66 67  68 69 6a 6b 6c 6d 6e 6f  |`abcdefghijklmno|
000001b0  70 71 72 73 74 75 76 77  78 79 7a 7b 7c 7d 7e 7f  |pqrstuvwxyz{|}~.|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  ff 00 00 00 cf 00 00 f5  f9 00 00 ae aa f0 00 00  |................|
000001f0  f8 00 00 00 ef 00 00 00  f7 00 00 af 00 00 00 00  |................|
00000200

Unknown BootLoader  on sdb8

00000000  6d 65 61 6e 73 29 33 30  20 62 28 74 68 65 29 68  |means)30 b(the)h|
00000010  28 53 47 4d 4c 29 66 0a  28 64 65 63 6c 61 72 61  |(SGML)f.(declara|
00000020  74 69 6f 6e 29 67 28 73  70 29 73 28 65 63 69 5c  |tion)g(sp)s(eci\|
00000030  30 31 34 65 64 29 66 28  69 6e 29 67 28 74 68 65  |014ed)f(in)g(the|
00000040  29 68 28 73 67 6d 6c 2d  64 65 63 6c 61 72 61 74  |)h(sgml-declarat|
00000050  69 6f 6e 29 67 28 76 29  2d 35 0a 62 28 61 72 69  |ion)g(v)-5.b(ari|
00000060  61 62 6c 65 29 33 39 30  20 32 38 34 30 20 79 20  |able)390 2840 y |
00000070  46 6b 28 5c 30 34 35 64  29 33 38 34 20 62 20 46  |Fk(\045d)384 b F|
00000080  6f 28 6d 65 61 6e 73 29  32 38 20 62 28 74 68 65  |o(means)28 b(the|
00000090  29 67 28 5c 30 31 34 6c  65 29 66 28 63 6f 6e 29  |)g(\014le)f(con)|
000000a0  6d 0a 28 74 61 69 6e 69  6e 67 29 67 28 74 68 65  |m.(taining)g(the|
000000b0  29 69 28 44 4f 43 54 59  50 45 29 65 28 64 65 63  |)i(DOCTYPE)e(dec|
000000c0  6c 61 72 61 74 69 6f 6e  2c 29 68 28 69 66 29 66  |laration,)h(if)f|
000000d0  28 6e 6f 74 29 68 28 69  6e 29 66 28 74 68 65 29  |(not)h(in)f(the)|
000000e0  68 0a 28 62 75 5c 30 31  33 65 72 29 33 39 30 20  |h.(bu\013er)390 |
000000f0  32 39 39 35 20 79 28 54  68 65 29 69 28 64 65 66  |2995 y(The)i(def|
00000100  61 75 6c 74 29 66 28 76  29 2d 35 20 62 28 61 6c  |ault)f(v)-5 b(al|
00000110  75 65 29 33 30 20 62 28  69 73 29 67 0a 46 6b 28  |ue)30 b(is)g.Fk(|
00000120  6e 73 67 6d 6c 73 29 65  28 2d 73 29 69 28 5c 30  |nsgmls)e(-s)i(\0|
00000130  34 35 73 29 67 28 5c 30  34 35 73 29 70 20 46 6f  |45s)g(\045s)p Fo|
00000140  28 2e 29 33 33 38 36 20  33 32 32 30 20 79 28 55  |(.)3386 3220 y(U|
00000150  73 65 72 29 68 28 4f 70  74 69 6f 6e 29 2d 33 37  |ser)h(Option)-37|
00000160  32 36 0a 62 20 46 66 28  73 67 6d 6c 2d 76 29 2d  |26.b Ff(sgml-v)-|
00000170  36 20 62 28 61 6c 69 64  61 74 65 2d 5c 30 31 34  |6 b(alidate-\014|
00000180  6c 65 73 29 33 39 30 20  33 33 32 39 20 79 20 46  |les)390 3329 y F|
00000190  6f 28 49 66 29 33 39 0a  62 28 6e 6f 6e 2d 6e 69  |o(If)39.b(non-ni|
000001a0  6c 2c 29 67 28 61 29 67  28 66 75 6e 63 74 69 6f  |l,)g(a)g(functio|
000001b0  6e 29 66 28 6f 66 29 68  28 6e 6f 29 67 28 61 72  |n)f(of)h(no)g(ar|
000001c0  67 75 6d 65 6e 29 6d 28  74 73 29 67 28 74 68 61  |gumen)m(ts)g(tha|
000001d0  74 29 68 28 72 65 74 75  72 6e 73 29 65 0a 28 61  |t)h(returns)e.(a|
000001e0  29 68 28 6c 69 73 74 29  66 28 6f 66 29 68 28 5c  |)h(list)f(of)h(\|
000001f0  30 31 34 6c 65 29 66 28  6e 61 6d 65 73 2e 29 36  |014le)f(names.)6|
00000200

```

Here's Kubuntu's menu.lst:

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
# kopt=root=UUID=1a959b97-58c1-4df7-979d-d9a269312fa4 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=1a959b97-58c1-4df7-979d-d9a269312fa4

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

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		1a959b97-58c1-4df7-979d-d9a269312fa4
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=1a959b97-58c1-4df7-979d-d9a269312fa4 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		1a959b97-58c1-4df7-979d-d9a269312fa4
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=1a959b97-58c1-4df7-979d-d9a269312fa4 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, memtest86+
uuid		1a959b97-58c1-4df7-979d-d9a269312fa4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1


```

And here's Mint's menu.lst:

```
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
##      altoptions=(single-user) single
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

title		Linux Mint 7 Gloria, kernel 2.6.28-13-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-13-generic root=/dev/sda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Linux Mint 7 Gloria, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-13-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Linux Mint 7 Gloria, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Kubuntu
root		(hd0,4)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Failsafe -- openSUSE 11.1 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-MAXTOR_STM3160815AS_6RA36BLA-part5 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a nopat 
initrd		/boot/initrd-2.6.27.7-9-default
savedefault
boot

```

---

### Post by coffeecat on 2010-08-18
I've re-read your first post and I would still say that a failing hard drive is possible. Not definite, but you would be well advised to backup all your data as a precaution. I see that Vista is spread over partitions #1 and #2. Is that a manufacturer's install, or did you install from a Microsoft Vista DVD? I ask because, if the drive is failing, you might need to reinstall Vista. Do you have an install DVD or a manufacturer's OEM restore disc just in case?

Anyway, looking at your script output and the two menu.lst files I see that you have Kubuntu on sda5 and Mint on sda7. Grub stage 1 in the MBR is pointing to sda5, which is consistent with your reinstalling Kubuntu's grub. However, there is no entry for Mint in your Kubuntu grub menu, so you can't boot Mint at the moment. I see that the Mint menu has a chainloading entry for Kubuntu on sda5, and since grub stage 1 is still in the boot sector of partition #5, if you reinstall grub stage 1 for the Mint grub, you should be able to boot both Kubuntu and Mint again. Do you need help with that?

I know that doesn't solve the grub error issue, but it might be an idea to reinstall the Mint grub stage 1 to see if there is any pattern to the grub errors, although if this is a failing drive you will probably get inconsistent messages as before. I'd be surprised if this is a filesystem problem, seeing as fsck didn't need to do anything.

---

### Post by Starlight on 2010-08-18
Hi!

I can still boot Mint without any problems. When I boot the computer, I get Mint's grub first, and the if I select Kubuntu, I get Kubuntu's grub. When I reinstalled Kubuntu's grub, I did it on Kubuntu's partition, so that I didn't lose Mint's grub. :)

Hmm... if it's a failing hard drive, are there some Linux programs that could check it to see what's wrong?

---

### Post by coffeecat on 2010-08-19
> **Starlight said:**
> When I reinstalled Kubuntu's grub, I did it on Kubuntu's partition, so that I didn't lose Mint's grub. :)

Yes, I see what you mean. A good way of doing it.

> **Starlight said:**
> Hmm... if it's a failing hard drive, are there some Linux programs that could check it to see what's wrong?

With the emphasis on **if** - but it's wise to be prepared for the worst - the palimpsest disk utility might help, but with two caveats.

It's a gnome app so will bring in a load of gnome dependencies if you install it in Kubuntu (unless it's already installed), and I don't think it was available in the version of Ubuntu (Jaunty/9.04) that your Mint is based on.

I've got Ubuntu Karmic (9.10 - the same version as your Kubuntu) and Maverick alpha/10.10 on this laptop and I've just compared the versions of palimpsest in the two. In Maverick, it shows the SMART ([Wikipedia on SMART]("http://en.wikipedia.org/wiki/S.M.A.R.T.")) status of the hard drive and can do a self-test, but in Karmic it reports smart status not available. Whether that's a limitation of the Karmic version or whether that's an issue between palimsest and my particular hard drive, I don't know.

And, if I remember correctly, the version of palimpest in Karmic was giving out false positives for some people in Karmic. Having said that, you could try installing palimpsest in Kubuntu (the package is gnome-disk-utility) and see what it reports.

If that doesn't work, try downloading and burning the live CD for the gnome version of Ubuntu Lucid (10.04) and running that live. You can find palimpsest under System > Administration > Disk Utility in gnome, but I don't know where it will be in KDE.

In the meantime, I'll have a look around and see if there are any other apps which might help.

---

### Post by Starlight on 2010-08-19
Thanks, I've tried the gnome disk utility on my Kubuntu, but it doesn't really seem to have any options... There's "check file system" available after unmounting. It shows no errors on one of the partitions, when I checked Mint's partition it said "file system is not clean" but it didn't give any details. So I closed it and tried running fsck on that partition, but it said "device or resource busy" even though it's not mounted.

However, it says that SMART is not available :( Is there anything like scandisk for Linux that just checks everything on the disk looking for errors?

edit: I've googled and found that there's a program called "badblocks" in Linux and it can check a disk. I'm trying it :) Right now it appears to be doing nothing at all... it's running but doesn't show any status or anything :O

edit 2: It hasn't found any bad blocks on Mint's partition, even though Mint's grub also had these errors, even sometimes it wasn't able to open some gfx file...

---

### Post by coffeecat on 2010-08-19
> **Starlight said:**
> However, it says that SMART is not available :( Is there anything like scandisk for Linux that just checks everything on the disk looking for errors?

Yes, I got SMART not available with the Karmic version, but with the Lucid and Maverick versions I get a whole load of SMART data and a "Run Self Test" option. Which would seem to be what scandisk does. Have you thought about my suggestion of downloading the Lucid live CD and running it to get the later version of disk utility so that you can do a SMART test? It comes on the live CD. 

> **Starlight said:**
>  edit: I've googled and found that there's a program called "badblocks" in Linux and it can check a disk. I'm trying it :) Right now it appears to be doing nothing at all... it's running but doesn't show any status or anything :O

edit 2: It hasn't found any bad blocks on Mint's partition, even though Mint's grub also had these errors, even sometimes it wasn't able to open some gfx file...

I believe there's more to SMART data than bad blocks.

---

### Post by Starlight on 2010-08-19
I actually have the newest Kubuntu Live CD somewhere around, I'll try to run Palimpsest from there, if it's possible. :)


edit: ok, I did the longest one of the three SMART tests, and it seems that there are no problems. The overall assessment is that the disk is healthy, and the only assessment that failed was airflow temperature, but it seems that it's just a little above normal.

---

### Post by coffeecat on 2010-08-19
That's interesting. And good news I suppose. It's not pleasant to contemplate a possible hard drive failure.

Which leads us back to why you were getting those grub error messages - and intermittently. At the moment I have no further ideas. Like you I find the near-instantaneous report from fsck of a clean filesystem somewhat unnerving. I've never worked out how to force fsck to do the long-winded check it does every 20-30 bootups.

---

### Post by Starlight on 2010-08-19
To be honest, I don't really believe fsck when it instantly tells me that everything's ok without even taking time to check everything... it's strange.


And here's another strange thing, I've recently noticed that a Windows partition (sda1) has a very strange label in KDE, I've attached a screenshot.

I can browse that partition without any problems, and Windows XP there boots with no problems as well.

---

### Post by coffeecat on 2010-08-19
> **Starlight said:**
> And here's another strange thing, I've recently noticed that a Windows partition (sda1) has a very strange label in KDE, I've attached a screenshot.

I can browse that partition without any problems, and Windows XP there boots with no problems as well.

I wonder if it's an odd partition label, although I would have thought you wouldn't be able to have a ? in a VFAT label. I've little recent experience of KDE, but the equivalent in gnome to what you've posted would show the partition label or something like "30GB Hard Disk" if there's no label. Try this from a terminal:

```
sudo blkid
```That lists partition labels, UUIDs and filesystem types. It'll show whether that "?PNG" is a label. If it isn't, I haven't a clue. :wink:

Apologies - I only just noticed the "XP" in the script output you posted yesterday. So - do you have XP on sda1 and Vista on sda2? Because your Mint grub menu is chainloading "Vista" from sda1. I'm intrigued.

---

### Post by Starlight on 2010-08-19
Here's what that terminal command says:
```

/dev/sda1: LABEL="M-^IPNG^M^J^Z" UUID="408C-EA93" TYPE="vfat"
```


So it appears to be a label... I have no idea if I ever gave that partition any label, I think I didn't. But if I did, it definitely wasn't anything like that :D

Both Mint's grub and Kubuntu's grub can launch Vista's bootloader, and Vista's bootloader gives me the choice between Vista and XP. As I said, I have a huge mess there :D

---

### Post by coffeecat on 2010-08-20
> **Starlight said:**
> To be honest, I don't really believe fsck when it instantly tells me that everything's ok without even taking time to check everything... it's strange.

@Starlight, I think I've found something which might help here. When I do a fsck on an ext4 partition, it's very quick and simply tells me the filesystem is clean and lists the number of files and blocks. I think it simply reads the journal. However, I've discovered ([one useful link]("http://adminschoice.com/repairing-unix-file-system-fsck")) that there is a force option (-f) which, irritatingly, is not listed in the man pages. This is what I get:

```
coffeecat@AcerMavericAlpha:~$ sudo fsck -f /dev/sda8
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Lucid: 327209/983040 files (0.2% non-contiguous), 1378333/3931900 blocks
```That was on an ext4 partition labelled "Lucid". I get the same sort of output with an ext3 partition. It takes a few seconds, with the ext3 check a little quicker than the ext4 one - which is odd. It's still quicker than the filesystem check you get periodically on bootup, but it's obviously more thorough than using fsck without options. It might be worth trying.

I'll do some more digging and see if there are any other useful options which are not in the man pages.

Are you still getting the strange grub errors?

---

### Post by Starlight on 2010-08-20
I did it, here's the result for my Kubuntu partition. It seems that there are no errors.

```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 337277/983040 files (0.6% non-contiguous), 3126774/3931900 blocks

```


I had the grub problem again today in the morning. I booted the computer, in Mint's grub I picked Kubuntu, and it couldn't load Kubuntu's grub because of a "read error". I rebooted, and this time it loaded Kubuntu's grub, but it couldn't load Kubuntu because of an "inconsistent filesystem structure". I rebooted again, and everything worked well.

It's strange, but I seem to have these problems only in the morning when I turn the computer on. Later, when I reboot it a few times to open a different operating system, I don't get these errors at all...

---

### Post by coffeecat on 2010-08-20
> **Starlight said:**
> It's strange, but I seem to have these problems only in the morning when I turn the computer on. Later, when I reboot it a few times to open a different operating system, I don't get these errors at all...

Curious. The fact that you are getting "read error" or "inconsistent filesystem" at times but not others when everything works OK, suggests that there is a read problem. Which brings us back to the possibility of a hard drive hardware problem - even though the SMART test was OK. If you are getting problems only in the morning, could this be because the drive is cold and it works properly only when it's warmed up? I don't know - I've never heard of such a thing. It is summer at the moment (theoretically - you should see the weather we've been getting here. :wink:) so the drive won't be that cold even in an unheated room.

Hmm. If it was my machine, I'd replace the drive and put the old one in a USB enclosure as a secondary backup drive (in case it did fail).

---

### Post by Starlight on 2010-08-20
It's summer, but recently it has been quite cold actually. :) The last really hot day was a few days ago, before this weird thing started happening. So maybe it has something to do with heat :shock:

But these read errors are strange if they only happen in GRUB... I haven't had any problems with opening any files or browsing through them, no matter if I do it on Linux or on Windows... everything except GRUB is working perfectly well. Wouldn't the system show some errors at least sometimes if it had problems reading something on the disk?

I think I'll wait to see if it gets worse. I got a new laptop recently and it's going to become my main computer, but my parents want to be able to use Windows on this one. So as long as Windows works well, it's ok. I think I'll try doing Vista's chkdsk later just to make sure nothing bad is going on with Vista's partition.

---

### Post by coffeecat on 2010-08-20
<snip>

In the meantime - yes, it's odd that the errors only occur with grub. But best of luck with using that machine for Vista for your parents.

> **Starlight said:**
> So as long as Windows works well, it's ok.

How would you be able to tell? :p

---

### Post by Starlight on 2010-08-20
Thanks! I hope it's not going to get worse or something :D

---

