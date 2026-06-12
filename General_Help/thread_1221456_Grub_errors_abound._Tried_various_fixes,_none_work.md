---
title: "Grub errors abound. Tried various fixes, none worked."
date: 2009-07-23
forum: General Help
---

### Post by zerosanity on 2009-07-23
So, I had 7.10 installed beside windows. It was working pretty swell, but I decided to make the jump to 9.04, and I've been regretting that decision since.  As soon as the install finished, I got Grub error 2.  After some fiddling based on a post in a similar grub-related thread, I managed to get rid of error 2. Then I started getting error 17.

Three or four grub reinstalls, some menu.lst changes, and a handful of 9.04 reinstalls using a couple different partition configurations, I'm getting Error 2 again.

Here's my bootinfoscript results:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and
                       looks at sector 64045119 of the same hard drive for
                       the stage2 file. A stage2 file is at this location on
                       /dev/sda. Stage2 looks on partition #1 for
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts
                       at sector 0. But according to the info from fdisk,
                       sda3 starts at sector 209712510.
    Operating System: 
    Boot files/dirs:  

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16e616e5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,712,509   209,712,447  83 Linux
/dev/sda3         209,712,510   575,576,819   365,864,310   c W95 FAT32 (LBA)
/dev/sda4         575,576,820   586,067,264    10,490,445  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16e616e6

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,810,649   160,810,587   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="2fde47b9-b053-4a42-ae54-3a887ec1e2a7" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda3: UUID="4772-65BF" TYPE="vfat"
/dev/sda4: UUID="0a63494d-4282-42d2-a519-6be54329ae1d" TYPE="swap"
/dev/sdb1: UUID="68FC2747FC270F3E" TYPE="ntfs"

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


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=2fde47b9-b053-4a42-ae54-3a887ec1e2a7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2fde47b9-b053-4a42-ae54-3a887ec1e2a7

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2fde47b9-b053-4a42-ae54-3a887ec1e2a7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2fde47b9-b053-4a42-ae54-3a887ec1e2a7 ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2fde47b9-b053-4a42-ae54-3a887ec1e2a7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2fde47b9-b053-4a42-ae54-3a887ec1e2a7 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2fde47b9-b053-4a42-ae54-3a887ec1e2a7
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2fde47b9-b053-4a42-ae54-3a887ec1e2a7 /               ext3    relatime,errors=remount-ro 0       1
# /mnt/unit-zero-two was on /dev/sda3 during installation
UUID=4772-65BF  /mnt/unit-zero-two vfat    utf8,umask=007,gid=46 0       1
# /windows was on /dev/sdb1 during installation
UUID=68FC2747FC270F3E /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap was on /dev/sda4 during installation
UUID=0a63494d-4282-42d2-a519-6be54329ae1d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  32.8GB: boot/grub/menu.lst
  32.7GB: boot/grub/stage2
  32.7GB: boot/initrd.img-2.6.28-11-generic
  32.8GB: boot/vmlinuz-2.6.28-11-generic
  32.7GB: initrd.img
  32.8GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
```

Obviously this is from the LiveCD

Apologies if the fix for this happens to be somewhere in the forums, but I've spent hours (since yesterday, actually) trying to get this working. I also apologize if I haven't posted all the necessary info.

Thanks in advance!



[EDIT: [SuperGrubDisk]("http://supergrubdisk.org") fixed my problem. Yay!! Downloading updates and what have you as I type this. :D:D]

---

