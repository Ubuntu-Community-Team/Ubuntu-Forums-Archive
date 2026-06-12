---
title: "Grub error 24 after 9.04 kernel update, continues with upgrade to 9.10"
date: 2009-11-02
forum: General Help
---

### Post by eco_was_taken on 2009-11-02
At some point I started receiving grub error 24 at boot (Attempt to access block outside partition).  Selecting another kernel from the list allowed me to boot.  I looked into it a little but was too busy at the time to investigate fully.  It seemed that people who switched to ext4 were getting this because they failed to run grub-install after the switch.  I was still running ext3 so that didn't apply to me.

I upgraded to 9.10 and am still receiving this error.  I've been googling around a lot lately but with no success.  I switched over to ext4 after I suspected a change to grub to support ext4 affected the way ext3 worked but the problem has remained unchanged.

The upgrade to 9.10 left me with two kernel versions: 2.6.28-15-generic (which does work) and the current default 2.6.31-14-generic (which doesn't boot).

I've grub-install'ed, fscked, removed all other hard disks, checked for hard disk errors with SeaTools, and just about everything else I could find to try with no luck.

Here is the output of boot_info_script032.sh:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f2303

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 2,910,624,569 2,910,624,507  83 Linux
/dev/sda2       2,910,624,570 2,930,272,064    19,647,495   5 Extended
/dev/sda5       2,910,624,633 2,930,272,064    19,647,432  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="114d66e9-c42f-449e-9a7c-a1e7ba23c04a" TYPE="ext4" 
/dev/sda5: UUID="351d4413-20d0-4691-bd6f-b7a2b828cdad" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/brad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brad)
jungledisk on /home/brad/JungleDisk type fuse.jungledisk (rw,nosuid,nodev,user=brad)


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
# kopt=root=UUID=114d66e9-c42f-449e-9a7c-a1e7ba23c04a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=114d66e9-c42f-449e-9a7c-a1e7ba23c04a

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

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        114d66e9-c42f-449e-9a7c-a1e7ba23c04a
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=114d66e9-c42f-449e-9a7c-a1e7ba23c04a ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        114d66e9-c42f-449e-9a7c-a1e7ba23c04a
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=114d66e9-c42f-449e-9a7c-a1e7ba23c04a ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        114d66e9-c42f-449e-9a7c-a1e7ba23c04a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=114d66e9-c42f-449e-9a7c-a1e7ba23c04a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        114d66e9-c42f-449e-9a7c-a1e7ba23c04a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=114d66e9-c42f-449e-9a7c-a1e7ba23c04a ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, memtest86+
uuid        114d66e9-c42f-449e-9a7c-a1e7ba23c04a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=114d66e9-c42f-449e-9a7c-a1e7ba23c04a /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=351d4413-20d0-4691-bd6f-b7a2b828cdad none            swap    sw              0       0
UUID=09cd0628-9cda-44d7-a0a0-7b80ea57762d /mnt/4disk    ext3    relatime,errors=remount-ro 0    0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-15-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.28-15-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

```I'm out of ideas and my system seems to be getting worse and worse with every update (sound stopped working with the upgrade to 9.10 but that's another issue).  Ubuntu has treated me well for years now but lately I can't keep it running stably.  I'm not looking forward to switching to another OS if I can't figure this out but I just might have to.  So please, does anyone have any ideas or insight I can try?


**Solved:**
I've resolved the problem by switching to grub2.  Using the testing chainloader installation ruined my regular grub install (left me with just a grub> prompt, no menu) but I went ahead and just replaced grub with grub2 without testing anyway and I can now boot into my 2.6.31 kernel.  This also fixed my sound and USB mass storage not working.

It really feels like Ubuntu upgrades are not tested to nearly the same level that fresh installs are.  This wouldn't be the first time a fresh install would have saved me hours of bug wrangling.

---

