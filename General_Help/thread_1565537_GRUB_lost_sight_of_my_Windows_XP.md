---
title: "GRUB lost sight of my Windows XP"
date: 2010-09-01
forum: General Help
---

### Post by Dart00 on 2010-09-01
Iv installed Ubuntu for many users but I never had this happon....on my own hardware too! :(

I did a dual boot install of Ubuntu 9.10. After that, when I rebooted my Windows XP was gone? I did update-grub and still nothing. I popped in the GRUB Super boot Disk 2 and browsed around, I think i found it but it says "Error: Invalid Signature". Iv googled and havent found a solution to this yet.

I booted off a XP CD into the recovery console, it sees my Windows partition and lets me get into it and browse all my files. So I know its there. I then tried fixmbr then fixboot and now all it loads is my Recovery Partition. I booted up SuperGrubDisk again and same results, it just sees my Ubuntu. I reinstalled grub and back to square 1. Then I tried a checkdsk /r and tried it all over again. Nothin'.... :(

I have some encrypted files on my drive using EFS....i guess it would be ok to loose them, but I put a lot of work into them....

Anyone have any ideas on how I can "wakeup" my XP again?

---

### Post by wilee-nilee on 2010-09-01
Can you post the results of; in the terminal in Ubuntu.
```
sudo fdisk -l
```

---

### Post by Dart00 on 2010-09-02
Currently my last command was the "Fixmbr" in a last attempt to get it going which killed grub, I was able to boot of the super grub disk and issue the command:

Its a single harddrive laptop (I think its Sata)

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f84afe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       10685    85819230    f  W95 Ext'd (LBA)
/dev/sda2           10686       18431    62219745   83  Linux
/dev/sda3   *       18432       19452     8201182+   c  W95 FAT32 (LBA)
/dev/sda4           19453       19457       40162+  ef  EFI (FAT-12/16/32)
/dev/sda5   *           2       10442    83867301    7  HPFS/NTFS
/dev/sda6           10443       10685     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x2ae52ae4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         984     1983619+   6  FAT16
```I think Sda is the harddrive and sdb is my 2GB SD card I have BackTrack on....

All i know is i have a Windows XP Pro, a Windows XP recovery partition, my Ubuntu and my Ubuntu SWAP....not sure what else there is.

---

### Post by wilee-nilee on 2010-09-02
Post the bootscript in my signature in code tags. It does look like you have both OS indications the script will give us more information.

---

### Post by Dart00 on 2010-09-25
Im so sorry..things have been all of a sudden real busy. I like my Ubuntu but am missing the files I have on my Windows. Heres the results from your script. I hope you can still help me:

Also I took my SD card out before I ran this script to help simplify things but for some reasons it shows it a sdc even while its sitting on the table lol

In review the only thing I know is I have:
- Windows XP
- Ubuntu 
- Linux SWAP
- Recovery (may be seen as Windows XP?)

Also GRUB should not be installed, when I did "fixmbr" it wiped it out, I had to boot of my Super Grub Disk. But im not sure of anything any more. :(

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 32.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f84afe8

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   171,654,524   171,638,460   f W95 Ext d (LBA)
/dev/sda5    *         16,128   167,750,729   167,734,602   7 HPFS/NTFS
/dev/sda6         167,750,793   171,654,524     3,903,732  82 Linux swap / Solaris
/dev/sda2         171,654,525   296,094,014   124,439,490  83 Linux
/dev/sda3    *    296,094,015   312,496,379    16,402,365   c W95 FAT32 (LBA)
/dev/sda4         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5841f2ff

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     4,030,463     4,030,432   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda2        b3effbff-f3a7-4179-935e-a9a5e7166672   ext4                                     
/dev/sda3        CCED-990E                              vfat       PE                            
/dev/sda5        CCC01D3FC01D30E6                       ntfs       Windows XP                    
/dev/sda6        54e9eea8-9fe0-4c67-b884-a12c5aeceb32   swap                                     
/dev/sdc1        5B7E-A521                              vfat       Drive                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,noatime,errors=remount-ro)
/dev/sr0         /media/CDROM             iso9660    (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sdc1        /media/Drive             vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


=========================== sda2/boot/grub/menu.lst: ===========================

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
timeout        5

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
# kopt=root=UUID=b3effbff-f3a7-4179-935e-a9a5e7166672 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b3effbff-f3a7-4179-935e-a9a5e7166672

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

title        Ubuntu 9.04, kernel 2.6.30.5-ep0
uuid        b3effbff-f3a7-4179-935e-a9a5e7166672
kernel        /boot/vmlinuz-2.6.30.5-ep0 root=UUID=b3effbff-f3a7-4179-935e-a9a5e7166672 ro quiet splash 
initrd        /boot/initrd.img-2.6.30.5-ep0
quiet

title        Ubuntu 9.04, kernel 2.6.30.5-ep0 (recovery mode)
uuid        b3effbff-f3a7-4179-935e-a9a5e7166672
kernel        /boot/vmlinuz-2.6.30.5-ep0 root=UUID=b3effbff-f3a7-4179-935e-a9a5e7166672 ro  single
initrd        /boot/initrd.img-2.6.30.5-ep0

title        Ubuntu 9.04, memtest86+
uuid        b3effbff-f3a7-4179-935e-a9a5e7166672
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows NT/2000/XP
rootnoverify    (hd0,2)
savedefault
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=b3effbff-f3a7-4179-935e-a9a5e7166672 /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=54e9eea8-9fe0-4c67-b884-a12c5aeceb32 none            swap    sw              0       0
# settings added by eeepc-tweaks
tmpfs        /tmp        tmpfs    defaults,noatime,mode=1777    0 0
tmpfs        /var/tmp    tmpfs    defaults,noatime,mode=1777    0 0
tmpfs        /var/log    tmpfs    defaults,noatime,mode=0755    0 0

=================== sda2: Location of files loaded by Grub: ===================


  92.5GB: boot/grub/menu.lst
  91.3GB: boot/grub/stage2
  89.2GB: boot/initrd.img-2.6.30.5-ep0
  88.5GB: boot/vmlinuz-2.6.30.5-ep0
  88.0GB: initrd.gz
  89.2GB: initrd.img
  88.5GB: vmlinuz
```

---

### Post by Dart00 on 2010-10-12
Bump Please

---

