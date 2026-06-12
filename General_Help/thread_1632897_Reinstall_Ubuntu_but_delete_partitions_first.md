---
title: "Reinstall Ubuntu but delete partitions first?"
date: 2010-11-28
forum: General Help
---

### Post by bobke on 2010-11-28
I have Edgy on hda1, Mepis on hda2, and Hardy on hda 5 in extended part 4. Right now I can't back-up to any external drive because they won't mount. My file system on hda1 can't be checked ( i believe because of a bad UUID which I have not been able to resolve). I have been using hda1-edgy as my main system and mepis-hda2 as a back-up.  But when I installed Hardy I lost my  UUIDs. My resolve for this is to try to delete Hardy (hda5) leaving hda2 and hda1-edgy so that I might at least be able to mount a removable to backup hda1. then I'll reinstall edgy, Hardy...and so on until I get to something that is current. At least that's my plan thus far. But before I do any of this I need to find out where GRUB is loaded. It is not with hda1 but would like to put it there. (Is this what- Active- means in Gparted?) Any suggestions on how not to loose my current files on hda1-edgy while reinstalling?

---

### Post by sikander3786 on 2010-11-28
By hda1, hda2.... do you mean separate Hard Drives or separate Partitions?

Which version of Ubuntu do you plan to install now?

If you can boot a Live CD/USB and post the output of bootinfoscript as per instructions here, it would be a great help for us to understand you current setup.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please wrap the output using proper code tags # from post menu. [/code] at the end and [code] at the beginning.

---

### Post by bobke on 2010-11-30
> **sikander3786 said:**
> By hda1, hda2.... do you mean separate Hard Drives or separate Partitions?

Which version of Ubuntu do you plan to install now?

If you can boot a Live CD/USB and post the output of bootinfoscript as per instructions here, it would be a great help for us to understand you current setup.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please wrap the output using proper code tags # from post menu. [/code] at the end and ```
 at the beginning.

1- I have been able to back up my home folder via Mepis to DVD. So I'm covered for a backup thus far, but couldn't back up via tar archive, had to drag files over directly uncompressed to the DVD. 

2- I thought it would be good to reinstall Edgy from the original CD (not live CD), then try backup via archive tool so after the next upgrade install all settings as well as my document files will be there.

3- Next, I'm wondering if I shouldn't reformat the computer and install windows then install Hardy as split partition. This was originally a Windows computer which I made into a Ubuntu/mepis/multi boot computer. This computer had a problem with the graphics card* and I installed a different card last year which confused things. I wonder if the HD isn't corrupt, which is why I think I should clean it out and start over. In this case I will only be able to drag doc files over and will need to redo all settings, I guess. If this is the case maybe I can go ahead and try to install the lastes Ubuntu and skip Hardy. I don't know I that will hurt too much.  If there is a better idea here, please let me know.

*The Computer is a PowerSpec about 5 yrs old w/ newer Geforce 8400 GS as an addition to the original onboard graphics.

In any case if I can resolve this partitioning issue, maybe I can get some better BU for hda1-edgy. I am particularly concerned about Bookmarks and Evolution BU.

These are the partitions on the same computer. This is such a neato tool, to veiw it all at once!

[CODE]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 6.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian and Ubuntu packages 
                       power the Magic of MEPIS TM Press Ctrl-Alt-F7, or 
                       maybe Ctrl-Alt-F8, for graphical login screen
    Boot files/dirs:   /etc/fstab

hda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hda1                  63   195,944,804   195,944,742  83 Linux
/dev/hda2         195,944,805   235,512,899    39,568,095  83 Linux
/dev/hda3         235,512,900   236,942,684     1,429,785  82 Linux swap / Solaris
/dev/hda4         236,942,685   312,576,704    75,634,020   5 Extended
/dev/hda5    *    236,942,748   309,444,029    72,501,282  83 Linux
/dev/hda6         309,444,093   312,576,704     3,132,612  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/evms/hda1   972af1d0-babe-4e0d-adba-962e1c6bd37c   ext3       Ubuntu6.06dapper              
/dev/evms/hda2   22d50617-d6da-465b-9870-6a0724af1e70   ext3       Mepis                         
/dev/evms/hda3   a6955f51-10ef-4927-a619-13fa99c5514c   swap                                     
/dev/evms/hda5   825dbbec-3a79-430a-8b63-0ae85a7daefd   ext3                                     
/dev/evms/hda6   85ebd510-66dd-4953-a61d-c776b19c5447   swap                                     
/dev/hda1        972af1d0-babe-4e0d-adba-962e1c6bd37c   ext3       Ubuntu6.06dapper              
/dev/hda2        22d50617-d6da-465b-9870-6a0724af1e70   ext3       Mepis                         
/dev/hda3        a6955f51-10ef-4927-a619-13fa99c5514c   swap                                     
/dev/hda5        825dbbec-3a79-430a-8b63-0ae85a7daefd   ext3                                     
/dev/hda6        85ebd510-66dd-4953-a61d-c776b19c5447   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/hda1        /                        ext3       (rw,errors=remount-ro)


=========================== hda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title        Ubuntu, kernel 2.6.17-12-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-12-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd        /boot/initrd.img-2.6.17-12-386
savedefault
boot

title        Ubuntu, kernel 2.6.17-12-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-12-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd        /boot/initrd.img-2.6.17-12-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title Edgy on hda5
root (hd0,4)
configfile /boot/grub/menu.lst

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        MEPIS at hda2, kernel 2.6.15-26-386 (on /dev/hda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 nomce quiet vga=791 
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        MEMTEST (on /dev/hda2)
root        (hd0,1)
kernel        /boot/memtest86+.bin  
savedefault
boot

=============================== hda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=49380a4b-5a11-4edc-b768-82ebdb1874a3 /media/hda5 ext3 defaults 0 2
# /dev/hda3 -- converted during upgrade to edgy
UUID=2c0c7405-9d7d-4a4c-b628-f7a4d85abfee none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== hda1: Location of files loaded by Grub: ===================


  28.6GB: boot/grub/menu.lst
  28.6GB: boot/grub/stage2
  28.6GB: boot/initrd.img-2.6.15-26-386
  28.6GB: boot/initrd.img-2.6.15-27-386
  28.6GB: boot/initrd.img-2.6.15-28-386
  28.7GB: boot/initrd.img-2.6.15-29-386
  28.6GB: boot/initrd.img-2.6.17-12-386
  28.7GB: boot/vmlinuz-2.6.15-26-386
  28.6GB: boot/vmlinuz-2.6.15-27-386
  28.6GB: boot/vmlinuz-2.6.15-28-386
  28.5GB: boot/vmlinuz-2.6.15-29-386
  28.6GB: boot/vmlinuz-2.6.17-12-386
  28.6GB: initrd.img
  28.7GB: initrd.img.old
  28.6GB: vmlinuz
  28.5GB: vmlinuz.old

=============================== hda2/etc/fstab: ===============================

# Pluggable devices are handled by uDev, they are not in fstab
/dev/hda2 / auto defaults,noatime 1 1
none /proc proc defaults 0 0
none /proc/bus/usb usbfs devmode=0666 0 0
none /dev/pts devpts mode=0622 0 0
none /sys sysfs defaults 0 0
# Dynamic entries below, identified by 'users' option
/dev/hda1 /mnt/hda1 ext3 noauto,users,exec 0 0
/dev/hda3 swap swap sw,pri=1 0 0
/dev/hda5 /mnt/hda5 ext3 noauto,users,exec 0 0
/dev/hda6 swap swap sw,pri=1 0 0
/dev/cdrom /media/cdrom iso9660,udf noauto,users,exec,ro 0 0

=================== hda2: Location of files loaded by Grub: ===================


 115.4GB: boot/grub/stage2
 115.4GB: boot/initrd.img-2.6.15-26-386
 115.4GB: boot/vmlinuz-2.6.15-26-386

=========================== hda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=825dbbec-3a79-430a-8b63-0ae85a7daefd ro

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=825dbbec-3a79-430a-8b63-0ae85a7daefd ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=825dbbec-3a79-430a-8b63-0ae85a7daefd ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        Ubuntu, kernel 2.6.17-12-386 (on /dev/hda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-12-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash 
initrd        /boot/initrd.img-2.6.17-12-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        Ubuntu, kernel 2.6.17-12-386 (recovery mode) (on /dev/hda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-12-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single 
initrd        /boot/initrd.img-2.6.17-12-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        Ubuntu, memtest86+ (on /dev/hda1)
root        (hd0,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        Ubuntu 6.06.1 LTS (6.06) (on /dev/hda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot


=============================== hda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=825dbbec-3a79-430a-8b63-0ae85a7daefd /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda3
UUID=a6955f51-10ef-4927-a619-13fa99c5514c none            swap    sw              0       0
# /dev/hda6
UUID=85ebd510-66dd-4953-a61d-c776b19c5447 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== hda5: Location of files loaded by Grub: ===================


 132.0GB: boot/grub/menu.lst
 132.1GB: boot/grub/stage2
 132.0GB: boot/initrd.img-2.6.24-19-generic
 132.0GB: boot/vmlinuz-2.6.24-19-generic
 132.0GB: initrd.img
 132.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hdc sda sdb sdc sdd 
=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file

```

---

### Post by Spyderkid on 2010-11-30
Why don't you just get it to use the whole disk by doing this it erases all past partitions, also it should give you options to delete partitions

---

### Post by sikander3786 on 2010-11-30
If I understood you correctly, your important data is on the Edgy partition, right? Did you try to boot into a live cd and mount your Edgy partition and backup your data? That should be simple.

If you are concerned about the HDD, I would definitely recommend to check it for bad sectors.

I am not sure which one of those operating system you wish to keep, and if you even wish to keep or not. Keeping any of them won't be beneficiery unless you upgrade them to a current version.

I would simply recommend to try to backup your data, try any of the newer version Ubuntu from the Live CD, 10.10 or 10.04 and if all goes well and all the hardware works with any of them, install that.

If you've any problem with backing up data or mounting the drive, you can definitely seek help here ;-)

Good Luck!

---

### Post by pricetech on 2010-11-30
It sounds like you'd be better off to wipe the whole drive and install Lucid, the latest LTS.  I agree with the above post about booting live first to make sure everything is happy.

Back up your data first, whatever you decide to do.  There's no guarantee either it or your settings will survive an upgrade.

---

### Post by bobke on 2010-11-30
> **pricetech said:**
> It sounds like you'd be better off to wipe the whole drive and install Lucid, the latest LTS.  I agree with the above post about booting live first to make sure everything is happy.

Back up your data first, whatever you decide to do.  There's no guarantee either it or your settings will survive an upgrade.

This was my very first thought - to install  the latest LTS over all. Obviously the simplest solution. But I thought I had to BU from edgy. I don't have an edgy live CD. So, are saying that I can BU from live Lucid LTS? If I can this should easily solve some problems, but I don't know how compatible my files will be moving them directly from edgy to Lucid. This is why I thought it would make more sense to see what works on Hardy first. But I'm not sure. I guess it can't hurt anything to experiment.

---

### Post by pricetech on 2010-11-30
What kind of files are we talking about ??  Your data, such as documents you've created, should open just fine in whatever program you're using now to open them.

If you're talking about bookmarks, your browser should be able to import them just fine.  Same with your address book in your email client.

Email messages might be a different story.  Mail clients differ on how they "store" your messages, but it should be pretty easy to import that into the latest version of the same client.

Settings can be a wildcard.  While many settings will work just fine, changes in applications over time might create issues with how a particular setting is interpreted by the program.  You may have to do application customizations again.

Otherwise, backing up your stuff is just a matter of being able to access it in some fashion, which a live CD, whatever version, will let you do.

---

### Post by bobke on 2010-12-05
> **pricetech said:**
> What kind of files are we talking about ??  Your data, such as documents you've created, should open just fine in whatever program you're using now to open them.

If you're talking about bookmarks, your browser should be able to import them just fine.  Same with your address book in your email client.

Email messages might be a different story.  Mail clients differ on how they "store" your messages, but it should be pretty easy to import that into the latest version of the same client.

Settings can be a wildcard.  While many settings will work just fine, changes in applications over time might create issues with how a particular setting is interpreted by the program.  You may have to do application customizations again.

Otherwise, backing up your stuff is just a matter of being able to access it in some fashion, which a live CD, whatever version, will let you do.

Yeah, I don' t have a problem with the document files. I have just installed edgy on another computer w/ windows, so i'm not to worried because I have the docs saved, but not the program files. I didn't compress the backup to DVD and they wouldn't all fit. I am in the process of doing that maybe tomorrow. If that works then I will have backup to my email and bookmarks as well which are still the only problem left. I have a snapshot of the bookmarks just in case and can do them by hand. As for the email I already no the settings for them and can save all msgs to separate file in my home folder as plain text. My real concern is that Lucid or what ever I will install will be completely compatible with my computer. Hardy did not completely install even from the CD. I think, after years of saying that I'm going to upgrade, I will finally get to it this week. I am more confident now!

---

