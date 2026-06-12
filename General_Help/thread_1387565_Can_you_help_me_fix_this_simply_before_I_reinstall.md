---
title: "Can you help me fix this simply before I reinstall?"
date: 2010-01-22
forum: General Help
---

### Post by sofasurfer on 2010-01-22
O,o!!
sda contains my old system that I am using now.
sdb contains...
1) Ubuntu 9.04
2) Ubuntu 9.10
3) Storage

I ran out of space on 9.04. So I booted with GParted and deleted 9.10 and enlarged 9.04.

Now I am able to boot sda but I cannot access sdb from it.
When I boot to 9.04 I get "unknown filesystem" and "grub repair" followed by a prompt.

What happened and is this an easy fix? 
I have tried repairing grub in the past and it is apparently beyond me. So do I fix or reinstall?

Thanks...

---

### Post by amsterdamharu on 2010-01-22
What does fdisk -l say and what is in your /boot/grub/grub.conf or /boot/grub/menu.lst?

---

### Post by lordskid on 2010-01-22
> **amsterdamharu said:**
> What does fdisk -l say and what is in your /boot/grub/grub.conf or /boot/grub/menu.lst?

that should be /boot/grub/grub.cfg....

backup your grub.cfg or menu.lst by 
cp /boot/grub/grub.cfg ~/grub.cfg-backup

then try running "sudo update-grub" this should fix your problem.

---

### Post by sofasurfer on 2010-01-22
I'll post the requested info in a while. I have to get a livecd loaded and running. BRB

---

### Post by sofasurfer on 2010-01-22
Ok, first some info.
When I deleted one partition and enlarged the other as stated above, GParted appeared to freeze up. I was able to close to partition window, but I could not exit the program. Si I just hit the reset button. I suspect this is what did the damage.

A little while ago I reran GParted and right clicked on 9.04 and chose "check" filesystem. The results of that process showed that it "grew" the enlarged partition at that time. So I must have shut it down before the process was done the first time.

Now, using a livecd, I am able to access both partitions on sdb and open the files. But I am still getting the grub repair message when I try to boot.

Heres the info you requested...

Sudo fdisk -l
--------------
[I]Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44694469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30147   242155746   83  Linux
/dev/sda2           30148       30515     2955960    5  Extended
/dev/sda5           30148       30515     2955928+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045568

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17007   136608696    5  Extended
/dev/sdb2           17008       38913   175959945   83  Linux
/dev/sdb5               1       16303   130953784+  83  Linux
/dev/sdb6           16639       17007     2963961   82  Linux swap / Solaris
/dev/sdb7           16304       16638     2690856   82  Linux swap / Solaris[/I]

/boot/grub/grub.cfg
--------------------
This does not exist. Here is a ls -la /media/backupsys/boot/grub
[I]total 228
drwxr-xr-x 2 root root   4096 2009-12-22 02:38 .
drwxr-xr-x 3 root root   4096 2009-12-22 02:39 ..
-rw-r--r-- 1 root root    197 2009-04-27 04:53 default
-rw-r--r-- 1 root root     15 2009-04-27 04:53 device.map
-rw-r--r-- 1 root root   8288 2009-04-27 04:53 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-04-27 04:53 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-04-27 04:53 installed-version
-rw-r--r-- 1 root root   8712 2009-04-27 04:53 jfs_stage1_5
-rw-r--r-- 1 root root   5519 2009-12-22 02:38 menu.lst
-rw-r--r-- 1 root root   5031 2009-12-22 02:38 menu.lst~
-rw-r--r-- 1 root root   7352 2009-04-27 04:53 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-04-27 04:53 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-04-27 04:53 stage1
-rw-r--r-- 1 root root 121740 2009-04-27 04:53 stage2
-rw-r--r-- 1 root root   9556 2009-04-27 04:53 xfs_stage1_5
[/I]


>then try running "sudo update grub" this should fix your problem. <

Where do I run this command? From the live cd?

---

### Post by lordskid on 2010-01-22
> **sofasurfer said:**
> Ok, first some info.
When I deleted one partition and enlarged the other as stated above, GParted appeared to freeze up. I was able to close to partition window, but I could not exit the program. Si I just hit the reset button. I suspect this is what did the damage.

A little while ago I reran GParted and right clicked on 9.04 and chose "check" filesystem. The results of that process showed that it "grew" the enlarged partition at that time. So I must have shut it down before the process was done the first time.

Now, using a livecd, I am able to access both partitions on sdb and open the files. But I am still getting the grub repair message when I try to boot.

Heres the info you requested...

Sudo fdisk -l
--------------
[I]Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44694469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30147   242155746   83  Linux
/dev/sda2           30148       30515     2955960    5  Extended
/dev/sda5           30148       30515     2955928+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045568

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17007   136608696    5  Extended
/dev/sdb2           17008       38913   175959945   83  Linux
/dev/sdb5               1       16303   130953784+  83  Linux
/dev/sdb6           16639       17007     2963961   82  Linux swap / Solaris
/dev/sdb7           16304       16638     2690856   82  Linux swap / Solaris[/I]

/boot/grub/grub.cfg
--------------------
This does not exist. Here is a ls -la /media/backupsys/boot/grub
[I]total 228
drwxr-xr-x 2 root root   4096 2009-12-22 02:38 .
drwxr-xr-x 3 root root   4096 2009-12-22 02:39 ..
-rw-r--r-- 1 root root    197 2009-04-27 04:53 default
-rw-r--r-- 1 root root     15 2009-04-27 04:53 device.map
-rw-r--r-- 1 root root   8288 2009-04-27 04:53 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-04-27 04:53 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-04-27 04:53 installed-version
-rw-r--r-- 1 root root   8712 2009-04-27 04:53 jfs_stage1_5
-rw-r--r-- 1 root root   5519 2009-12-22 02:38 menu.lst
-rw-r--r-- 1 root root   5031 2009-12-22 02:38 menu.lst~
-rw-r--r-- 1 root root   7352 2009-04-27 04:53 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-04-27 04:53 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-04-27 04:53 stage1
-rw-r--r-- 1 root root 121740 2009-04-27 04:53 stage2
-rw-r--r-- 1 root root   9556 2009-04-27 04:53 xfs_stage1_5
[/I]


>then try running "sudo update grub" this should fix your problem. <

Where do I run this command? From the live cd?

from livecd you have to mount your partition

assuming it is /dev/sda2
open a terminal or press ctrl-alt-f2
type sudo mount /dev/sda2 /mnt
type sudo mount --bind /dev /mnt/dev
then chroot to /mnt by...
sudo chroot /mnt
from there type update-grub
press crtl-d to exit chroot.
and sudo umount /mnt/dev
and sudo umount /mnt
you can now reboot
sudo reboot

---

### Post by sofasurfer on 2010-01-22
I followed your steps and they all worked with no problems. But when I tried to boot to the system I got...
*Grub loading*
*error:unknown filesystem*
*grub rescue*

I am now back in the livecd and mounted the system again according to your method and I am able to access the filesystem.

I will probably hit the hay pretty soon, but if you have any other ideas please share them. I'll be on here probably another1/2 hour.
Thanks for helping.

---

### Post by rnerwein on 2010-01-22
> **sofasurfer said:**
> O,o!!
sda contains my old system that I am using now.
sdb contains...
1) Ubuntu 9.04
2) Ubuntu 9.10
3) Storage

I ran out of space on 9.04. So I booted with GParted and deleted 9.10 and enlarged 9.04.

Now I am able to boot sda but I cannot access sdb from it.
When I boot to 9.04 I get "unknown filesystem" and "grub repair" followed by a prompt.

What happened and is this an easy fix? 
I have tried repairing grub in the past and it is apparently beyond me. So do I fix or reinstall?

Thanks...
hi
just a question - you delete 9.10 and i think this had the fs-type ext4 and ext4 comes with unbutu 9.04 in 2009 as an option - may be that's your problem.
ciao

---

### Post by lordskid on 2010-01-22
I mis-understood your posts and assumed you have grub2 installed (my bad) can you post here what your menu.lst looks like?

---

### Post by kansasnoob on 2010-01-22
The quickest way to get this sorted would be to see the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It takes all the guess work out of things.

---

### Post by sofasurfer on 2010-01-22
I'll post this stuff tomorrow afternoon. 
Thanks so much for helping.

---

### Post by kansasnoob on 2010-01-22
> **sofasurfer said:**
> I'll post this stuff tomorrow afternoon. 
Thanks so much for helping.

Feel free to click on my user name and send me a brief PM just pointing me back to this thread.

This should be very simple once I can see the output of the Boot Info Script.

---

### Post by kansasnoob on 2010-01-22
Actually what might work (some guessing involved) is just from the Live CD:

```
sudo grub
```

```
find /boot/grub/stage1
```

Which will probably give you two options like:

(hd0,0)
(hd1,1) *This could be (hd1,4).*

Anyway you know the Ubuntu you want to boot again is on sdb which in grub lingo is (hd1), so you want to use whatever the output above is for (hd1,?), understand?

sdb2 = (hd1,1)
sdb5 = (hd1,4)

So then:

```
root (hd1,1)
``` 

```
setup (hd1)
```

```
quit
```

Clear as mud :confused:

---

### Post by 00_Spykes on 2010-01-22
First of all don't count on being able to resize partitions, it's always dangerous (or so they say). I think I've even read that you can't resize or move ext4 partitions, but you just removed it right? Make sure the partition you want to resize isn't an ex4.

I don't know if this is helpful but be sure to use the right grub command, I've seen both update grup and grub-install, but don't know which one is the correct for you.

---

### Post by sofasurfer on 2010-01-22
Here is my menu.lst...

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
# kopt=root=UUID=20ce761a-c233-4139-a855-282f5cdaf037 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=20ce761a-c233-4139-a855-282f5cdaf037

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		20ce761a-c233-4139-a855-282f5cdaf037
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=20ce761a-c233-4139-a855-282f5cdaf037 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		20ce761a-c233-4139-a855-282f5cdaf037
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=20ce761a-c233-4139-a855-282f5cdaf037 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		20ce761a-c233-4139-a855-282f5cdaf037
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=20ce761a-c233-4139-a855-282f5cdaf037 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		20ce761a-c233-4139-a855-282f5cdaf037
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=20ce761a-c233-4139-a855-282f5cdaf037 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		20ce761a-c233-4139-a855-282f5cdaf037
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=20ce761a-c233-4139-a855-282f5cdaf037 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		20ce761a-c233-4139-a855-282f5cdaf037
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=20ce761a-c233-4139-a855-282f5cdaf037 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		20ce761a-c233-4139-a855-282f5cdaf037
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by sofasurfer on 2010-01-22
Kansasnoob...
Your instructions in post #13 did the trick. Thank ya thank ya thank ya.

Was grub damaged? Did this reinstall grub? 
I'd like to know what it did and what situation calls for this repair.

I'll file those instructions away for future disasters.
Thanks to all you participated.

---

### Post by 00_Spykes on 2010-01-22
Yeah, I think that procedure works as follows:
Enter the Grub shell (kind of like entering the program). 
Tell Grub that your root filesystem is located at the second (1) partition on the second (1) drive.
Then you tell Grub that it should install itself into the MBR (master boot record) of the second drive. 

I think that the bootloader that's loaded is the one on the drive which you boot from first. Basically just make sure the bootloader (Grub) that you use have the right info. Personally, the only time I've been forced to re-install Grub is when I install Windows (why, oh why, it's Blizzard's fault!).

---

