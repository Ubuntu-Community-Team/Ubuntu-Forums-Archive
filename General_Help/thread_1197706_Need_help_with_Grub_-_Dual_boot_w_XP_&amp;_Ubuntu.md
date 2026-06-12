---
title: "Need help with Grub - Dual boot w/ XP &amp; Ubuntu"
date: 2009-06-26
forum: General Help
---

### Post by pozer69 on 2009-06-26
I need to be able to dual boot for work reasons. Right now I can boot into Ubuntu with no problem however when I try to boot into windows I receive bootmgr error. When I disconnect all of my hdd except the windows one i can boot just fine. I have added and removed numerous hard drives in the past and I have reinstalled grub numerous times and I think my Grub Loader is messed up. I have determined that my Windows Boot Loader is on /dev/sdd (hd3). 

Here is my **device.map**:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
(hd5)	/dev/sdf
```

**fdisk -l**

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488391041    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf96c0a67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0de4c840

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         973     7815591   83  Linux
/dev/sdc2             974        4998    32330812+   5  Extended
/dev/sdc5            4788        4998     1694826   82  Linux swap / Solaris
/dev/sdc6             974        4787    30635892   83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6fc103f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9731    78164226    7  HPFS/NTFS

```

**boot_info_script032.sh**

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #5 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       976769023 sectors, but according to the info from 
                       fdisk, it has 976782082 sectors.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,784,129   976,782,082   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf96c0a67

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0de4c840

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    15,631,244    15,631,182  83 Linux
/dev/sdc2          15,631,245    80,292,869    64,661,625   5 Extended
/dev/sdc5          76,903,218    80,292,869     3,389,652  82 Linux swap / Solaris
/dev/sdc6          15,631,371    76,903,154    61,271,784  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6fc103f2

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   156,328,514   156,328,452   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1824548B24546DAE" LABEL="Temp" TYPE="ntfs" 
/dev/sdb1: UUID="EED622CCD62294BD" LABEL="PSP" TYPE="ntfs" 
/dev/sdc1: UUID="1cea9977-feef-4fb6-b459-2bffa54bce89" TYPE="ext2" 
/dev/sdc5: UUID="e23c19c2-6242-4c49-a748-f9524fcba755" TYPE="swap" 
/dev/sdc6: UUID="8c204c27-66d1-4009-bbd9-357ca985965b" TYPE="ext3" 
/dev/sdd1: UUID="4694BCC594BCB8AF" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext2 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joseph/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joseph)
/dev/sda1 on /media/Temp type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdc1/boot/grub/menu.lst: ===========================

default 0
timeout 10

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
# kopt=root=UUID=1cea9977-feef-4fb6-b459-2bffa54bce89 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1cea9977-feef-4fb6-b459-2bffa54bce89

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



## title		Ubuntu 9.04, kernel 2.6.28-11-generic
## uuid		1cea9977-feef-4fb6-b459-2bffa54bce89
## kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1cea9977-feef-4fb6-b459-2bffa54bce89 ro quiet splash
## initrd		/boot/initrd.img-2.6.28-11-generic
## quiet

## title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
## uuid		1cea9977-feef-4fb6-b459-2bffa54bce89
## kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1cea9977-feef-4fb6-b459-2bffa54bce89 ro  single
## initrd		/boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-13-generic
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=1cea9977-feef-4fb6-b459-2bffa54bce89 ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=1cea9977-feef-4fb6-b459-2bffa54bce89 ro  single
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows XP Professional x64 Edition
root (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1
savedefault
makeactive


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde1 during installation
UUID=1cea9977-feef-4fb6-b459-2bffa54bce89 /               ext2    relatime,errors=remount-ro 0       1
# /home was on /dev/sde6 during installation
UUID=8c204c27-66d1-4009-bbd9-357ca985965b /home           ext3    relatime        0       2
# swap was on /dev/sde5 during installation
UUID=e23c19c2-6242-4c49-a748-f9524fcba755 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/menu.lst
    .2GB: boot/grub/stage2
   7.7GB: boot/initrd.img-2.6.28-11-generic
    .7GB: boot/initrd.img-2.6.28-13-generic
   7.7GB: boot/vmlinuz-2.6.28-11-generic
    .6GB: boot/vmlinuz-2.6.28-13-generic
    .7GB: initrd.img
   7.7GB: initrd.img.old
    .6GB: vmlinuz
   7.7GB: vmlinuz.old

================================ sdd1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

```

Can you please explain to me how to read this information and how to fix it. I am always changing my configuration. I already searched and this is where I was able to produce this info. Thanks.

---

