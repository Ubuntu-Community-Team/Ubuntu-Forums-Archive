---
title: "Grub broken after windows 7 install"
date: 2009-07-05
forum: General Help
---

### Post by moodog on 2009-07-05
In first installed windows XP, then installed Ubuntu, then installed Windows 7. Win 7 obviously overwrote the MBR and I've followed every guide since to try to get grub back up and running, and I now just get dumped to the grub prompt on boot up. I tried this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

and this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
(second set of instructions), and it won't work. my disks arelogical as follows:

winxp                 /dev/sda1
win7                  /dev/sda2
extended partition    /dev/sda4 (containing boot)
/boot                 /dev/sda5
/                     /dev/sda3

the / partition was initially physically located as the third partition on the disk, but I wanted to resize the win7 partition, so using the liveCD, I used gparted to move it (not sure if this matters, but thought I should mention it)

/boot still contains the /grub folder and menu.lst still looks fine 


/home is on /dev/sdb if it matters

---

### Post by 7raTEYdCql on 2009-07-05
Which version of ubuntu are you using. If you are still using 6.10, then i don't think it has Windows 7 support. You will have to upgrade Grub in some manner. Or just reformat your 6.10 partition, after taking backup. An ubuntu live disk should be helpful.

---

### Post by moodog on 2009-07-05
This is ubuntu 9.04

---

### Post by moodog on 2009-07-05
Given the standard method of restoring doesn't work, are there any other ways to get the system up and running other than reinstalling? That would be great, as I've just spent about 4 hours getting the new sytem up and running... so reinstalling would be about the least preferred method...

---

### Post by ivanvajar on 2009-07-05
Did you restore GRUB to MBR hd0?

---

### Post by ivanvajar on 2009-07-05
If I get this, you have 2 HDDs. I guess that you installed GRUB to sdb. You can boot Ubuntu if you change boot disk to that one in BIOS, but it is still good idea to install GRUB on sda. That way you will have no BIOS changes.

So, > setup (hd0)

---

### Post by moodog on 2009-07-05
Sorry, I should have listed the commands I ran. I executed the following

sudo grub
root (hd0,4)
setup (hd0)
quit


when I first ran 
sudo grub

and find /boot/grub/stage1, it didn't find anything, so I had to mount the drives and figure out which one I should have been working with, and then ran 

grub-install --root-directory= etc. 

(from here:
[http://ubuntuforums.org/showthread.php?t=485422](http://ubuntuforums.org/showthread.php?t=485422)
)

---

### Post by ivanvajar on 2009-07-05
OK, let's see. You do have 2 HDDs? I see that /home is on /dev/sdb

---

### Post by moodog on 2009-07-05
output of fdisk -l

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e82c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2           11504       19152    61440592+   7  HPFS/NTFS
/dev/sda3            8287       11473    25599577+  83  Linux
/dev/sda4           11474       11503      240975    5  Extended
/dev/sda5           11474       11503      240943+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000a91a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         892     7164958+  82  Linux swap / Solaris
/dev/sdb2             893        5991    40957717+   7  HPFS/NTFS
/dev/sdb3           16191       48060   255995775   83  Linux
```

---

### Post by ivanvajar on 2009-07-05
Does Ubuntu boot when you change boot priority to 2nd HDD in BIOS? It looks like you need to do this:
> sudo grub
find /boot/grub/stage1
root (hd1,2)
setup (hd0)
quit

---

### Post by moodog on 2009-07-05
will try this, but doesn't hd(1.x) equate to sdb? The only linux partition on sdb is /home (apart from swap).

The output of find /boot/grub/stage1 is hd0,4...

---

### Post by moodog on 2009-07-05
if I do anything other than

```
root (hd0,4)
setup (hd0)
```

I get the following error:

```
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

---

### Post by ivanvajar on 2009-07-05
See if > setup (hd0,2) helps. It seems that boot is there if on hd0,4 isn't

---

### Post by moodog on 2009-07-05
setup (anything) only works if I use 

```
root (hd0,4)
```

I've tried 

```
setup (hd0)
setup (hd1)
setup (hd0,4)
```

and nothing gets past the grub prompt.

---

### Post by ivanvajar on 2009-07-05
This is so odd. So, root is on hd0,4. I can't understand why it doesn't install grub to hd0. If you tried to install GRUB on hd1, you might be able to boot Ubuntu when you change boot priority of HDDs in BIOS. Try that. It is possible that BootLoader installed by Win 7 doesn't allow GRUB to be installed. You tried setup (hd1) and therefore you should be able to use GRUB if installed on sdb. The only thing is to make current sdb bootable in BIOS. In other words just make CDROM 1st and 'sdb' 2nd boot device.

---

### Post by enli on 2009-07-05
Hi, here is what I have understood so far. You have 2 HDD and the Ubuntu is installed on 2nd HDD while Vista is one the first. And when you set bootorder to boot from first HDD it cant find the Grub files as those are on second HDD. No matter what you tried, didnt work. So here is a work-around I used a while ago for the same problem. I had 2 HDDs too.

Create a small sized ext3 logical partition on your Vista HDD - size could be 10MB to hold grub files and point them with grub installer.

I suggest you boot from Ubuntu CD for following steps and not from Ubuntu hard-disk. Lets not complicate the things :)
 
As you mentioned you have already used Partitioner then you shouldn`t have problems in resizing and creating a ext3 partition.After you have created this partition copy "/boot/grub" folder from Ubuntu partition to this newly created ext3 partion. On this ext3 partition then you should have folder structure /boot/grub (grub files here). And also create a dummy file named HERE.

Open the terminal and
sudo grub
find /boot/grub/HERE
(hd0,x)                <- x is your ext3 partition number on Win7 disk
root (hd0,x)
setup (hd0)            <- This will install MBR code in Win7 disk
quit

Now you need to edit your /boot/grub/menu.lst on new partition.
Invert every entry of root - (hd0,x) to (hd1,x) and vice versa.

Let me know if this worked or not.

---

### Post by ivanvajar on 2009-07-05
Hi, Enli. This is weird situation here. He installed Win7 and now he can't restore GRUB. setup (hd0) didn't work.

---

### Post by enli on 2009-07-05
> **moodog said:**
> if I do anything other than

```
root (hd0,4)
setup (hd0)
```

I get the following error:

```
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

I think he is trying to install grub when normal installation of Ubuntu is booted, so that the error of not finding files makes sense. Because if he has booted Ubuntu that means that partition will be primary and (hd0,4) would in most cases will give ubuntu partition number. 

When he executed root(hd0,4) the MBR is actually installed on 2nd HDD containing Ubuntu which is for time being primary. So when next time he uses Vista HDD has primary grub cant locate files.

I think he should follow the steps I gave in my previous post and lets see if that resolves the problem.

---

### Post by ivanvajar on 2009-07-05
Worth trying. I noticed that he's offline. Moodog, read Enli's post carefully. Best of luck!

---

### Post by enli on 2009-07-05
misplaced comment - nvm

---

### Post by moodog on 2009-07-05
Hey guys, thanks for trying here. I'm not at home now so can't try anything for a while, but it appears that there has been some confusion with regards to the partitions. I've relisted the output of fdisk -l below, with the use of each partition added. Note that there is nothing OS specific on the second drive, it is only for /home, documents and settings, and swap. Therefore I believe it is irrelevant to this problem (although it may not be). All OS related partitions are on the first drive (hd0, sda).
```

	   	Device Boot      Start         End      Blocks   Id  System
winxp		/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
WIN7		/dev/sda2           11504       19152    61440592+   7  HPFS/NTFS
ubuntu root (/)	/dev/sda3            8287       11473    25599577+  83  Linux
extended	/dev/sda4           11474       11503      240975    5  Extended
ubuntu /boot	/dev/sda5           11474       11503      240943+  83  Linux


   Device Boot      Start         End      Blocks   Id  System
ubuntu swap	/dev/sdb1               1         892     7164958+  82  Linux swap / Solaris
win Docs&Set	/dev/sdb2             893        5991    40957717+   7  HPFS/NTFS
ubuntu /home	/dev/sdb3           16191       48060   255995775   83  Linux
```

When trying to install grub, I've been doing it from the live CD. 


I should have just waited to install ubuntu after Win7, but I had to wait to download the Win7 RC iso, so installed Ubuntu to kill time...

---

### Post by enli on 2009-07-05
Thanks for replying back and clearing the confusion.

I went through your previous posts and it looks like grub is fine. Its just that it can not find Ubuntu kernel to boot from. May be after the resize of the partitions the partition numbers might have changed which shouldnt happen unless you delete and create partition. The best way to check if this is the case, First write on paper the menu.lst entry (should have kernel, initrd and root options)for Ubuntu somewhere from your installed ubuntu partition /boot/grub/menu.lst. 

When you are thrown to grub prompt after boot, 
find out which is your Ubuntu partition by
```
find /boot/grub/menu.lst
```
it should return a line like (hd0,x) where x is your ubuntu partition number.

enter the menu.lst entry one line by one and after that enter "boot" and see if it boots Ubuntu. You may have to substitute the occurances of (hd0,x) from menu.lst to that of above returned x.

If this also fails, I have no idea why it is failing. Must be menu.lst problem on your side as grub is loaded. If you get any error/message when you are thrown to grub prompt, please let us know, that would help too.

---

### Post by moodog on 2009-07-06
I hope you're right enli :) would love to not have to reinstall. Am still not at home, so can't try anything, but remembered some other info relevant to your most recent post.

My menu.lst contains partitions referenced by uuid, so it's not immediately clear which partitions it points to, but I was able to reconcile, and I think the menu.lst value for groot was the same partition as /boot, and the other root variable in menu.lst pointed to the partition that contained /. All of the menu entries then pointed to the uuid for the /boot partition. 

I'll test your suggestions at the earliest opportunity (not sure if that will be tonight)

Thanks again for your help!

---

### Post by enli on 2009-07-06
I think that will be related to UUID. Good point. I am 100% sure but it gets changed after you do partition operations.

Get your new Ubuntu UUID and replace in menu.lst.
To find out UUID : [http://ubuntuforums.org/showthread.php?t=349376](http://ubuntuforums.org/showthread.php?t=349376)

---

### Post by moodog on 2009-07-09
So I've finally got around to trying to sort this out, and it appears that you're right enli, it couldn't find the kernel. I set root to (hd0,4) - the boot partiton, and then at the grub prompt entered details for kernel and initrd, and when I typed boot, it started to boot. 

It then got stuck at usbhid: v2.6:USB HID core driver, then printed

Done.
Gave up waiting for root device. Common problems.....

I thought the output of a script I found on another thread may be useful:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #1 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 184400850 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e82c9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,199,154    51,199,092   7 HPFS/NTFS
/dev/sda2         184,795,695   307,676,879   122,881,185   7 HPFS/NTFS
/dev/sda3         133,114,590   184,313,744    51,199,155  83 Linux
/dev/sda4         184,313,745   184,795,694       481,950   5 Extended
/dev/sda5         184,313,808   184,795,694       481,887  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000a91a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    14,329,979    14,329,917  82 Linux swap / Solaris
/dev/sdb2          14,329,980    96,245,414    81,915,435   7 HPFS/NTFS
/dev/sdb3         260,092,350   772,083,899   511,991,550  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9630D75630D73BC5" TYPE="ntfs" 
/dev/sda2: UUID="019519DF0C2C78A3" TYPE="ntfs" 
/dev/sda3: UUID="750863c1-7d34-44af-b6f1-81f9ea44f5a8" TYPE="ext4" 
/dev/sda5: UUID="f688976f-622b-40ba-8ea1-9cfdbab0113e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: TYPE="swap" UUID="464b4846-07e9-4f3b-8c35-ddde760b9fac" 
/dev/sdb2: UUID="148A8A0D191A27A3" TYPE="ntfs" 
/dev/sdb3: UUID="a2971e1d-a113-4dd7-a372-29e0d4a9fa29" TYPE="ext4" 

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

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=f688976f-622b-40ba-8ea1-9cfdbab0113e /boot           ext3    relatime        0       2
# /home was on /dev/sdb3 during installation
UUID=a2971e1d-a113-4dd7-a372-29e0d4a9fa29 /home           ext4    relatime        0       2
# swap was on /dev/sdb1 during installation
UUID=464b4846-07e9-4f3b-8c35-ddde760b9fac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

192.168.1.32:/mnt/store         /media/spankytv         nfs     defaults        0       0
192.168.1.32:/mnt/recordings            /media/recordings               nfs     defaults        0       0


============================= sda5/grub/menu.lst: =============================

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
# kopt=root=UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f688976f-622b-40ba-8ea1-9cfdbab0113e

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
uuid		f688976f-622b-40ba-8ea1-9cfdbab0113e
kernel		/vmlinuz-2.6.28-13-generic root=UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 ro quiet splash 
initrd		/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		f688976f-622b-40ba-8ea1-9cfdbab0113e
kernel		/vmlinuz-2.6.28-13-generic root=UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 ro  single
initrd		/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f688976f-622b-40ba-8ea1-9cfdbab0113e
kernel		/vmlinuz-2.6.28-11-generic root=UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f688976f-622b-40ba-8ea1-9cfdbab0113e
kernel		/vmlinuz-2.6.28-11-generic root=UUID=750863c1-7d34-44af-b6f1-81f9ea44f5a8 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f688976f-622b-40ba-8ea1-9cfdbab0113e
kernel		/memtest86+.bin
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


=================== sda5: Location of files loaded by Grub: ===================


  94.4GB: boot/grub/stage2
  94.5GB: grub/menu.lst
  94.5GB: grub/stage2
  94.3GB: initrd.img-2.6.28-11-generic
  94.4GB: initrd.img-2.6.28-13-generic
  94.3GB: vmlinuz-2.6.28-11-generic
  94.3GB: vmlinuz-2.6.28-13-generic

```

---

### Post by enli on 2009-07-09
Yes, this seems to be a problem caused by UUID. To make things easier you have to change 2 lines from your grub /boot/grub/menu.lst file.

Find out your Ubuntu parition UUID as as told earlier in post. And replace every occurance of of UUID to that of found using my above post.

Let me know if that works out.

Btw, what is this script? Looks really good for troubleshooting the grub problems.

---

### Post by moodog on 2009-07-09
Thanks enli - will try to sort it out over the weekend, but I think I'm abuot to give up and reinstall. Might waste another hour on it. I feel I'm close, but getting frustrated.

I came across that script while researching my problem - found it on this thread here:

[http://ubuntuforums.org/showthread.php?t=1027432](http://ubuntuforums.org/showthread.php?t=1027432)

mentioned on post #2

---

### Post by enli on 2009-07-09
If you are new Ubuntu switcher above tasks could take anywhere between 30-40 minutes. So yes reinstalling will be a lot easier.

---

### Post by moodog on 2009-07-10
Well, I at least got it to boot at last. The issue appears to be that I was able to tell it where the grub files were, and then when I got it to the last point I mentioned, it was finding the /boot partition, but not the / partition, hence the error I mentioned. To get it to boot properly, the critical parameter I was missing was the "root" option at the end of the 
kernel line.

I was only using:
```

kernel		/vmlinuz-2.6.28-13-generic
```

I should have been using:

```
kernel		/vmlinuz-2.6.28-13-generic root=/dev/sda3
```

Anyway - feel a bit stoopid now, but it's working...Was able to boot into ubuntu manually entering the parameters, then ran grub-install, and Ubuntu, Win7 and WinXP all boot fine now.

Thanks a lot for your help.

---

### Post by enli on 2009-07-10
Glad that you sorted out the problem and didn't re-install. I hope that was great experience for you toying with the first encounter with shell :D

Thanks for replying back, I just learned something new today. It could have been also fixed by correct UUID but this method of adding root is much better.

---

### Post by moodog on 2009-07-11
Thanks for your help

It wasn't really my first encounter with shell - I've been using Linux for about the last 12 years or so off and on... hence why I felt a bit silly for not using the entire root line from menu.lst at the grub prompt... It was a good feeling to not have to reinstall though.

---

