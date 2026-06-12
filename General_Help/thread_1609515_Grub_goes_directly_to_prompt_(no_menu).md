---
title: "Grub goes directly to prompt (no menu)"
date: 2010-10-30
forum: General Help
---

### Post by patricker on 2010-10-30
I rebooted my computer recently after installing some updates in Ubuntu and now when grub launches it goes straight to the grub prompt and I don't get a menu.  I tried searching around online and have tried what seemed like the most common fix but to no avail:[INDENT] find /boot/grub/stage1 (returns hd1,0)
root (hd1,0)
setup (hd0) -I also tried (hd1,0) and (hd1)
-then reboot- (still get no menu and goes straight to the prompt)
[/INDENT]I then tried booting into Ubuntu live, using apt-get to install Grub, and then running through the install process using similar commands, but to no avail.  When I run setup it finds my config info and doesn't show any errors.  I have a menu.lst file with lots of entries for different kernel versions and a windows 7 install on hd0,0.  I am running Ubuntu Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic-pae.

Any help would be appreciated.

---

### Post by drs305 on 2010-10-30
Depending on how you installed things, there's a good chance you are now using Grub2.

We can find out a lot about your boot files if you will run the boot info script found in the link below. It will generate a file called RESULTS.txt. Please paste the contents here. When you are ready to paste, click on the # icon to generate "code" tags and paste between them. It will tell us which version of Grub you are using, where your files are and where Grub is looking to find them (which may not be the same).

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by patricker on 2010-10-30
Here you go:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 
    1966407714 of the same hard drive for the stage2 file. A stage2 file is at 
    this location on /dev/sdb. Stage2 looks on partition #1 for 
    /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   293,044,223   293,042,176   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34 3,891,968,784 3,891,968,751 Linux or Data
/dev/sdb2   3,891,968,785 3,907,029,134    15,060,350 Linux Swap

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34 3,907,029,134 3,907,029,101 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E26CA7BD6CA78B3D                       ntfs       Fast Storage                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1        39aab7bd-af38-4c7b-ba75-40b9962a8a8d   ext3                                     
/dev/sdb2        2232abd4-6446-404a-a49c-6146c4c47615   swap                                     
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        0427fb41-4bdb-4852-8abd-f09852beb622   ext4       Storage                       
/dev/sdc: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/Storage           ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/39aab7bd-af38-4c7b-ba75-40b9962a8a8d ext3       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=39aab7bd-af38-4c7b-ba75-40b9962a8a8d

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic-pae
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic-pae
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic-pae (recovery mode)
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro  single
initrd        /boot/initrd.img-2.6.32-25-generic-pae

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic-pae
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic-pae
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic-pae (recovery mode)
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro  single
initrd        /boot/initrd.img-2.6.32-24-generic-pae

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic-pae
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic-pae
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic-pae (recovery mode)
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro  single
initrd        /boot/initrd.img-2.6.32-23-generic-pae

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic (recovery mode)
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        39aab7bd-af38-4c7b-ba75-40b9962a8a8d
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


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=39aab7bd-af38-4c7b-ba75-40b9962a8a8d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=2232abd4-6446-404a-a49c-6146c4c47615 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


1113.3GB: boot/grub/menu.lst
1006.8GB: boot/grub/stage2
1006.8GB: boot/initrd.img-2.6.28-19-generic
1006.7GB: boot/initrd.img-2.6.31-22-generic
1006.8GB: boot/initrd.img-2.6.32-23-generic
1006.8GB: boot/initrd.img-2.6.32-23-generic-pae
 531.8GB: boot/initrd.img-2.6.32-24-generic
 531.8GB: boot/initrd.img-2.6.32-24-generic-pae
 531.8GB: boot/initrd.img-2.6.32-25-generic
 531.8GB: boot/initrd.img-2.6.32-25-generic-pae
1006.7GB: boot/vmlinuz-2.6.28-19-generic
1006.7GB: boot/vmlinuz-2.6.31-22-generic
1006.8GB: boot/vmlinuz-2.6.32-23-generic
1006.8GB: boot/vmlinuz-2.6.32-23-generic-pae
1113.2GB: boot/vmlinuz-2.6.32-24-generic
1114.3GB: boot/vmlinuz-2.6.32-24-generic-pae
 531.8GB: boot/vmlinuz-2.6.32-25-generic
 531.8GB: boot/vmlinuz-2.6.32-25-generic-pae
 531.8GB: initrd.img
 531.8GB: initrd.img.old
 531.8GB: vmlinuz
 531.8GB: vmlinuz.old

```

---

### Post by drs305 on 2010-10-30
Thanks for posting the information. The boot script confirms you are using Grub legacy.

I don't see any flagrant problems with the information, but I never knew a lot about Grub legacy. I can't remember how Grub legacy wrote to sectors...  Have you tried hitting ESC to reveal the menu during boot? If you can get to a menu I'd try an older working kernel to see if it boots.

The one thing I noticed is that the menu.lst is very 'deep' into the disk. Have you moved any partitions, changed the boot order, or done anything similar?  Since you are still using Grub legacy, I'm guessing this might be an older motherboard/BIOS and it may not be able to see the files on boot unless the BIOS has been updated or 'large drive' option has been enabled. 

If you haven't changed anything then there is no reason to suspect that is the problem in this case.

You'll have to wait for someone more familiar with Grub legacy to come along to analyze this. 

I'd suggest upgrading to Grub2 unless you have a reason for sticking with Grub legacy. The package is "grub-pc". But in fairness if you are into tweaking grub you will find the upgrade is a major change. If all you care about is seeing a menu and letting it boot, the changes are significant but you don't have to deal with them often...

---

### Post by patricker on 2010-10-30
Well I definitely don't have an old motherboard/bios.  I'm running an EVGA x58 SLI LE which supports 3 way SLI and I have a couple of 2TB HD's in there.  I'm not doing anything special with Grub, I just want it to work, I also haven't done any messing around with partitions or the like.

I'll try installing the new version of Grub and see if it fixes the issue.

---

### Post by srs5694 on 2010-11-01
I also note that you've got the Master Boot Record (MBR) partition table type on /dev/sda, but GUID Partition Table (GPT) on /dev/sdb and /dev/sdc. There are a couple of issues with this:


[list]
[*]Grub Legacy, which you're using, doesn't support GPT except in patched versions. I don't know offhand what versions of Ubuntu include the necessary patches, but if you're using an old version, or installed an old version via some third-party source, it could be you've got a version of GRUB Legacy without GPT support. In that case, you'll need to switch to a version of GRUB Legacy with GPT support in order to boot anything off /dev/sdb or /dev/sdc. (Alternatively, you could convert /dev/sdb and /dev/sdc to MBR, but it's probably better to get a GPT-aware boot loader.)
[*]GRUB 2 includes GPT support, but you may need to add the line 'GRUB_PRELOAD_MODULES="part_msdos"' to /etc/default/grub and then run 'sudo update-grub' to get it to play nice with both MBR and GPT disks.
[*]GRUB 2 works best with a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) on GPT disks. I'm not sure if this is necessary in your case, though, since your main boot disk is an MBR partition. It won't hurt to add such a partition to your /dev/sdb and/or /dev/sdc disks, though, at least assuming you've got enough free space on those disks.
[/list]

---

### Post by bacardiandwatermelon on 2010-11-01
It is definately a grub prompt and not related to this eh?

[http://ubuntuforums.org/showthread.php?t=1601810]("http://ubuntuforums.org/showthread.php?t=1601810")

---

