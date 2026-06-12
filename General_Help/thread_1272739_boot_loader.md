---
title: "boot loader"
date: 2009-09-22
forum: General Help
---

### Post by mupto on 2009-09-22
i had installed linux after installing windows like i have 500 times, but this time i decided to go into advanced and change where it placed the grub bootloader. i tried installing it on my windows partition. when i boot up i can get into linux fine and my windows entry is there but when i click on windows it just takes me back to grub and doesnt say anything. i checked the grub options and its settings all seem fine. anyone know the problem?

---

### Post by arrange on 2009-09-22
If you erased the Windows bootloader then you are in trouble. Could you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") here?

---

### Post by mupto on 2009-09-22
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 207231830 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   234,436,544    70,589,610   5 Extended
/dev/sda5         163,846,998   231,448,454    67,601,457  83 Linux
/dev/sda6         231,448,518   234,436,544     2,988,027  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="d32c4352-76af-447f-9bee-43628a1a0405" TYPE="ext3" 
/dev/sda6: UUID="c2bb5953-c633-491a-976a-c3ad902f6a06" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)


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
# kopt=root=UUID=d32c4352-76af-447f-9bee-43628a1a0405 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d32c4352-76af-447f-9bee-43628a1a0405

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		d32c4352-76af-447f-9bee-43628a1a0405
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d32c4352-76af-447f-9bee-43628a1a0405 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		d32c4352-76af-447f-9bee-43628a1a0405
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=d32c4352-76af-447f-9bee-43628a1a0405 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d32c4352-76af-447f-9bee-43628a1a0405
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d32c4352-76af-447f-9bee-43628a1a0405 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d32c4352-76af-447f-9bee-43628a1a0405
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d32c4352-76af-447f-9bee-43628a1a0405 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d32c4352-76af-447f-9bee-43628a1a0405
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
root		(hd0,0)
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
UUID=d32c4352-76af-447f-9bee-43628a1a0405 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c2bb5953-c633-491a-976a-c3ad902f6a06 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 106.1GB: boot/grub/menu.lst
 106.1GB: boot/grub/stage2
 106.1GB: boot/initrd.img-2.6.28-11-generic
 106.1GB: boot/initrd.img-2.6.28-15-generic
 106.0GB: boot/vmlinuz-2.6.28-11-generic
 106.1GB: boot/vmlinuz-2.6.28-15-generic
 106.1GB: initrd.img
 106.1GB: initrd.img.old
 106.1GB: vmlinuz
 106.0GB: vmlinuz.old

---

### Post by arrange on 2009-09-22
> **mupto said:**
> 
 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 207231830 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

You probably erased the Windows bootloader. **sda** is not the same as **sda1**. Let's hope someone knows if this is repairable. I don't, sorry... :(

---

### Post by mupto on 2009-09-22
well thank you for trying at least. so far nobody else seems to know i guess :/

---

### Post by mupto on 2009-09-22
i cant even see or mount my windows partition to save files that i deseratly need from my windows partiton. can someone please help me fix this piece of ****.

---

### Post by P4man on 2009-09-22
I think arrange is right. You installed grub on sda[COLOR="Red"]1[/COLOR], which is the windows partition. It should have been installed on sda so it wouldn't touch the windows partition and only write stage1 to the master boot record.

I think your only option is to boot a windows cd, and run "fixmbr" and/or "fixboot" from the recovery console (dont remember exact name in windows).
That should hopefully restore your windows, but im not even sure of that. After that, you can boot a ubuntu live cd and reinstall grub on to hd(0,0) allowing you to dual boot again.

edit: I hadn't noticed your last post. If you cant even see the ntfs partition, then its worse than I feared. fixboot/fixmbr may well not be enough.. You might need testdisk to retrieve data from the nts partition and do a full windows reinstall :s

---

### Post by arrange on 2009-09-22
Have a look at [this link]("http://www.ntfs.com/boot-sector-damaged.htm") or just google *recover xp volume boot sector* or some such.

---

### Post by egalvan on 2009-09-22
MASTER Boot Records (MBR) belong to drives, not partitions..
Boot Sectors belong to partitions...
(More or less)


SuperGRUB LiveCD has this option, which should suit you...

"**you can use the new SGD option: Windows Partition Boot Restore**"

you can download supergrub from here...

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

burn iso and boot from it...

herman has some good general info on this..

[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

and this link from his page also has some excellent info on "missing ntldr" error messages and such...

[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)


and in case you are interested in (much, much) more info on GRUB and MBR's and etc...

try this link

[http://members.iinet.net.au/~herman546/p6.html](http://members.iinet.net.au/~herman546/p6.html)

the entire site is loaded with information,
and herman is a member of this forum..

further, if you have a bootable XP CD, you can try the "repair installation" option.
There is also the "Recovery Console" option.

Yes, this is a fair amount of work, but Windows is like this...

ErnestG

---

### Post by Darkwing-Duck on 2009-09-23
Here is another option for fixing your MBR and grub.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by mike555 on 2009-09-23
What I do (because I often reinstall) is use "GAG" boot manager and just install grub to the front of each partition during install of each OS , it works great and is free .    [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

