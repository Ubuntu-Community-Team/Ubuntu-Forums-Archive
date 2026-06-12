---
title: "GRUB Error 17"
date: 2009-10-03
forum: General Help
---

### Post by iEthan on 2009-10-03
At the moment, I'm dual-booting XP and Ubuntu. I also have another 10GB partition. I was running out of space on my Ubuntu partition, so I went into XP and deleted the 10GB partition with Disk Management.

So, I rebooted, and I get to GRUB, and it says Error 17.

I'm using a Live CD right now. How could I fix it?

---

### Post by iEthan on 2009-10-03
Also, I ran the following:

```

sudo grub
find /boot/grub/stage1

```

Which returned:

```
Error 15: File not found
```

Meh.

---

### Post by arrange on 2009-10-03
Please attach the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") here.

---

### Post by iEthan on 2009-10-03
Wait, hold on. I tried again and it's doing something now.

---

### Post by iEthan on 2009-10-03
Nevermind >.<. I did sudo sh instead of sudo bash. Here are the outputs:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652  de Dell Utility
/dev/sda2    *     21,157,605   269,309,836   248,152,232   7 HPFS/NTFS
/dev/sda3         269,313,660   312,576,704    43,263,045   5 Extended
Empty Partition
/dev/sda5         308,865,753   310,681,034     1,815,282  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0B1B" TYPE="vfat" 
/dev/sda2: UUID="F20045C400459091" TYPE="ntfs" 
/dev/sda5: UUID="37f37731-7141-4488-94a2-97aa02852abe" TYPE="swap" 

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


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


```

---

### Post by Bucky Ball on 2009-10-03
[http://members.iinet.net.au/~herman546/p15.html#17]("http://members.iinet.net.au/%7Eherman546/p15.html#17")

Open your /boot/grub/menu.lst file and look for the windows entry and make sure yours has the line in bold:

```
title         Windows
**root          (hd0,1)**
savedefault
makeactive
chainloader   +1
```On that drive (sda) you have a Linux swap partition but Linux install. Is that right??

---

### Post by iEthan on 2009-10-03
The /boot/grub/ directory doesn't exist.

---

### Post by Bucky Ball on 2009-10-03
Like I say, there doesn't appear to be an installed Linux operating system on the physical drive sda.

---

### Post by iEthan on 2009-10-03
There is, though. How do I fix this?

---

### Post by arrange on 2009-10-03
As you may see, you probably deleted your Ubuntu partition. You will have to create the partition in the Partition Editor and make a fresh install :(

---

### Post by iEthan on 2009-10-03
Meh. I might as well just wipe the entire thing and start from scratch. I'm fed up.

But before I do that, I want a second opinion. Anyone?

---

### Post by Bucky Ball on 2009-10-03
> **iEthan said:**
> There is, though. How do I fix this?

Sorry, there is no Ubuntu install on that drive (sda). Only a Linux swap file on the last partition. 

```
Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652  de Dell Utility
/dev/sda2    *     21,157,605   269,309,836   248,152,232   7 HPFS/NTFS
/dev/sda3         269,313,660   312,576,704    43,263,045   5 Extended
**Empty Partition**
/dev/sda5         308,865,753   310,681,034     1,815,282  82 **Linux swap** / Solaris

```You have your Dell recovery, Windows, an empty extended partition (sda3) and a swap partition (I think, though you may have an empty partition and the swap in your extended partition). Where is Ubuntu? Not there.

---

### Post by bumanie on 2009-10-03
Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       176,714       176,652  de Dell Utility
/dev/sda2    *     21,157,605   269,309,836   248,152,232   7 HPFS/NTFS
/dev/sda3         269,313,660   312,576,704    43,263,045   5 Extended
Empty Partition
/dev/sda5         308,865,753   310,681,034     1,815,282  82 Linux swap / Solaris

As far as I can see, there are 2 options available
1. Reinstall ubuntu to the empty partition ; it would be advisable to use 'manual' at the partitioning stage so that you preserve your restore partition and windows installation

or

2. Try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover the lost partition. Then follow the [step-by-step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") and look at this [too]("http://members.iinet.net.au/~herman546/p21.html"). Again, be mindful of preserving the restore partition and windows installation.

---

### Post by shaon3343 on 2009-10-03
I think you must make a fresh install . Theres aint no way :(

---

### Post by Ferguson9 on 2009-10-03
Ive done exactly the same so now im doing a fresh install. Ive chosen the "Use continuous free disk space" option and its currentl installing but im worried that the old one might still be there. Does anyone know if it will be or will this overwrite it?

---

### Post by Ferguson9 on 2009-10-03
My re-install has finished and luckily I no longer get the error and can boot into Windows fine. However, I now have the option to boot into Vista, the old ubuntu and now the new one. How can I completely remove the old ubuntu? 

I ran sudo fisk -l and got the following:

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd87ed87e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       68293   548563491    7  HPFS/NTFS
/dev/sda2           68294       91201   184008510    5  Extended
/dev/sda5           68294       77689    75473307   83  Linux
/dev/sda6           77690       78094     3253131   82  Linux swap / Solaris
/dev/sda7           90664       91201     4321453+  82  Linux swap / Solaris
/dev/sda8           78095       90146    96807658+  83  Linux
/dev/sda9           90147       90663     4152771   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by oldfred on 2009-10-03
Windows will not see the ext3 Ubuntu partition so it will look like an empty partition.

You had no linux and one swap, now you have 2 linux and 3 swaps? It looks like you installed it twice unless the install somehow recovered your old install. 

If you delete the 2 extra swaps make sure you do not delete the one your install is using or edit fstab to use the one you keep.

---

### Post by Bucky Ball on 2009-10-04
> **Ferguson9 said:**
> My re-install has finished and luckily I no longer get the error and can boot into Windows fine. However, I now have the option to boot into Vista, the old ubuntu and now the new one. How can I completely remove the old ubuntu? 

You should have done it by 'manual partitioning' and setting up the partitions the way you wanted when you were installing rather than choosing 'free space'. That way you can see what partitions are already there and keep or delete. :)

It pays to plan by visually dividing up your disk with pen and paper before you install then you get it right first time.

---

### Post by Ferguson9 on 2009-10-04
> **Bucky Ball said:**
> You should have done it by 'manual partitioning' and setting up the partitions the way you wanted when you were installing rather than choosing 'free space'. That way you can see what partitions are already there and keep or delete. :)

It pays to plan by visually dividing up your disk with pen and paper before you install then you get it right first time.

Thanks for the advice, ill remember that next time :)

Unfortunately, Ive already done it now so can someone please help me get back to just Windows and Ubuntu 9.04? 

Thanks

---

### Post by arrange on 2009-10-04
Post the [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") results again please (use CODE tags if possible).

---

### Post by Ferguson9 on 2009-10-04
> **arrange said:**
> Post the [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") results again please (use CODE tags if possible).

I have downloaded the file to my desktop but how do I run it? (Sorry but I am a noob with Linux)

THanks

---

### Post by iEthan on 2009-10-04
Right-click it and open with Text Editor. A README inside will tell you what to do.

---

### Post by Ferguson9 on 2009-10-04
> **iEthan said:**
> Right-click it and open with Text Editor. A README inside will tell you what to do.

It says to run sudo bash boot_info_script_028.sh or su - bash boot_info_script_028.sh which Ive tried and Ive also tried sudo bash boot_info_script032.sh and su - bash boot_info_script032.sh because the filename is called boot_info_script032.sh but none of them seem to work?!

---

### Post by Ferguson9 on 2009-10-04
Ignore that I wasnt in the desktop directory, thought I was. The results are below:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd87ed87e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,097,127,044 1,097,126,982   7 HPFS/NTFS
/dev/sda2       1,097,127,045 1,465,144,064   368,017,020   5 Extended
/dev/sda5       1,097,127,171 1,248,073,784   150,946,614  83 Linux
/dev/sda6       1,248,073,848 1,254,580,109     6,506,262  82 Linux swap / Solaris
/dev/sda7       1,456,501,158 1,465,144,064     8,642,907  82 Linux swap / Solaris
/dev/sda8       1,254,580,173 1,448,195,489   193,615,317  83 Linux
/dev/sda9       1,448,195,553 1,456,501,094     8,305,542  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="94E2F558E2F53F54" TYPE="ntfs" 
/dev/sda5: UUID="8a46888c-dc13-41a4-a5c4-657eb6ec0834" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="54ad8438-bde0-4387-9e4b-95800807f4ee" 
/dev/sda7: TYPE="swap" UUID="e2890c84-03ac-41a1-898c-cd8a9e38e6e3" 
/dev/sda8: UUID="1915a441-b915-404a-b6ad-56c43f81f909" TYPE="ext3" 
/dev/sda9: TYPE="swap" UUID="2022c4ec-60a5-46ac-ba85-31b9cc2cbc8c" 

=============================== "mount" output: ===============================

/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)


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
# kopt=root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8a46888c-dc13-41a4-a5c4-657eb6ec0834

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		8a46888c-dc13-41a4-a5c4-657eb6ec0834
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		8a46888c-dc13-41a4-a5c4-657eb6ec0834
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		8a46888c-dc13-41a4-a5c4-657eb6ec0834
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8a46888c-dc13-41a4-a5c4-657eb6ec0834
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8a46888c-dc13-41a4-a5c4-657eb6ec0834
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8a46888c-dc13-41a4-a5c4-657eb6ec0834
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8a46888c-dc13-41a4-a5c4-657eb6ec0834
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=54ad8438-bde0-4387-9e4b-95800807f4ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 602.8GB: boot/grub/menu.lst
 602.8GB: boot/grub/stage2
 598.8GB: boot/initrd.img-2.6.27-11-generic
 609.4GB: boot/initrd.img-2.6.27-14-generic
 609.4GB: boot/initrd.img-2.6.27-7-generic
 609.4GB: boot/vmlinuz-2.6.27-11-generic
 609.4GB: boot/vmlinuz-2.6.27-14-generic
 609.4GB: boot/vmlinuz-2.6.27-7-generic
 609.4GB: initrd.img
 598.8GB: initrd.img.old
 609.4GB: vmlinuz
 609.4GB: vmlinuz.old

=========================== sda8/boot/grub/menu.lst: ===========================

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
default		6

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
# kopt=root=UUID=1915a441-b915-404a-b6ad-56c43f81f909 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1915a441-b915-404a-b6ad-56c43f81f909

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
# defoptions=quiet splash vga=769

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
uuid		1915a441-b915-404a-b6ad-56c43f81f909
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=1915a441-b915-404a-b6ad-56c43f81f909 ro quiet splash vga=769 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		1915a441-b915-404a-b6ad-56c43f81f909
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=1915a441-b915-404a-b6ad-56c43f81f909 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		1915a441-b915-404a-b6ad-56c43f81f909
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1915a441-b915-404a-b6ad-56c43f81f909 ro quiet splash vga=769 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		1915a441-b915-404a-b6ad-56c43f81f909
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1915a441-b915-404a-b6ad-56c43f81f909 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		1915a441-b915-404a-b6ad-56c43f81f909
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8a46888c-dc13-41a4-a5c4-657eb6ec0834 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=1915a441-b915-404a-b6ad-56c43f81f909 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=2022c4ec-60a5-46ac-ba85-31b9cc2cbc8c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 697.9GB: boot/grub/menu.lst
 697.9GB: boot/grub/stage2
 697.9GB: boot/initrd.img-2.6.28-11-generic
 697.9GB: boot/initrd.img-2.6.28-15-generic
 697.9GB: boot/vmlinuz-2.6.28-11-generic
 697.9GB: boot/vmlinuz-2.6.28-15-generic
 697.9GB: initrd.img
 697.9GB: initrd.img.old
 697.9GB: vmlinuz
 697.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by arrange on 2009-10-04
You want to delete the old Ubuntu 8.10 installation? 

First boot into Ubuntu (9.04!). Go to Terminal and open Nautilus```
gksudo nautilus
```Navigate to */boot/grub/* directory. Back up the *menu.lst* file (Ctrl + C, Ctrl + V) and open the original file in a text editor. Delete the old Ubuntu lines so that the file looks like this```
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
default		6

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
# kopt=root=UUID=1915a441-b915-404a-b6ad-56c43f81f909 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1915a441-b915-404a-b6ad-56c43f81f909

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
# defoptions=quiet splash vga=769

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
uuid		1915a441-b915-404a-b6ad-56c43f81f909
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=1915a441-b915-404a-b6ad-56c43f81f909 ro quiet splash vga=769 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		1915a441-b915-404a-b6ad-56c43f81f909
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=1915a441-b915-404a-b6ad-56c43f81f909 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		1915a441-b915-404a-b6ad-56c43f81f909
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1915a441-b915-404a-b6ad-56c43f81f909 ro quiet splash vga=769 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		1915a441-b915-404a-b6ad-56c43f81f909
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1915a441-b915-404a-b6ad-56c43f81f909 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		1915a441-b915-404a-b6ad-56c43f81f909
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```Reboot. If you are able to succesfully boot into Windows and Ubuntu 9.04 you can remove the old *sda5* partition.

---

### Post by Ferguson9 on 2009-10-04
Excellent. 8.10 has now been removed from startup. Final thing, how do I remove the old sda5 partition? (Last thing I promise!)

---

### Post by arrange on 2009-10-04
Never say die :P

You can do it in **GParted** aka **Partition editor**. IMO you can delete the partitions *sda5*-*sda7*, because your 9.04 uses *sda9* as swap. But - be careful :) DON'T delete *sda1* (Win), *sda2* (extended), *sda8* (Ubu 9.04), *sda9* (swap).

This way you can extend Ubu 9.04 to its full volume! (over former *sda5*-*sda7* partitions) Numbering (i.e. *sd?*) could change, but that's OK since you're using UUID for partition identification.

Good luck :)

---

### Post by Ferguson9 on 2009-10-04
> **arrange said:**
> Never say die :P

You can do it in **GParted** aka **Partition editor**. IMO you can delete the partitions *sda5*-*sda7*, because your 9.04 uses *sda9* as swap. But - be careful :) DON'T delete *sda1* (Win), *sda2* (extended), *sda8* (Ubu 9.04), *sda9* (swap).

This way you can extend Ubu 9.04 to its full volume! (over former *sda5*-*sda7* partitions) Numbering (i.e. *sd?*) could change, but that's OK since you're using UUID for partition identification.

Good luck :)

I cant seem to delete 5-7?! I get an error message saying...

Unable to delete /dev/sda5!
PLease unmount any logical partitions having a number higher than 5.

What does that mean?!

---

### Post by arrange on 2009-10-04
You have to do it from a LiveCD or such because you need to unmount both the extended partition and the partitions you want to remove.

But - to be able to unmount the extended partition you have to unmount sda8-9 too, because they lie within the borders of the extended partition! :)

I hope you've backed up any important data you may have!

---

### Post by Ferguson9 on 2009-10-04
> **arrange said:**
> You have to do it from a LiveCD or such because you need to unmount both the extended partition and the partitions you want to remove.

But - to be able to unmount the extended partition you have to unmount sda8-9 too, because they lie within the borders of the extended partition! :)

I hope you've backed up any important data you may have!

This sounds too scary to be honest!! Is there a way I can completely remove everything except Vista and just extend my hard drive so that it contains Vista only? Dont think im ready for Linux right now!

---

### Post by arrange on 2009-10-04
Well, repartitioning is always a serious business, and shouldn't be done when you don't know what you're doing I think.

If you're scared, just leave it as it is (I use an old Ubuntu for backup and reference too) and you can do it later when you feel more confident.

---

### Post by Ferguson9 on 2009-10-04
> **arrange said:**
> Well, repartitioning is always a serious business, and shouldn't be done when you don't know what you're doing I think.

If you're scared, just leave it as it is (I use an old Ubuntu for backup and reference too) and you can do it later when you feel more confident.

Yeah I understand that but I think I would just like my whole hard drive to hold Vista as I am getting WIndows 7 when it comes out. Therefore, if possible would you be able to give me a step by step guide to remove all unnecessary partitions, leaving me with just Vista on my 750gb hard drive? Surely it cant be THAT hard if im removing them all except one?! Or am I underestimating it a bit?

---

### Post by arrange on 2009-10-04
LiveCD - Partition Editor - remove all partitions but Vista - extend sda1 to full. Important: fix MBR with the original Vista CD (as you have Grub there). But don't know how that's done, possibly google it.

---

### Post by Ferguson9 on 2009-10-04
> **arrange said:**
> LiveCD - Partition Editor - remove all partitions but Vista - extend sda1 to full. Important: fix MBR with the original Vista CD (as you have Grub there). But don't know how that's done, possibly google it.

Done it :)

Thanks a lot for all your help, appreciated.

---

