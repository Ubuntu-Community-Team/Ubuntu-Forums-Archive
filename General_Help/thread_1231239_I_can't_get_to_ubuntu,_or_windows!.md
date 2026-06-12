---
title: "I can't get to ubuntu, or windows!"
date: 2009-08-04
forum: General Help
---

### Post by Kaninepete on 2009-08-04
Yesterday, I was re-arranging files in ubuntu, and must have deleted something important to windows by mistake, because the next time I tried to boot windows, it couldn't. It asked to do a system recovery, and acting in fear, I chose yes. I think that the recovery program removed or replaced the GRUB bootloader in favor of whatever windows uses. 
I have a thumb drive with a live version of Gparted, and I used it to set the linux partition (thank god, it was still there) to be flagged as "boot" obviously, to no avail.
I've recently had to reinstall linux for other reasons, and I'm not eager to do it again if I don't have to.
     I'm typing this on a borrowed laptop that has a CD burner. looked up how to create a live CD for GRUB, and it seems too complicated for me. I still have the Live CD that I installed ubuntu from. 
Is re-installing ubuntu the easiest way to fix this?
Any suggestions, please.

Kaninepete

---

### Post by chriskin on 2009-08-04
reinstalling grub is not difficult , you might be following a strange tutorial
check this one instead

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

it is like 3 commands :popcorn:

---

### Post by Kaninepete on 2009-08-04
I did everything on that tutorial, and it seemed to be working fine,
but when I rebooted, nothing changed.
I goes straight to a black screen with white letters saying "we apologize, but windows did not start up successfully"
after the countdown clock reaches zero, it tries again, but I never see the GRUB screen.
     Might I have installed grub wrong? I got the 
"
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda" as conformation,
but right before that, it said it had a problem.
'could not find /grub/.map, or something'
    Any ideas of how I could save either ubuntu or windows?

---

### Post by merlinus on 2009-08-04
Post results of

```
sudo fdisk -l
```

---

### Post by Kaninepete on 2009-08-04
ubuntu@ubuntu:-$ sudo fdisk -l

Disk /dev/sda: 80.0GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120  * 512 = 7741440 bytes
Disk identifier: Ox 1549f232

     Device Boot     Start      End      Blocks   Id  System
/dev/sda1              1       832    6289888+    c W95 FAT32 (LBA)
/dev/sda2   *         833     6254   40990320  7  HPFS/NTFS
/dev/sda3             6255   10337   3086748   5  Extended
/dev/sda5   *        6255   10265  30323128+ 83  Linux
/dev/sda6           10266   10337  544288+    82  Linux swap/Solaris

Disk /dev/sdb: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2816 * 512 = 1032192 bytes
Disk identifier: 0x0000000

     Device boot         Start         End       BLocks     Id   System
/dev/sdb1                      1          984       991747    6    FATT16

---

### Post by merlinus on 2009-08-04
Mount ubuntu by clicing on computer in places, and post results of

```
cat /media/disk/boot/grub/menu.lst
```First navigate to /media to make sure it is mounted at disk.

---

### Post by Kaninepete on 2009-08-04
I don't know what it means to "navigate to / media" nor to "make sure that it is mounted at disk" 
but when I typed what you gave me, it returned

"no such file or directory"

---

### Post by merlinus on 2009-08-04
Use nautilus -- look in places/computer/filesystem/media.

---

### Post by Kaninepete on 2009-08-04
I see the folders disk, JUMP DRIVE, PRESARIO, and PRESARIO_RP.

---

### Post by Kaninepete on 2009-08-04
ubuntu@ubuntu:~$ cat /media/disk/boot/grub/menu.lst
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
# kopt=root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd490384-16f6-4610-9576-346c4ffb53a7

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        dd490384-16f6-4610-9576-346c4ffb53a7
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        dd490384-16f6-4610-9576-346c4ffb53a7
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        dd490384-16f6-4610-9576-346c4ffb53a7
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        dd490384-16f6-4610-9576-346c4ffb53a7
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        dd490384-16f6-4610-9576-346c4ffb53a7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        dd490384-16f6-4610-9576-346c4ffb53a7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        dd490384-16f6-4610-9576-346c4ffb53a7
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by merlinus on 2009-08-05
Delete this from menu.lst:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

You can edit it this way:

```
gksudo gedit /media/disk/boot/grub/menu.lst
```

Then:

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

and restart.

---

### Post by Kaninepete on 2009-08-05
ubuntu@ubuntu:~$ gksudo gedit /media/disk/boot/grub/menu.lst
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)

It also opened a window titled "*menu,1st (/media/disk/boot/grub) - gedit
Is any of this a problem? and if not, do I type the code you gave me in the new window, or in the terminal?

---

### Post by merlinus on 2009-08-05
l is a lowercase L, not a 1 -- menu.lst

The commands are to be typed in a terminal.  Why don't you try them first.  Editing menu.lst can wait.

---

### Post by Kaninepete on 2009-08-05
I tried that twice, and got no response, even after rebooting. 
Thank you all for your help so far but,
with the live CD, I was able to backup all of the information that I would need to completely reinstall linux, and be a very happy camper. If you can give a reason that this will not work, or provide a simpler, or easier solution, I will give it another shot.

---

### Post by merlinus on 2009-08-05
Since you were able to back up your data, then a fresh install seems easiest.  You may wish to consider creating a separate /home partition as well.  This is where applications settings, configurations, email, bookmarks and such live, and you can choose not to format that partition when reinstalling, or installing a newer version.

---

### Post by Kaninepete on 2009-08-07
I have successfully installed ubuntu again, in addition to windows, and the original ubuntu. 
Will I have to install all my programs on the new one and delete the old, or is there an easy way to continue using the old one, and delete the new? I can get to the old one with grub, but is not set to default, the way I would like it to be, and if I deleted the new version I don't think grub would continue working at all.
*just to clairify, I installed the exact same version of ubuntu twice, not a newer version.

---

### Post by merlinus on 2009-08-07
Did you reinstall to a new partition, or to the existing ubuntu one?

In any event, post results of

```
sudo fdisk -l
sudo blkid
cat /boot/grub/menu.lst
```

---

### Post by Kaninepete on 2009-08-07
I shrank the old ubuntu partition as far I could, and used "largest continuous free space" for installing the new one.



To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

parker@parker-desktop:~$ sudo fdisk -l
[sudo] password for parker: 
Sorry, try again.
[sudo] password for parker: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *         833        6254    40990320    7  HPFS/NTFS
/dev/sda3            6255       10337    30867480    5  Extended
/dev/sda5   *        6255        8483    16851208+  83  Linux
/dev/sda6           10266       10337      544288+  82  Linux swap / Solaris
/dev/sda7           10194       10265      544288+  82  Linux swap / Solaris
/dev/sda8            8484       10121    12383248+  83  Linux
/dev/sda9           10122       10193      544288+  82  Linux swap / Solaris

Partition table entries are not in disk order
parker@parker-desktop:~$ sudo blkid
/dev/sda1: LABEL="PRESARIO_RP" UUID="429B-938F" TYPE="vfat" 
/dev/sda2: UUID="29D562D17E37DA48" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sda5: UUID="dd490384-16f6-4610-9576-346c4ffb53a7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="2334b43f-1729-4b60-955a-7ed1f64df62b" 
/dev/sda7: TYPE="swap" UUID="61f83fcc-645f-47ad-904b-6c5ad61ce0e4" 
/dev/sda8: UUID="de791369-4171-44cd-858d-6db4e1b325de" TYPE="ext3" 
/dev/sda9: TYPE="swap" UUID="6b82136a-5e84-4fca-8dae-be10989885db" 
parker@parker-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=de791369-4171-44cd-858d-6db4e1b325de ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de791369-4171-44cd-858d-6db4e1b325de

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
uuid        de791369-4171-44cd-858d-6db4e1b325de
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=de791369-4171-44cd-858d-6db4e1b325de ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        de791369-4171-44cd-858d-6db4e1b325de
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=de791369-4171-44cd-858d-6db4e1b325de ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        de791369-4171-44cd-858d-6db4e1b325de
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro single 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro single 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=dd490384-16f6-4610-9576-346c4ffb53a7 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot

---

### Post by merlinus on 2009-08-07
The new linux partition is sda8, and the old one is sda5.  But note that you now have three swap partitions.

So what are you wanting to do?  Antyhing will require some extensive shuffling with gparted.

Can you now access windows?

---

### Post by Kaninepete on 2009-08-07
I can't use windows at all.
the only reason I still have it is so ubuntu can get the internet settings from it, because I don't know any of them. If I can delete the windows partitions, and still get the internet, I could use the extra space.
as for the three swap things, I was worried about deleting any of them because I don't know which ones I need. they don't take up much space, so I'm okay with keeping them.

Most preferably, I'd like to go back to my old ubuntu setup, because it has all of my programs installed. if that would be loads of work, staying with the new one wouldn't be that bad.
as it is now, I don't have enough space to do the "update manager" with either of them, so something has to go.

---

### Post by merlinus on 2009-08-07
If you have your data backed up, then I would suggest a fresh install, completely replacing everything but windows. 

You can use gparted on the live cd to delete all the linux partitions, and then whilst installing select either side-by-side with windows, or use largest free space, for ubuntu.

---

