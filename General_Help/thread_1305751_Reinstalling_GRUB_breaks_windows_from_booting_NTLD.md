---
title: "Reinstalling GRUB breaks windows from booting NTLDR is missing"
date: 2009-10-30
forum: General Help
---

### Post by domokunrox on 2009-10-30
Solution found!

Problem: Upon the attempt to boot windows it simply prompts me that NTLDR is missing ctrl+alt+delete to restart.

Here is my boot info script. As you can see Windows is marked entirely wrong as shown in red. 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21432143

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b9b3b9b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63        16,064        16,002   7 HPFS/NTFS
/dev/sdb2              16,065   488,392,064   488,376,000  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="565CB14E5CB1299F" TYPE="ntfs" 
/dev/sdb1: UUID="568C126A8C124541" TYPE="ntfs" 
/dev/sdb2: UUID="31e43d63-289c-473e-b451-29de4aa0a3e2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/domokun/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=domokun)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=31e43d63-289c-473e-b451-29de4aa0a3e2

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
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

#title		Ubuntu 9.04, kernel 2.6.28-13-generic
#uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
#kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-13-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
#uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
#kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
#initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

#title		Ubuntu 9.04, kernel 2.6.27-11-generic
#uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
#uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
#initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		[COLOR="Red"](hd1,0)[/COLOR]
savedefault
makeactive
[COLOR="Red"]map		(hd0) (hd1)
map		(hd1) (hd0)[/COLOR]
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 176.5GB: boot/grub/menu.lst
 176.5GB: boot/grub/stage2
 176.5GB: boot/initrd.img-2.6.27-11-generic
 176.6GB: boot/initrd.img-2.6.28-11-generic
 176.5GB: boot/initrd.img-2.6.28-13-generic
 176.5GB: boot/initrd.img-2.6.28-14-generic
 176.5GB: boot/initrd.img-2.6.28-15-generic
 176.5GB: boot/initrd.img-2.6.28-16-generic
 176.5GB: boot/vmlinuz-2.6.27-11-generic
 176.5GB: boot/vmlinuz-2.6.28-11-generic
 176.5GB: boot/vmlinuz-2.6.28-13-generic
 176.5GB: boot/vmlinuz-2.6.28-14-generic
 176.5GB: boot/vmlinuz-2.6.28-15-generic
 176.5GB: boot/vmlinuz-2.6.28-16-generic
 176.5GB: initrd.img
 176.5GB: initrd.img.old
 176.5GB: vmlinuz
 176.5GB: vmlinuz.old
```

Now here is the state and situation as given to me by performing

```
sudo fdisk -l
```

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21432143

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b9b3b9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           1        8001    7  HPFS/NTFS
/dev/sdb2               2       30401   244188000   83  Linux

```

What happened is that I reinstalled Grub after reinstalling windows xp and well Grub overwrote all the windows boot files, so how was I going to get those files back and windows working again? Heres how. [COLOR="Red"]First download the attachment of the windows xp boot files to your ubuntu Desktop[/COLOR] then run this in your terminal exactly as it is typed. **[COLOR="Red"]Do NOT miss the capital letters. [/COLOR]**

```
sudo mount /dev/sda1 /mnt
cd ~/Desktop
unzip WinXP_boot_files1.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```

Then once you done that do

```
gksudo gedit /boot/grub/menu.lst
```

go down to the bottom and edit the last section which should look something like this

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd[COLOR="Red"]?,?[/COLOR])
savedefault
makeactive[COLOR="Red"]
map		(hd0) (hd1)
map		(hd1) (hd0)[/COLOR]
chainloader	+1
```

Go ahead and edit the red to your particular configuration. I just went ahead and deleted the "map" sections out of there and saved it.

Then go ahead and run

```
sudo update-grub
```

Restart the computer and it should start your windows partition.

I dunno how to get this to work with Windows 7. [COLOR="Red"]This is specifically for Windows XP and for use with GRUB[/COLOR] not GRUB2

---

### Post by pro003 on 2009-10-30
get a supergrub cd, is about 4mb, burn it boot it and try to automatically fix your boot linux / windows problem, easy to follow... as for other methods you'll have to more experienced linux user...

---

### Post by domokunrox on 2009-10-30
I'm pretty good with the terminal. So, don't strike that out just yet.

Link to Supergrub CD if you don't mind?

---

### Post by kelvin spratt on 2009-10-30
Use this link if you are having problems with 9.10 [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
Also use these commands as grub2 is very much different from the old grub?
[B]sudo apt-get install os-prober 
sudo os-prober 
sudo update-grub

[/B]

---

### Post by domokunrox on 2009-10-30
no, those commands still work for grub

I did sudo os-prober and got this

```
/dev/sdb1:Microsoft Windows XP Professional:Windows:chain

```

---

### Post by gedas0220 on 2009-10-30
just installed 9.10 and i have similar problems when I try to boot windows 7 from Grub 2 menu my pc just restarts

sudo os-prober answer:
/dev/sdb3:Windows 7 (loader):Windows:chain

---

### Post by domokunrox on 2009-10-30
For the record, I'm not on 9.10.

I'm on 9.04

Edit: 

Here, let me suggest that something happened to the UUID of the windows partition. If this was the case, how do I go about fixing that?

Btw is this supposed to be there? Also, I've been trying to edit a combination of the blue highlight to see if it changes anything.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd[COLOR="Blue"]1,1[/COLOR])
savedefault
makeactive
[COLOR="Red"]map		(hd0) (hd1)
map		(hd1) (hd0)[/COLOR]
chainloader	+1
```

---

### Post by domokunrox on 2009-10-30
I think my problem is this

> 
OK, your Windows partition is missing its boot files, so what might have happened is Windows originally put its boot files on the sdb drive, but then you installed Ubuntu and used that entire drive (and thus unintentionally deleted the Windows boot files). Anyway, to fix the problem, how about downloading the attached "WinXP_boot_files1.zip" to your Ubuntu desktop and do:
Code:

sudo mount /dev/sda1 /mnt
[COLOR="Blue"]cd ~/Desktop[/COLOR]
unzip WinXP_boot_files1.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt

Also, make sure you are using your original Grub entry to boot Windows:
Code:

title		Windows XP Pro SP2
root		(hd0,0)
makeactive
chainloader	+1



However, i can't get the blue command to work out for me.

---

### Post by Mi*6d@# on 2009-10-30
Have you tried updating grub config (**sudo update-grub**) after os-probe?

---

### Post by domokunrox on 2009-10-30
Ha! Fixed it!

my newbie self forgot to capitalize the D!

Here, I'll get the solution up for everyone else in the original post

---

