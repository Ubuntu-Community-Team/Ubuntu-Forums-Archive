---
title: "Boot error 15"
date: 2011-01-16
forum: General Help
---

### Post by chitragurung on 2011-01-16
Hello,
 
I am using ubuntu 8.04 with dell inspiron mini. Since couple of days, I got following error
 
error 15: file not found
 
Press any key to continue
 
After than
 
it appears
 
Ubuntu 8.04.2 kernel 2.6.24-27-lpia
Ubuntu 8.04.2, kernel 2.6.24-27-lpia ( recovery mode )
Ubuntu 8.04.2, kernel 2.6.24-24-lpia 
Ubuntu 8.04.2, kernel 2.6.24-24-lpia ( recovery mode )
Ubuntu 8.04.2, kernel 2.6.24-22-lpia 
Ubuntu 8.04.2, kernel 2.6.24-22-lpia ( recovery mode )
 
System Restore
 
Use the Up and Down keys to select which entry is highlighted press enter to boot selected OS, "e" to edit the commands before booting, or c for command line.
 
 
Before it was not like this. How can I fix it for smooth running.

---

### Post by oldfred on 2011-01-17
Info on grub legacy's error 15.
[http://members.iinet.net.au/~herman546/p15.html#15](http://members.iinet.net.au/~herman546/p15.html#15)

run this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by chitragurung on 2011-01-17
Hello,

Here is the results.  

              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  According to the info in the boot sector, sda1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 329683 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e3e8e76

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        48,194        48,132  de Dell Utility
/dev/sda2    *         48,195   308,656,844   308,608,650  83 Linux
/dev/sda3         308,656,845   312,576,704     3,919,860  1c Hidden W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D9-0306                              vfat       DellUtility                   
/dev/sda2        77eb26dc-768b-4e59-bf5a-bb0e8f20f746   ext3                                     
/dev/sda3        49D0-D617                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw)


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
timeout        0

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
# kopt=ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
## e.g. in_domU=detect
##      in_domU=true
##      in_domU=false
# in_domU=false

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

title        Ubuntu 8.04.2, kernel 2.6.24-27-lpia
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-27-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic 

initrd        /boot/initrd.img-2.6.24-27-lpia
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-27-lpia (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-27-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled single
initrd        /boot/initrd.img-2.6.24-27-lpia

title        Ubuntu 8.04.2, kernel 2.6.24-24-lpia
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled quiet splash
initrd        /boot/initrd.img-2.6.24-24-lpia
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-lpia (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled single
initrd        /boot/initrd.img-2.6.24-24-lpia

title        Ubuntu 8.04.2, kernel 2.6.24-22-lpia
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-22-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled quiet splash
initrd        /boot/initrd.img-2.6.24-22-lpia
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-22-lpia (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-22-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled single
initrd        /boot/initrd.img-2.6.24-22-lpia

title        Ubuntu 8.04.2, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title System Restore
root (hd0,2)
chainloader +1
boot

=============================== sda2/etc/fstab: ===============================

/dev/sda2        /                ext3 defaults    0 0
proc            /proc            proc    defaults    0 0

=================== sda2: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
   1.9GB: boot/initrd.img-2.6.24-24-lpia
   1.8GB: boot/initrd.img-2.6.24-24-lpia.bak
   2.5GB: boot/vmlinuz-2.6.24-24-lpia
   1.9GB: initrd.img.old
   2.5GB: vmlinuz.old

=================== sda3: Location of files loaded by Grub: ===================


 158.0GB: initrd0.img
 159.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by chitragurung on 2011-01-17
Here is the results
         

       Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  According to the info in the boot sector, sda1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 329683 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e3e8e76

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        48,194        48,132  de Dell Utility
/dev/sda2    *         48,195   308,656,844   308,608,650  83 Linux
/dev/sda3         308,656,845   312,576,704     3,919,860  1c Hidden W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D9-0306                              vfat       DellUtility                   
/dev/sda2        77eb26dc-768b-4e59-bf5a-bb0e8f20f746   ext3                                     
/dev/sda3        49D0-D617                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw)


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
timeout        0

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
# kopt=ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
## e.g. in_domU=detect
##      in_domU=true
##      in_domU=false
# in_domU=false

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

title        Ubuntu 8.04.2, kernel 2.6.24-27-lpia
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-27-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic 

initrd        /boot/initrd.img-2.6.24-27-lpia
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-27-lpia (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-27-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled single
initrd        /boot/initrd.img-2.6.24-27-lpia

title        Ubuntu 8.04.2, kernel 2.6.24-24-lpia
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled quiet splash
initrd        /boot/initrd.img-2.6.24-24-lpia
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-lpia (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled single
initrd        /boot/initrd.img-2.6.24-24-lpia

title        Ubuntu 8.04.2, kernel 2.6.24-22-lpia
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-22-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled quiet splash
initrd        /boot/initrd.img-2.6.24-22-lpia
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-22-lpia (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-22-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled single
initrd        /boot/initrd.img-2.6.24-22-lpia

title        Ubuntu 8.04.2, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title System Restore
root (hd0,2)
chainloader +1
boot

=============================== sda2/etc/fstab: ===============================

/dev/sda2        /                ext3 defaults    0 0
proc            /proc            proc    defaults    0 0

=================== sda2: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
   1.9GB: boot/initrd.img-2.6.24-24-lpia
   1.8GB: boot/initrd.img-2.6.24-24-lpia.bak
   2.5GB: boot/vmlinuz-2.6.24-24-lpia
   1.9GB: initrd.img.old
   2.5GB: vmlinuz.old

=================== sda3: Location of files loaded by Grub: ===================


 158.0GB: initrd0.img
 159.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
> **oldfred said:**
> Info on grub legacy's error 15.
[http://members.iinet.net.au/~herman546/p15.html#15]("http://members.iinet.net.au/%7Eherman546/p15.html#15")

run this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by oldfred on 2011-01-18
Did you manually edit?

kernel        /boot/vmlinuz-2.6.24-27-lpia ro  root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux  hpet=disabled quiet splash 
initrd        /boot/initrd.img-[COLOR=Red]2.6.28-11[/COLOR]-generic 

You do not have a .28 just the 2.6.24 versions.

---

### Post by chitragurung on 2011-01-18
I think I had edit menu list to work with CDMA usb modem ? But I do not know where I edit.
 
How can I fix it. I try to remove others like 2.6.27, 22 through synaptic manager but nothing happen.
 
Also how can I fix it ?
 
> **oldfred said:**
> Did you manually edit?
 
kernel /boot/vmlinuz-2.6.24-27-lpia ro root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux hpet=disabled quiet splash 
initrd /boot/initrd.img-[COLOR=red]2.6.28-11[/COLOR]-generic 
 
You do not have a .28 just the 2.6.24 versions.

---

### Post by oldfred on 2011-01-19
IF you cannot boot with the second line, then you will have to edit from a liveCD.

Have you tried using escape from BIOS until menu appears and use the recovery mode boot or the boot lines with .24. 

It looks like you deleted all the kernels except .24 including some of the newer ones.

---

### Post by chitragurung on 2011-01-25
How can I edit this ?

Please advice.



> **oldfred said:**
> IF you cannot boot with the second line, then you will have to edit from a liveCD.

Have you tried using escape from BIOS until menu appears and use the recovery mode boot or the boot lines with .24. 

It looks like you deleted all the kernels except .24 including some of the newer ones.

---

### Post by oldfred on 2011-01-26
It has been a while since I used old grub, but did it not also include the e for edit where you could edit the boot lines? Escape should give you the grub menu if you do not get it normally.

Otherwise you have to use a liveCD and edit menu.lst with gedit or your favorite editor.

---

