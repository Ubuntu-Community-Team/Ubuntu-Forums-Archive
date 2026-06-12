---
title: "Unable to boot into ubuntu."
date: 2011-04-23
forum: General Help
---

### Post by karthick87 on 2011-04-23
Unable to boot into ubuntu,getting grub screen.

            ```
    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       192,779       192,717  83 Linux
/dev/sda2             192,780     2,184,839     1,992,060  82 Linux swap / Solaris
/dev/sda3           2,184,840   156,248,189   154,063,350  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4002 MB, 4002910208 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,818,183     7,818,121   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        b878705b-2d90-440a-85f9-63c00363511f   ext3                                     
/dev/sda2                                               swap                                     
/dev/sda3        f8b09312-6801-4cd7-a284-ce5e6498eccd   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A839-F9F8                              vfat       UBUNTU                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.24-19-generic
    .0GB: initrd.img-2.6.24-19-generic.bak
    .0GB: vmlinuz-2.6.24-19-generic

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f8b09312-6801-4cd7-a284-ce5e6498eccd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=b878705b-2d90-440a-85f9-63c00363511f /boot           ext3    relatime        0       2
# /dev/sda2
UUID=eec4712f-e3cb-4d7e-8796-bcc1e43b5f2b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by hansdown on 2011-04-23
Hi karthick87.

Your boot info script is from Feb. 2010.

You seem to have a boot flag (*) on sdba1, and sdb1.

Have you been upgrading?

Going from ext.3 to ext.4, may cause some problems.

---

### Post by Hedgehog1 on 2011-04-23
karthick87,

Please use the newest version of the boot info script found at the site shown below.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the **ENTIRE** script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by wilee-nilee on 2011-04-23
Boot Info Script 0.55    dated February 15th,

That is the latest script.

And that is one messed up setup, or the script is misreading, but there is a lot missing.

OP you could have a more up to date streamlined setup if you wanted this one looks like more trouble than it might be worth, at least to me.

---

### Post by kiyop on 2011-04-23
At the GRUB prompt, press C key.
If you can get into grub prompt like,
```
grub>
```Then, type
```
set root="(hd0,1)"
ls /
```If "vmlinuz-..." and "initrd.img-..." are displayed, type:
```
linux /vmlinuz-... root=/dev/sda3 ro
initrd /initrd.img-...
boot
```You should change above "..." into the displayed one.
I guess "..." is "2.6.24-19-generic".

If vmlinuz-... and initrd.img-... are not displayed, please type:
```
ls /boot
```if vmlinuz-... and initrd.img-... are not displayed, please type:
```
ls (hd0,3)/boot
```By the way, if your 8.04 is desktop edition, the support will be expired this month.

---

### Post by karthick87 on 2011-04-23
Thanks it solved the problem :)

---

### Post by kiyop on 2011-04-23
If you could successfully boot ubuntu, how about executing in terminal the following?
```
sudo apt-get update
sudo apt-get install grub-pc
sudo grub-install /dev/sda
sudo update-grub
```

---

