---
title: "Another grub dual boot issue."
date: 2009-07-08
forum: General Help
---

### Post by Derviansoul on 2009-07-08
Hello I need to work with nokia s60 sdk, so I need unfortunately to go back to windows. I installed windows xp on my 1st hard drive on a primary ntfs partition. that destroyed the grub mbr, I restored the mbr following the instructions from ubuntu website for it. But now I cannot boot into windows to start working on it. There is nothing wrong with the windows mbr because if I unplug the hd's that have ubuntu installed, it boots straight to windows, but if I have them plugged-in I cannot boot into windows, i tried loads of combinations in my menu.lst. and nothing this is really getting me frustrated. Apparently this is happening quite often with more people.

Here is my system info from boot_info_script

```

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 680767 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sdb5 and looks 
                       at sector 20180678 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,777,704,704 1,777,704,642  83 Linux
/dev/sda2    *  1,777,704,705 1,953,503,999   175,799,295   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08c2adbb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    58,589,054    58,588,992  83 Linux
/dev/sdb2          58,589,055   625,137,344   566,548,290   f W95 Ext d (LBA)
/dev/sdb5          58,589,118   625,137,344   566,548,227  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a6efc91

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   388,676,609   388,676,547  83 Linux
/dev/sdc3         388,676,610   398,283,479     9,606,870  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="/media/movies" UUID="5af4c8d2-0b19-4596-a865-9205b052143d" TYPE="ext4" 
/dev/sda2: UUID="A85492185491E978" TYPE="ntfs" 
/dev/sdb1: UUID="0aaece6c-cea5-44cf-9a3a-8ea5ffa51221" TYPE="ext4" 
/dev/sdb5: UUID="e53a3553-c21e-4f84-8ab8-9e3665729ca1" TYPE="ext3" 
/dev/sdc1: UUID="aa9f886c-d648-4d32-b204-b62bc8f4f9ed" TYPE="ext3" 
/dev/sdc3: UUID="d2aa97a1-b13b-4634-807f-62827df1f805" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc1 on /media/documents type ext3 (rw,relatime)
/dev/sdb5 on /media/myfiles type ext3 (rw,relatime)
/dev/sda1 on /media/movies type ext4 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
# kopt=root=UUID=0aaece6c-cea5-44cf-9a3a-8ea5ffa51221 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0aaece6c-cea5-44cf-9a3a-8ea5ffa51221

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		0aaece6c-cea5-44cf-9a3a-8ea5ffa51221
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0aaece6c-cea5-44cf-9a3a-8ea5ffa51221 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		0aaece6c-cea5-44cf-9a3a-8ea5ffa51221
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0aaece6c-cea5-44cf-9a3a-8ea5ffa51221 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		0aaece6c-cea5-44cf-9a3a-8ea5ffa51221
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0aaece6c-cea5-44cf-9a3a-8ea5ffa51221 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		0aaece6c-cea5-44cf-9a3a-8ea5ffa51221
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0aaece6c-cea5-44cf-9a3a-8ea5ffa51221 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		0aaece6c-cea5-44cf-9a3a-8ea5ffa51221
kernel		/boot/memtest86+.bin
quiet



## END DEBIAN AUTOMAGIC KERNELS LIST
title Windows XP
rootnoverify (hd0,1)
chainloader +1
makeactive
boot

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0aaece6c-cea5-44cf-9a3a-8ea5ffa51221 /               ext4    relatime,errors=remount-ro 0       1
# /media/documents was on /dev/sdb1 during installation
UUID=aa9f886c-d648-4d32-b204-b62bc8f4f9ed /media/documents ext3    relatime        0       2
# /media/myfiles was on /dev/sda5 during installation
UUID=e53a3553-c21e-4f84-8ab8-9e3665729ca1 /media/myfiles  ext3    relatime        0       2
# swap was on /dev/sdb3 during installation
UUID=d2aa97a1-b13b-4634-807f-62827df1f805 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=5af4c8d2-0b19-4596-a865-9205b052143d /media/movies/ ext4 relatime,errors=remount-ro 0       2
=================== sdb1: Location of files loaded by Grub: ===================


   8.2GB: boot/grub/menu.lst
    .3GB: boot/grub/stage2
   6.0GB: boot/initrd.img-2.6.28-11-generic
   7.3GB: boot/initrd.img-2.6.28-13-generic
   6.6GB: boot/vmlinuz-2.6.28-11-generic
   4.2GB: boot/vmlinuz-2.6.28-13-generic
   7.3GB: initrd.img
   6.0GB: initrd.img.old
   4.2GB: vmlinuz
   6.6GB: vmlinuz.old

```

I tried to change the entry in the menu.lst with the map keyword, using:

```

map (hd1) (hd0)
map (hd0) (hd1)

```

Or vice-versa changing the numbers of the hd's but the result is always the same error 12 on the grub loader.

I also changed the rootnoverify (hd0,0) and this brings me back to grub for some reason. i done this since windows boots automatically when just using the windows hd.

The windows hd is the first hd, but my bios allows me to choose the boot order for each hd. so the sdb is the one that has the priority to boot.

Could anyone give me some hints its being a week that i've been trying to boot to windows with no success. Apparently this happens with allot of people. I thought that was because of this that grub replaced lilo at the early years of linux. because was simpler and more secure.

Regards

---

### Post by Jebtrix on 2009-07-08
Why not just use virtualbox instead of dualboot? I use it for same reason you do, winworld programming.

---

### Post by merlinus on 2009-07-08
Windows is on sda2, which if your second hdd in booting order is (hd1,1)

So this may work in menu lst:

title windows xp
rootnoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by Derviansoul on 2009-07-09
> **merlinus said:**
> Windows is on sda2, which if your second hdd in booting order is (hd1,1)

So this may work in menu lst:

title windows xp
rootnoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

That worked really well thanks allot u saved me.

Merlinus: i find virtual machines really slow and annoying thats why i installed windows on a separated partitions. I installed kubuntu on a macbook two months ago with virtualbox and i found it really slow. Thats i done this way.

---

