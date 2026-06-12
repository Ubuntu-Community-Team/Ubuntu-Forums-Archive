---
title: "First Grub, then a second boot screen! How do I delete it?"
date: 2010-01-06
forum: General Help
---

### Post by Blue1 on 2010-01-06
As the topic state I have double boot screens...

First time a installed Ubuntu I tried to use the simple way by booting from the DVD and click install on the desktop. Not very surprisingly, this failed...
It did however install a boot screen giving me two boot options; Win XP and Ubuntu,

Since this failed I did install Ubuntu the other way from the DVD and this was successful.
It now installed Grub so I can chose OS. The first boot screen is however still there. Every time I boot I need to select Ubuntu twice, first in Grub and then again in the second boot screen.

How do I delete this second boot screen??

Regards

---

### Post by Leppie on 2010-01-06
what does the second boot screen look like?

could you run this command and then post the generated RESULTS.txt:
```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.44/boot_info_script044.sh/download' \
&& chmod 755 boot_info_script044.sh \
&& sudo ./boot_info_script044.sh
```

---

### Post by presence1960 on 2010-01-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Need that info because you gave not enough info to even begin diagnosing what the problem may be.

---

### Post by Blue1 on 2010-01-07
Here's the Result file. Followed the first instructions since I've lost my boot CD.

The second boot screen is just a black screen with two options and some text. Also a tim out counter.

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________
sudo ./boot_info_script044.sh
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -sudo ./boot_info_script044.sh
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100,0 GB, 100030242816 byte
255 huvuden, 63 sektorer/spår, 12161 cylindrar, totalt 195371568 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Diskidentifierare: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    45,057,599    45,057,537   7 HPFS/NTFS
/dev/sda2          45,057,662   195,366,464   150,308,803   f W95 Ext d (LBA)
/dev/sda5          45,057,663   174,418,245   129,360,583   7 HPFS/NTFS
/dev/sda6         174,433,833   194,370,434    19,936,602  83 Linux
/dev/sda7         194,370,498   195,366,464       995,967  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="90948E25948E0E42" TYPE="ntfs" 
sda5: UUID="DA1C5D941C5D6C8F" TYPE="ntfs" 
sda6: UUID="1f4a8d43-b55e-4545-8a81-288fb4761109" TYPE="ext3" 
sda7: UUID="9df4b555-0745-4305-bfc6-cf5a3b1de1d3" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/carl/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=carl)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sda6/boot/grub/menu.lst: ===========================

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
default        8

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
## Splash image!
splashimage=/boot/grub/splash.xpm.gz

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
# kopt=root=UUID=1f4a8d43-b55e-4545-8a81-288fb4761109 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1f4a8d43-b55e-4545-8a81-288fb4761109

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        1f4a8d43-b55e-4545-8a81-288fb4761109
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=1f4a8d43-b55e-4545-8a81-288fb4761109 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        1f4a8d43-b55e-4545-8a81-288fb4761109
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=1f4a8d43-b55e-4545-8a81-288fb4761109 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        1f4a8d43-b55e-4545-8a81-288fb4761109
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=1f4a8d43-b55e-4545-8a81-288fb4761109 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-genericsudo ./boot_info_script044.sh
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        1f4a8d43-b55e-4545-8a81-288fb4761109
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=1f4a8d43-b55e-4545-8a81-288fb4761109 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-14-generic
uuid        1f4a8d43-b55e-4545-8a81-288fb4761109
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=1f4a8d43-b55e-4545-8a81-288fb4761109 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid        1f4a8d43-b55e-4545-8a81-288fb4761109
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=1f4a8d43-b55e-4545-8a81-288fb4761109 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.10, memtest86+
uuid        1f4a8d43-b55e-4545-8a81-288fb4761109
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



=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=1f4a8d43-b55e-4545-8a81-288fb4761109 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9df4b555-0745-4305-bfc6-cf5a3b1de1d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  89.3GB: boot/grub/menu.lst
  89.3GB: boot/grub/stage2
  89.3GB: boot/initrd.img-2.6.28-14-generic
  89.3GB: boot/initrd.img-2.6.31-14-generic
  89.3GB: boot/initrd.img-2.6.31-16-generic
  89.3GB: boot/vmlinuz-2.6.28-14-generic
  89.3GB: boot/vmlinuz-2.6.31-14-generic
  89.3GB: boot/vmlinuz-2.6.31-16-generic
  89.3GB: initrd.img
  89.3GB: initrd.img.old
  89.3GB: vmlinuz
  89.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc 
```

---

### Post by Leppie on 2010-01-07
the first menu is grub, the second menu is the windows menu (with the two options "Microsoft Windows XP" and "Ubuntu")?

to modify the windows boot menu, boot into xp and follow the [ms instructions]("http://support.microsoft.com/kb/289022"):
> **Edit the Boot.ini File**
To view and edit the Boot.ini file:
Right-click My Computer, and then click Properties.
-or-
Click Start, click Run, type sysdm.cpl, and then click OK.
On the Advanced tab, click Settings under Startup and Recovery.
Under System Startup, click Edit.

remove the line:
```
C:\wubildr.mbr = "Ubuntu" 
```
save and exit.

---

