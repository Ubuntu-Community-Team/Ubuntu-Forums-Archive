---
title: "Ubuntu and broken XP dual boot problem"
date: 2011-05-27
forum: General Help
---

### Post by sirLeonardo on 2011-05-27
Hi everybody!

I did some mess to my computer and now i can't repair it. Maybe someone will be nice enough to help me ;)

I've had dual boot Ubuntu and Windows XP, something got wrong with Ubuntu so I started "do things". I somehow (i can't even recall the scenario that drove me to this sad situation) ended up with a corrupted Windows XP on one of my partitions and nicely working Windows XP on the second one. After i copied important data from the corrupted one to the working one i decided to install Ubuntu (using wubi) on partition with corrupted Windows. After that i couldn't boot any system (no drives found or smthg like that was the message). So I installed Ubuntu (whithout even touching partition with XP cos I was hoping to set a dual boot later) and it works, but I can't boot my XP now. I was reading many topics, but it didn't help me :(

Here are some info (fdisk, sfdisk, parted):

```
marcin@marcin-laptop:~$ sudo fdisk -lu
[sudo] password for marcin: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cac5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16126   230500619   115242247    f  W95 Ext'd (LBA)
/dev/sda2       230502400   484491263   126994432   83  Linux
/dev/sda3   *   484491264   488394751     1951744   82  Linux swap / Solaris
/dev/sda5   *       16128   230500619   115242246    7  HPFS/NTFS

Disk /dev/dm-0: 1998 MB, 1998585856 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x600d58f8

Disk /dev/dm-0 doesn't contain a valid partition table
marcin@marcin-laptop:~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=    16126, size=230484494, Id= f
/dev/sda2 : start=230502400, size=253988864, Id=83
/dev/sda3 : start=484491264, size=  3903488, Id=82, bootable
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=    16128, size=230484492, Id= 7, bootable

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/dm-0: unrecognized partition table type
No partitions found
marcin@marcin-laptop:~$ sudo parted /dev/sda print
Model: ATA ST9250827AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      8257kB  118GB  118GB   extended               lba
 5      8258kB  118GB  118GB   logical   ntfs         boot
 2      118GB   248GB  130GB   primary   ext4
 3      248GB   250GB  1999MB  primary                boot

marcin@marcin-laptop:~$ 
```

What I get now is when I try boot Windows XP like that:
title           Windows XP
root            (hd0,4)
makeactive
chainloader +1

I get grub error:
error 12: Invalid Device Requested

Same if I change root to (hd0,0).
If I change root to rootonverify it just reboots.

Any help appreciated :)

Peace

---

### Post by Rubi1200 on 2011-05-28
Hi and welcome to the forums :-)

In order to get a better overview of what is going on please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by sirLeonardo on 2011-05-29
Hi :)

Thanks for Your reply. Your instructions seem like You think I can't boot my computer at all, so mby i wasn't clear enough: I can boot Ubuntu, but I can't boot Windows XP anymore (I would like to have dual boot). Here are the results of boot info script 055 (which I did run from my working Ubuntu, not from LiveCD):
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

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
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 415336704 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,126   230,500,619   230,484,494   f W95 Ext d (LBA)
/dev/sda5    *         16,128   230,500,619   230,484,492   7 HPFS/NTFS
/dev/sda2         230,502,400   484,491,263   253,988,864  83 Linux
/dev/sda3    *    484,491,264   488,394,751     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/cryptswap1 7b73aca9-fc79-4868-8d5f-f12a49bac389   swap                                     
/dev/sda1: PTTYPE="dos" 
/dev/sda2        29e6f4f2-1904-46e1-b1c5-9e442b7565a2   ext4                                     
/dev/sda5        FE1046291045E8EB                       ntfs       Windows XP                    
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
cryptswap1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda5/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

=========================== sda2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout		20

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
# kopt=root=UUID=29e6f4f2-1904-46e1-b1c5-9e442b7565a2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=29e6f4f2-1904-46e1-b1c5-9e442b7565a2

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

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		29e6f4f2-1904-46e1-b1c5-9e442b7565a2
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=29e6f4f2-1904-46e1-b1c5-9e442b7565a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		29e6f4f2-1904-46e1-b1c5-9e442b7565a2
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=29e6f4f2-1904-46e1-b1c5-9e442b7565a2 ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, memtest86+
uuid		29e6f4f2-1904-46e1-b1c5-9e442b7565a2
kernel		/boot/memtest86+.bin

title		Windows XP
root		(hd0,0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=db9fe40e-d997-47d0-b827-81fecf03cc95 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sda2: Location of files loaded by Grub: ===================


 210.8GB: boot/grub/menu.lst
 212.6GB: boot/grub/stage2
 120.0GB: boot/initrd.img-2.6.38-8-generic
 212.6GB: boot/vmlinuz-2.6.38-8-generic
 120.0GB: initrd.img
 212.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

NOTE: I didn't have these files: /BOOT.INI /NTLDR /NTDETECT.COM on my Windows partition at all, so I downloaded it and put there manually (hoping this will help, because I don't have my windows recovery CD).

---

### Post by Rubi1200 on 2011-05-30
Hi,
sorry for the delayed response. Thanks for the script results. I see some odd things going on here and I am going to pass this one on to some other users to offer their opinions as to the best course of action here.

Thanks for being so patient.

---

### Post by sirLeonardo on 2011-05-30
Well, to be honest I am very grateful that anyone is willing to help me at all :) Thanks for Your help. I will wait as long as it's necessary.

---

### Post by hal8000 on 2011-05-30
I've spotted two anomalies with your setup
From your original fdisk partition table:


Disk /dev/sda: 250.1 GB, 250059350016 bytes
--snip--
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16126   230500619   115242247    f  W95 Ext'd (LBA)
/dev/sda2       230502400   484491263   126994432   83  Linux
/dev/sda3   *   484491264   488394751     1951744   82  Linux swap / Solaris
/dev/sda5   *       16128   230500619   115242246    7  HPFS/NTFS

Two partitions are both marked as active /dev/sda3 and /dev/sda5
and the other error in windws boot.ini



================================ sda5/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect



The line
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 

needs to be changed to

default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS 

That tells windows that its NTFS partition is on the first extended
partition sda5.
You can possibly edit that file by mounting the sda5 partition
with gedit and saving the changes, I would possibly back the
file up first and save it as boot.ini.bak or similar.

As for two partitions being marked active, this wont affect linux
but may stop windows loading, I had a quick look at my partitions:-

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   268317629   134158783+   7  HPFS/NTFS
/dev/sda2   *   268317630   677910869   204796620    7  HPFS/NTFS
/dev/sda3       677910870   718860615    20474873   A5  FreeBSD
/dev/sda4       718860616   976768064   128953724+   5  Extended
/dev/sda5       718860618   718892684       16033+  82  Linux swap / Solaris
/dev/sda6       718892748   739873574    10490413+  83  Linux
/dev/sda7       739873638   781835354    20980858+  83  Linux
/dev/sda8       781836288   801366015     9764864   83  Linux
/dev/sda9       801366079   840440474    19537198   83  Linux
/dev/sda10      840440538   860907284    10233373+  83  Linux

And notice that only one partition is marked as active, the above example
is for Windows 7 which controls either XP or Win7.
Also windows always likes the first partition, which is not true in your
example.

It maybe that your partitions are in the wrong order, but I would not 
touch this for the moment.

Changing the boot flag is easier, though I would edit the boot.ini first
To toggle boot flag
sudo fdisk /dev/sda

Press p to print your partition,
a to toggle boot flg
3 to change partition 3 to not bootable
p to check changes are made
w to write changes
x to exit.

If however you can still access windows partitions via ubuntu
then for safety back up all your data from windows and ubuntu
onto a CD or removable drive.

---

### Post by oldfred on 2011-05-30
Windows does not officially boot from a logical partition. Per windows it has to be sda1 thru sda4. But I think that is only the windows boot code in the MBR. But you can get XP to boot from a logical. Since windows combines all the boots into the system in a primary partition did you have another copy of windows in sda3 where the boot flag is now shown on swap? That was probably where your boot files were.

hal8000 noticed the boot.ini, but the partition boot sector also needs to be correct. Also be careful in editing boot.ini from Ubuntu that you save with dos line endings. gedit has a save as and lets you select dos style line endings. Or use nano.

If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.

More detail on the inner workings, when moving windows to another partition.
HOWTO: Moving/Copying Windows XP to another Partition 
[http://ubuntuforums.org/showthread.php?t=916146](http://ubuntuforums.org/showthread.php?t=916146)
May be easier to use testdisk to rebuild partition boot sector see link below by 

Boot WinXP from extended partition - Herman
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)

How to fix XP when the boot files are missing & info on windows in logical partitions Posts by meieifra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

Windows repairs just do not work as it cannot see the logical partition. The other choice which is the windows way is to create a new primary partition and use it as a windows boot partition.

I have never encrypted a swap file so I do not know about how that works.

---

### Post by sirLeonardo on 2011-06-01
@hal8000:
I did what You suggested, but that didn't solve the problem. It's still invalid device requested error. Thanks anyways!

@oldfred:
You're right I've had my windows boot things on other partition which I formatted to install linux. I just thought that since it's old and broken Windows and I installed new one on other partition it doeasn't matter. I'll read topics You linked in Your post and try making something happen. Then I'll post results. Thanks!

---

### Post by oldfred on 2011-06-01
While this mostly discusses Vista and dual booting with other windows, it is valid for all MBR/msdos computers. Grub does not use boot flag nor PBR - partition boot sector, but MBR and partitions and multi-booting are explained. If you do not want all the details, you can just review pictures and get an idea how things work.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by katykat on 2011-06-01
Just a thought, as I have no clue as to mixed partitions (all my OS's are on separate drives). 

It looks like grub 0.96 is being used. 

No mention was made of the distribution used. 

If recent, it *could* be a version conflict.

Or not.

---

