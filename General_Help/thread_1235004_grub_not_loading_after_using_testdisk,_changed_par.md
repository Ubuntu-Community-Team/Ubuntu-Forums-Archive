---
title: "grub not loading after using testdisk, changed partition?"
date: 2009-08-08
forum: General Help
---

### Post by rustyrussell on 2009-08-08
Hi,
I was trying to recover a hard drive using the testdisk utility, it didn't detect the hd i was trying to fix so i accidentally accessed my main hd. I believe i rewrote the partition table (though I think it should have been the same as before anyway) and now i get grub error 22 on startup. There were 3 partitions on the drive, one with ubuntu, one with windows and one for files.
How should i proceed?
I would be very apricative of any advice.
Sincerely,
Russell

---

### Post by merlinus on 2009-08-08
Post results of

```
sudo fdisk -l
```

---

### Post by louieb on 2009-08-08
When GRUB puts code in the MBR it hard codes where to look for stage2 (main grub program).  

It does sound like something changed. testdisk is probably your best bet to get things back the way they were.  

1st thing I would do is follow the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  It does not write anything to the drive so should be safe to run.  Put the results.txt file in your next post.  Lots of good boot information is gathered by this script.

---

### Post by rustyrussell on 2009-08-08
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf90bf90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce6bce6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            4345        4865     4184932+   f  W95 Ext'd (LBA)
/dev/sdb5            4345        4865     4184901    7  HPFS/NTFS



the second hard disk is the one which it should be booting from.
thanks

---

### Post by rustyrussell on 2009-08-08
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf90bf90

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   398,267,414   398,267,352   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xce6bce6b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1          69,786,360    78,156,224     8,369,865   f W95 Ext d (LBA)
/dev/sdb5          69,786,423    78,156,224     8,369,802   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="E8F0F82CF0F8029C" TYPE="ntfs" 
/dev/sdb5: UUID="B8844181844142DC" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

---

### Post by merlinus on 2009-08-08
From results of fdisk, you no longer have any linux partiitions.  Looks like it was sdb6, but that no longer seems to exist.

What does gparted show for sdb?

---

### Post by rustyrussell on 2009-08-08
this:
Linux should have been on one of the 4gb partitions.

---

### Post by louieb on 2009-08-08
Looks like Ubuntu is now in unallocated space. At this point you have nothing to loose by running testdisk again and see if it can restore the partition table to what it was before.  
  
May want to unplug the drive with windows on before you begin.

---

### Post by rustyrussell on 2009-08-09
ok, so i ran testdisk again (using a ubuntu recovery remix cd since the normal ubuntu live wouldnt let me install it) and i have put the partitions back in place. I still get an error, which is now error 17, but thats progress. this is my fdisk result now:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf90bf90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce6bce6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3735    30001356    7  HPFS/NTFS
/dev/sdb2            3736        4865     9076693+   f  W95 Ext'd (LBA)
/dev/sdb5            3736        4311     4626657   83  Linux
/dev/sdb6            4312        4344      265041   82  Linux swap / Solaris
/dev/sdb7            4345        4865     4184901    7  HPFS/NTFS

I think I now need to redirect GRUB to look in the right place. would it be a good idea to use super grub? 

thanks.

edit: see attached file for more info from the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/")

---

### Post by merlinus on 2009-08-09
Try this:

```
sudo grub 
root (hd1,4)
setup (hd1)
quit
```and restart.

This will set up grub in the mbr of sdb.  If you want it in the mbr of sda, then change setup to (hd0,0).

---

### Post by rustyrussell on 2009-08-09
that did the trick, thank you for all you help.

edit: just checked and its not finding the windows, its looking for it on hd0,0. should i change this to hd1,0?

---

### Post by rustyrussell on 2009-08-09
i'm still not getting windows to start. The possible partitions for hd0 come up as:
partition num: 0, filesystem type unknown, partition type 0x7
partition num: 4, filesystem type is ext2fs, partition type 0x83
partition num: 5, filesystem type unknown, partition type 0x82
partition num: 6, filesystem type unknown, partition type 0x7

fdisk can tell what type 0,6 is, so why cant grub?
sorry to still be taking up your time.

---

### Post by merlinus on 2009-08-09
Is windows on sdb1 or sda1?  Also, what is the boot order of hdds in bios?

And post results of

```
cat /boot/grub/menu.lst
```

---

### Post by louieb on 2009-08-10
> **rustyrussell said:**
> ... not finding the windows, its looking for it on hd0,0. should i change this to hd1,0?
Great that you got Ubuntu going again.
Grub depended on boot order to tell which drive is which. So if boot order changes so does grubs decision of which drive is which. 
Your latest results.txt file shows you have boot-able installs of XP in both sda1 and sdb1. 

Your just going to have to experiment to see what works. Won't hurt anything - it will either boot XP or it won't. 

May have to use the map command to boot XP on the 2nd drive.  (Makes the system think its booting from the 1st drive) 
 

```
title Win XP 
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1
```

---

### Post by rustyrussell on 2009-08-10
> **louieb said:**
> 
 

```
title Win XP 
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1
```


this worked, to an extent, windows starts loading but crashes before it finishes. Am i right in thinking that nothing more can be done from grub about this problem now?


here is the result of[FONT=monospace] [/FONT]cat /boot/grub/menu.lst anyway
```
rst@rst-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=ce7d540e-f7d5-438a-a2a5-3f9571e1935d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ce7d540e-f7d5-438a-a2a5-3f9571e1935d

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
uuid        ce7d540e-f7d5-438a-a2a5-3f9571e1935d
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=ce7d540e-f7d5-438a-a2a5-3f9571e1935d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        ce7d540e-f7d5-438a-a2a5-3f9571e1935d
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=ce7d540e-f7d5-438a-a2a5-3f9571e1935d ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        ce7d540e-f7d5-438a-a2a5-3f9571e1935d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ce7d540e-f7d5-438a-a2a5-3f9571e1935d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        ce7d540e-f7d5-438a-a2a5-3f9571e1935d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ce7d540e-f7d5-438a-a2a5-3f9571e1935d ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ce7d540e-f7d5-438a-a2a5-3f9571e1935d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ce7d540e-f7d5-438a-a2a5-3f9571e1935d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ce7d540e-f7d5-438a-a2a5-3f9571e1935d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ce7d540e-f7d5-438a-a2a5-3f9571e1935d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ce7d540e-f7d5-438a-a2a5-3f9571e1935d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

rst@rst-desktop:~$ 

```

---

### Post by merlinus on 2009-08-10
At the risk of going over old ground --

What hdd and partition is your xp install -- looks like it is sda1.

What is the boot order of your hdds in bios?  And does /boot/grub/device.map reflect this correctly?

---

### Post by rustyrussell on 2009-08-11
the windows on sdb is the one we are trying to get working, the copy on sda is one left over from an older system.
My bios is set to boot from hdb first and /boot/grub/device.map returns only
(hd0)    /dev/sda
which i guess is wrong, but i'm too new to this to change it. edit: thats a nice FAQ you have there [louieb]("http://ubuntuforums.org/member.php?u=120176") :)
thank you for your patience.

---

### Post by louieb on 2009-08-11
Just saw something - looking at your boot.ini wonder why the partiton # is 2 on sdb1 - that may be why XP crashed. Never messed with that file so don't know. 
```

================================ sda1/boot.ini: 

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition([COLOR=Red]1[/COLOR])\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

================================ sdb1/boot.ini: 

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition([COLOR=Red]2[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

```What type of drives are these SATA (narrow cable to motherboard) or PATA (wide flat ribbon cable). or one of  each? 
Really just at a loss now just throwing stuff against the wall and see what sticks (works). Might try unplugging sda temporary   and making sdb turn in to sda. and see what works. 

If there PATA drives you need to check and maybe change jumper settings. SATA drives don't use jupers..

Your window entry in this case should look like: 
```
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```which is the way you originally had it.

---

### Post by merlinus on 2009-08-11
```
gksudo gedit /boot/grub/device.map
```

and change to:

(hd0) /dev/sdb
(hd1) /dev/sda

Then in menu.lst:

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by rustyrussell on 2009-08-11
I think i have found what may be the problem, sda7 has window in it and is part of an extended partiton; see attached pic. It was never originaly like that i think. I can i fix this with gparted? I dont trust testdisk much!
also, my cables are PATA and i've disconnected the other hard drive to avoid confusion. that one doesnt seem to be causing the problem.

---

### Post by rustyrussell on 2009-08-11
and.... fixed! I used testdisk again, and set sda7 to be a primary partition instead of a logical part of the extended.
I wont trust testdisk to guess again.
I'd like to thank you both again, i've learned a lot.

---

### Post by merlinus on 2009-08-11
Excellent news!  Have fun...

---

### Post by louieb on 2009-08-11
Great,

---

