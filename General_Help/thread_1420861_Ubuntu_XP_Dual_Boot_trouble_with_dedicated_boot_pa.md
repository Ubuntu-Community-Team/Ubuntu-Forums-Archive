---
title: "Ubuntu XP Dual Boot trouble with dedicated /boot partition"
date: 2010-03-03
forum: General Help
---

### Post by Dilbert_ on 2010-03-03
Hi all. I successfully set up a dual boot ubuntu/xp machine but it stopped working after booting into XP and ubuntu once. I have a single harddrive in a Dell Inspiron 9200. Oiginally, it contained a Dell Utilities Partition, Windows Partition, and Dell Restore Partition.  I deleted the Dell Utilities Parition and added a partition for ubuntu and also a dedicated boot partition using a bootable gparted usb key.  Then I installed Hardy and at the end of the install I used the advanced button to install grub to the ubuntu partition. The MBR is configured with Grub stage 1 and points to stage 2 on the boot partition. This loads a menu.lst with all the usual linux options.  The last option, for the windows bootloader, is the one that has stopped working.

I added Ubuntu to the windows boot.ini file by creating a bootsector.lin file containing the 512 byte ubuntu boot sector. And I also installed windows in Grub. As such, I could boot to the grub menu, chainload the windows boot menu, and then chainload back to grub, and etc.. Of course, selecting a windows option (normal, safe mode, etc) from the windows bootloader would boot XP and choosing an ubuntu option from Grub would load Ubuntu.

However, after booting into Ubuntu, then XP, and then Ubuntu again.... the XP option stopped working.  Selecting Windows from grub results in a blank screen with just the word "Starting.." in white text in the upper left corner. I can still mount the NTFS partition in linux and look at all my windows files. I just cant boot the XP OS.  I tried using super grub disk. It detects the windows partition but doesn't boot it either. I also tried ms-sys which install a windows bootloader in the mbr. This failed to boot and I had to reinstall grub to the MBR.

I have spent a lot of time researching this on the web and running tests.  I'm a newb to linux, but I've done my homework.  (Originally, my dual boot config didn't work because my BIOS doesn't support LBA and my Ubuntu partion was past 1024 cyclinders. Thats the primary reason for shifting my partitions around and addind a small boot partition up front. I also realized, that a boot partition is desirable if you have multiple OS's and reload or change them alot.)

Can anybody tell me what has gone wrong? I think I've lost the bootloader code from my XP partition but I'm not sure how that would happen and what I need to do to fix it.  All of the fix MBR options out there don't seem to work. It's not really the Master Boot Record of the drive that needs fixing. I think its the boot sector of my XP partition that needs help.

I've attached the output of Boot Info Script 0.55 for diagnostic info.

Any help is greatly appreciated!

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 28487 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 0.97 in the file /ubuntu.bin looks at sector 
                       439120089 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst. Grub 
                       0.97 in the file /ubuntu_loader.bin looks at sector 
                       28487 of the same hard drive for the stage2 file. A 
                       stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #1 for /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub 0.97 in the file /ubuntu.bin looks at sector 
                       439120089 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst. Grub 
                       0.97 in the file /ubuntu_boot.bin looks at sector 
                       439120089 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst. Grub 
                       0.97 in the file /ubuntu_loader.bin looks at sector 
                       28487 of the same hard drive for the stage2 file. A 
                       stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #1 for /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef22ef22

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  83 Linux
/dev/sda2    *         96,390   333,541,529   333,445,140   7 HPFS/NTFS
/dev/sda3         481,050,360   488,392,064     7,341,705  db CP/M / CTOS / ...
/dev/sda4         333,541,530   481,050,359   147,508,830   5 Extended
/dev/sda5         333,541,593   474,977,789   141,436,197  83 Linux
/dev/sda6         474,977,853   481,050,359     6,072,507  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2f7c5253-7c0c-4e26-ab81-5f70b05550d8   ext2       Boot                          
/dev/sda2        EC6CD86D6CD83454                       ntfs                                     
/dev/sda3        0000-0000                              vfat       DellRestore                   
/dev/sda5        b668adfe-9546-4d08-8df9-b1b4fd8f9b59   ext3                                     
/dev/sda6        3cd0725c-45c1-4bb7-8d3f-c6560425c855   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)


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
# kopt=root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

# This is a description line to display the location of this menu.lst file
title        /Boot partition
root

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Back to Microsoft Bootloader
root (hd0,1)
#savedefault
makeactive
chainloader    +1
boot

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.24-26-generic
    .0GB: boot/vmlinuz-2.6.24-26-generic

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
c:\ubuntu_loader.bin="Go to Ubuntu GRUB Loader"


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
default        6

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
# kopt=root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# howmany=3

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
root        (hd0,1)
savedefault
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3cd0725c-45c1-4bb7-8d3f-c6560425c855 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 224.8GB: boot/grub/menu.lst
 224.8GB: boot/grub/stage2
 224.7GB: boot/initrd.img-2.6.24-26-generic
 224.8GB: boot/initrd.img-2.6.24-27-generic
 224.8GB: boot/initrd.img-2.6.24-27-generic.bak
 224.7GB: boot/vmlinuz-2.6.24-26-generic
 224.8GB: boot/vmlinuz-2.6.24-27-generic
 224.8GB: initrd.img
 224.7GB: initrd.img.old
 224.8GB: vmlinuz
 224.7GB: vmlinuz.old

```

---

### Post by gsmanners on 2010-03-03
What does the boot.ini look like? Here's a more normal one:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by oldfred on 2010-03-03
You have grub in the windows partition. Windows also chainboots and has to have its boot files in the boot sector.

To see how it works:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

to repair window you need to run the fixboot command from an XP disk. If you run fixmbr it will overwrite grub in the MBR which you do not want.

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.


FIXBOOT  C:

Alt From linux:
Restore PBR boot sectot for windows from linux using testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Dilbert_ on 2010-03-04
First of all, thanks for the responses.

Secondly, here is my boot.ini.  It pretty standard except for the last line with the dot bin file which is a copy of the bootsector on the Ubuntu partition

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
c:\ubuntu_loader.bin="Go to Ubuntu GRUB Loader"


```

And lastly, I'm going to give that Multiboot article a good read and then get my hands on an XP disk from somewhere and try the suggested fix.  I'll post back with any results/revelations.

---

### Post by Dilbert_ on 2010-03-04
Okay, I tried booting into recovery mode on an XP cd, but I can not get past the administrator password. My user account is an administrator account but that password doesn't work. There aren't any other accounts on the system unless a default administrator account is created when XP is installed. If that's true, I have no idea what the password is. I already tried "enter".

As for TestDisk, I had already used it to recover the backup PBR.  (Perhaps that means grub somehow got in the NTFS partitions PBR and backup PBR.  So I used TestDisk to rebuild the MBR instead.

Now, if you look at the output of Boot Info Script you will notice sda2 is NTFS with Boot Sector Type: Windows XP (as opposed to Grub before.)


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 28487 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 0.97 in the file /ubuntu.bin looks at sector 
                       439120089 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst. Grub 
                       0.97 in the file /ubuntu_loader.bin looks at sector 
                       28487 of the same hard drive for the stage2 file. A 
                       stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #1 for /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub 0.97 in the file /ubuntu.bin looks at sector 
                       439120089 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst. Grub 
                       0.97 in the file /ubuntu_boot.bin looks at sector 
                       439120089 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst. Grub 
                       0.97 in the file /ubuntu_loader.bin looks at sector 
                       28487 of the same hard drive for the stage2 file. A 
                       stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #1 for /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef22ef22

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  83 Linux
/dev/sda2    *         96,390   333,541,529   333,445,140   7 HPFS/NTFS
/dev/sda3         481,050,360   488,392,064     7,341,705  db CP/M / CTOS / ...
/dev/sda4         333,541,530   481,050,359   147,508,830   5 Extended
/dev/sda5         333,541,593   474,977,789   141,436,197  83 Linux
/dev/sda6         474,977,853   481,050,359     6,072,507  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2f7c5253-7c0c-4e26-ab81-5f70b05550d8   ext2       Boot                          
/dev/sda2        EC6CD86D6CD83454                       ntfs                                     
/dev/sda3        0000-0000                              vfat       DellRestore                   
/dev/sda5        b668adfe-9546-4d08-8df9-b1b4fd8f9b59   ext3                                     
/dev/sda6        3cd0725c-45c1-4bb7-8d3f-c6560425c855   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/scd0        /media/GRTMHFPP_EN       iso9660    (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


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
# kopt=root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

# This is a description line to display the location of this menu.lst file
title        /Boot partition
root

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Back to Microsoft Bootloader
root (hd0,1)
#savedefault
makeactive
chainloader    +1
boot

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.24-26-generic
    .0GB: boot/vmlinuz-2.6.24-26-generic

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
c:\ubuntu_loader.bin="Go to Ubuntu GRUB Loader"


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
default        6

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
# kopt=root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# howmany=3

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
root        (hd0,1)
savedefault
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b668adfe-9546-4d08-8df9-b1b4fd8f9b59 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3cd0725c-45c1-4bb7-8d3f-c6560425c855 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 224.8GB: boot/grub/menu.lst
 224.8GB: boot/grub/stage2
 224.7GB: boot/initrd.img-2.6.24-26-generic
 224.8GB: boot/initrd.img-2.6.24-27-generic
 224.8GB: boot/initrd.img-2.6.24-27-generic.bak
 224.7GB: boot/vmlinuz-2.6.24-26-generic
 224.8GB: boot/vmlinuz-2.6.24-27-generic
 224.8GB: initrd.img
 224.7GB: initrd.img.old
 224.8GB: vmlinuz
 224.7GB: vmlinuz.old

```

I still can't dual boot to XP. As usual, the MBR goes to boot/grub/menu.lst on my dedicated boot partition. I can tell becasue I added a description line at the top of the menu.lst on the boot partition. (There is another menu.lst on the ubuntu partition.) All the linux selections work but the XP option does not. It still produces the message "Starting..." and then stops.

Any thoughts????

---

### Post by oldfred on 2010-03-04
It does not look like testdisk recovered it. This is what my XP partition looks like, you need to try the windows repairs:
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

---

### Post by meierfra. on 2010-03-04
> I think its the boot sector of my XP partition 

None of the RESULTS.txt show any problem with the XP boot sector.

> Boot file info:     Grub 0.97 in the file /ubuntu.bin looks at sector 
                       439120089 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #5 for /boot/grub/menu.lst. Grub 
                       0.97 in the file /ubuntu_loader.bin looks at sector 
                       28487 of the same hard drive for the stage2 file. A 
                       stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #1 for /boot/grub/menu.lst.
This just shows the files you have been using to chainload Grub from XP boot loader.    They are not installed in the boot sector and should not cause any problems.

Were you ever able to boot Window from the Grub menu?

Try this

```

sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```

Change 

title        Back to Microsoft Bootloader
root (hd0,1)
#savedefault
makeactive
chainloader    +1
boot

to

title        Back to Microsoft Bootloader
rootnoverify (hd0,1)
chainloader    +1

Reboot and see whether you can boot XP.

If that did not work, might also see what happens if your restore your MBR with lilo:

```
sudo apt-get install lilo
```
(ignore the warnings)
and

```
sudo lilo -M /dev/sda mbr
```

Reboot. You should get the Windows Boot Menu. Maybe you will be able to boot into XP and Ubuntu from the Windows Boot Menu.

---

