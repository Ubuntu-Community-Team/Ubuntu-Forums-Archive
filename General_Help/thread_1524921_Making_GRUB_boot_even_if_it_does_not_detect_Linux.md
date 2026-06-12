---
title: "Making GRUB boot even if it does not detect Linux"
date: 2010-07-05
forum: General Help
---

### Post by pFREDq on 2010-07-05
If this is the wrong place for this I apologize.

Here is my current setup for my laptop: I dual boot Windows Vista and Ubuntu 9.04. Vista is on the laptop's HDD while Ubuntu is on an external USB HDD. When turning my laptop on, if the external hard drive is either not on or disconnected, I get "Error 21" and nothing happens. Normally this wouldn't be a problem, but when I need to take my laptop somewhere where I do not have access to my external HDD, it is rendered completely useless.

So is it possible to set up GRUB (or possibly another bootloader) to boot regardless of whether or not it detects the drive Ubuntu is installed on?

---

### Post by wilee-nilee on 2010-07-05
> **pFREDq said:**
> If this is the wrong place for this I apologize.

Here is my current setup for my laptop: I dual boot Windows Vista and Ubuntu 9.04. Vista is on the laptop's HDD while Ubuntu is on an external USB HDD. When turning my laptop on, if the external hard drive is either not on or disconnected, I get "Error 21" and nothing happens. Normally this wouldn't be a problem, but when I need to take my laptop somewhere where I do not have access to my external HDD, it is rendered completely useless.

So is it possible to set up GRUB (or possibly another bootloader) to boot regardless of whether or not it detects the drive Ubuntu is installed on?

Post the bootscript in my signature in code tags as described.

If you do not have a Vista install or recovery disc download this one, and burn it at a slow as possible 4x.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

To be honest to I believe support for 9.04 ends this year September I think.
[http://www.ubuntugeek.com/wp-content/uploads/2009/12/ubuntu-release-cycle_6.png](http://www.ubuntugeek.com/wp-content/uploads/2009/12/ubuntu-release-cycle_6.png)

---

### Post by pFREDq on 2010-07-06
Yeah, I really need to upgrade. Anyway, here is RESULTS.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8d64c3d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   292,984,830   292,984,768   7 HPFS/NTFS
/dev/sda2         292,984,832   312,573,951    19,589,120   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbce2081

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,922,396,582 1,922,396,520   7 HPFS/NTFS
/dev/sdb2       1,922,398,208 1,932,883,967    10,485,760   7 HPFS/NTFS
/dev/sdb3       1,932,886,016 1,953,519,615    20,633,600  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4690451B904512BB                       ntfs                                     
/dev/sda2        42E44E1AE44E1119                       ntfs       PRESARIO_RP                   
/dev/sdb1        D27431CF7431B6D7                       ntfs       Iomega HDD                    
/dev/sdb2        8C1AF3791AF35F20                       ntfs       XP                            
/dev/sdb3        b49dac7a-a68e-4e4a-89ba-04e84614b12d   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb2        /media/XP                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdb3/boot/grub/menu.lst: ===========================

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
default        4

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
# kopt=root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b49dac7a-a68e-4e4a-89ba-04e84614b12d

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
uuid        b49dac7a-a68e-4e4a-89ba-04e84614b12d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b49dac7a-a68e-4e4a-89ba-04e84614b12d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b49dac7a-a68e-4e4a-89ba-04e84614b12d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 993.9GB: boot/grub/menu.lst
 994.0GB: boot/grub/stage2
 994.0GB: boot/initrd.img-2.6.28-11-generic
 994.0GB: boot/vmlinuz-2.6.28-11-generic
 994.0GB: initrd.img
 994.0GB: vmlinuz
```

---

### Post by wilee-nilee on 2010-07-06
Actually I just noticed the windows bootloader in the external, I would wait for somebody more experienced. I'm just not familiar with how to load grub-legacy in general.

---

### Post by pFREDq on 2010-07-06
Looking at this, I think the reason it doesn't load is because it searches for stage2 and menu.lst on the external. So if the location of these were changed to the laptop's hard drive, GRUB would load, correct? Is there a way to do this? Also, I'm probably wrong here (I'm generally unfamiliar with the MBR and everything it's for) but doesn't GRUB take care of all the bootloading stuff? Isn't Window's bootloader unnecessary now that GRUB is installed, so even if the bootloader that's installed in the external wasn't there, Windows would still boot, right?

---

### Post by WorMzy on 2010-07-06
If you created a boot partition on your internal hard drive for grub to reside in, then you could boot regardless of the external HD being present or not. You wouldn't be able to edit it without booting into Ubuntu, another Linux OS, or a LiveCD, but you could still boot Windows without needing the external HD.

To do this, you're going to need to resize one of your internal drive's ntfs partitions, as there's no free space for the new partition at present. To resize your ntfs partitions, I recommend booting into Vista (or Win 7, whichever you're using), and using the native partition management software to resize one of them. I don't know how much space is required, but I'd suggest freeing about 5GB, you can try less if you'd prefer, Grub legacy generally only takes up ~170kb.

After you've freed up some space, boot into Ubuntu or a LiveCD, and run gparted (you may need to install gparted - [sudo apt-get install gparted]), use the GUI to create a new ext4 partition in the space you've freed up.

Next, install grub to the new partition. Find out what the new partition's location is (e.g. /dev/[COLOR="Red"]sda3[/COLOR]) and run ```
install-grub /dev/[COLOR="Red"]sda3[/COLOR]
```

You should then be able to edit the menu.lst in the new boot partition to your liking. Note that you may need to make some fundamental changes to the contents of it if you use your Ubuntu's menu.lst as a basis; notably that your Ubuntu installation entries may need to be told where their root is, e.g.:
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root         (hd1,2)
kernel       /boot/vmlinuz-2.6.28-11-generic root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro quiet splash 
initrd       /boot/initrd.img-2.6.28-11-generic
quiet

```

---

### Post by oldfred on 2010-07-06
Does your windows boot ok. The script is not showing:
/Windows/System32/winload.exe

With Ubuntu on an external you normally install grub to the external and set the BIOS to boot the external first adn internal second. If found it boots thru grub and gives you a choice for Ubuntu or windows. If the external is not found it boots the internal drive which still has the windows boot loader. You can create a new grub only partition if you want, but it is not necessary if all you want is to boot windows.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by pFREDq on 2010-07-06
> **WorMzy said:**
> If you created a boot partition on your internal hard drive for grub to reside in, then you could boot regardless of the external HD being present or not. You wouldn't be able to edit it without booting into Ubuntu, another Linux OS, or a LiveCD, but you could still boot Windows without needing the external HD.

To do this, you're going to need to resize one of your internal drive's ntfs partitions, as there's no free space for the new partition at present. To resize your ntfs partitions, I recommend booting into Vista (or Win 7, whichever you're using), and using the native partition management software to resize one of them. I don't know how much space is required, but I'd suggest freeing about 5GB, you can try less if you'd prefer, Grub legacy generally only takes up ~170kb.

After you've freed up some space, boot into Ubuntu or a LiveCD, and run gparted (you may need to install gparted - [sudo apt-get install gparted]), use the GUI to create a new ext4 partition in the space you've freed up.

Next, install grub to the new partition. Find out what the new partition's location is (e.g. /dev/[COLOR=Red]sda3[/COLOR]) and run ```
install-grub /dev/[COLOR=Red]sda3[/COLOR]
```You should then be able to edit the menu.lst in the new boot partition to your liking. Note that you may need to make some fundamental changes to the contents of it if you use your Ubuntu's menu.lst as a basis; notably that your Ubuntu installation entries may need to be told where their root is, e.g.:
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root         (1,2)
kernel       /boot/vmlinuz-2.6.28-11-generic root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro quiet splash 
initrd       /boot/initrd.img-2.6.28-11-generic
quiet

```
Okay, I did all that and it still gives me an error (Error 21) when the external isn't detected. I think I'll just do what oldfred suggested, unless you have an idea why it's still giving me the error.

---

### Post by WorMzy on 2010-07-06
I hate error 21. It's like saying "something went wrong, somewhere. Maybe. I'm not sure what". Can you rerun the boot info script and hopefully it'll tell us what went wrong.

Oldfred's suggestion is probably the better solution though, I didn't think of that, but it makes more sense.

---

### Post by pFREDq on 2010-07-06
Hm, apparently it's still looking for stage2 and menu.lst on the external. -__-

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 1941471240 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8d64c3d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   282,499,062   282,499,000   7 HPFS/NTFS
/dev/sda2         292,984,832   312,573,951    19,589,120   7 HPFS/NTFS
/dev/sda3         282,503,025   292,977,404    10,474,380  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbce2081

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,918,202,270 1,918,202,208   7 HPFS/NTFS
/dev/sdb2       1,918,203,904 1,932,883,967    14,680,064   7 HPFS/NTFS
/dev/sdb3       1,932,886,016 1,953,519,615    20,633,600  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4690451B904512BB                       ntfs                                     
/dev/sda2        42E44E1AE44E1119                       ntfs       PRESARIO_RP                   
/dev/sda3        91eb3bec-d744-4bbf-90be-e584344570c8   ext4                                     
/dev/sdb1        D27431CF7431B6D7                       ntfs       Iomega HDD                    
/dev/sdb2        86C80F6EC80F5BB5                       ntfs       XP                            
/dev/sdb3        b49dac7a-a68e-4e4a-89ba-04e84614b12d   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb2        /media/XP                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdb3/boot/grub/menu.lst: ===========================

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
default        4

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
# kopt=root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b49dac7a-a68e-4e4a-89ba-04e84614b12d

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
uuid        b49dac7a-a68e-4e4a-89ba-04e84614b12d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b49dac7a-a68e-4e4a-89ba-04e84614b12d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b49dac7a-a68e-4e4a-89ba-04e84614b12d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 994.0GB: boot/grub/menu.lst
 994.0GB: boot/grub/stage2
 994.0GB: boot/initrd.img-2.6.28-11-generic
 994.0GB: boot/vmlinuz-2.6.28-11-generic
 994.0GB: initrd.img
 994.0GB: vmlinuz
```

---

### Post by WorMzy on 2010-07-06
It doesn't seem to have actually installed the necessary files to the boot partition like I thought it would. Never mind, you can either fix this or delete the partition and follow oldfred's advice.

If you want to continue this way, then try booting into Ubuntu and using mount to mount your boot partition over /boot:
```
sudo mount -t ext4 /dev/sda3 /boot
```
Then reinstall grub
```
sudo apt-get install --reinstall grub
```
Then run
```
sudo update-grub
```
Finally, run
```
sudo grub
```
```
find /boot/grub/stage1
```
Hopefully it'll list something like (hd0,2), as well as (hd1,2). If so, run:
```
root (hd0,2)
setup (hd0)
```

And that should be it. Exit with ```
quit
``` and reboot.

---

### Post by pFREDq on 2010-07-06
Okay, I did all that, but when I got to "find /boot/grub/stage1" it said something like "file not found." I figured maybe I mistyped something, so I exited with "quit" and then closed terminal (not sure why I did that). And now whenever I try to open terminal again, I get the error message "There was an error creating the child process for this terminal" and I can't type anything.

EDIT: I rebooted and terminal is working now. I redid it and the same thing happened.

---

### Post by WorMzy on 2010-07-06
I made a mistake

```
sudo mount -t ext4 /dev/sda3 /dev
```
Should have been
```
sudo mount -t ext4 /dev/sda3 /**boot**
```

Reboot again and try it again with the right command. Sorry for the confusion. :)

---

### Post by pFREDq on 2010-07-06
Well that solved that problem, but now after "find /boot/grub/stage1" it returns (hd1,2), nothing about hd0.

After "sudo update-grub", it returned this: "Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###" Is it supposed to say this? If not, should I run "mkdir /boot/grub" and try again?

---

### Post by WorMzy on 2010-07-06
Yes, run 'mkdir /boot/grub', then try again.

---

### Post by pFREDq on 2010-07-06
"find /boot/grub/stage1" still only returns (hd1,2).

---

### Post by WorMzy on 2010-07-06
I'm getting very confused by this now. If you've still got the boot partition mounted, what does /boot/grub have in it now?

Try running:
```
grub-install /dev/sda3
```
Then do the grub -> find commands again.

---

### Post by pFREDq on 2010-07-06
And after that it still only returns (hd1,2). If it helps, "sudo grub-install /dev/sda3" returns:

"Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda3 as (hd0,2)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb"

---

### Post by WorMzy on 2010-07-06
That looks fine. But find should definitely be showing (hd0,2) now. Oh well, try running```
root (hd0,2)
setup (hd0)
```

It's telling you that it's installed to hd0,2 without problems, so these commands should work fine.

---

### Post by pFREDq on 2010-07-06
Alright, I did that and rebooted. Now whether it detects the external or not it loads some console-esque screen. At the top it says something along the lines of "press Tab to see a list of commands" and underneath that it says "grub>" with a blinking cursor. Looking at the commands, one was "boot", so I tried that and it said the kernel has to be loaded. "Kernel" was one of the commands so I tried that and it said I have to refer to a specific location.

Since I'm unable to boot anything, I am currently using the Ubuntu live CD.

EDIT: I'm looking at the files on the 5GB ext4 partition I made, and the folder "grub" is at the root while on the Ubuntu partition, it's in a folder called "boot". Could that have something to do with it?
EDIT2: I thought I had seen the screen somewhere, it's the same as when you type "sudo grub" into terminal.

---

### Post by WorMzy on 2010-07-06
Believe it or not, that's a good sign. We've finally got it to install and use the boot partition. Now you just need to modify the menu.lst.

So in the LiveCD, mount your boot partition
```
sudo mount -t ext4 /mnt
```
Then
```
gksu gedit /mnt/grub/menu.lst
```

Like I said before, you can use your Ubuntu menu.lst as a basis if you want:
```
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
default        4

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
# kopt=root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b49dac7a-a68e-4e4a-89ba-04e84614b12d

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
uuid        b49dac7a-a68e-4e4a-89ba-04e84614b12d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b49dac7a-a68e-4e4a-89ba-04e84614b12d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b49dac7a-a68e-4e4a-89ba-04e84614b12d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b49dac7a-a68e-4e4a-89ba-04e84614b12d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

```

Just be aware that you may need to add
```
root (hd1,2)
```
to your Ubuntu entries.

EDIT: It shouldn't matter that it's not in /boot/grub, it's finding it, that's all that matters.

---

### Post by pFREDq on 2010-07-06
It worked! Thank you guys so much for taking time out of your day to help me out, I really appreciate it! I also learned a few things, so maybe next time I won't have to bug you guys when something goes wrong. Maybe. ;)
Thanks again! ^_^

---

### Post by WorMzy on 2010-07-06
I'm glad we managed to get it sorted (eventually!)

I'm sorry it took so long to get it working, but I think I've learnt from this experience too, so the next time I come across a topic like this, I'll be able to help the OP much quicker.

:)

---

