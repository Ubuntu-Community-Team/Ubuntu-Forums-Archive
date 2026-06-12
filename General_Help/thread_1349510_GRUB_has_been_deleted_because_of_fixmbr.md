---
title: "GRUB has been deleted because of fixmbr?"
date: 2009-12-08
forum: General Help
---

### Post by searchfgold6789 on 2009-12-08
Hey all,
One day I had it in my head to create an MS-DOS startup disk. I did so, and made a small (a few megabytes) FAT12 partition on my Windows-dedicated hard disk, so I could save QBasic stuff. I had to shrink my Windows partition to do this. When I rebooted my computer would boot into DOS, of course, but when I tried to access Windows XP Home from Grub it said:
```
Error 22


No such partition
```(Lesson learned here: GRUB stores partition data and won't boot unless partition matches what it has on record.)
Then, I tried to do a fixboot from the Windows CD, same error. Then I did a few bootcfg things, still same. Then I did a fixmbr, which of course kicked GRUB's @$$ and now it says:
```
Initializing Intel Boot Agent Version 2.2..Press any key to boot from CD.....Error Loading Operating System
```and if I unplug the Linux hard drive's cable, it'll boot into Windows like nothing ever happened. How do I get GRUB back into working order?
Cheers!
 - Rich

---

### Post by searchfgold6789 on 2009-12-08
Anyone? [-o< :-({|=

---

### Post by rahilm on 2009-12-08
Try fixing grub from the Live-CD.

If you have Karmic Live-CD and Karmic installed
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

See section 12

---

### Post by searchfgold6789 on 2009-12-08
> **rahilm said:**
> Try fixing grub from the Live-CD.

If you have Karmic Live-CD and Karmic installed
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

See section 12
I have Karmic, um, installed and not booting, but I don't have the live CD. Is it possible to do this repair from the Jaunty CD? (I have installed Jaunty and did the whole system-release-upgrade-thing.)

---

### Post by rahilm on 2009-12-08
> **searchfgold6789 said:**
> I have Karmic, um, installed and not booting, but I don't have the live CD. Is it possible to do this repair from the Jaunty CD? (I have installed Jaunty and did the whole system-release-upgrade-thing.)
Oh dear god.

I have no idea how to get to the grub menu in jaunty. All i can say is that once you make it there and have successfully booted into karmic once. The MBR can definitely be fixed inside karmic.

I am not much experienced but i'll look into it

---

### Post by bumanie on 2009-12-08
If you are still running grub-legacy (opposed to grub 2), you should be able to reinstall grub from the jaunty live cd, but the method of reinstalling is different. Follow [this]("http://ubuntuforums.org/showthread.php?t=224351") ONLY if you have grub-legacy running. I have read that by using upgrade-manager -d that grub-legacy remains and is not replaced by grub 2, but I have been running grub 2 since jaunty, so can't say from personal experience. If you have grub 2, you will probably have to download and burn a karmic cd and then look at the first link sent to you.

---

### Post by rahilm on 2009-12-08
Okay..Its all about taking chances. I have three solutions for this. One is tested while two are not.
Solution 1:
Download the Karmic live-cd and follow my previous instructions

Solution 2:
Create another partition and install Ubuntu 9.04 on it.

Solution 3:
Boot with the Live-CD and install grub2 in it. Then follow my previous instructions.

I'll be trying another serious solution in my virtualbox. But it'll take much time. What can i say. I like playing with Grub

---

### Post by searchfgold6789 on 2009-12-08
> Solution 3:
Boot with the Live-CD and install grub2 in it. Then follow my previous instructions.
This appeals to me. You probably mean that I should boot from the live CD, open up a terminal and run some commands to install grub, which I forget...what are they?

---

### Post by oldfred on 2009-12-08
Pick your poison. This shows how to reinstall all the boot loaders, but the commands have to match the CD you have.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by searchfgold6789 on 2009-12-08
<.<
>.>
<.<
>.<
I will try that from the Live CD.
I will not forget to mark this thread as solved, when it is solved (It will be solved, right?).

---

### Post by searchfgold6789 on 2009-12-08
OK, almost there. Grub still loads OK, but now it's turning more into a Windows problem, as I thought it would, which is why I first listed this thread as "other".

I googled until my googler was sore, and I eventually reinstalled Grub. One of you diligent Ubuntu people had already posted a link to the page anyway, sorta, but in any case when I try to select "Windows XP Home Edition" from the Grub menu, it still comes up with:
```
Error 22:


No such partition
```
Is there anyone else out there willing to google this for me? I have to go to bed.;) Thanks! :D

---

### Post by searchfgold6789 on 2009-12-08
Should I start a new thread on this?

---

### Post by oldfred on 2009-12-09
This is still a grub error. See Herman's page.
[http://members.iinet.net.au/~herman546/p15.html#22](http://members.iinet.net.au/~herman546/p15.html#22)

This is saying that the windows stanza is chainbooting to a incorrect partition.

Lets take a look at you entire setup.

Boot Info Script 0.39 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions
  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 [http://ubuntuforums.org/showthread.php?p=8279056#1](http://ubuntuforums.org/showthread.php?p=8279056#1)
  caljohnsmith
 [http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3) 
cd to directory saved to: 
chmod 755 boot_info_script039.sh 
sudo ./boot_info_script039.sh 
or as example if on desktop from liveCD download 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by rahilm on 2009-12-09
Though I think nobody cares about it. I am having a hard time experimenting with grub-legacy. But since you have successfully done it. Hats off!.
Be sure to post the RESULTS.txt file. It helped me once.

---

### Post by searchfgold6789 on 2009-12-09
> **oldfred said:**
> This is still a grub error. See Herman's page.
[http://members.iinet.net.au/~herman546/p15.html#22]("http://members.iinet.net.au/%7Eherman546/p15.html#22")

This is saying that the windows stanza is chainbooting to a incorrect partition.

Lets take a look at you entire setup.

Boot Info Script 0.39 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions
  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 [http://ubuntuforums.org/showthread.php?p=8279056#1](http://ubuntuforums.org/showthread.php?p=8279056#1)
  caljohnsmith
 [http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3) 
cd to directory saved to: 
chmod 755 boot_info_script039.sh 
sudo ./boot_info_script039.sh 
or as example if on desktop from liveCD download 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.
ummm ok, just so I don't screw something up, I:

[LIST=1]
[*]Go to the first link and download the software they have there
[*]click one of the three following links for instructions on how to use the software
[*]type in the terminal:
[/LIST]

[LIST]
[*]chmod 755 boot_info_script039.sh, then
[*]sudo ./boot_info_script039.sh
[/LIST]
replacing ./ with the location i saved a results.txt file to.
then open the file, and copy and paste the entirety of it wrapped in code things back here.
Sorry, I'm not that linux-savvy. Could it be more step-by-step?
thanks

---

### Post by ranch hand on 2009-12-09
Yes.

---

### Post by searchfgold6789 on 2009-12-10
Here Goes:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 38109247 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30003240960 bytes
255 heads, 63 sectors/track, 3647 cylinders, total 58600080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc945c945

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    56,082,914    56,082,852  83 Linux
/dev/sda2          56,082,915    58,589,054     2,506,140   5 Extended
/dev/sda5          56,082,978    58,589,054     2,506,077  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb1a0b1a0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   240,107,489   240,107,427   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="98113b03-bf95-45fd-bae5-c032a8fc5683" TYPE="ext3" 
/dev/sda5: UUID="724532ba-aa91-402f-afc3-a50c45ccd9f1" TYPE="swap" 
/dev/sdb1: UUID="01CA4935A4825660" LABEL="XP Home" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/a/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=a)
/dev/sdb1 on /media/XP Home type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
# kopt=root=UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98113b03-bf95-45fd-bae5-c032a8fc5683

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
uuid        98113b03-bf95-45fd-bae5-c032a8fc5683
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        98113b03-bf95-45fd-bae5-c032a8fc5683
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        98113b03-bf95-45fd-bae5-c032a8fc5683
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        98113b03-bf95-45fd-bae5-c032a8fc5683
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        98113b03-bf95-45fd-bae5-c032a8fc5683
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        98113b03-bf95-45fd-bae5-c032a8fc5683
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        98113b03-bf95-45fd-bae5-c032a8fc5683
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        98113b03-bf95-45fd-bae5-c032a8fc5683
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        98113b03-bf95-45fd-bae5-c032a8fc5683
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,1)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


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
UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=724532ba-aa91-402f-afc3-a50c45ccd9f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
```

---

### Post by rahilm on 2009-12-10
There is a menu.lst file in you /boot/grub directory. Take a backup of it.
Then edit ist
```
sudo gedit /boot/grub/menu.lst
```Look for the Windows entry
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,1)

change it to
rootnoverify (hd1,0)


I cannot guarantee it will work. Its what I do when i am in such problems

If that doesn't work try changing the entire entry to:
```

title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by oldfred on 2009-12-10
I see you now have windows in the MBR of both drives. You will have to reinstall grub to sda to get Ubuntu to boot. I would leave windows in the MBR of sdb and if sda does not work in the future you can switch drives in BIOS and still boot.

Your windows stanza shows rootnoverify    (hd1,1) but old grub counts from zero so windows is in (hd1,0) and that is why you are getting error 22 since there is not partition 1.

Besure to follow the instruction for grub legacy not grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

backup & edit menu.lst
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

---

### Post by ranch hand on 2009-12-10
OK, you are running grub-legacy so this must be an upgrade fro m 9.04.  This is fine.  The recovery procedures are completely different.  Everything looks good so doing this should work fine.

You need to boot to a live CD for an Ubuntu that uses grub-legacy, hopefully you have your old 9.04  CD.

When you are in it run, in terminal the following commands in this order;
```

sudo grub
(this will get you a grub prompt)
grub> fine /boot/grub/stage1
(this will list where you have grub results out to be like below)
(hd0,0)
grub> root (hd0,0)
(this is assuming that it comes up with that in the "find" command)
grub> setup (hd0)
grub> quit

```
You should be fixed at this point so restart your box and see.

---

### Post by rahilm on 2009-12-10
> **oldfred said:**
> 
Your windows stanza shows rootnoverify    (hd1,1) but old grub counts from zero so windows is in (hd1,0) and that is why you are getting error 22 since there is not partition 1.

Precisely
> **oldfred said:**
> 
backup & edit menu.lst
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

---

### Post by searchfgold6789 on 2009-12-10
I wound up editing my "menu.lst" file, which worked beutifully but was kind of a letdown because I would have loved the try ranch hand's technical approach with the grub prompt. My next quest is to get DOS running again, find out how to do the fat12 partition thing, and how much disk space is needed to do that [SIZE=1](Wait wait dont tell me!)[/SIZE] Thanks so much for all the help.
See you all in a few days with my next tragic computer issue!
 - Richie

---

