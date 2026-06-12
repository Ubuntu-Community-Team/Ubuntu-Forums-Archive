---
title: "I think I broke my sister's laptop. :("
date: 2011-02-05
forum: General Help
---

### Post by anselmo_crowley on 2011-02-05
Hi!
  My sister and I have been using Ubuntu for some months (we’re still newbies though).
  She told me she wanted me to erase her Windows partition from her laptop because it was taking up too much space, so she’d only have Ubuntu. I figured it would be easy, since I’ve used partitioning software before and I’ve never had a problem. But now everything is messed up. I can’t boot Ubuntu and when I use a LiveCD, I can’t mount the /home partition. So basically, everything is broken!
  Is there a way to fix this? Or maybe retrieve her files and reinstall Ubuntu from scratch?
  I don’t know what to do. All her stuff is in there. I feel really bad because I don’t want her to lose all her files! 
  Please help me!
  

Thanks so much!

---

### Post by Elfy on 2011-02-05
Boot with the livecd - open a terminal and run this please - give us the outputs.

Did something go wrong during the partitioning?

```
sudo fdisk -l
```

---

### Post by marin123 on 2011-02-05
did you erase wrong partition?
maybe you messed up MBR partition?
it can happen to anyone, just one second and everything goes down the drain...

---

### Post by anselmo_crowley on 2011-02-05
Thanks so much for answering!
Nothing went wrong during the partitioning process. (Not that I know of, but I'm pretty sure it did)
Here's what I got (I hope I'm posting this the right way):

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00074d53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        1306    10490413+  83  Linux
/dev/sda3            1392        5842    35752657+  83  Linux
/dev/sda4            1307        1391      682762+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by CorruptDNA on 2011-02-05
> **marin123 said:**
> did you erase wrong partition?
maybe you messed up MBR partition?
it can happen to anyone, just one second and everything goes down the drain...

yeah... it seems u were successful in erasing your window's partition. Maybe there is something wrong with the grub? cause thats what happened to me..

---

### Post by anselmo_crowley on 2011-02-05
Thanks for answering!
I think I erased the right partition, but I don't know about the MBR! Is that GRUB? Because when I turn on the computer GRUB appears but then Ubuntu won't start.
I know! It sucks! What really bothers me is that it's not my computer and I don't want my sister to lose all her files! :(

---

### Post by Elfy on 2011-02-05
Edit - try the grub reinstall at the bottom first.


Try this 

```
sudo mkdir /mnt/tmp /mnt/tmp1
sudo mount -t ext4 /dev/sda2 /mnt/tmp
sudo mount -t ext4 /dev/sda3 /mnt/tmp1
```

Assuming they work without error
```

nautilus /mnt/tmp
nautilus /mnt/tmp1
```

See if you get at the files in either of those.

It would be useful to know why you can't boot, possibly removing windows has done something to grub and a reinstall of that would deal with it.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If all else fails - [go here]("http://bootinfoscript.sourceforge.net/") - follow the instructions - all of them and paste the results.

---

### Post by anselmo_crowley on 2011-02-05
I think the filesystem is ext3, so when I write that in the terminal should I still write ext4 or do I replace it with ext3? I'm really sorry if this is a dumb question.

---

### Post by Elfy on 2011-02-05
use ext3 then :)

But try the reinstall grub first ...

---

### Post by Rubi1200 on 2011-02-05
Part of the problem could be that you appear to have installed Ubuntu twice or is that a separate /home partition?

> /dev/sda2   *           1        1306    10490413+  83  Linux
/dev/sda3            1392        5842    35752657+  83  Linux

---

### Post by anselmo_crowley on 2011-02-05
I reinstalled GRUB and after the computer rebooted this is what I got:

```
[CENTER]GNU GRUB version 1.97~beta4
[/CENTER]
 [ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>
```

Is that normal? What am I supposed to do after that?

Rubi1200: Honestly, I'm not really sure what's going on anymore and I'm don't understand much abount Ubuntu, but I think sda2 is Ubuntu and sda3 is /home (/home is where the files are, right?) I'm really confused right now, I'm sorry if I'm not making any sense.

---

### Post by Rubi1200 on 2011-02-05
It's okay, first take a deep breath and then we will try and help you sort this out.

And, no, you should not be seeing the prompt if GRUB was properly reinstalled.

First thing I would like you to do is the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Once we see the results, it will be a lot easier to advise you.

---

### Post by anselmo_crowley on 2011-02-05
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00074d53

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *             63    20,980,889    20,980,827  83 Linux
/dev/sda3          22,346,415    93,851,729    71,505,315  83 Linux
/dev/sda4          20,980,890    22,346,414     1,365,525  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda2        083535b2-fc66-450e-ac4b-22c5b7228702   ext3                                     
/dev/sda3        1c46bd12-6933-43c3-b377-2ec3b9ebbf7d   ext3                                     
/dev/sda4        d49e905d-1363-47e7-96da-f3b95df2504a   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=083535b2-fc66-450e-ac4b-22c5b7228702 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=083535b2-fc66-450e-ac4b-22c5b7228702

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic
uuid        083535b2-fc66-450e-ac4b-22c5b7228702
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=083535b2-fc66-450e-ac4b-22c5b7228702 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-27-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic (recovery mode)
uuid        083535b2-fc66-450e-ac4b-22c5b7228702
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=083535b2-fc66-450e-ac4b-22c5b7228702 ro  single
initrd        /boot/initrd.img-2.6.32-27-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        083535b2-fc66-450e-ac4b-22c5b7228702
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=083535b2-fc66-450e-ac4b-22c5b7228702 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=1c46bd12-6933-43c3-b377-2ec3b9ebbf7d /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=d49e905d-1363-47e7-96da-f3b95df2504a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   3.9GB: boot/grub/core.img
   4.0GB: boot/grub/menu.lst
   3.9GB: boot/grub/stage2
   4.3GB: boot/initrd.img-2.6.32-27-generic
   4.3GB: boot/vmlinuz-2.6.32-27-generic

```

---

### Post by anselmo_crowley on 2011-02-05
That's what I got. Thanks for the help. :)

---

### Post by Rubi1200 on 2011-02-05
Okay, I have to go out for a couple of hours, but will look back in as soon as I get home.

Meantime, this is what I would like you to do:

You have a mix of GRUB-legacy and GRUB2; not a good situation.

You need to purge and reinstall GRUB:
detailed instructions here:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

This what you need to do from the LiveCD:
```
sudo mkdir /mnt/temp 
sudo mount /dev/sda2 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done 
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```

This will bring you to a root prompt, then run these commands:
```
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
update-grub 
exit
for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
```
Then reboot and you should be back into Ubuntu.

The problem with sda3 is that there are file system errors. We can take care of that later hopefully.

Last thing, did you move partitions around? There is no sda1 and fstab reports that the root file system was on sda4?

What you can also do once you reboot and you can get in is to post the output of this command:
```
sudo blkid
```.

Be back soon!

---

### Post by anselmo_crowley on 2011-02-05
OK! Thanks so much! I'll do everything you said and I'll get back to you when it's done! Thanks! :D

---

### Post by peculiar penguin on 2011-02-05
Please boot the LiveCD and backup her data to an external drive or a network share before you further muck up things.

---

### Post by anselmo_crowley on 2011-02-05
But I can't access her files! That's basically the issue. When I use the LiveCD it tells me it can't mount the partition. Right now I have no access to any of her data. :(

---

### Post by ChipOManiac on 2011-02-05
> **anselmo_crowley said:**
> When I use the LiveCD it tells me it can't mount the partition. Right now I have no access to any of her data. :(

Does It Give Any Detailed Information When It Tells You That You Can't Mount It?

Okay I Went Back An Looked At Post #13... Is "sda3" The Partition You're Trying To Access?

---

### Post by marin123 on 2011-02-05
```
sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

i think this is what happened to your /home.

you can run disk recovery to save any data.

---

### Post by hansolo4949 on 2011-02-05
If all you are worried about is the data, you should be okay. Have you managed to mount the partition in the livecd yet? Because if you can get into the partition, you can get the data, if you know the right folder to look under.I think that's what you should concentrate on first, then worry about getting Ubuntu fixed:).

---

### Post by anselmo_crowley on 2011-02-05
I tried to purge and reinstall the GRUB but I got this:

```
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
The following packages will be REMOVED:
  grub* grub-common*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 5,267kB disk space will be freed.
Do you want to continue [Y/n]? y
/bin/sh: /usr/sbin/dpkg-preconfigure: Input/output error
dpkg: warning: 'ldconfig' not found on PATH.
dpkg: warning: 'start-stop-daemon' not found on PATH.
dpkg: 2 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

What went wrong? What am I supposed to do after that?

---

### Post by anselmo_crowley on 2011-02-05
> **marin123 said:**
> ```
sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```i think this is what happened to your /home.

you can run disk recovery to save any data.

What is disk recovery? How do I run it? Thanks!

---

### Post by anselmo_crowley on 2011-02-05
> **ChipOManiac said:**
> 
Is "sda3" The Partition You're Trying To Access?

Yes, sda3 is the partition with all her files, and the one I can't access. Thanks for answering!

---

### Post by anselmo_crowley on 2011-02-05
> **hansolo4949 said:**
> If all you are worried about is the data, you should be okay. Have you managed to mount the partition in the livecd yet? Because if you can get into the partition, you can get the data, if you know the right folder to look under.I think that's what you should concentrate on first, then worry about getting Ubuntu fixed:).

I still can't mount the partition. Maybe if I could just retrieve her files someway and then reinstall Ubuntu from scratch it wouldn't be so bad. Thanks for answering! :)

---

### Post by Rubi1200 on 2011-02-05
I don't know what went wrong with the purge and reinstall except that perhaps there is also file system damage on the root partition.

First, exit the chroot with these commands:
```
exit
for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
```You could try installing a different bootloader:

```
sudo apt-get update
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```ignore all the warning messages, we just want lilo installed in the MBR.

Then reboot and tell us what happens.

---

### Post by anselmo_crowley on 2011-02-05
> **Rubi1200 said:**
> 
Then reboot and tell us what happens.

I rebooted and a quick message appeared:

No boot signature in partition.

Then, this is what i got:

Yukon PXE v3.5.2.3 (20050803)
(C)Copyright 2003-2005 Marvell(R). All rights reserved.

Pre-boot eXecution Environment (PXE) v2.1
(C)Copyright 1997-2000 Intel Corporation.
PXE-E61:Media test failure, check cable
PXE-M0F: Exiting PXE ROM.

And that's it. I'm guessing this isn't OK. :|

---

### Post by oldfred on 2011-02-05
I am not sure much works with a partition error. You need to resolve that first.

From liveCD so everything is unmounted,swap off if necessary, change sda3 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sda3
if errors:
sudo e2fsck -f -y -v /dev/sda3

---

### Post by Rubi1200 on 2011-02-05
I would definitely follow oldfred's advice on this one.

 If that does not work then try with backup superblocks or testdisk. It  should be recoverable, but then it is photorec if all else fails.

---

### Post by anselmo_crowley on 2011-02-05
I used ```
sudo e2fsck -C0 -p -f -v /dev/sda3
``` and I got this:
```
e2fsck: A block group is missing an inode table while checking ext3 journal for /dev/sda3
```

When I used ```
sudo e2fsck -f -y -v /dev/sda3
``` it did some stuff for a while but then it showed me this:

```
Relocating group 49's inode bitmap from 1605637 to 1606659...
Error allocating 509 contiguous block(s) in block group 49 for inode table: Could not allocate block in ext2 filesystem
Relocating group 81's block bitmap from 2654212 to 2655234...
Relocating group 81's inode bitmap from 2654213 to 2655235...
Relocating group 81's inode table from 2654214 to 2657717...
Relocating group 125's block bitmap from 4096004 to 4097026...
Relocating group 125's inode bitmap from 4096005 to 4097027...
Error allocating 509 contiguous block(s) in block group 125 for inode table: Could not allocate block in ext2 filesystem
Relocating group 243's block bitmap from 7962628 to 7963650...
Relocating group 243's inode bitmap from 7962629 to 7963651...
Relocating group 243's inode table from 7962633 to 7963652...
e2fsck: aborted
```

:(

---

### Post by oldfred on 2011-02-05
You can try with backup superblocks.

List backup superblocks:
sudo dumpe2fs /dev/sda3 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda3

---

### Post by anselmo_crowley on 2011-02-05
```
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda3 | grep -i backup
dumpe2fs 1.41.9 (22-Aug-2009)
dumpe2fs: A block group is missing an inode table while reading journal inode
Journal **[COLOR=Red]backup[/COLOR]**:           inode blocks
```

That's all I got from that last one. Was it supposed to give me a number?

---

### Post by oldfred on 2011-02-05
You should get a long list of backup inodes.

I might try using testdisk to see if it can see past the error.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by anselmo_crowley on 2011-02-05
Well, I used PhotoRec and I recovered some stuff but it's all messed up. I organized it with PhotoRec Sorter but it's still kinda wrong. I didn't get like complete songs, just small files with bits of music. Same with other file types.
I know it's progress but I still feel really bad because most of the information is gone.
Is this the last resort I've got?
Isn't there any other way to fix the file system or the partitions or something? Even if it's hard work, I'll do it. (I don't want this to be a burden for any of you though, I just need directions or something).
Right now TestDisk is doing a deep search and it's taking a long time. I don't know if this is good or bad. What should I do after this? ReWrite the partition table? I read the Step by Step guide and that's what I kinda understood.
So, anyway. Thanks to everybody who tried to help and if someone knows if there's anything else I could do, I'd highly appreciate it!
Thanks so much!

---

### Post by anselmo_crowley on 2011-02-05
It has finished the search and it says this:

The harddisk size: HD jumpers setting, BIOS detection..

The following partition can't be recovered:

Partition         Start          End     Size in sectors
Linux       5842 0 1 10292 254 60   71505312

---

### Post by anselmo_crowley on 2011-02-05
Anyone knows if there's any software that I can use to extract her files. But with folders and everything. Not just bits and pieces of files. I was searching the web and found GetDataBack, but it costs and only works on FAT and NTFS. Anybody knows there something similar to it for ext3?
Thanks!

---

### Post by anselmo_crowley on 2011-02-06
Anyone? :(

---

### Post by Rubi1200 on 2011-02-06
I am really sorry that this has not worked out very well.

I also want to apologize to you if any advice I gave you might have exacerbated the situation.

You can take a look here and try some of the other data recovery tools mentioned, though I do not know how well they work.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

In the worst case, you might have to consider taking the drive to a professional recovery service (but this may cost thousands of dollars from what I have read).

I really hope you manage to salvage some more data.

---

### Post by anselmo_crowley on 2011-02-06
No worries, man. Thanks for the help! Anyway, I don't think it's worse than it was.
I already tried some of the things in the DataRecovery link, but they didn't work. I'll keep trying and if anything weird (or HOPEFULLY a solution) comes up, I'll post it here!
Thanks for all the effort and help!

---

### Post by Rubi1200 on 2011-02-06
I have been doing some reading and it seems that recovering files from ext3 is not that simple.

But, I did find this:
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

and this:
[http://www.linuxquestions.org/questions/linux-distributions-5/best-live-rescue-cd-for-ext3-data-recovery-417651/](http://www.linuxquestions.org/questions/linux-distributions-5/best-live-rescue-cd-for-ext3-data-recovery-417651/)

I hope it might prove useful in some way.

---

### Post by oldfred on 2011-02-06
Just to see if hard drive is on its last legs, would you check System, Administration, Disk Utility and click on drive. Under SMART see what it says. I do not know details but it should give some indication if it has lots of errors. Small numbers of errors supposedly are not a major problem.

---

### Post by randiroo76073 on 2011-02-06
I'm kinda scratchin for this. Let's go back to basics(kiss),can you beg/borrow an external usb hard disk from someone, it would be really helpful. From the live cd desktop open a terminal and run:  " sudo nautilus " . Once nautilus comes up navigate to the "media" folder, right click & make a new folder called "sda3". Then navigate to the file "/etc/fstab" and open, add this line to it somewhere in the middle:  " /dev/sda3  /media/sda3  ext3  relatime  0  2 " save & close. Back to terminal & enter: " sudo mount /dev/sda3 " If this is successful you should be able to access the files in nautilus and move them to an external source. I'm not sure how much of the data this will recover, if any, but it's worth a shot. If you get in try transfering 1 folder at a time, less likely to get mixups/overwrites.
Good luck and hope it works

---

### Post by anselmo_crowley on 2011-02-06
OMG Thanks for still being here! I hadn't checked the forum, but it's nice to see you're still trying to help! Thanks so much! :D

> **Rubi1200 said:**
> But, I did find this:
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html]("http://www.xs4all.nl/%7Ecarlo17/howto/undelete_ext3.html")
and this:
[http://www.linuxquestions.org/questi...covery-417651/]("http://www.linuxquestions.org/questions/linux-distributions-5/best-live-rescue-cd-for-ext3-data-recovery-417651/")

The first link says it doesn't deal with a corrupted file system, just deleted files and the second one has links to some really interesting software but they're for ext2, does that mean they'll work with ext3 as well? Besides, they're *.tar.gz files and I have no idea what to do with them. Are those the files you have to "build" or something?

> **oldfred said:**
> Just to see if hard drive is on its last legs, would you check System, Administration, Disk Utility and click on drive. Under SMART see what it says.

Under SMART status it says Not Supported. :(

> **randiroo76073 said:**
> I'm kinda scratchin for this. Let's go  back to basics(kiss),can you beg/borrow an external usb hard disk from  someone, it would be really helpful.

I did it and after sudo mount -dev-sda3 it displayed this:

```
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
 missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
```I typed dmesg | tail in the terminal and at the end is said this:

```
 [   1340.934828 ] EXT3-fs (sda3): error: unrecognized mount option "realtime" or missing value
```Thanks for still being here trying to help! :D

---

### Post by randiroo76073 on 2011-02-06
Again, barking at trees. Try changing the "ext3" to "ext4" or "ext2" in /etc/fstab, maybe it'll shake something loose.

The spelling on that is "relatime" check that too.

---

### Post by topher-t-mill on 2011-02-06
This is a salutory tale, which we all learn the hard way: back up important files at least once and possibly twice! especially before doing risky manouvres. I once had to manually recover loads of  important files in Windows when I messed with a zip drive.
t sounds like a re install job to me. But you could copy the partition to another drive using Gparted before you make that decision.

---

### Post by anselmo_crowley on 2011-02-06
It's "relatime"! Sorry. My bad.
I changed the spelling and it gave me this:

```
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
```

" dmesg | tail " gave me this:

```
 [  423.500787] EXT3-fs error (device sda3): ext3_check_descriptors: Block bitmap
for group 1 not in group (block 0)!
[  423.501174] EXT3-fs (sda3): error: group descriptors corrupted
```

ext2 and ext4 gave me the same thing. :(

---

### Post by anselmo_crowley on 2011-02-06
> **topher-t-mill said:**
> This is a salutory tale, which we all learn the hard way: back up important files at least once and possibly twice! especially before doing risky manouvres. I once had to manually recover loads of  important files in Windows when I messed with a zip drive.
t sounds like a re install job to me. But you could copy the partition to another drive using Gparted before you make that decision.

I know! If it would have happened to my own files I wouldn't feel so bad, because I'd know I messed up my own things. But I feel terrible because it's my sister who lost everything because of me. :(

---

### Post by topher-t-mill on 2011-02-06
I do understand!

---

### Post by matt_symes on 2011-02-06
Hi

There may be something else you can try. I have never used this technique so use at your own risk and it has risks.

From the LiveCD make sure the partition is _not_ mounted and....

1. Get the block size

```
sudo dumpe2fs /dev/sda3 | grep "block size" -i
```

On my PC this returns 

```
Block size:               **4096**
```

2. Format the superblocks. This will not format the whole partition just the superblocks. This is where you need the block size above

From the man page of mke2fs.....

> S     Write superblock and group descriptors only.  This is useful  if
              all  of the superblock and backup superblocks are corrupted, and
              a last-ditch recovery method is desired.  It  causes  mke2fs  to
              reinitialize  the  superblock  and  group descriptors, while not
              touching the inode table and the block and inode  bitmaps.   The
              e2fsck  program  should  be run immediately after this option is
              used, and there is no guarantee that any data will  be  salvage&#8208;
              able.   It  is critical to specify the correct filesystem block&#8208;
              size when using this option, or there is no chance of recovery.

Use the correct block size!!!!!!!

```
sudo mke2fs -S -b **4096** -v /dev/sda3
```

3. Run fsck on the partition to check the inodes

```
sudo e2fsck -y -f -v -C 0 /dev/sda3
```

4. Rebuild the journal

```
sudo tune2fs -j /dev/sd3
```

Understand that if this does not work your looking at a reinstall.

It's very much a last ditch attempt at recovery and might not work.

Best of luck to you.

Kind regards

---

### Post by anselmo_crowley on 2011-02-06
Thanks for the advice! I did it and now when I try to mount, it displays a message that reads:

Unable to mount 37 GB Filesystem
Error mounting: mount: Stale NFS file handle

So, I'm guessing that was the last resort and I'll need to reinstall from scratch. :(

---

### Post by anselmo_crowley on 2011-02-06
I think that superblock thing formatted the partition. I can't mount it but now it says there are 724.31 MB used and 33.39GB unused. Did I just format the whole partition? Because I'm seriously considering taking the computer to one of those recovery services, even if it costs.

---

### Post by matt_symes on 2011-02-06
Hi 

Try unmounting and remounting the drive.

Kind regard

---

### Post by anselmo_crowley on 2011-02-06
It displays the same message and GParted says there are 724. 31 MB used and 33.39 GB free.

---

### Post by matt_symes on 2011-02-06
Hi

> Did I just format the whole partition?
 
No. That should have just recreated the superblock structures. That is why i quoted the man page for mke2fs. As the man pages suggest it is a last ditch method.

I think professional data recovery might be the best way forward. At least you got off as much as you could using test disc. I would always recommend using test disc before the technique i posted.

I think the file system has had it. Sorry. 

Next time backup the hard drive before making changes to partitions. Use CloneZilla or some such.

Kind regards

---

### Post by anselmo_crowley on 2011-02-06
Yeah. I think the data is definitely gone now. I've just found a Windows freeware from Disk Internals called Linux Recovery. I'll see if it works.

Thanks anyway.

---

### Post by marshag63 on 2011-02-06
Just asking because I'm curious - was sda1 your windows partition?
Sda2 is your original ubuntu install?

MDG

---

### Post by anselmo_crowley on 2011-02-06
> **marshag63 said:**
> Just asking because I'm curious - was sda1 your windows partition?
Sda2 is your original ubuntu install?

MDG

Yes, I think that's the way it used to be.

---

### Post by anselmo_crowley on 2011-02-06
Before the partition was formatted I created a *.dd image of it. Does anyone know how can I replace the partition with that image so I can use Disk Internals Linux Recovery on it?
Thanks!

---

### Post by anselmo_crowley on 2011-02-07
Anyone?

---

### Post by tredegar on 2011-02-07
> Before the partition was formatted I created a *.dd image of it. Does anyone know how can I replace the partition with that image so I can use Disk Internals Linux Recovery on it?
If you have a dd image of a partition you have now messed up, then you have all the data still in that image.

Just mount the image  with the **loop** and _read-only_ options and your files should be all be there

```

# Make a mountpoint
sudo mkdir /mnt/help
# Mount the dd image, read only
sudo mount -o loop,ro   /path/to/image.dd   /mnt/help
# list the files (if any!)
ls  /mnt/help
```

---

