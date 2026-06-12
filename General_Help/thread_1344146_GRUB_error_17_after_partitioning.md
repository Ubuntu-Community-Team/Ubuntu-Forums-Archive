---
title: "GRUB error 17 after partitioning"
date: 2009-12-02
forum: General Help
---

### Post by TironN on 2009-12-02
Alright guys,
So I did something really stupid. After booting up partition magic I changed the partitioning on my root Linux part. I was originally dual booting Win XP and Ubuntu but I reformatted the windows part. I then deleted it and expanded the Linux part. Now I get error 17 for GRUB.
Any ideas?

---

### Post by utnubuuser on 2009-12-02
If all else fails, you can always use a liveCD to re-install grub. - Existing partitions will be recognized etc. - there is a Ubuntu grub2 how-to wiki.
> [https://wiki.ubuntu.com/Grub]("https://wiki.ubuntu.com/Grub")

I've not tried this, but you might be able to just fix the existing grub through a liveCD as well with > sudo update-grub

---

### Post by TironN on 2009-12-03
Well I reinstalled GRUB... and now I don't get an error but on start up I get dropped into the GRUB shell.. It reads:
> GNU GRUB version 1.97~beta4
[Minimal BASH-like yada yada...]
sh:grub>  

---

### Post by namok on 2009-12-03
[Follow this link]("http://ubuntuforums.org/showthread.php?t=1291280") and add RESULT.txt to the next post.

---

### Post by TironN on 2009-12-03
Ok here it is one hell of a post:
```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 568814952 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e93c6

Partition  Boot         Start           End          Size  Id System

/dev/sda1         335,148,030   539,944,649   204,796,620  83 Linux
/dev/sda2                  63   252,027,719   252,027,657   b W95 FAT32
/dev/sda3         539,944,650   625,121,279    85,176,630   f W95 Ext d (LBA)
/dev/sda5         539,944,776   623,193,479    83,248,704  83 Linux
/dev/sda6         623,193,543   625,121,279     1,927,737  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="66e9edf4-38b3-426d-8348-428982763568" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="3EDC-3071" TYPE="vfat" 
/dev/sda5: UUID="c7379927-d39d-47f6-ac1b-3ac610dc979b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="8b33e847-5ca1-4fec-91b5-12f96d923b3a" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
# kopt=root=UUID=c7379927-d39d-47f6-ac1b-3ac610dc979b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c7379927-d39d-47f6-ac1b-3ac610dc979b

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

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        c7379927-d39d-47f6-ac1b-3ac610dc979b
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=c7379927-d39d-47f6-ac1b-3ac610dc979b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        c7379927-d39d-47f6-ac1b-3ac610dc979b
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=c7379927-d39d-47f6-ac1b-3ac610dc979b ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        c7379927-d39d-47f6-ac1b-3ac610dc979b
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=c7379927-d39d-47f6-ac1b-3ac610dc979b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        c7379927-d39d-47f6-ac1b-3ac610dc979b
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=c7379927-d39d-47f6-ac1b-3ac610dc979b ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        c7379927-d39d-47f6-ac1b-3ac610dc979b
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c7379927-d39d-47f6-ac1b-3ac610dc979b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        c7379927-d39d-47f6-ac1b-3ac610dc979b
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c7379927-d39d-47f6-ac1b-3ac610dc979b ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        c7379927-d39d-47f6-ac1b-3ac610dc979b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
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
UUID=c7379927-d39d-47f6-ac1b-3ac610dc979b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8b33e847-5ca1-4fec-91b5-12f96d923b3a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda2    /media/bigd    auto    rw,user,auto,exec,umask=000    0    0
/dev/sda1    /media/ldat    auto    rw,user,auto,exec    0    0

=================== sda5: Location of files loaded by Grub: ===================


 276.4GB: boot/grub/menu.lst
 276.4GB: boot/grub/stage2
 276.4GB: boot/initrd.img-2.6.28-16-generic
 276.4GB: boot/initrd.img-2.6.31-14-generic
 276.4GB: boot/initrd.img-2.6.31-15-generic
 276.4GB: boot/vmlinuz-2.6.28-16-generic
 276.4GB: boot/vmlinuz-2.6.31-14-generic
 276.4GB: boot/vmlinuz-2.6.31-15-generic
 276.4GB: initrd.img
 276.4GB: initrd.img.old
 276.4GB: vmlinuz
 276.4GB: vmlinuz.old
```

---

### Post by namok on 2009-12-03
Everything is clear. You have installed Grub2 and should Grub Legacy (you have file *'menu.lst'* not *'grub.cfg'*). Boot to livecd and install Grub Legacy in MBR: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) (How to restore the Ubuntu grub bootloader (up to 9.04))

---

### Post by TironN on 2009-12-03
Hmmm.. Well I open terminal and enter
```
sudo grub
```
and I get command not found.. Do i need an older live cd?

---

### Post by namok on 2009-12-03
> **TironN said:**
> Hmmm.. Well I open terminal and enter
```
sudo grub
```and I get command not found.. Do i need an older live cd?
Yes. You should use version 9.04.[IMG]http://www.google.pl/images/cleardot.gif[/IMG]

---

### Post by TironN on 2009-12-04
Ok! Booted my 9.04 drive and followed your instructions and all is well!
Thanks heaps!!

---

