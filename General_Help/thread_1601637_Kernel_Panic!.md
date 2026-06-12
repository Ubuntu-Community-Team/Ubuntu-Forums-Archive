---
title: "Kernel Panic!"
date: 2010-10-20
forum: General Help
---

### Post by Dennetik on 2010-10-20
Concerning an installation of Ubuntu 10.0.4 LST.
After update from Update Manager, where a kernel update was installed:

```
mount: mounting /dev/disk/by-uuid/62643a8f-2322-4a0d-07842ff6a26 on /root
failed: invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
```

After this, it opens up BusyBox - when I exit from here, it responds with "Kernel Panic - attempting to kill init."

I assumed this means the kernel can't be mounted, but I'm not great with these matters.

Could anyone help?
Is there more information that could help?

Thank you,
Dennetik

---

### Post by Dennetik on 2010-10-20
I found [this]("http://ubuntuforums.org/showthread.php?t=1591382&highlight=%2Fsbin%2Finit") thread, and will run the bootinfoscript used there.

I'll post the results here when I've done that.

---

### Post by Dennetik on 2010-10-21
Here's the result of the boot info script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       498,014       497,952  83 Linux
/dev/sda2             498,015   117,692,189   117,194,175  83 Linux
/dev/sda3         117,692,190   976,768,064   859,075,875   5 Extended
/dev/sda5         117,692,253   195,511,049    77,818,797  83 Linux
/dev/sda6         195,511,113   976,768,064   781,256,952  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1017 MB, 1017643008 bytes
2 heads, 63 sectors/track, 15774 cylinders, total 1987584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             32     1,987,583     1,987,552   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7212db52-5cb2-4e60-ab02-8216140ea56c   ext2                                     
/dev/sda2        62643a8f-2322-4a0d-80b8-07842ff6ab26   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        99abea48-7f2f-490f-84e3-89adde276a49   ext3                                     
/dev/sda6        01224a3a-bfb3-4cd0-ae4f-7fc3503423bb   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        F43E-8252                              vfat       UHESBEE                       
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/01224a3a-bfb3-4cd0-ae4f-7fc3503423bb ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/99abea48-7f2f-490f-84e3-89adde276a49 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/7212db52-5cb2-4e60-ab02-8216140ea56c ext2       (rw,nosuid,nodev,uhelper=udisks)


============================= sda1/grub/menu.lst: =============================

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
# kopt=root=UUID=62643a8f-2322-4a0d-80b8-07842ff6ab26 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7212db52-5cb2-4e60-ab02-8216140ea56c

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid		7212db52-5cb2-4e60-ab02-8216140ea56c
kernel		/vmlinuz-2.6.32-25-generic root=UUID=62643a8f-2322-4a0d-80b8-07842ff6ab26 ro quiet splash 
initrd		/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid		7212db52-5cb2-4e60-ab02-8216140ea56c
kernel		/vmlinuz-2.6.32-25-generic root=UUID=62643a8f-2322-4a0d-80b8-07842ff6ab26 ro  single
initrd		/initrd.img-2.6.32-25-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		7212db52-5cb2-4e60-ab02-8216140ea56c
kernel		/vmlinuz-2.6.32-24-generic root=UUID=62643a8f-2322-4a0d-80b8-07842ff6ab26 ro quiet splash 
initrd		/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		7212db52-5cb2-4e60-ab02-8216140ea56c
kernel		/vmlinuz-2.6.32-24-generic root=UUID=62643a8f-2322-4a0d-80b8-07842ff6ab26 ro  single
initrd		/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid		7212db52-5cb2-4e60-ab02-8216140ea56c
kernel		/vmlinuz-2.6.32-23-generic root=UUID=62643a8f-2322-4a0d-80b8-07842ff6ab26 ro quiet splash 
initrd		/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		7212db52-5cb2-4e60-ab02-8216140ea56c
kernel		/vmlinuz-2.6.32-23-generic root=UUID=62643a8f-2322-4a0d-80b8-07842ff6ab26 ro  single
initrd		/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		7212db52-5cb2-4e60-ab02-8216140ea56c
kernel		/vmlinuz-2.6.32-22-generic root=UUID=62643a8f-2322-4a0d-80b8-07842ff6ab26 ro quiet splash 
initrd		/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		7212db52-5cb2-4e60-ab02-8216140ea56c
kernel		/vmlinuz-2.6.32-22-generic root=UUID=62643a8f-2322-4a0d-80b8-07842ff6ab26 ro  single
initrd		/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		7212db52-5cb2-4e60-ab02-8216140ea56c
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: grub/menu.lst
    .2GB: grub/stage2
    .0GB: initrd.img-2.6.32-22-generic
    .0GB: initrd.img-2.6.32-23-generic
    .0GB: initrd.img-2.6.32-24-generic
    .0GB: initrd.img-2.6.32-25-generic
    .0GB: vmlinuz-2.6.32-22-generic
    .0GB: vmlinuz-2.6.32-23-generic
    .0GB: vmlinuz-2.6.32-24-generic
    .0GB: vmlinuz-2.6.32-25-generic
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by Hippytaff on 2010-10-21
Which version did you update from? not sure, but looks like you've got grub legacy, not grub 2

---

### Post by Dennetik on 2010-10-21
Based on [this]("http://ubuntuforums.org/showthread.php?t=1591382&highlight=%2Fsbin%2Finit") thread, I've run the following commands; it should be obvious that, though I've read up on the basic purposes of e2fsck, I have no clue what exactly I'm doing here:

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda2
/dev/sda2: recovering journal
Error reading block 7294845 (Attempt to read block from filesystem resulted in short read).  

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
```

As could be anticipated from the other thread, this fails.
So here I've run the second indicated command:

```
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda2
e2fsck 1.41.12 (17-May-2010)
/dev/sda2: recovering journal
Error reading block 7294845 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 7288275 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Clearing orphaned inode 3115096 (uid=1000, gid=1000, mode=0100600, size=0)
Clearing orphaned inode 3115095 (uid=1000, gid=1000, mode=0100600, size=4096)
Clearing orphaned inode 3115094 (uid=1000, gid=1000, mode=0100600, size=35491)
Clearing orphaned inode 3115093 (uid=1000, gid=1000, mode=0100600, size=0)
Clearing orphaned inode 3115092 (uid=1000, gid=1000, mode=0100600, size=2344)
Clearing orphaned inode 3115091 (uid=1000, gid=1000, mode=0100600, size=14790)
Clearing orphaned inode 433488 (uid=0, gid=0, mode=0100644, size=9748)
Clearing orphaned inode 433485 (uid=0, gid=0, mode=0100644, size=30684)
Clearing orphaned inode 433484 (uid=0, gid=0, mode=0100644, size=71432)
Clearing orphaned inode 433483 (uid=0, gid=0, mode=0100755, size=117086)
Clearing orphaned inode 433480 (uid=0, gid=0, mode=0100644, size=34408)
Clearing orphaned inode 433478 (uid=0, gid=0, mode=0100644, size=42572)
Clearing orphaned inode 433477 (uid=0, gid=0, mode=0100644, size=22036)
Clearing orphaned inode 433476 (uid=0, gid=0, mode=0100644, size=30496)
Clearing orphaned inode 433475 (uid=0, gid=0, mode=0100644, size=79676)
Clearing orphaned inode 433473 (uid=0, gid=0, mode=0100644, size=149392)
Clearing orphaned inode 433472 (uid=0, gid=0, mode=0100644, size=9736)
Clearing orphaned inode 433471 (uid=0, gid=0, mode=0100644, size=38360)
Clearing orphaned inode 433469 (uid=0, gid=0, mode=0100755, size=1405508)
Clearing orphaned inode 558072 (uid=0, gid=0, mode=0100644, size=9540)
Clearing orphaned inode 558015 (uid=0, gid=0, mode=0100644, size=9532)
Clearing orphaned inode 557962 (uid=0, gid=0, mode=0100644, size=9528)
Clearing orphaned inode 557878 (uid=0, gid=0, mode=0100644, size=26048)
Clearing orphaned inode 417064 (uid=0, gid=0, mode=0100755, size=113964)
Clearing orphaned inode 3035507 (uid=1000, gid=1000, mode=0100644, size=59179901)
Clearing orphaned inode 1955546 (uid=1000, gid=1000, mode=0100644, size=32768)
Clearing orphaned inode 1954766 (uid=1000, gid=1000, mode=0100600, size=36240)
Clearing orphaned inode 1676090 (uid=0, gid=0, mode=0100700, size=830676)
Clearing orphaned inode 1676089 (uid=112, gid=125, mode=0100600, size=0)
Clearing orphaned inode 1676086 (uid=112, gid=125, mode=0100600, size=0)
Clearing orphaned inode 1676085 (uid=112, gid=125, mode=0100600, size=0)
Clearing orphaned inode 1676084 (uid=112, gid=125, mode=0100600, size=0)
Clearing orphaned inode 1676083 (uid=112, gid=125, mode=0100600, size=0)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Entry 'c0e4581462dc001f17cb875d4643f010' in /home/sollicity/workspace/.metadata/.plugins/org.eclipse.core.resources/.history/f5 (3035644) has deleted/unused inode 3036352.  Clear? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached inode 3036353
Connect to /lost+found? yes

Inode 3036353 ref count is 2, should be 1.  Fix? yes

Unattached inode 3036354
Connect to /lost+found? yes

Inode 3036354 ref count is 2, should be 1.  Fix? yes

Unattached inode 3036355
Connect to /lost+found? yes

Inode 3036355 ref count is 2, should be 1.  Fix? yes

Unattached inode 3036361
Connect to /lost+found? yes

Inode 3036361 ref count is 2, should be 1.  Fix? yes

Unattached inode 3036365
Connect to /lost+found? yes

Inode 3036365 ref count is 2, should be 1.  Fix? yes

Unattached inode 3036366
Connect to /lost+found? yes

Inode 3036366 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068545
Connect to /lost+found? yes

Inode 3068545 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068546
Connect to /lost+found? yes

Inode 3068546 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068547
Connect to /lost+found? yes

Inode 3068547 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068548
Connect to /lost+found? yes

Inode 3068548 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068551
Connect to /lost+found? yes

Inode 3068551 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068552
Connect to /lost+found? yes

Inode 3068552 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068554
Connect to /lost+found? yes

Inode 3068554 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068555
Connect to /lost+found? yes

Inode 3068555 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068559
Connect to /lost+found? yes

Inode 3068559 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068560
Connect to /lost+found? yes

Inode 3068560 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068562
Connect to /lost+found? yes

Inode 3068562 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068564
Connect to /lost+found? yes

Inode 3068564 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068565
Connect to /lost+found? yes

Inode 3068565 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068567
Connect to /lost+found? yes

Inode 3068567 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068568
Connect to /lost+found? yes

Inode 3068568 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068569
Connect to /lost+found? yes

Inode 3068569 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068570
Connect to /lost+found? yes

Inode 3068570 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068571
Connect to /lost+found? yes

Inode 3068571 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068573
Connect to /lost+found? yes

Inode 3068573 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068575
Connect to /lost+found? yes

Inode 3068575 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068576
Connect to /lost+found? yes

Inode 3068576 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068578
Connect to /lost+found? yes

Inode 3068578 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068579
Connect to /lost+found? yes

Inode 3068579 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068581
Connect to /lost+found? yes

Inode 3068581 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068582
Connect to /lost+found? yes

Inode 3068582 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068583
Connect to /lost+found? yes

Inode 3068583 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068584
Connect to /lost+found? yes

Inode 3068584 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068586
Connect to /lost+found? yes

Inode 3068586 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068587
Connect to /lost+found? yes

Inode 3068587 ref count is 2, should be 1.  Fix? yes

Unattached inode 3068588
Connect to /lost+found? yes

Inode 3068588 ref count is 2, should be 1.  Fix? yes

Pass 5: Checking group summary information
Block bitmap differences:  +(12171496--12171523) +12288539 +(12302648--12302733) +12310557
Fix? yes

Free blocks count wrong for group #371 (13354, counted=13326).
Fix? yes

Free blocks count wrong for group #375 (27524, counted=27436).
Fix? yes

Free blocks count wrong (6377674, counted=6377558).
Fix? yes

Inode bitmap differences:  +(3036353--3036366) +(3068545--3068590)
Fix? yes

Free inodes count wrong for group #371 (5123, counted=5109).
Fix? yes

Free inodes count wrong for group #375 (5628, counted=5582).
Fix? yes

Free inodes count wrong (3265016, counted=3264956).
Fix? yes


/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****

  397892 inodes used (10.86%)
    8395 non-contiguous files (2.1%)
     690 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 16806/724/0
 8271713 blocks used (56.47%)
       0 bad blocks
       2 large files

  307358 regular files
   46673 directories
      68 character device files
      26 block device files
       6 fifos
     630 links
   43688 symbolic links (35733 fast symbolic links)
      64 sockets
--------
  398477 files
```

---

### Post by Hippytaff on 2010-10-21
Did you back stuff up before you upgraded?
 
Have you got a live cd or access to a working pc where you can download one?
 
if you upgraded from anything earlier than 10.04 lucid lynx then that might be why this ids happening?

---

