---
title: "Grub Err 15: File Not Found - No Boot - 8.04"
date: 2009-08-19
forum: General Help
---

### Post by wavevaw on 2009-08-19
I suspect file system corruption.  Should the boot and proc directories be empty??

Ubuntu 8.04 is no longer booting, and Grub is returning Error 15: File not Found

I have one day's experience with Linux, so thanks for your patience.

---

### Post by louieb on 2009-08-19
/boot should not be empty. You may have a corrupt file system. How did you install (WUBI or in its own partition)?

More info would be helpful. Please [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  and put the results.txt file in your next post. (its long please use code  tags).

---

### Post by wavevaw on 2009-08-20
Thank you, louieb

Method of installation is unknown.  (Helping a friend, and can I just say that I am really digging the logic of Linux.)
There is no Windows installation on the system, so I assume no WUBI.
The owner tells me that her son may have made unknown changes to software only.

Boot Info Script Results:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 20074655 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ee484

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,000,924    20,000,862  83 Linux
/dev/sda2    *     20,000,925    20,097,314        96,390  83 Linux
/dev/sda4          20,097,315   488,392,064   468,294,750   5 Extended
/dev/sda5          28,097,748    30,089,744     1,991,997  83 Linux
/dev/sda6          20,097,441    28,097,684     8,000,244  82 Linux swap / Solaris
/dev/sda7          30,089,808    38,090,114     8,000,307  83 Linux
/dev/sda8          38,090,178   238,083,299   199,993,122  83 Linux
/dev/sda9         238,083,363   488,392,064   250,308,702  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8053 MB, 8053063680 bytes
175 heads, 32 sectors/track, 2808 cylinders, total 15728640 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    15,663,103    15,663,072   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="58a5b585-d591-4906-8656-4e589c34a560" TYPE="xfs" 
/dev/sda2: UUID="0510409e-082d-4679-a83e-283950951954" TYPE="ext2" 
/dev/sda5: UUID="1df4f144-bda0-4a2e-a514-17ca50d135fa" TYPE="xfs" 
/dev/sda6: TYPE="swap" UUID="49226440-0809-455e-b44f-343dbd551f42" 
/dev/sda7: UUID="e5eb1d8d-5c3b-4507-a49d-9bf8e5f2e0dd" TYPE="xfs" 
/dev/sda8: UUID="e88692a7-52d4-4f8f-a34c-7766790329f0" TYPE="xfs" 
/dev/sda9: UUID="cb399c72-1bf9-4e8d-aafb-1fd13d15839f" TYPE="xfs" 
/dev/sdb1: LABEL="THEKNAPSACK" UUID="7AC3-ED08" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/THEKNAPSACK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=58a5b585-d591-4906-8656-4e589c34a560 /               xfs     relatime        0       1
# /dev/sdb9
UUID=cb399c72-1bf9-4e8d-aafb-1fd13d15839f /archive        xfs     relatime        0       2
# /dev/sdb2
UUID=0510409e-082d-4679-a83e-283950951954 /boot           ext2    relatime        0       2
# /dev/sdb8
UUID=e88692a7-52d4-4f8f-a34c-7766790329f0 /home           xfs     relatime        0       2
# /dev/sdb5
UUID=1df4f144-bda0-4a2e-a514-17ca50d135fa /tmp            xfs     relatime        0       2
# /dev/sdb7
UUID=e5eb1d8d-5c3b-4507-a49d-9bf8e5f2e0dd /var            xfs     relatime        0       2
# /dev/sdb6
UUID=49226440-0809-455e-b44f-343dbd551f42 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

============================= sda2/grub/menu.lst: =============================

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
timeout        3

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
# kopt=root=UUID=58a5b585-d591-4906-8656-4e589c34a560 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root        (hd0,1)
kernel        /vmlinuz-2.6.24-19-generic root=UUID=58a5b585-d591-4906-8656-4e589c34a560 ro quiet splash
initrd        /initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /vmlinuz-2.6.24-19-generic root=UUID=58a5b585-d591-4906-8656-4e589c34a560 ro single
initrd        /initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,1)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda2: Location of files loaded by Grub: ===================


  10.2GB: grub/menu.lst
  10.2GB: grub/stage2
  10.2GB: initrd.img-2.6.24-21-generic
  10.2GB: initrd.img-2.6.24-22-generic
  10.2GB: initrd.img-2.6.24-22-generic.bak
  10.2GB: vmlinuz-2.6.24-19-generic
  10.2GB: vmlinuz-2.6.24-21-generic
  10.2GB: vmlinuz-2.6.24-22-generic

```

Please Note sdb is USB Flash Drive

---

### Post by louieb on 2009-08-20
When are you getting the Grub error 15? Before or after the Grub menu is displayed? my guess is after.

Looks like /boot is in its own partition (sda2) and its missing  [COLOR=Red]initrd.img-2.6.24-19-generic.[/COLOR]

things of interest from results.txt
```
title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /vmlinuz-2.6.24-19-generic root=UUID=58a5b585-d591-4906-8656-4e589c34a560 ro quiet splash
[COLOR=Red]initrd        /initrd.img-2.6.24-19-generic[/COLOR]
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /vmlinuz-2.6.24-19-generic root=UUID=58a5b585-d591-4906-8656-4e589c34a560 ro single
[COLOR=Red]initrd        /initrd.img-2.6.24-19-generic
[/COLOR] 
=================== sda2: Location of files loaded by Grub: 

  10.2GB: grub/menu.lst
  10.2GB: grub/stage2
  10.2GB: initrd.img-2.6.24-21-generic
  10.2GB: initrd.img-2.6.24-22-generic
  10.2GB: initrd.img-2.6.24-22-generic.bak
  10.2GB: vmlinuz-2.6.24-19-generic
  10.2GB: vmlinuz-2.6.24-21-generic
  10.2GB: vmlinuz-2.6.24-22-generic
```Anyway for a temporary fix highlight the 1st Ubuntu entry and press e to edit then edit the kernel and initrd lines so that the version number is the same and points to files that are there [B] initrd.img-2.6.24-22-generic  and initrd.img-2.6.24-22-generic

[/B]If it boots the you can edit /boot/grub/menu.lst to make permanent. 

press alt+f2 then enter ```
gksudo gedit /boot/grub/menu.lst
```

Wonder how it got that way?

---

### Post by wavevaw on 2009-08-20
Worked!  Thank you.

You are right, the Grub Error 15: File Not Found was occurring after Grub displayed the boot options menu.
I am sorry I don't have more background info on how this happened.

Two questions - 

- Do the version of the kernel and the initrd.img have to match?

Regarding the file system:
I believe I made an error in saying that /boot was empty.
While booted to LiveCD, sda2/boot appeared empty.  
- Am I correct that this directory is actually mapped to the boot partition sda1 when Ubuntu is booted, but *should* appear empty from LiveCD?

As you noted, there were files on the boot partition, but not the initrd.img-2.6.24-19-generic file that Grub was looking for.

Thanks again for the help.

---

### Post by louieb on 2009-08-20
> **wavevaw said:**
> - Do the version of the kernel and the initrd.img have to match?
They should match - initrd is built when the kernel is installed/
> **wavevaw said:**
> 
- Am I correct that this directory is actually mapped to the boot partition sda1 when Ubuntu is booted, but *should* appear empty from LiveCD?


In this case /dev/sda2 was in Linux terms **mounted **on  /boot at startup and should be empty in sda1 when being browsed with a live CD. That PC has other partitions mounted at boot. File /etc/fstab  is where you would look to see what gets mounted where at boot. 

Glad you got it going.

---

