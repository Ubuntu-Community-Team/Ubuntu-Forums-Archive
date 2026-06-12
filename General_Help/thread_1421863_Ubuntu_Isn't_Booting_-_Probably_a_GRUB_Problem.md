---
title: "Ubuntu Isn't Booting - Probably a GRUB Problem"
date: 2010-03-04
forum: General Help
---

### Post by Bradj47 on 2010-03-04
It all started when I tried installing Ubuntu on my flash drive. I chose to format and install to sdc (my flash drive) theoretically leaving sda (my main hard drive) untouched. Of course when I try booting from my flash drive it tells me **BOOT ERROR. INSERT SYSTEM DISK AND PRESS ENTER. ** I decide to give up on it for the day and start Ubuntu from sda. It doesn't give me an error. It just gives me a GRUB recovery prompt. ( **grub recovery> ** ). I boot from the live cd and check my **/boot/grub/menu.lst** file. It seems normal. I don't know what happened. My guess would be that GRUB was installed on sda instead of my flash drive but that doesn't make sense because wouldn't it just give me a regular GRUB menu? What could have gone wrong? 

The Ubuntu installed on sda is version 9.04. The Ubuntu I attempted to install on my flash drive is version 9.10. The probably completely irrelevant OS installed on sdb is Solaris 10 5/09. Thought I'd mention it just in case it is relevant. 

Thanks in advance, 
Brad

---

### Post by oldfred on 2010-03-04
Just to be sure what is where, download & run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by Bradj47 on 2010-03-14
> **oldfred said:**
> Just to be sure what is where, download & run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

Sorry it took me so long to respond. Here is the contents of the file that the script produced: 
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=66e5e0a6-b7d6-43eb-99e0-5b057b89842d)/boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.95 is installed in the boot sector of sdb1 and 
                       looks at sector 16115 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000586a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   151,043,129   151,043,067  83 Linux
/dev/sda2         151,043,130   156,296,384     5,253,255   5 Extended
/dev/sda5         151,043,193   156,296,384     5,253,192  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 10.3 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders, total 20044080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x505d505c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,065    20,033,054    20,016,990  bf Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2c532ecb-2908-49be-95d5-17de21ce2288   ext3                                     
/dev/sda5        750d878c-e5ce-4587-a94b-ea4324da98b3   swap                                     
/dev/sdb5                                               zfs                                      
/dev/sdb                                                ufs                                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/2c532ecb-2908-49be-95d5-17de21ce2288 ext3       (rw,nosuid,nodev,uhelper=devkit)


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
#timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
# color blue/black cyan/green

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password topsecret

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
# kopt=root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2c532ecb-2908-49be-95d5-17de21ce2288

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
# defoptions=quiet splash vga=798

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		2c532ecb-2908-49be-95d5-17de21ce2288
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		2c532ecb-2908-49be-95d5-17de21ce2288
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

# title		Ubuntu 9.04, kernel 2.6.28-13-generic
# uuid		2c532ecb-2908-49be-95d5-17de21ce2288
# kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro quiet splash 
# initrd		/boot/initrd.img-2.6.28-13-generic
# quiet

# title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
# uuid		2c532ecb-2908-49be-95d5-17de21ce2288
# kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro  single
# initrd		/boot/initrd.img-2.6.28-13-generic

# title		Ubuntu 9.04, kernel 2.6.28-11-generic
# uuid		2c532ecb-2908-49be-95d5-17de21ce2288
# kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro quiet splash 
# initrd		/boot/initrd.img-2.6.28-11-generic
# quiet

# title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
# uuid		2c532ecb-2908-49be-95d5-17de21ce2288
# kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro  single
# initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		2c532ecb-2908-49be-95d5-17de21ce2288
kernel		/boot/memtest86+.bin
quiet

title		Solaris 10 5/09
root (hd1,0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
# Splash image
splashimage (hd0,1)/grub/images/your_splash.xpm.gz

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
UUID=2c532ecb-2908-49be-95d5-17de21ce2288 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=750d878c-e5ce-4587-a94b-ea4324da98b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto            0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

=================== sda1: Location of files loaded by Grub: ===================


  27.4GB: boot/grub/menu.lst
  12.3GB: boot/grub/stage2
  26.3GB: boot/initrd.img-2.6.28-11-generic
  30.3GB: boot/initrd.img-2.6.28-13-generic
  16.7GB: boot/initrd.img-2.6.28-14-generic
  18.8GB: boot/initrd.img-2.6.28-15-generic
  26.9GB: boot/initrd.img-2.6.28-16-generic
  12.3GB: boot/vmlinuz-2.6.28-11-generic
  26.3GB: boot/vmlinuz-2.6.28-13-generic
  23.3GB: boot/vmlinuz-2.6.28-14-generic
  13.0GB: boot/vmlinuz-2.6.28-15-generic
  14.0GB: boot/vmlinuz-2.6.28-16-generic
  26.9GB: initrd.img
  18.8GB: initrd.img.old
  14.0GB: vmlinuz
  13.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 04 4d 33 2e 30 fa fc  be 00 7c bf 00 06 8c c8  |..M3.0....|.....|
00000010  8e d0 89 f4 8e c0 8e d8  51 b9 00 01 f3 a5 59 e9  |........Q.....Y.|
00000020  00 8a fb b4 02 cd 16 24  03 3c 03 75 05 c6 06 61  |.......$.<.u...a|
00000030  07 01 bb be 07 b9 04 00  80 3f 80 74 0e 83 c3 10  |.........?.t....|
00000040  e2 f6 bd 75 07 b9 13 00  e9 e6 00 b4 00 cd 13 53  |...u...........S|
00000050  b4 41 bb aa 55 b9 00 00  cd 13 72 3f 81 fb 55 aa  |.A..U.....r?..U.|
00000060  75 39 f7 c1 01 00 74 33  bd a4 07 b9 03 00 e8 c8  |u9....t3........|
00000070  00 5b 53 b9 05 00 66 6a  00 66 ff 77 08 66 ff 36  |.[S...fj.f.w.f.6|
00000080  5c 07 6a 01 6a 10 b4 42  89 e6 cd 13 9f 83 c4 10  |\.j.j..B........|
00000090  9e 73 7b b4 00 cd 13 e2  dd eb 6b bd a7 07 b9 03  |.s{.......k.....|
000000a0  00 e8 95 00 5b 53 8a 16  60 07 b4 08 cd 13 73 08  |....[S..`.....s.|
000000b0  bd 62 07 b9 13 00 eb 79  88 c8 24 3f a2 59 07 fe  |.b.....y..$?.Y..|
000000c0  c6 f6 e6 a3 5a 07 8b 47  08 8b 57 0a f7 36 5a 07  |....Z..G..W..6Z.|
000000d0  89 c3 89 d0 f6 36 59 07  fe c4 30 c9 88 fd c1 e9  |.....6Y...0.....|
000000e0  02 80 e1 c0 08 e1 88 dd  88 c6 8a 16 60 07 c4 1e  |............`...|
000000f0  5c 07 be 05 00 b8 01 02  cd 13 73 12 b4 00 cd 13  |\.........s.....|
00000100  4e 83 fe 00 75 ef bd 88  07 b9 0e 00 eb 23 bb 00  |N...u........#..|
00000110  7c 81 bf fe 01 55 aa 74  08 bd 96 07 b9 0b 00 eb  ||....U.t........|
00000120  10 8a 16 60 07 5e 66 ff  16 5c 07 bd a1 07 b9 03  |...`.^f..\......|
00000130  00 bb 4f 00 e8 0c 00 cd  18 80 3e 61 07 00 74 18  |..O.......>a..t.|
00000140  bb 1f 00 60 b8 01 13 ba  00 17 cd 10 b0 07 b9 01  |...`............|
00000150  00 cd 10 b4 00 cd 16 61  c3 00 00 00 00 7c 00 00  |.......a.....|..|
00000160  80 00 43 61 6e 27 74 20  72 65 61 64 20 67 65 6f  |..Can't read geo|
00000170  6d 65 74 72 79 4e 6f 20  61 63 74 69 76 65 20 70  |metryNo active p|
00000180  61 72 74 69 74 69 6f 6e  43 61 6e 27 74 20 72 65  |artitionCan't re|
00000190  61 64 20 50 42 52 42 61  64 20 50 42 52 20 73 69  |ad PBRBad PBR si|
000001a0  67 21 21 21 4c 42 41 43  48 53 00 00 00 00 00 00  |g!!!LBACHS......|
000001b0  00 00 00 00 00 00 00 00  5c 50 5d 50 00 00 80 00  |........\P]P....|
000001c0  01 01 bf fe ff ff c1 3e  00 00 5e 6f 31 01 00 00  |.......>..^o1...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

But I ran this while running an Ubuntu live CD. Will that change the results?

---

### Post by Bradj47 on 2010-03-14
Bump.

---

### Post by oldfred on 2010-03-14
It looks like you did not have sdc plugged in when you ran the script. If you plug sdc back in can you boot? If so reinstall grub2 to sdc first.

You had sda set as the boot drive when you installed to sdc and therefore grub2 installed to the boot drive - sda. There is an advanced button (when you finalize partitions) if you want to choose the boot drive or you can set the boot drive in BIOS before you install so grub will automatically be installed to that drive.

If you want to boot 9.04 you will have to reinstall grub legacy to sda. You may be able to use a 9.10 liveCD to install grub 0.97 legacy but Karmic it is set up for grub2. 

Follow the directions for 9.04 or before:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,1)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd0,1)
setup (hd0)

I do not think the script is set up to see the Solaris install (unique formats) and I do not know anything about that system.

---

### Post by Bradj47 on 2010-03-15
> **oldfred said:**
> It looks like you did not have sdc plugged in when you ran the script. If you plug sdc back in can you boot? If so reinstall grub2 to sdc first. 

No. If I plug sdc back in and put sda first in the boot order in the bios, it gives me a GRUB recovery prompt. If I put sdc first in the boot order in the bios, it tells me to put in system disk and press enter to continue.

> **oldfred said:**
> You had sda set as the boot drive when you installed to sdc and therefore grub2 installed to the boot drive - sda. There is an advanced button (when you finalize partitions) if you want to choose the boot drive or you can set the boot drive in BIOS before you install so grub will automatically be installed to that drive.

If you want to boot 9.04 you will have to reinstall grub legacy to sda. You may be able to use a 9.10 liveCD to install grub 0.97 legacy but Karmic it is set up for grub2. 

Follow the directions for 9.04 or before:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,1)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd0,1)
setup (hd0)

I do not think the script is set up to see the Solaris install (unique formats) and I do not know anything about that system.

Thanks, will do. I'll post back here if I run into any problems.

---

