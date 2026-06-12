---
title: "Multiboot system now giving GRUB error 17"
date: 2010-02-12
forum: General Help
---

### Post by wootcat on 2010-02-12
I have an XP/Ubunti multiboot system. The motherboard developed a bad capacitor, so I sent it off to be fixed. Just before it was sent back to me, the system tested fine. When I got it back and tried to boot it up the first time, I get a GRUB Error 17.

I'm no Ubuntu expert. Can someone please help me fix this problem?

Thanks!

---

### Post by louieb on 2010-02-12
Need a bit of information. 

Where do you get the error? Before or after the Grub menu?
Does XP load?
Does Ubuntu load?
What version of Ubuntu?  Does it boot using the live CD?
Is this a WUBI (inside window) install?

---

### Post by wootcat on 2010-02-13
No problem! It may be difficult to get all the info you might need, but I think I can answer all your questions at the moment...

1. I get the error before the GRUB menu. It says GRUB loading, then I get the Error 17 message. I never get a chance to select an OS to load.

2. Neither XP or Ubuntu load.

3. Ubuntu 9.x I believe. At least that was the Ubuntu Live CD I was able to find. I have not tried loading Ubuntu from the live CD, but I did also find a Super GRUB CD I had burned a while back, which I was able to use to boot from to bypass the error and get into XP.

4. No, it is not a WUBI. I have 2 hard drives in my box. Sadly, I can't remember ATM if I put XP and Ubuntu on separate partitions on the same HD, or if I put XP on one HD and Ubuntu on the other.

If it helps, when I originally got the computer back, the first boot gave me an Error 21 in the same location as I mentioned above in #1. I opened up the case and found one drive's SATA cable unplugged. I'm assuming it came loose during transit. After plugging it back in, that's when I started getting the Error 17's.

Thanks for your help!!!

---

### Post by lenoirrichelieu on 2010-02-13
For me it sounds like a mismatch between Grub on MBR and the files needed for booting. I mean by this you have installed Grub as bootloader on MBR but somehow (i cannot tell exactely because you didn't provide much info) the boot files aren't there where it is supposed to be.
 
Use the LiveCD to boot in Ubuntu and then try to follow the steps mentioned here
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
If you don't manage this then get the Windows XP CD, boot from CD, enter Recovery mode, and from command prompt try a *fixmbr. *This should recover the bootloader of XP and try reinstall Ubuntu after.

---

### Post by wootcat on 2010-02-13
Cool, thanks! 

I'll give those a try tomorrow!

---

### Post by oldfred on 2010-02-13
You probably plugged the SATA drives into different ports and the order is different. You may have had another boot loader on the drive that now boots first.

If you want to see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by louieb on 2010-02-13
> **oldfred said:**
> Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
+1 Good information it will help.

---

### Post by wootcat on 2010-02-13
lenoirrichelieu,

I'm a little further along now. I followed the instructions and now I get as far as GRUB's boot menu. If I select XP, I get Error 13: Invalid or unsupported executable format.

---

### Post by wootcat on 2010-02-13
Oldfred, Here's the info you requested.

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007aa7f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07c707c6

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   476,327,249   476,327,187  83 Linux
/dev/sdb2         476,327,250   488,392,064    12,064,815   5 Extended
/dev/sdb5         476,327,313   488,392,064    12,064,752  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        4890076890075C36                       ntfs                                     
/dev/sdb1        7abd61eb-f5eb-4b94-8cfc-972411eefde1   ext3                                     
/dev/sdb5        72e0e12b-12f2-4084-8f65-ff3dbb975c95   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=rod)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# kopt=root=UUID=7abd61eb-f5eb-4b94-8cfc-972411eefde1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7abd61eb-f5eb-4b94-8cfc-972411eefde1

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
uuid		7abd61eb-f5eb-4b94-8cfc-972411eefde1
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=7abd61eb-f5eb-4b94-8cfc-972411eefde1 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		7abd61eb-f5eb-4b94-8cfc-972411eefde1
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=7abd61eb-f5eb-4b94-8cfc-972411eefde1 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		7abd61eb-f5eb-4b94-8cfc-972411eefde1
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7abd61eb-f5eb-4b94-8cfc-972411eefde1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		7abd61eb-f5eb-4b94-8cfc-972411eefde1
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7abd61eb-f5eb-4b94-8cfc-972411eefde1 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, memtest86+
uuid		7abd61eb-f5eb-4b94-8cfc-972411eefde1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=7abd61eb-f5eb-4b94-8cfc-972411eefde1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=72e0e12b-12f2-4084-8f65-ff3dbb975c95 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  63.9GB: boot/grub/menu.lst
  63.9GB: boot/grub/stage2
  63.9GB: boot/initrd.img-2.6.28-15-generic
  63.9GB: boot/initrd.img-2.6.31-14-generic
  63.9GB: boot/vmlinuz-2.6.28-15-generic
  63.9GB: boot/vmlinuz-2.6.31-14-generic
  63.9GB: initrd.img
  63.9GB: initrd.img.old
  63.9GB: vmlinuz
  63.9GB: vmlinuz.old
```

---

### Post by louieb on 2010-02-13
Things look ok. Does Ubuntu boot now?
For XP edit /boot/grub/menu.list.
Press Alt+F2 to bring up the run dialog.
```
gksu gedit  /boot/grub/menu.lst 
```

go to the bottom and add this - reboot and try it. - boot order is how grub determines which drive is which. You 1st entry should work if the windows drive is 1st in the boot order. 
But it looks like the windows drive is now 2nd in the boot order. Since you can boot with Super Grub I believe this will work too. 

```

title Win XP using Map command
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      chainloader +1
      boot


```

---

### Post by wootcat on 2010-02-14
That worked! Thanks!

---

