---
title: "dual booting vista/ubuntu 9.10"
date: 2010-02-27
forum: General Help
---

### Post by dragoon3 on 2010-02-27
Right, so I updated Ubuntu from 9.04 to 9.10. I've been dual booting the whole time with no problems whatsoever. However, since restarting after my update, I find that my option to boot Windows has disappeared from Grub/menu.lst.

I am a complete newbie to Linux so could all help be kept simple please. 

Here's some extra information if you need it:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7b5e4268

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    15,448,063    15,446,016  27 Hidden HPFS/NTFS
/dev/sda2    *     15,448,064   230,309,392   214,861,329   7 HPFS/NTFS
/dev/sda3         230,323,905   390,716,864   160,392,960   5 Extended
/dev/sda5         230,323,968   335,774,564   105,450,597   b W95 FAT32
/dev/sda6         335,774,628   374,844,644    39,070,017  83 Linux
/dev/sda7         374,844,708   384,612,164     9,767,457  83 Linux
/dev/sda8         384,612,228   390,716,864     6,104,637  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   E0FD-1813                              vfat       1GB SD                        
/dev/mspblk0p1   54C1-563E                              vfat       PHONE CARD                    
/dev/sda1        7A1229EE1229B055                       ntfs       Recovery                      
/dev/sda2        D8822CCA822CAEC6                       ntfs                                     
/dev/sda5        8663-CBEB                              vfat                                     
/dev/sda6        4ab8ccfc-0511-4501-abd1-057f6d3f3b8f   ext3                                     
/dev/sda7        fd141902-d1ec-446f-b99f-a3a401503bd6   ext3                                     
/dev/sda8        f7978475-ee20-4898-8d10-7539bc34e031   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda5        /data                    vfat       (rw,utf8,umask=007,gid=46)
/dev/sda7        /home                    ext3       (rw,relatime)
/dev/mmcblk0p1   /media/1GB SD            vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda2        /media/D8822CCA822CAEC6  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4ab8ccfc-0511-4501-abd1-057f6d3f3b8f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4ab8ccfc-0511-4501-abd1-057f6d3f3b8f

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        4ab8ccfc-0511-4501-abd1-057f6d3f3b8f
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=4ab8ccfc-0511-4501-abd1-057f6d3f3b8f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        4ab8ccfc-0511-4501-abd1-057f6d3f3b8f
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=4ab8ccfc-0511-4501-abd1-057f6d3f3b8f ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        4ab8ccfc-0511-4501-abd1-057f6d3f3b8f
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=4ab8ccfc-0511-4501-abd1-057f6d3f3b8f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        4ab8ccfc-0511-4501-abd1-057f6d3f3b8f
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=4ab8ccfc-0511-4501-abd1-057f6d3f3b8f ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, memtest86+
uuid        4ab8ccfc-0511-4501-abd1-057f6d3f3b8f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1



=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=4ab8ccfc-0511-4501-abd1-057f6d3f3b8f /               ext3    relatime,errors=remount-ro 0       1
# /data was on /dev/sda5 during installation
UUID=8663-CBEB  /data           vfat    utf8,umask=007,gid=46 0       1
# /external was on /dev/sdc1 during installation
UUID=9218E01B18DFFBDB /external       ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /home was on /dev/sda7 during installation
UUID=fd141902-d1ec-446f-b99f-a3a401503bd6 /home           ext3    relatime        0       2
# swap was on /dev/sda8 during installation
UUID=f7978475-ee20-4898-8d10-7539bc34e031 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 173.2GB: boot/grub/menu.lst
 173.3GB: boot/grub/stage2
 173.3GB: boot/initrd.img-2.6.28-15-generic
 173.3GB: boot/initrd.img-2.6.31-19-generic
 173.2GB: boot/vmlinuz-2.6.28-15-generic
 173.2GB: boot/vmlinuz-2.6.31-19-generic
 173.3GB: initrd.img
 173.2GB: vmlinuz
```

---

### Post by Robster2 on 2010-02-27
How did you Upgrade?

menu.lst is not used by Grub2.

---

### Post by dragoon3 on 2010-02-27
I just used Update Manager.

---

### Post by Mark Phelps on 2010-02-27
> **Robster2 said:**
> How did you Upgrade?

menu.lst is not used by Grub2.

True ... but when you "upgrade" a 9.04 system to 9.10, it retains legacy GRUB.

So ... the menu.lst file is still used.

---

### Post by Mark Phelps on 2010-02-27
> **dragoon3 said:**
> Right, so I updated Ubuntu from 9.04 to 9.10. I've been dual booting the whole time with no problems whatsoever. However, since restarting after my update, I find that my option to boot Windows has disappeared from Grub/menu.lst.

That's probably because the update created a new menu.lst file -- which would NOT include other OSs by default.

You need to add a stanza to the new menu.lst file for MS Windows.

Do you know how to do that? Or do you need some instructions?

Also, next time, save off a copy of the current menu.lst file before you do any updates.  If you had this backup copy, you could simply copy the working stanza to the new menu.lst file and be done.

---

### Post by oldfred on 2010-02-27
You have a windows stanza but it is looking for sda1 (hd0,0) which looks like a recovery partition. Your windows install is in sda2 (hd0,1). You should be able to edit menu.lst and just change the partition it points to. Of course make a backup first just in case.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```

---

### Post by MarioA on 2010-05-02
Look into this, it worked for me:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

