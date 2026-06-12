---
title: "How to replace previous Ubuntu with Ubuntu?"
date: 2009-11-05
forum: General Help
---

### Post by Pipps on 2009-11-05
**[COLOR="Red"]Update[/COLOR]: Please go straight to [this post]("http://ubuntuforums.org/showthread.php?p=8329057#post8296951").** **Thanks.**

I currently have Linux Mint (a Ubunutu derivative) installed at sda3. I would like to install Ubuntu 9.10 in its place.

**Question**
I already have GRUB customised and setup in its own independent partition, to manage my multi-boot system.

Would it be possible to install Ubuntu 9.10 from a Live USB disc, specifically to the sda 3 partition, without allowing Ubuntu to re-install its own version of Grub in the process?


**Background**
By way of additional background, I have used 'Boot Info Script 0.32' to create the following results file. I hope this helps.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 7 Gloria - Main 
                       Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda4 and looks 
                       at sector 924436402 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedf4edf4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   901,005,524   901,005,462   7 HPFS/NTFS
/dev/sda2         913,279,185   976,768,064    63,488,880   7 HPFS/NTFS
/dev/sda3         901,005,525   913,086,404    12,080,880  83 Linux
/dev/sda4         913,086,405   913,279,184       192,780  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cd17c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8589 MB, 8589934080 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777215 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="CE00E7B800E7A625" TYPE="ntfs" 
/dev/sda2: UUID="294A9CE43EA5868D" TYPE="ntfs" 
/dev/sda3: UUID="64c248b7-b0b3-4b72-8601-2734bb8f7838" TYPE="ext3" 
/dev/sda4: LABEL="GRUB" UUID="ea340f4c-def5-4a5e-9559-d20c1c3d12f7" TYPE="ext3" 
/dev/sdb1: UUID="1B75BED556178367" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rp)
/dev/sda4 on /media/GRUB type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN /NOGUIBOOT


=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color white/black white/red

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
##      altoptions=(single-user) single
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

title Windows XP Performance Edition SP3
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

title Windows Vista SP2
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

title		Linux Mint 7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=64c248b7-b0b3-4b72-8601-2734bb8f7838 /               ext3    relatime,errors=remount-ro 0       1

=================== sda3: Location of files loaded by Grub: ===================


 466.6GB: boot/grub/menu.lst
 467.0GB: boot/grub/stage2
 466.6GB: boot/initrd.img-2.6.28-11-generic
 466.2GB: boot/vmlinuz-2.6.28-11-generic
 466.6GB: initrd.img
 466.2GB: vmlinuz

=========================== sda4/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color white/black white/aqua

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
##      altoptions=(single-user) single
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

title Windows XP Performance Edition SP3
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

title Windows Vista SP2
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

title		Linux Mint 7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

=================== sda4: Location of files loaded by Grub: ===================


 467.5GB: boot/grub/menu.lst
 467.5GB: boot/grub/stage2
```

I look forward to any comments. Thank you for your time.

---

### Post by alphaniner on 2009-11-05
In 9.04, on the very last step of installation via LiveCD, there is a button labeled 'Advanced...'  Click it and you will be given an option to not install a GRUB.  I'm pretty sure it is the same in 9.10.

---

### Post by Pipps on 2009-11-05
That is brilliant! Thank you! I now have one additional question...

During the Installation preparation screens, from the Live USB, when I specify the partition in which I would like Ubuntu to be installed into, I am asked for a mount-point, too.

On the basis that I already have Grub installed in its own partition and managing things independently, what should I specify as my Ubuntu mount-point, in this instance?

---

### Post by alphaniner on 2009-11-05
If you're only using the one partition, the mount point will have to be ' / '.  The bootloader has nothing to do with it.

And I double-checked the installer, the option to not install GRUB is still there in 9.10, on Step 6.

---

### Post by Pipps on 2009-11-05
You are most kind! Thank you for your incredibly speedy help! :)

---

### Post by Pipps on 2009-11-05
Update: Problem!

I now experience a 'Grub Error 15' when I try to boot into Ubuntu from my main Grub boot menu.

Is this a UUID problem?

---

### Post by alphaniner on 2009-11-05
Good thinking.  If you reformatted the partition, it probably got a new UUID.

---

### Post by Pipps on 2009-11-05
I am currently only able to boot into Ubuntu using the Live USB disc.

How should I use the terminal in Live mode, to navigate to my fresh sda3 Ubuntu installation, and determine the new UUID for that partition?

---

### Post by Pipps on 2009-11-05
I have just performed:

```
sudo su
blkid
```

And was advised of the following:

```
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="79fce625-9f86-409c-87cc-d577e60fbf37" TYPE="ext3" 
/dev/sda1: UUID="CE00E7B800E7A625" TYPE="ntfs" 
/dev/sda3: UUID="fa1271c3-f4f7-4fb8-848a-56d73f2b82cc" TYPE="ext3" 
/dev/sda4: LABEL="GRUB" UUID="ea340f4c-def5-4a5e-9559-d20c1c3d12f7" TYPE="ext3" 
/dev/sdb1: UUID="69BB752362738AB1" TYPE="ntfs" 
/dev/sdd1: LABEL="USB4GB" UUID="64ED-E898" TYPE="vfat" 
```

Sweet! :)

NB: Just *blkid* did not work on its own, in Live USB, until I performed the *sudo su* command first! Weird! :-?

---

### Post by Pipps on 2009-11-05
My Grub partition's *menu.lst* contains the following:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color white/black white/aqua

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
##      altoptions=(single-user) single
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

title Windows XP Performance Edition SP3
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

title		Linux Mint 7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
```

How do I update the Linux entry to allow me to boot into the freshly installed Ubuntu 9.10 at sda3?

What should I do with my newly ascertained new UUID?

---

### Post by alphaniner on 2009-11-05
It looks like your GRUB isn't using UUID after all.  I think what you need to do is check your /boot folder on the new install and update the kernel and initrd lines in menu.lst:```
## ## End Default Options ##

title Windows XP Performance Edition SP3
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

title		Linux Mint 7
root		(hd0,2)
kernel		/boot/**vmlinuz-2.6.28-11-generic** root=/dev/sda3 ro quiet splash
initrd		/boot/**initrd.img-2.6.28-11-generic**
quiet

title		memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
```

I think kernel should be **vmlinuz-2.6.31-14-generic**, and the initrd should be **initrd.img-2.6.31-14-generic**.

---

### Post by P4man on 2009-11-05
This here is wrong in your menu.lst I think:
```

# groot=(hd0,2)
```

grub root is sda4 which would be hd(0,3). 
**[COLOR="Red"]edit:[/COLOR]** there is even a spelling error in there.

 Changing that would solve the grub error 15 I think.

As for adding ubuntu.. where are ubuntu's kernels? On the sda4 boot partition or in ubuntu's partition in the /boot  folder ?

---

### Post by Pipps on 2009-11-05
> **alphaniner said:**
> It looks like your GRUB isn't using UUID after all.  I think what you need to do is check your /boot folder on the new install and update the kernel and initrd lines in menu.lst:```
## ## End Default Options ##

title Windows XP Performance Edition SP3
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

title		Linux Mint 7
root		(hd0,2)
kernel		/boot/**vmlinuz-2.6.28-11-generic** root=/dev/sda3 ro quiet splash
initrd		/boot/**initrd.img-2.6.28-11-generic**
quiet

title		memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
```

I think kernel should be **vmlinuz-2.6.31-14-generic**, and the initrd should be **initrd.img-2.6.31-14-generic**.

I have just used:

```
sudo gedit /boot/grub/menu.lst
```

to edit the Grub menu.lst as you have instructed.

Time for a reboot, and to see if that Grub Error 15 remains!

---

### Post by Pipps on 2009-11-05
Just attempted a reboot. It failed.

*'Grub Error 1...'*, this time.

---

### Post by Pipps on 2009-11-05
> **P4man said:**
> This here is wrong in your menu.lst I think:
```

# groot=(hd0,2)
```

grub root is sda4 which would be hd(0,3). 
[COLOR="Red"]**edit:**[/COLOR] there is even a spelling error in there.

 Changing that would solve the grub error 15 I think.

As for adding ubuntu.. where are ubuntu's kernels? On the sda4 boot partition or in ubuntu's partition in the /boot  folder ?
Thank you for assisting! :)

Can you help me understand what is the spelling mistake within my *menu.lst* file?

What should I do to determine where my Ubuntu kernels are located?

[COLOR="Red"]**Edit:**[/COLOR] I have just checked again, and can now can confirm that the kernels are not located in the sda4 Grub boot directory. There seem to be no files within that directory. But in my new sda3 Ubuntu directory, there are a number files, which include:
```
initrd.img-2.6.31-14-generic-pae; and
vmlinuz-2.6.31-14-generic-pae
```

Are these the two kernels that I should be looking for?

And if so, what does this mean in relation to my faulty *menu.lst* file?

---

### Post by P4man on 2009-11-05
Your grub menu shows:
# groot=(hd0,2)

The correct syntax is
# groot=hd(x,y)

Note the placements of the brackets. Did you change that manually? Or am I unaware the first notation is also correct?

As for the numbers. grub starts counting at zero. First drive is zero, so x should be zero. First partition on that drive is zero, and grub is on the 4th, so y should 3

in short:
# groot=(hd0,3)

That should give your current grub menu  I hope, but no ubuntu yet, since its not in there.. This links shows how to install and configure grub legacy from a live cd:
[http://developer.spikesource.com/wiki/index.php/Article:Ubuntu_how_to_re-install_grub_using_chroot](http://developer.spikesource.com/wiki/index.php/Article:Ubuntu_how_to_re-install_grub_using_chroot)

That said, the default grub in karmic is grub2 which is totally different, if you want grub 2 you can follow the instructions here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I

---

### Post by alphaniner on 2009-11-05
Once you get groot fixed as pointed out by P4man, I think all you should need to do is change this```
title		**[COLOR="Red"]Linux Mint 7[/COLOR]**
root		(hd0,2)
kernel		/boot/**[COLOR="Red"]vmlinuz-2.6.28-11-generic[/COLOR]** root=/dev/sda3 ro quiet splash
initrd		/boot/**[COLOR="Red"]initrd.img-2.6.28-11-generic[/COLOR]**
quiet
```

to this```
title		**[COLOR="SeaGreen"]Ubuntu 9.10[/COLOR]**
root		(hd0,2)
kernel		/boot/**[COLOR="SeaGreen"]vmlinuz-2.6.31-14-generic-pae[/COLOR]** root=/dev/sda3 ro quiet splash
initrd		/boot/**[COLOR="SeaGreen"]initrd.img-2.6.31-14-generic-pae[/COLOR]**
quiet
```

provided you are keeping the kernel and initrd in the /boot directory of the Ubuntu install.  But I could be wrong.  I wouldn't be hurt if you waited for a second opinion. :P

---

### Post by Pipps on 2009-11-05
Hi P4man, allow me to provide a reply to the two parts of your message in turn:

> Note the placements of the brackets. Did you change that manually?
I can say that I have not ever touched the brackets within the syntax of the driver identifiers in the *menu.lst*. Also, when I had been using Mint 7 at sda3 previously, at that same partition location, and referenced within Grub in precisely that aforementioned bracketed format, I was able to boot successfully. Though I do not doubt you for a minute, and I have no idea what the correct syntax should be, I am unaware of where the discrepancy could lie. I would be interested to know what other thoughts you have on this.

> As for the numbers. grub starts counting at zero. First drive is zero, so x should be zero. First partition on that drive is zero, and grub is on the 4th, so y should 3

in short:
# groot=(hd0,3)

That should give your current grub menu I hope, but no ubuntu yet, since its not in there.. This links shows how to install and configure grub legacy from a live cd... .
I might be missing something here, but I am not sure that this quite addresses my difficulties with enabling Ubuntu to boot from Grub, under these particular circumstances.

---

### Post by Pipps on 2009-11-05
> **alphaniner said:**
> Once you get groot fixed as pointed out by P4man, I think all you should need to do is change this```
title		**[COLOR="Red"]Linux Mint 7[/COLOR]**
root		(hd0,2)
kernel		/boot/**[COLOR="Red"]vmlinuz-2.6.28-11-generic[/COLOR]** root=/dev/sda3 ro quiet splash
initrd		/boot/**[COLOR="Red"]initrd.img-2.6.28-11-generic[/COLOR]**
quiet
```

to this```
title		**[COLOR="SeaGreen"]Ubuntu 9.10[/COLOR]**
root		(hd0,2)
kernel		/boot/**[COLOR="SeaGreen"]vmlinuz-2.6.31-14-generic-pae[/COLOR]** root=/dev/sda3 ro quiet splash
initrd		/boot/**[COLOR="SeaGreen"]initrd.img-2.6.31-14-generic-pae[/COLOR]**
quiet
```

provided you are keeping the kernel and initrd in the /boot directory of the Ubuntu install.  But I could be wrong.  I wouldn't be hurt if you waited for a second opinion. :P

Thank you for spelling this out for me and making it unmistakably clear! I am, admittedly, rather in need of the clarity! ;)

I used the command: *sudo gedit /media/GRUB/boot/grub/menu.lst* to attempt to edit the *menu.lst* file. I reboot, but I now get a *Grub error 11*.

I return to the Live CD and examine the */media/GRUB/boot/grub/* directory within Gnome. I note that there are now two *menu.lst* files within the directory. The new file is entitled *menu.lst~*. It is described, in the 'File Type' menu, as being a *backup file*.

What does this mean, and how can I force Gnome to update this simple text file with the changes which I have made to it?

---

### Post by P4man on 2009-11-05
You are wrong not to doubt me. Some googling reveals that the original  syntax is  (also?) correct. it looks strange to me  but it is what it is

# groot=(hdx,y)

should work.As for the nunbers, I now see you posted this:

```
/dev/sda1: UUID="CE00E7B800E7A625" TYPE="ntfs" 
/dev/sda3: UUID="fa1271c3-f4f7-4fb8-848a-56d73f2b82cc" TYPE="ext3" 
/dev/sda4: LABEL="GRUB" UUID="ea340f4c-def5-4a5e-9559-d20c1c3d12f7" TYPE="ext3" 

```

Which doesnt show partition 2 which is shown in the output of boot info script. Its probably a hidden partition (vista recover?) and now you make me wonder if hidden partitions are counted by grub or not.

If you did not change partition size or locations, then you can probably safely ignore all my comments and keep your groot line as it was and I will crawl back under a rock :)

But if you are having grub error 15 ,then you may try changing that number regardless.

As for how it relates to booting ubuntu: it doesnt. I was trying to make grub load. Once that does load you can use alphaniner's edits to boot ubuntu from grub. Or run grub-update as explained in the links i gave earlier it should achieve the same.

---

### Post by P4man on 2009-11-05
> **Pipps said:**
> Thank you for spelling this out for me and making it unmistakably clear! I am, admittedly, rather in need of the clarity! ;)

I used the command: *sudo gedit /media/GRUB/boot/grub/menu.lst* to attempt to edit the *menu.lst* file. I reboot, but I now get a *Grub error 11*.


error 11 relates to device.map in your grub folder.
Can you post its contents?

> 
I return to the Live CD and examine the */media/GRUB/boot/grub/* directory within Gnome. I note that there are now two *menu.lst* files within the directory. The new file is entitled *menu.lst~*. It is described, in the 'File Type' menu, as being a *backup file*.

Thats normal. gedit automatically makes a backup of the file you edited, which is a very nice feature.

---

### Post by Pipps on 2009-11-05
I have tried deleting the *menu.lst~* backup file, and then attempting a reboot.

This time, it works!

I am now able to boot into Ubuntu 9.10 successfully, using my pre-existing Grub menu and the previous Linux partition.

I really like the improved look and feel of Ubuntu 9.10. Thank you for all your kind assistance in helping me use it! :)

---

### Post by P4man on 2009-11-05
> **Pipps said:**
> I have tried deleting the *menu.lst~* backup file, and then attempting a reboot.

This time, it works!

You deleted an innocent, unused backup file and *that* solves it?
That makes zero sense, but then neither did I this thread so lets just be happy and enjoy or up/down grade :)

---

### Post by Pipps on 2009-11-05
[COLOR="Red"]**Update:**[/COLOR]
Now, when I try to boot into WinXP located at (hda0,0), I now receive a *Grub Error 11 Unrecognized Device String&#8206;*!

What could have caused this problematic change in behaviour? :(

---

### Post by Pipps on 2009-11-05
**Solution:**
I change the amended *hda(0,0)* back to *(hda0,0)*, and XP now boots fine!

This thread has definitely been weird! I thought I was just beginning to understand a little about Ubuntu. Now I am not so sure! :-k

---

### Post by Pipps on 2009-11-11
**[COLOR="Red"]Update[/COLOR]**

Another, even stranger problem. Please help!

I have reinstalled Ubuntu 9.10 onto this partition again. The only change being that I reformatted it from ext3 to ext4.

Now, when I log into Ubuntu, from Grub, instead of being taken through to the Ubuntu desktop as normal, I am eventually presented with the following screen:

> Ubuntu 9.10 Pipps-desktop tty1
Pipps-desktop login:
Password:
Linux Pipps-desktop 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686

To access official Ubuntu documentation, please visit:
[http://help.ubuntu/com/](http://help.ubuntu/com/)

85 packages can be updated.
22 updates are security updates.

The programs included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

To run a command as administrator user "root"), use "sudo <command>".
See "man sudo_root" for details

Pipps@Pipps-desktop:~$_


This is really strange, because during the installation screens, I specifically requested that I would like to be logged-in automatically at boot.

I have retried this installation three times now, and each time I am presented with exactly the same seemingly failed boot.

Can anyone help me understand why this is happening?

---

### Post by P4man on 2009-11-12
X is not starting. 
What happens when you type

```
sudo /etc/init.d/gdm restart
```

---

### Post by Pipps on 2009-11-12
Thank you for your help!

I tried the command precisely as you recommended. 

I received the following:

> Rather than invoking init scripts through /etc/init.d, use the service( 8) utility, e.g. service gdm restart

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the restart( 8) utility, e.g. restart gdm gdm start/running, process 1884
Pipps@Pipps-desktop:~4 _

The screen flashed violently, before this message was fully displayed.

My machine still will not boot to the Ubuntu desktop.

What has gone wrong?

---

### Post by P4man on 2009-11-12
Right, i forgot karmic uses upstart.
What happens when you run
```

sudo service gdm restart
```

I dont assume it will solve anything but the error may help understanding.

To actually make it boot the GUI again try this:

```
sudo dpkg-reconfigure xserver-xorg 
```

Select the VESA option to have a (far chance of having a) GUI again but it will be slow as hell.

---

### Post by Pipps on 2009-11-12
Thank you again for your much appreciated reply.

When I type *'sudo service gdm restart'* I receive only the message:
```
restart: unknown instance
```

And when I type *'sudo dpkg-reconfigure xserver-xorg'*, I receive nothing whatsoever in response.

What could all this mean? 

Will I ever be able to run Karmic?

---

### Post by Pipps on 2009-11-16
Any thoughts please, anyone? 8-[

---

### Post by P4man on 2009-11-16
You didnt do a server install by any chance did you?
If you did (or even if you didnt) try  this perhaps:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by jimpr13 on 2009-11-16
> **P4man said:**
> You didnt do a server install by any chance did you?
If you did (or even if you didnt) try  this perhaps:

```
sudo apt-get install ubuntu-desktop
```

yes i tried it too but i had problem with posix

---

