---
title: "Accidently install Ubuntu: Are my data in Window still available?"
date: 2010-12-20
forum: General Help
---

### Post by Newbie10 on 2010-12-20
Hi guys,

I accidentally install Ubuntu without any knowledge of Linux. I'm not sure too how I created the partition :-( It seems that I didn't create any partition..  Currently,  I cannot access any files that I used to access in my XP such as any pictures, music, etc.

Please anyone suggest me what should I do to get my data back and back to XP?. I Please find my boot infor script below. Thank you so much in advance

Very newbie :-(


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   150,288,074   150,288,012  83 Linux
/dev/sda2         150,288,075   156,296,384     6,008,310   5 Extended
/dev/sda5         150,288,138   156,296,384     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        dc2901d2-438b-4ad2-9150-ca723e5ae7e1   ext3                                     
/dev/sda5        3b11843e-23bd-49ba-9dbc-7c834bda1328   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro)
/dev/scd0        /media/cdrom0            iso9660    (ro,noexec,nosuid,nodev,user=ken)


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)


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
# kopt=root=UUID=dc2901d2-438b-4ad2-9150-ca723e5ae7e1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## ## End Default Options ##

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=dc2901d2-438b-4ad2-9150-ca723e5ae7e1 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=dc2901d2-438b-4ad2-9150-ca723e5ae7e1 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dc2901d2-438b-4ad2-9150-ca723e5ae7e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3b11843e-23bd-49ba-9dbc-7c834bda1328 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda1: Location of files loaded by Grub: ===================


  48.5GB: boot/grub/menu.lst
  48.4GB: boot/grub/stage2
  48.4GB: boot/initrd.img-2.6.20-15-generic
  48.4GB: boot/initrd.img-2.6.20-15-generic.bak
  48.4GB: boot/vmlinuz-2.6.20-15-generic
  48.4GB: initrd.img
  48.4GB: vmlinuz

---

### Post by bluefrog on 2010-12-20
apparently you installed it over windows. Bye to your windows data.

---

### Post by Rubi1200 on 2010-12-20
Unfortunately, I think bluefrog is probably right :-(

However, if you stop all read/write activity on the drive now there is a slim chance you might be able to recover some of your files using Testdisk.

Use a LiveCD to boot the computer and at the live desktop install testdisk:

```
sudo apt-get install testdisk
```

It is a CLI application, so you need to run it in the terminal:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Good luck!

---

### Post by Newbie10 on 2010-12-20
sudo apt-get install testdisk

I try the above code and the it said that Couldn't find package testdisk..Does it imply something? Thanks

---

### Post by amsterdamharu on 2010-12-20
If you run from a live cd you cannot reboot and I think running testdisk in a terminal will ask you to reboot.

Boot from live cd and open a terminal (press alt + F2 and type xterm).
Copy and paste the following command in the terminal:
```
sudo apt-get install testdisk
```If that gives you an error please copy and paste everything in the terminal and post it here.

If not and it's finished you can log out [COLOR=Red]do not reboot[/COLOR].
Press control + alt + F1 and type the following commands (you have to get a pen and paper and write this down).

```
sudo service gdm stop
sudo testdisk
```Your windows install is probably gone but if you're able to recover the old partition table you might have a shot at recovering your pictures.

---

### Post by Rubi1200 on 2010-12-20
Are you using the CD for 7.04?

Why, it is no longer supported?

Testdisk is only available on later versions I believe.

You need to download and make a CD with the latest version:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by katykat on 2010-12-20
It implies that it cannot find the file.

Go to System/Administration/Synaptic Package Manager

Then Settings/Repositories and mke sure UNIVERSE is checked. 
Then RELOAD.

You can then put testdisk in the search bar, or exit and try again.

---

### Post by ajgreeny on 2010-12-20
You do seem to have installed Ubuntu over windows, and as Rubi1200 is suggesting, it appears to be an older version of Ubuntu no longer supported, hence your inability to install anything.

I do not understand how you could possibly install an OS and not know that you are doing so, however, if you can get testdisk on a live CD by using someone else's computer to download and burn it you may be lucky, and get back at least some of your files.

I think it very unlikely that you will get everything back, and hope you have a backup available.

---

