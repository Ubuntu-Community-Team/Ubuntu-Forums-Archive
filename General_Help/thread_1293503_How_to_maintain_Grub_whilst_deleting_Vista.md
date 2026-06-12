---
title: "How to maintain Grub whilst deleting Vista?"
date: 2009-10-17
forum: General Help
---

### Post by Pipps on 2009-10-17
Hello

**Summary**
I need help understanding on how to re-jig my local partitions without causing any subsequent boot problems with Grub. I would like to remove the Vista partition at sda2 and merge the free space into the XP partition at sda1. 

**Background**
I use Ubuntu for my everyday computing. Though I am required to maintian a more sizeable XP partition for client work. I previously needed Vista, but no longer use it. My Grub bootloader is located within its own separate partition. 

By way of additional background, I have used 'Boot Info Script 0.32' to create the following results file. I hope this helps. 

(My question is then located below.)

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 7 Gloria - Main 
                       Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda4 and looks 
                       at sector 924436402 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedf4edf4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   901,005,524   901,005,462   7 HPFS/NTFS
/dev/sda2         913,279,185   976,768,064    63,488,880   7 HPFS/NTFS
/dev/sda3         901,005,525   913,086,404    12,080,880  83 Linux
/dev/sda4         913,086,405   913,279,184       192,780  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cd17c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8589 MB, 8589934080 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777215 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="CE00E7B800E7A625" TYPE="ntfs" 
/dev/sda2: UUID="294A9CE43EA5868D" TYPE="ntfs" 
/dev/sda3: UUID="64c248b7-b0b3-4b72-8601-2734bb8f7838" TYPE="ext3" 
/dev/sda4: LABEL="GRUB" UUID="ea340f4c-def5-4a5e-9559-d20c1c3d12f7" TYPE="ext3" 
/dev/sdb1: UUID="1B75BED556178367" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rp)
/dev/sda4 on /media/GRUB type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN /NOGUIBOOT


=========================== sda3/boot/grub/menu.lst: ===========================

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

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color white/black white/red

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title Windows XP Performance Edition SP3
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

title Windows Vista SP2
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

title		Linux Mint 7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=64c248b7-b0b3-4b72-8601-2734bb8f7838 /               ext3    relatime,errors=remount-ro 0       1

=================== sda3: Location of files loaded by Grub: ===================


 466.6GB: boot/grub/menu.lst
 467.0GB: boot/grub/stage2
 466.6GB: boot/initrd.img-2.6.28-11-generic
 466.2GB: boot/vmlinuz-2.6.28-11-generic
 466.6GB: initrd.img
 466.2GB: vmlinuz

=========================== sda4/boot/grub/menu.lst: ===========================

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

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color white/black white/aqua

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title Windows XP Performance Edition SP3
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

title Windows Vista SP2
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

title		Linux Mint 7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

=================== sda4: Location of files loaded by Grub: ===================


 467.5GB: boot/grub/menu.lst
 467.5GB: boot/grub/stage2

```

**Question**
If I simply use GParted to delete sda2 and than expand sda1 to occupy the resulting free space, will this create problems for Grub on sda4, with issues such as partition sizing and indexing recognition?

Are there any recommended steps which I should take before performing such a procedure, to ensure that Grub does not get confused and crash when I next attempt to boot XP?

I know that some people might say *'just use the Super Grub Disc if you run into any problems'*, but I would prefer not to take this approach, as I believe that prevention is preferable to cure, especially where it provides the opportunity to learn something new about proper computing.

I hope this hasn't been too long a request. And I hope that someone might be able to advise me on the best way to approach this task. Any suggestions would be much appreciated.

Thank you. Pipps.

---

### Post by mikewhatever on 2009-10-17
You may have a problem with the Linux partition numbering. Ubuntu shouldn't care about it since it uses UUIDs instead of sdXY, but according to the menu.lst you use Linux Mint and not Ubuntu. If the partition numbering changes, you'll get boot errors from Grub and will have to modify the menu.lst using a live cd.
I'd also recommend making a backup of files on Windows, or clone the entire sda1 with Partimage or Clonezilla.

---

### Post by Pipps on 2009-10-18
Great advice. Thank you!

I will proceed first with Clonezilla, and report back shortly.

---

### Post by Pipps on 2009-11-05
I am pleased to report that you were entirely right!

It would appear that Linux only concerns itself with partition numbers, and not reference tables or any other nonsense.

When I moved and expanded the partitions on my local drive, the Grub bootloader simply picked up where it left off, and continued to recognise the partitions based on their continuing identification numbers.

I am very pleased with this! Thank you for your support! :)

---

