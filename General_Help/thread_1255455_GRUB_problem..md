---
title: "GRUB problem."
date: 2009-09-01
forum: General Help
---

### Post by Farsk1 on 2009-09-01
I've just installed ubuntu on my brand new laptop, dual-booting with Windows XP(it came pre-installed). Ubuntu works just perfect as always, but my Windows XP is not showing up in GRUB. I've tried editing the /boot/grub/menu.lst in many different ways but no luck so far, therefore I'm asking you.

My current menu.lst:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		149a6725-7cf4-46b5-abc5-365950387ca5
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=149a6725-7cf4-46b5-abc5-365950387ca5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		149a6725-7cf4-46b5-abc5-365950387ca5
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=149a6725-7cf4-46b5-abc5-365950387ca5 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic
uuid		149a6725-7cf4-46b5-abc5-365950387ca5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=149a6725-7cf4-46b5-abc5-365950387ca5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid		149a6725-7cf4-46b5-abc5-365950387ca5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=149a6725-7cf4-46b5-abc5-365950387ca5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, memtest86+
uuid		149a6725-7cf4-46b5-abc5-365950387ca5
kernel		/boot/memtest86+.bin
quiet

title              Windows XP
rootnoverify (hd0,8)
chainloader (hd0,4)+1 

### END DEBIAN AUTOMAGIC KERNELS LIST

**_This is the one with the best results so far, It shows up in the GRUB menu but if i choose it I get this:_**

Starting up...
_


**_I waited for 20 minutes, but nothing happened_**



###Output from fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1d68c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29126   233954563+   f  W95 Ext'd (LBA)
/dev/sda2           29127       30402    10241024   83  Linux
/dev/sda5   *         193        4016    30716248+   7  HPFS/NTFS
/dev/sda6            4017       29126   201696043+   7  HPFS/NTFS
/dev/sda7               1         192     1542145+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1014 MB, 1014497280 bytes
255 heads, 63 sectors/track, 123 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e0fed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         122      979933+   6  FAT16



###END###
[B]
My WinXP is located on /dev/sda5/[/B]

---

### Post by egalvan on 2009-09-01
First, the XP stanza should be BELOW the 

```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

divider... 

OK, having said that...let's move on...

this is the XP stanza from my menu.lst
It is the same on five different machines that I am dual/multi-booting Windows/Linux/etc..


```
title		WinXP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


The 'savedefault' option will make no difference,
but the 'makeactive' on will make a difference.

It may or may not help you.

---

### Post by Farsk1 on 2009-09-01
No, that did'nt help.Got Error 12: "Cannot mount selected partition"

So i tried to experiment with the code:

title		WinXP Pro
root		(hd0,5)
savedefault
makeactive
chainloader	+1

title		WinXP Pro
root		(hd0,4)
savedefault
makeactive
chainloader	+1

title		WinXP Pro
root		(hd0,4)+1
savedefault
makeactive
chainloader	+1

[B]But all of them returned Error 12, so i added: mount
Just to test, dunno if it is a command in GRUB
[/B]

title		WinXP Pro
mount           /dev/sda5
root		(hd0,5)
savedefault
makeactive
chainloader	+1

title		WinXP Pro
mount           /dev/sda
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		WinXP Pro
mount           /dev/sda
root		(hd0,5)
savedefault
makeactive
chainloader	+1


**These also returned Error 12.**

---

### Post by egalvan on 2009-09-01
Forum member 'caljohnsmith' (an absolute genius at solving boot problems) along with meifera (another genius) had a script called

boot_info_script32.sh

it's on Sourceforge, here...

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

you donwload it to your desktop, run it,
(it scans all available drives for specific files, and other info)
then upload the 'results.txt' file that it generates.

---

### Post by Farsk1 on 2009-09-01
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb1d68c10

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   467,909,189   467,909,127   f W95 Ext d (LBA)
/dev/sda5    *      3,084,543    64,517,039    61,432,497   7 HPFS/NTFS
/dev/sda6          64,517,103   467,909,189   403,392,087   7 HPFS/NTFS
/dev/sda7                 189     3,084,479     3,084,291  82 Linux swap / Solaris
/dev/sda2         467,912,704   488,394,751    20,482,048  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1014 MB, 1014497280 bytes
255 heads, 63 sectors/track, 123 cylinders, total 1981440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e0fed

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     1,959,929     1,959,867   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="149a6725-7cf4-46b5-abc5-365950387ca5" TYPE="ext3" 
/dev/sda5: UUID="4650894850894023" TYPE="ntfs" 
/dev/sda6: UUID="005809535809493C" TYPE="ntfs" 
/dev/sda7: UUID="dacae840-120e-4a76-b958-c147753ace35" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" UUID="18CD-C451" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/havar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=havar)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda5 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=149a6725-7cf4-46b5-abc5-365950387ca5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=149a6725-7cf4-46b5-abc5-365950387ca5

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
uuid		149a6725-7cf4-46b5-abc5-365950387ca5
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=149a6725-7cf4-46b5-abc5-365950387ca5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		149a6725-7cf4-46b5-abc5-365950387ca5
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=149a6725-7cf4-46b5-abc5-365950387ca5 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic
uuid		149a6725-7cf4-46b5-abc5-365950387ca5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=149a6725-7cf4-46b5-abc5-365950387ca5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid		149a6725-7cf4-46b5-abc5-365950387ca5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=149a6725-7cf4-46b5-abc5-365950387ca5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, memtest86+
uuid		149a6725-7cf4-46b5-abc5-365950387ca5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		WinXP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=149a6725-7cf4-46b5-abc5-365950387ca5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=dacae840-120e-4a76-b958-c147753ace35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 245.9GB: boot/grub/menu.lst
 245.9GB: boot/grub/stage2
 245.1GB: boot/initrd.img-2.6.27-7-generic
 245.2GB: boot/initrd.img-2.6.28-15-generic
 245.9GB: boot/vmlinuz-2.6.27-7-generic
 245.3GB: boot/vmlinuz-2.6.28-15-generic
 245.2GB: initrd.img
 245.1GB: initrd.img.old
 245.3GB: vmlinuz
 245.9GB: vmlinuz.old

---

### Post by egalvan on 2009-09-01
OK, using boot_script, here is what my system shows...

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    [B]File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    [COLOR="Red"]Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM[/COLOR][/B]

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbbbbbbbb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    16,370,234    16,370,172   7 HPFS/NTFS
/dev/sda2          16,370,235   156,248,189   139,877,955   5 Extended
/dev/sda5          16,370,298   129,965,849   113,595,552  83 Linux
/dev/sda6         129,965,913   150,448,724    20,482,812  83 Linux
/dev/sda7         150,448,788   156,248,189     5,799,402  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ade62

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,465,144,064 1,465,144,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="805424F85424F318" LABEL="gx280-xp" TYPE="ntfs" 
/dev/sda5: UUID="0933d680-d893-40fa-a01d-3c819f0b2ea3" TYPE="ext3" 
/dev/sda6: LABEL="puppy" UUID="3119f61a-7ab2-4b91-b9c8-44fa795dfae5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" LABEL="swap" UUID="7f9f938e-90da-4c2d-a75a-bd680b97aa4e" 
/dev/sdb1: LABEL="750-data1" UUID="ea49cca2-75fc-4082-a4d7-4bc040df5d8b" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/ernest/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ernest)
/dev/sdb1 on /media/750-data1 type ext3 (rw,nosuid,nodev,uhelper=hal)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
#

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
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue blink-white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=0933d680-d893-40fa-a01d-3c819f0b2ea3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)ns for automagic boot options (hd0,4)

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
# defoptions=

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
# altoptions=(profile mode) profile

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,4)ns for automagic boot options (hd0,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0933d680-d893-40fa-a01d-3c819f0b2ea3 ro 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,4)ns for automagic boot options (hd0,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0933d680-d893-40fa-a01d-3c819f0b2ea3 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (profile mode)
root		(hd0,4)ns for automagic boot options (hd0,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0933d680-d893-40fa-a01d-3c819f0b2ea3 ro profile
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,4)ns for automagic boot options (hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0933d680-d893-40fa-a01d-3c819f0b2ea3 ro 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)ns for automagic boot options (hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0933d680-d893-40fa-a01d-3c819f0b2ea3 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (profile mode)
root		(hd0,4)ns for automagic boot options (hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0933d680-d893-40fa-a01d-3c819f0b2ea3 ro profile
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,4)ns for automagic boot options (hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider,
# added to separate the menu items below from the Debian
# ones above.
title		Other *nix OS's:
root

#   original puppy frugal install, no longer used, does not exist
# title		Puppy Linux 4.00, no longer used, does not exist
# rootnoverify	(hd0,5)
# kernel	/vmlinuz root=/dev/ram0 pmedia=idehd
# initrd	/initrd.gz

#   previous puppy frugal install, using folder, no longer used, still exists
#title		Puppy 4.11
#rootnoverify	(hd0,5)
#kernel		/puppy_411/vmlinuz root=/dev/ram0 pmedia=idehd psubdir=puppy_411
## pfix=ram	if used, will not load "save files"
#initrd		/puppy_411/initrd.gz

#   current puppy frugal install, using folder
title		Puppy 4.12, using 411 "save files"
rootnoverify	(hd0,5)
kernel		/puppy_412/vmlinuz root=/dev/ram0 pmedia=idehd psubdir=puppy_412
# pfix=ram	if used, will not load "save files"
initrd		/puppy_412/initrd.gz


#--------------------------------------------------------------------------
# This entry automatically added by the Debian installer for a non-*nix OS
# on /dev/sda1

title		Other non-*nix OS's:
root

title		WinXP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=0933d680-d893-40fa-a01d-3c819f0b2ea3 / ext3 relatime,errors=remount-ro 0 1
LABEL=swap none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda1 /mnt/gx280-xp ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/menu.lst
  30.1GB: boot/grub/stage2
  30.1GB: boot/initrd.img-2.6.24-22-generic
  30.2GB: boot/initrd.img-2.6.24-22-generic.bak
  30.2GB: boot/initrd.img-2.6.24-23-generic
  30.2GB: boot/initrd.img-2.6.24-23-generic.bak
  30.1GB: boot/initrd.img-2.6.24-24-generic
  30.2GB: boot/initrd.img-2.6.24-24-generic.bak
  30.2GB: boot/vmlinuz-2.6.24-22-generic
  30.1GB: boot/vmlinuz-2.6.24-23-generic
  30.1GB: boot/vmlinuz-2.6.24-24-generic
  30.1GB: initrd.img
  30.2GB: initrd.img.old
  30.1GB: vmlinuz
  30.1GB: vmlinuz.old

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
```

The most glaring difference is in the red highlighted section...
yours shows no boot directories or files...

---

### Post by egalvan on 2009-09-01
screenshot using gparted ( partition editor )

---

