---
title: "dual boot problem"
date: 2009-09-30
forum: General Help
---

### Post by DannyJohansson on 2009-09-30
hello, i think this is simple but just can't get my mind wrapped around it.  my system was set to dual boot, it worked great.  i upgraded to ubuntu 9.04.  when I rebooted, it got to GRUB and I would choose any of the ubuntu options, and halfway thru the system would freeze.

none of the recovery options worked, and I was still able to boot into windows via GRUB.  so on the partition where ubuntu resided, i did a clean install of ubuntu.  when i got to the installation of GRUB, i think this is where I got screwed up.  so now, the system boots to GRUB and I can get ubuntu running, but when I choose windows, it dies.  when I boot off windows CD and recover the MBR, I can then get windows running, but of course, GRUB is then not seen.

the info from the Boot Info Script is below.  It appears to me that the way it is currently set up, I have GRUB installed twice.  I am pretty sure that XP is installed on /dev/sdb1 and Ubuntu is installed on /dev/sdb2.

All I really want is to get GRUB running, with the ability to choose to boot into either Ubuntu or XP.

Any help would be much appreciated.

===========================================================================
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 914259213.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x457c1076

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   914,259,149   914,259,087   7 HPFS/NTFS
/dev/sda2         914,259,150   976,768,064    62,508,915   5 Extended
/dev/sda5         914,259,213   971,595,134    57,335,922   b W95 FAT32
/dev/sda6         971,595,198   976,768,064     5,172,867  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe1acecb5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   144,215,504   144,215,442   7 HPFS/NTFS
/dev/sdb2         144,215,505   286,888,769   142,673,265  83 Linux
/dev/sdb3         286,888,770   293,041,664     6,152,895   5 Extended
/dev/sdb5         286,888,833   293,041,664     6,152,832  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0b2ec84

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9C8237218236FF78" LABEL="EasternAvenue" TYPE="ntfs" 
/dev/sda5: LABEL="SEWALLSTREE" UUID="479E-6395" TYPE="vfat" 
/dev/sda6: UUID="e155d296-269b-496f-a0b4-1f862f8eb139" TYPE="swap" 
/dev/sdb1: UUID="F890F32A90F2EDCE" LABEL="CoburnStreet" TYPE="ntfs" 
/dev/sdb2: UUID="37e7e50e-f011-4a77-8a99-f04b7f636512" TYPE="ext4" 
/dev/sdb5: UUID="289e31e3-815b-4c9c-81ca-be2bc99ff56a" TYPE="swap" 
/dev/sdc1: UUID="D4E8F74AE8F7297E" LABEL="EssexStreet" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect


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
# kopt=root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=37e7e50e-f011-4a77-8a99-f04b7f636512

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e155d296-269b-496f-a0b4-1f862f8eb139 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=289e31e3-815b-4c9c-81ca-be2bc99ff56a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  80.5GB: boot/grub/menu.lst
  75.9GB: boot/grub/stage2
  77.5GB: boot/initrd.img-2.6.28-11-generic
  80.5GB: boot/initrd.img-2.6.28-15-generic
  75.9GB: boot/vmlinuz-2.6.28-11-generic
  78.1GB: boot/vmlinuz-2.6.28-15-generic
  80.5GB: initrd.img
  77.5GB: initrd.img.old
  78.1GB: vmlinuz
  75.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

==========================================================================

---

### Post by Littleweseth on 2009-10-01
It sounds like GRUB is confused about where to find your windows install.

Please post the following :
1) the contents of /boot/grub/menu.lst. This is the file that tells GRUB where to look for your Linux and Windows installs.

2) the output of 'sudo fstab -l'. This is your partition table; from this, we should be able to tell what to write in menu.lst.

- L.

---

### Post by DannyJohansson on 2009-10-01
menu.lst

=========================================================================

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
# kopt=root=UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=37e7e50e-f011-4a77-8a99-f04b7f636512

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7
f636512 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7
f636512 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7
f636512 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=37e7e50e-f011-4a77-8a99-f04b7
f636512 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		37e7e50e-f011-4a77-8a99-f04b7f636512
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

==========================================================================


I don't know about sudo fstab -1, I tried and that command didn't work.  
if you want the contents of the fstab file, here it is:


==========================================================================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=37e7e50e-f011-4a77-8a99-f04b7f636512 /               ext4    relatime,error
s=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e155d296-269b-496f-a0b4-1f862f8eb139 none            swap    sw            
  0       0
# swap was on /dev/sdb5 during installation
UUID=289e31e3-815b-4c9c-81ca-be2bc99ff56a none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

==========================================================================

Again, thanks for any and all help,

dan

---

### Post by Littleweseth on 2009-10-02
fdisk -l (that's a lowercase L, not a number 1.) The fdisk output is what I really want to see. :)

Post back once you have it.

- L.

---

### Post by oldfred on 2009-10-02
The fdisk -l is part of the bootinfo script. It is at the top.

The script says you have grub in both your first and second drives and a windows boot in your third drive, and windows is in your second drive. The menu.lst looks correct as it is mapping the windows in your second drive to be first as windows wants if sda boots first.

The important thing is which drive is first in BIOS. either sda or sdb should get you to Ubuntu as it uses UUIDs that do not change, but only sda boot will current menu.lst have the correct entry for windows as it is on sdb1 or (hd1,0). If you boot sdb first then windows is (hd0,1).

---

### Post by DannyJohansson on 2009-10-02
thanks oldfred - i must admit, i enjoy reading responses from you linux guys.  usually i have no idea what you said, and this time it is mostly still true! :D

anyway, i tried changing the boot order in the bios to look at the first drive, which is not the drive where anything is installed other than, i guess, grub.  works like a charm.

just cause i am curious, which drive am i actually booting off of?  there are no OS's on the first drive, yet i point the bios to it anyway.  this strikes me as odd.  is it just that GRUB is on the first drive and then GRUB knows where everything is - on the second drive?

Thanks again, i am glad someone knows what is going on, because it sure ain't me!!!

---

### Post by jward3010 on 2009-10-02
I hate to say it, but why the complexity? Do you enjoy headaches! I'll re-read. Even though you've already posted it, could you post fdisk -l again in code tags or even edit the above posts, makes everything way easier to read? If you don't know what I mean let me know.

---

### Post by jward3010 on 2009-10-02
> **DannyJohansson said:**
> just cause i am curious, which drive am i actually booting off of?  there are no OS's on the first drive, yet i point the bios to it anyway.  this strikes me as odd.  is it just that GRUB is on the first drive and then GRUB knows where everything is - on the second drive?
There's a bootsector and MBR on the first empty drive which has directions to point towards the next drive for the first OS to boot more than likely.

You can do things like that, in fact you can take bootsectors completely off hard disks and put them onto, for example, floppies or USB keys only so that you actually need those removable devices plugged in at the time of boot to find the operating systems on the HD's. Sometimes this is used as a safety mechanism to prevent the wrong people from having access to a system.

---

### Post by oldfred on 2009-10-03
When in BIOS you tell the computer what to boot first from. That device will have MBR-master boot record which is small and really just points to a location elsewhere to continue the boot process. The computer only knows to go to the first device and try to boot. If the MBR points to grub stage1.5 or stage2, grub will then give you a menu or additonal info to tell the computer what to do.

Floppy drives, USB keys, CD's and Hard drives all have MBR which is the old dos fat based technology used to boot computers. Apple and some Windows servers have converted to a newer technology and when we start getting drives over 2TB (i just saw a 2TB drive for sale at Fry's) they will have to use the newer tech as MBR cannot go that large. 

The original poster (OP)  loaded a copy of his results.txt that is generated by bootinfoscript32.sh. This script combines a lot of commands and outputs a file that gives just about all the info required to understand how the computer is or is not booting. So we did not need to run extra commands to see his system configuration.

If you want to see all the details of how your system boots:
Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)

---

### Post by Littleweseth on 2009-10-03
Never seen that bootinfo script around. Another one for my bag of tricks, I think. :)

---

### Post by jward3010 on 2009-10-03
> **oldfred said:**
> The original poster (OP)  loaded a copy of his results.txt that is generated by bootinfoscript32.sh. This script combines a lot of commands and outputs a file that gives just about all the info required to understand how the computer is or is not booting. So we did not need to run extra commands to see his system configuration.
Well I would always recommend people to post terminal output in "code" tags as it sets the text as fixed-width just like a terminal window spits it out, which means columns and the like line up properly, hence it's way easier to read.

---

