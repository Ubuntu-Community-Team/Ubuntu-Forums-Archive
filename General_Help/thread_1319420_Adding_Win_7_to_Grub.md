---
title: "Adding Win 7 to Grub ??"
date: 2009-11-08
forum: General Help
---

### Post by Tom_T on 2009-11-08
Hi

How would I add Windows 7 to my grub menu ?

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2895    23254056    c  W95 FAT32 (LBA)
/dev/sda2            6213       12161    47785342+   5  Extended
/dev/sda3            2896        6212    26643802+   7  HPFS/NTFS
/dev/sda5            6213        9459    26081464+  83  Linux
/dev/sda6            9460        9605     1172713+  82  Linux swap / Solaris
/dev/sda7            9606       12161    20531038+   7  HPFS/NTFS

```

/dev/sda3 is Windows 7. (XP is /dev/sda1)

Any ideas ??

Thanks

---

### Post by ranch hand on 2009-11-08
The first thing I would try is running;
```

sudo update-grub

```
this does the trick 90% of the time.

---

### Post by abdusamed on 2009-11-08
sorry..but im a bit scared.. will this get rid of the message which appears on every boot?? hdd 0 no wublbr not found? :KS

---

### Post by ranch hand on 2009-11-08
I hate to say it but I have no idea what you are talking about.

On the other hand I don't think it can do any harm.

Did you do an install with Wubi?

---

### Post by Tom_T on 2009-11-08
> **ranch hand said:**
> The first thing I would try is running;
```

sudo update-grub

```
this does the trick 90% of the time.

Thanks tried that.. didn't work !!

Any other ideas ??
Thanks :)

---

### Post by ranch hand on 2009-11-08
Well, I do not have any MS on my box so this is a little tough for me.

You have, I take it, a working XP menuentry.  I would add that to my menu and edit it to fit your other partition.

I always thought that MS did not do well installed on an extended partition.  Obviously I could be wrong on this but have you checked that?

I would be glad to help with editing your menu but I have no idea what grub you are using and they are different.

---

### Post by Tom_T on 2009-11-08
The XP install works fine from Grub. Win 7 is the issue.

Does this help ??

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /boot/bcd 
                       /BOOT/bcd /Boot/bcd /boot/BCD /BOOT/BCD /Boot/BCD 
                       /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 122028994 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa5a6a5a6

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    46,508,174    46,508,112   c W95 FAT32 (LBA)
/dev/sda2          99,795,780   195,366,464    95,570,685   5 Extended
/dev/sda5          99,795,906   151,958,834    52,162,929  83 Linux
/dev/sda6         151,958,898   154,304,324     2,345,427  82 Linux swap / Solaris
/dev/sda7         154,304,388   195,366,464    41,062,077   7 HPFS/NTFS
/dev/sda3    *     46,508,175    99,795,779    53,287,605   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="ACER" UUID="320D-180E" TYPE="vfat" 
/dev/sda3: UUID="560756760DC5AC00" LABEL="7" TYPE="ntfs" 
/dev/sda5: UUID="495dec8e-1c37-49cc-8930-c09fc1a320eb" TYPE="ext3" 
/dev/sda6: UUID="d9c86fd5-05ef-4215-9598-1be5125a8572" TYPE="swap" 
/dev/sda7: UUID="CCF8CC43F8CC2E10" LABEL="New Volume" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/default/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=default)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


================================ sda1/BOOT.INI: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=495dec8e-1c37-49cc-8930-c09fc1a320eb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=495dec8e-1c37-49cc-8930-c09fc1a320eb

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		495dec8e-1c37-49cc-8930-c09fc1a320eb
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=495dec8e-1c37-49cc-8930-c09fc1a320eb ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		495dec8e-1c37-49cc-8930-c09fc1a320eb
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=495dec8e-1c37-49cc-8930-c09fc1a320eb ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		495dec8e-1c37-49cc-8930-c09fc1a320eb
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=495dec8e-1c37-49cc-8930-c09fc1a320eb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		495dec8e-1c37-49cc-8930-c09fc1a320eb
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=495dec8e-1c37-49cc-8930-c09fc1a320eb ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		495dec8e-1c37-49cc-8930-c09fc1a320eb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=495dec8e-1c37-49cc-8930-c09fc1a320eb /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d9c86fd5-05ef-4215-9598-1be5125a8572 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  51.0GB: boot/grub/menu.lst
  51.0GB: boot/grub/stage2
  51.0GB: boot/initrd.img-2.6.28-16-generic
  51.0GB: boot/initrd.img-2.6.31-14-generic
  51.0GB: boot/vmlinuz-2.6.28-16-generic
  51.0GB: boot/vmlinuz-2.6.31-14-generic
  51.0GB: initrd.img
  51.0GB: initrd.img.old
  51.0GB: vmlinuz
  51.0GB: vmlinuz.old
```

Thanks

---

### Post by ranch hand on 2009-11-08
Yes it does.  I still think that there is a problem with MS on a logical partition.

It will not hurt to add this entry to your /boot/grub/menu.lst;
```

title        Microsoft Windows 7
rootnoverify    (hd0,6)
savedefault
makeactive
chainloader    +1

```
That should point you at the partition where Win 7 is and chainload to its bootloader if it works where it is.

---

### Post by oldfred on 2009-11-08
Win7 combines its boot with any other windows it finds on your drive so you only boot into one windows and choose from that which windows to boot. Once win7 has combined the boot it will not boot on its own from grub. Users who have deleted an old windows find they cannot boot win7 without major repairs,since they have deleted parts of the win7 boot loader.

Herman is the only one who has gotten any windows - winXP to boot from an extended partition, I do not know if the same can even be done for win7 - see herman's posts:
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)

---

### Post by ranch hand on 2009-11-08
> **oldfred said:**
> Win7 combines its boot with any other windows it finds on your drive so you only boot into one windows and choose from that which windows to boot. Once win7 has combined the boot it will not boot on its own from grub. Users who have deleted an old windows find they cannot boot win7 without major repairs,since they have deleted parts of the win7 boot loader.

Herman is the only one who has gotten any windows - winXP to boot from an extended partition, I do not know if the same can even be done for win7 - see herman's posts:
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)
Thanks for that.  I should have known that herman had something on this.

I am really in the dark with MS.  Don't use those "off brand" OS'.

---

### Post by Tom_T on 2009-11-09
Thanks for the replies.

Adding the entry to menu.lst didn't work.. got a 'bootloader' type of error.

However.. using my old XP Grub menu option, now boots me to the new MS boot menu offering Windows 7 or my old XP.

So it's 2 clicks to get to Windows.. or 1 to Ubuntu. :)

Yeh !! Ubuntu !!

---

### Post by ranch hand on 2009-11-09
Mark the the thread solved (top of page under Thread Tools) I am sure you are not the only one with this problem.

---

### Post by oldfred on 2009-11-09
Glad that your got it to work. I would keep your XP partition as long as you want Win7. The Win7 may not be repairable  since it is in an extended partition. And then plan on reinstalling win7 if you ever want to delete the XP partition.

---

### Post by wayneox on 2009-11-13
i understand this is solved but a bit of info...

on my old tower i installed xp onto a extended partition... [D: drive]...
i created a partition, in the install, and then instead of creating my documents partition i clicked enter n off winxp went installing itself... works fine.. i dual boot with ubuntu and no problems however all the autoexec etc files r in c: -> the primary partition. 

and i assume this is where the ntldr list goes to also... my ntldr is in c: also.. when i installed ubuntu at first it added itself to my ntldr n not install grub... - not sure how... but it worked, when i installed onto a seperate 20gb hd for ubuntu, i had to edit the ntldr list in xp - using the startup options of system... 

also,,, i sort of dual boot my vista laptop,,, i connect a usb hd to it when i wanna ubuntu... its my mrs laptop mainly... - shes still not convinced with the whole ubuntu thing... mostly because non of our cams work on ubuntu. so she cant skype in it... but when i load the grub off the usb h.d it detects both my vista install and my vista backup partition, and i can boot into either... - almost formatted oneday when i chose the wrong one :P 
however that was the oem partition install from acer...

- im sure it is possible to load directly to win7 just not sure HOW :P
maybe a second ntldr on another hd etc... if u want that, that is :P can always dd the win7 partition, to another hds primary partition then fixmbr on that drive... ???

---

