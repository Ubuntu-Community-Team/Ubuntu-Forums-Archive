---
title: "fstab is broken?"
date: 2010-06-18
forum: General Help
---

### Post by imjscn on 2010-06-18
I need to repair MBR, so I am installing lilo. after install, it says I must run the  liloconfig to get lilo working. I run the file, got this warning message:
```
Your /etc/fstab configuration file gives device            &#9618; 
  &#9474; UUID=8a22f6ac-37fd-4dbf-abd8-ade21a005a5e as the root      &#9618; 
  &#9474; filesystem device. This doesn't look to me like an         &#9618; 
  &#9474; "ordinary" block device. Either your fstab is broken and   &#9618; 
  &#9474; you should fix it, or you are using hardware (such as a    &#9618; 
  &#9474; RAID array) which this simple configuration program does   &#9618; 
  &#9474; not handle.                                                &#9618; 
  &#9474;                                                            &#9618; 
  &#9474; You should either repair the situation or hand-roll your   &#9618; 
  &#9474; own /etc/lilo.conf configuration file; you can then run    &#9618; 
  &#9474; /usr/sbin/liloconfig again to retry the configuration      &#9618; 
  &#9474; process.

```

I don't understand what's wrong in the fstab. Maybe there's something about my partitions. 
I have 1 harddisk with 2 partitions. First partition is where I installed Xubuntu; Second partition is a Hidden Area Partition where Thinkpad use it to store factory state harddisk image.

When I install Xubuntu, I saw the Hidden Area Partition is listed on the partition table. I choose "Do not use this", I also saw this partition is listed as sda2.

For the first partition, I made the partition table like this:
/
/boot
swamp
/home
/tmp
/user

Here's a scan result of my boot info:
```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    29,302,559    29,302,497  83 Linux
/dev/sda2         107,064,720   117,195,119    10,130,400  12 Compaq diagnostics
/dev/sda3    *     29,302,560    33,206,354     3,903,795  83 Linux
/dev/sda4          33,206,355   107,057,159    73,850,805   5 Extended
/dev/sda5          33,206,418    35,166,284     1,959,867  82 Linux swap / Solaris
/dev/sda6          35,166,348    74,236,364    39,070,017  83 Linux
/dev/sda7          74,236,428    76,196,294     1,959,867  83 Linux
/dev/sda8          76,196,358   107,057,159    30,860,802  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        257a7d04-2874-4282-9bb7-77b06fe4b471   ext3                                     
/dev/sda2        D005-3738                              vfat       IBM_SERVICE                   
/dev/sda3        ae9a8425-b9ec-41ac-8399-0fb9e41649c7   ext3                                     
/dev/sda5        3618fbc0-1750-46dd-938c-7437a39a469d   swap                                     
/dev/sda6        66b82697-508a-454e-b28a-2cfcb4d8db10   ext3                                     
/dev/sda7        cc6f9869-9ee1-4909-a377-a2142f3b1b6e   ext3                                     
/dev/sda8        f8c6f3d3-5f31-4cb3-990a-c4e332706e8f   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda3        /boot                    ext3       (rw,relatime)
/dev/sda6        /home                    ext3       (rw,relatime)
/dev/sda7        /tmp                     ext3       (rw,relatime)
/dev/sda8        /usr                     ext3       (rw,relatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=257a7d04-2874-4282-9bb7-77b06fe4b471 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=ae9a8425-b9ec-41ac-8399-0fb9e41649c7 /boot           ext3    relatime        0       2
# /dev/sda6
UUID=66b82697-508a-454e-b28a-2cfcb4d8db10 /home           ext3    relatime        0       2
# /dev/sda7
UUID=cc6f9869-9ee1-4909-a377-a2142f3b1b6e /tmp            ext3    relatime        0       2
# /dev/sda8
UUID=f8c6f3d3-5f31-4cb3-990a-c4e332706e8f /usr            ext3    relatime        0       2
# /dev/sda5
UUID=3618fbc0-1750-46dd-938c-7437a39a469d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: initrd.img
    .0GB: vmlinuz

================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\ = "PC-DOS"


============================= sda3/grub/menu.lst: =============================

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
# kopt=root=UUID=257a7d04-2874-4282-9bb7-77b06fe4b471 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=257a7d04-2874-4282-9bb7-77b06fe4b471 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=257a7d04-2874-4282-9bb7-77b06fe4b471 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=================== sda3: Location of files loaded by Grub: ===================


  15.7GB: grub/menu.lst
  15.7GB: grub/stage2
  15.0GB: initrd.img-2.6.24-16-generic
  15.0GB: initrd.img-2.6.24-16-generic.bak
  15.0GB: vmlinuz-2.6.24-16-generic
```

Could anybody help me sort out what's going wrong and how to fix?

---

### Post by diesch on 2010-06-18
*liloconfig* doesn't understand the *UUID=... *syntax that Ubuntu uses in [I]/etc/fstab.

[/I]Either change it to use proper */dev/* files or write a *lilo.conf* manually.Why do you want to use LILO instead og GRUB?

---

### Post by WorMzy on 2010-06-18
According to your blkid output, that partition doesn't exist. :confused:

Also, you have seven partitions, not two.

---

### Post by imjscn on 2010-06-18
Diesch, 
I install lilo because according to an article, lilo can help repair windows mbr. I don't think I'm able to edit the /dev files or lilo configure files. Maybe I'll just quit install lilo. But, Does Grub help repair windows mbr?

Wormzy, maybe it's because lilo try to install files into the Hidden partition which is sda2 ? 
Sorry, it's 7 partitions. I meant to say, it was 1 hidden partion untouched and linux is installed in the rest of free space.

---

### Post by diesch on 2010-06-18
LILO writes a new MBR if installed into the MBR. GRUB does that, too.

---

### Post by oldfred on 2010-06-19
Lilo is a simple boot loader like windows. It looks at the partition table in the MBR and sees a boot flag (active partition) and jumps to the code in the boot sector of that partition. 

You have the boot flag on sda3, but your windows install is in sda2. Also your boot.ini refers to sda3 but is now in sda2. Do not use gedit to modify it as linux uses different line endings. Or you can use windows tools. Change 3 to 2.
multi(0)disk(0)rdisk(0)[COLOR=Red]partition(3)[/COLOR]\WINDOWS="Microsoft Windows XP Professional" /fastdetect

If editing windows files like boot.ini from liveCD: Use nano instead of gedit, it's better for dos-style linebreaks.
Edit Boot.ini
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

