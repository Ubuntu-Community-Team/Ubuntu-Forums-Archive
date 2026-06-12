---
title: "Can't load windows vista"
date: 2009-09-14
forum: General Help
---

### Post by jobbesat on 2009-09-14
After having some problems with hard disks, I finally have my ubuntu box up and running, but it doesn't load windows vista any more, spitting > error 13 invalid or unsupported executable format.

I have 2 hd, I'm posting my fdisk and menu.lst:
```
Disco /dev/sda: 250.0 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x83adbacc

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648        4255     4883760   82  Linux swap / Solaris
/dev/sda3            4256       30401   210017745   83  Linux

Disco /dev/sdb: 500.1 GB, 500107862016 byte
255 testine, 63 settori/tracce, 60801 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x8d399bc0

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS
```

Here's my menu.lst
```
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
timeout		60

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,0)/boot/grub/splashimages/Mac4Lin_1.0_GRUB3.xpm.gz

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
# kopt=root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=splash vga=792

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro splash vga=792 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro splash vga=792 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro splash vga=792 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro splash vga=792 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
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
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

I tried to modify menu.lst at the end changing from
> root		(hd0,0)
to
> root		(hd1,0)
but no luck :(

Thanks a lot in advance for any help!

---

### Post by jobbesat on 2009-09-18
Up

---

### Post by rocket16 on 2009-09-18
What is seen when you try to enter Vista?

---

### Post by rocket16 on 2009-09-18
Oh Sorry. I did not see the line "error 13 invalid or unsupported executable format".

---

### Post by rocket16 on 2009-09-18
I think your BCD.exe (bootloader in Vista) has encounted a potential damage. Just repair the Vista Bootloader. Follow the link [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD). There, the recovery is stated.

---

### Post by bumanie on 2009-09-18
Windows does not like being on the second hard drive. To overcome this, map commands are added to the vista part of the menu, which usually tricks vista into believing it is on the first hard drive.

Open your boot/grub/menu.lst with this command > gksudo gedit boot/grub/menu.lstGo to this part of the menu and add the bit in red
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
[COLOR="Red"]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader	+1

Sometimes it is necessary to have root[COLOR="Red"]noverify[/COLOR] rather than just root, but try the map commands first. Save the file and reboot and see if it works.

---

### Post by jobbesat on 2009-09-18
Already tried with:
map (hd0) (hd1)
map (hd1) (hd0)

but it doesn't work.
It splits:
> Starting up...
NTLDR missing

I post the results of Boot Info Script:
> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 250.0 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri, totale 488397168 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x83adbacc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    58,589,054    58,588,992  83 Linux
/dev/sda2          58,589,055    68,356,574     9,767,520  82 Linux swap / Solaris
/dev/sda3          68,356,575   488,392,064   420,035,490  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 500.1 GB, 500107862016 byte
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x8d399bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="a182a19a-01e8-482b-8c24-3115814e430a" 
/dev/sda3: UUID="7e42c6b9-d192-4caa-a088-0dfb1a5c0608" TYPE="ext3" 
/dev/sdb1: UUID="74B0D039B0D00410" LABEL="Elements" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /home type ext3 (rw,relatime)
none on /proc/bus/usb type usbfs (rw,devgid=126,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
gvfs-fuse-daemon on /home/jobbe/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jobbe)
/dev/sdb1 on /media/Elements_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=512)


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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		60

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,0)/boot/grub/splashimages/Mac4Lin_1.0_GRUB3.xpm.gz

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
# kopt=root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=splash vga=792

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro splash vga=792 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro splash vga=792 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro splash vga=792 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro splash vga=792 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
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
root		(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5e6f6bf9-8bda-414f-ae17-6559fe6b5e3f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=7e42c6b9-d192-4caa-a088-0dfb1a5c0608 /home           ext3    relatime        0       2
# /dev/sdb2
UUID=a182a19a-01e8-482b-8c24-3115814e430a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=126,devmode=664 0 0

=================== sda1: Location of files loaded by Grub: ===================


  24.8GB: boot/grub/menu.lst
  24.8GB: boot/grub/stage2
  24.9GB: boot/initrd.img-2.6.27-14-generic
  24.8GB: boot/initrd.img-2.6.28-11-generic
  24.8GB: boot/initrd.img-2.6.28-12-generic
  24.9GB: boot/initrd.img-2.6.28-13-generic
  25.0GB: boot/initrd.img-2.6.28-14-generic
  24.8GB: boot/initrd.img-2.6.28-15-generic
  24.9GB: boot/vmlinuz-2.6.27-14-generic
  24.9GB: boot/vmlinuz-2.6.28-11-generic
  24.9GB: boot/vmlinuz-2.6.28-12-generic
  24.8GB: boot/vmlinuz-2.6.28-13-generic
  24.9GB: boot/vmlinuz-2.6.28-14-generic
  25.0GB: boot/vmlinuz-2.6.28-15-generic
   7.3GB: grub/stage2
  24.8GB: initrd.img
  25.0GB: initrd.img.old
  25.0GB: vmlinuz
  24.9GB: vmlinuz.old

I'm really sorry to bother :(
Thanks for your time and help.

---

### Post by jobbesat on 2009-09-22
Nothing to do?

---

### Post by Tipped OuT on 2009-09-22
Boot up into a Windows /Vista/7 installation disk. Go into recovery mode.

Enter "**fixmbr**".

Done.

---

