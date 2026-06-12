---
title: "Ubuntu - Partition Issue"
date: 2011-04-02
forum: General Help
---

### Post by jag2010 on 2011-04-02
Hello,

I'm fairly new to Ubuntu and I'd like some help.  I've got a Samsung R710 laptop currently running Ubuntu 10.04.  There's only one main partition, then the swap and extended.  My question is how do I spit the partition which currently houses Ubuntu and all my other files?  There's plenty of space, I just want to create a partition to install Win XP Pro SP3 on.  I've Googled with limited success.  GParted won't let me change the active partition because, I assume, it's currently in use running programs and stuff.  Help!

Thanks in advance.

---

### Post by Anonymous is Incognito on 2011-04-02
Hi and welcome to the forums,

> **jag2010 said:**
> I assume, it's currently in use running programs and stuff.

You are correct, try to run GParted from the Ubuntu live CD.

Feel free to post any other questions if you have them.

---

### Post by jag2010 on 2011-04-02
Ahhh, I don't know why I didn't think of that.  Thanks for the advice.

---

### Post by Anonymous is Incognito on 2011-04-02
You're welcome.

Please don't forget to mark this thread as solved ;-)

---

### Post by jag2010 on 2011-04-03
Ok, right.  I've created the partition and installed XP on it.  Now when I try and start the computer it says:

"Disk error
Press any key to restart"

When I do try and restart it just comes up with this again and again.

Any ideas?

---

### Post by TomAnkcorn on 2011-04-03
Its probably a grub issue
(installing windows after ubuntu usually messes with stuff)
if that is the problem then you need to create a grup and restore grup with it
[http://www.supergrubdisk.org/2011/03/07/rescatux-0-25-released/]("http://www.supergrubdisk.org/2011/03/07/rescatux-0-25-released/")
if its not grub im not sure what the problem could be

---

### Post by jag2010 on 2011-04-03
Ok, managed to restored grub to the MBR, but because it was pre-Win install it just loads straight back to Ubuntu.  Any ideas how I get the option to loads Windows on the list?

---

### Post by oldfred on 2011-04-03
Did you install windows to a primary partition? That it did not boot on its own is not a good sign.

This should find windows, if it is working, but if it did not boot before it may not be working. :

sudo update-grub

If that does not work post boot info script.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by jag2010 on 2011-04-03
I've managed to make the partition with Windows on it work and Windows load, but I can't get Grub to give me the option between Windows and Ubuntu as the menu.lst doesn't include Windows.  

Contents of results.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   318,070,934   318,070,872  83 Linux
/dev/sda2         318,070,935   607,016,024   288,945,090   7 HPFS/NTFS
/dev/sda3         607,016,025   625,137,344    18,121,320   5 Extended
/dev/sda5         607,016,088   625,137,344    18,121,257  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        f5f4dae2-2fea-4067-a00d-ad346bb56ea2   ext3                                     
/dev/sda2        722802D32802966F                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        d81d91a4-560f-40b4-95f5-e45f6ae0fd2e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


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
# kopt=root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f5f4dae2-2fea-4067-a00d-ad346bb56ea2

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

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-30-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.32-30-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-28-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.32-28-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-26-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-26-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-26-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.32-26-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-25-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-24-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-23-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-22-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-20-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-19-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-19-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-17-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-16-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-16-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-15-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-15-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-14-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.28-11-generic
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.04.2 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04.2 LTS, memtest86+
uuid		f5f4dae2-2fea-4067-a00d-ad346bb56ea2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f5f4dae2-2fea-4067-a00d-ad346bb56ea2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d81d91a4-560f-40b4-95f5-e45f6ae0fd2e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  96.9GB: boot/grub/menu.lst
  96.8GB: boot/grub/stage2
  96.8GB: boot/initrd.img-2.6.28-11-generic
  96.8GB: boot/initrd.img-2.6.31-14-generic
  96.7GB: boot/initrd.img-2.6.31-15-generic
  96.8GB: boot/initrd.img-2.6.31-16-generic
  96.8GB: boot/initrd.img-2.6.31-17-generic
  96.8GB: boot/initrd.img-2.6.31-19-generic
  19.3GB: boot/initrd.img-2.6.31-20-generic
  96.9GB: boot/initrd.img-2.6.32-22-generic
  96.9GB: boot/initrd.img-2.6.32-23-generic
  96.9GB: boot/initrd.img-2.6.32-24-generic
  96.9GB: boot/initrd.img-2.6.32-25-generic
  96.9GB: boot/initrd.img-2.6.32-26-generic
  36.1GB: boot/initrd.img-2.6.32-28-generic
  30.2GB: boot/initrd.img-2.6.32-30-generic
  96.7GB: boot/vmlinuz-2.6.28-11-generic
  96.7GB: boot/vmlinuz-2.6.31-14-generic
  96.8GB: boot/vmlinuz-2.6.31-15-generic
  96.8GB: boot/vmlinuz-2.6.31-16-generic
  96.8GB: boot/vmlinuz-2.6.31-17-generic
  96.8GB: boot/vmlinuz-2.6.31-19-generic
  96.8GB: boot/vmlinuz-2.6.31-20-generic
  96.9GB: boot/vmlinuz-2.6.32-22-generic
  96.8GB: boot/vmlinuz-2.6.32-23-generic
  96.9GB: boot/vmlinuz-2.6.32-24-generic
  96.9GB: boot/vmlinuz-2.6.32-25-generic
  96.9GB: boot/vmlinuz-2.6.32-26-generic
  34.9GB: boot/vmlinuz-2.6.32-28-generic
  23.1GB: boot/vmlinuz-2.6.32-30-generic
  30.2GB: initrd.img
  36.1GB: initrd.img.old
  23.1GB: vmlinuz
  34.9GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by oldfred on 2011-04-03
With old grub legacy we often had to add windows boot stanzas as it would not find it. Especially with win7.

You also have  a lot of kernels, note that the grub menu has a box and if full you may have to scroll down to find an entry at the bottom. There is a little tiny arrow on the right bottom of the menu if there are more entries.

Your install is in sda2, and with old grub legacy's nomenclature that is (hd0,1)

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
rootnoverify (hd0,1)
savedefault
chainloader +1

```

Houseclean kernels.
Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Note sure if some of the newer gui tools still work with grub legacy. 

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

