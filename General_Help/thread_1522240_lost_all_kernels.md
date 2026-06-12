---
title: "lost all kernels"
date: 2010-07-01
forum: General Help
---

### Post by mambo801 on 2010-07-01
hi guys

i'm a wubi 9.10 ubuntu user. i was using ubuntu and well it froze (this is not normal) and so i rebooted the computer. after i selected ubuntu as normal, instead of being given the next menu screen with all the kernels to pick from. i now get 'what i think' is the grub rescue promt screen. the screen just tells me "Grub 1.97~beta4,  Minimal  BASH command line...goes on about TAB etc."

i have tried alot of different things but i am a newbie and am now asking for help.

how can i rescue my ubuntu OS??

cheers mambo801

---

### Post by duanedesign on 2010-07-01
If GRUB 2 fails to find a usable grub.cfg file it should revert to the grub-rescue mode. The command line prompt will display grub-rescue>  and no menu will be displayed. From this command line the user can attempt to manually enter the instructions to boot to a usable system. 

If the command line prompt is not already active press "c" to enter the Command Line mode. You will see the GRUB 2 prompt: grub>  or grub rescue>

** ls**  -  Run ls to see the devices recognized by GRUB 2. Example: (hd0) (hd0,1) (hd1,5) In this example sda, sda1, sdb5 are recognized.

**Boot to most recent kernel - Wubi instructions**
Press Return after each command. Not all commands will return something.
```
set root=(loop0) 
```
Type with correct X,Y results from the ls command.	
Example: linux /vmlinuz root=/dev/sda3 loop... 
```
linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro 
```
Select the latest initrd image.
```
initrd /initrd.img
```
Boot to the latest kernel on the selected partition.
```
boot
```

These changes are not permanent. After successfully booting into the system the user should run sudo update-grub and inspect the GRUB 2 configuration file (/boot//grub/grub.cfg). For problems with booting the main linux kernel, ensure the search, linux, and initrd lines in the [### BEGIN /etc/grub.d/10_linux ###] section of the file now correctly point to the correct locations. The user may need to reinstall GRUB 2 (sudo grub-install /dev/sdX). 

Information from:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

---

### Post by mambo801 on 2010-07-04
Hi and thanks for your reply.

To start with i'm now not sure if it is the grub-rescue promt that i'm getting.. so ive written everything down to hopefully help you help me.

so after i choose ubuntu from the selection screen, instead of showing me the kernel screen for me to select from i get the following:

[CENTER]GNU GRUB version 1.97~beta4
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.]

[LEFT]sh:grub>


So the above "sh:grub>" i don't think is the correct grub promt you've refered too and even after pressing TAB to see what options i had and attempting to press "c" to enter the command line mode i did not get the grub> or grub rescue>.

If you need me to post the options i was given by pressing TAB then please let me know and i'll write them all down too.

however i did follow your instructions anyway and i got the following responses after each code line.

[/LEFT]
[/CENTER]

> **duanedesign said:**
> 

** ls**  -  Run ls to see the devices recognized by GRUB 2. Example: (hd0) (hd0,1) (hd1,5) In this example sda, sda1, sdb5 are recognized.

[COLOR=Red]I entered the "ls" command as follows:

sh:grub> ls 

and got :[/COLOR]
```
(hd0) (hd0,3) (hd0,2) (hd0,1) (fd0)
sh:grub>
```[COLOR=Red]i then entered
[/COLOR]```
set root=(loop0) 
```[COLOR=Red]sh:grub> set root(loop0)

and got

[/COLOR]```
sh:grub>
```like you said not all commands will return something.

[COLOR=Red]i then entered[/COLOR]
```
linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro 
```[COLOR=Red]sh:grub> linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro[/COLOR]

[COLOR=Red]and got

[/COLOR]```
error: no such disk
sh:grub>
```i realise that at this appoint some thing is not correct but i continued with your instructions any way.

[COLOR=Red]i entered[/COLOR]
```
initrd /initrd.img
```[COLOR=Red]sh:grub> initrd /initrd.img[/COLOR]

[COLOR=Red]and got[/COLOR]

```
error: you need to load the kernel first.
sh:grub>
```[COLOR=Red]i entered
[/COLOR]```
boot
```[COLOR=Red]sh:grub> boot

and got[COLOR=Black]

[/COLOR][/COLOR]```
error: no loaded kernel
sh:grub>
```

I understand that it may have something to do with me indicating the incorrect drive ie "sda1" that ubuntu should be running on. however, the other thing i can say is that after starting up windows XP i checked on my c: drive, which is the hard drive ubuntu is installed on, to check if the folder and file "/ubuntu/disks/root.disk" actually exists on my system and i can confirm that they are/were there. i say were becuase after the second time i started up windows XP it decided to run the chkdisk thing and i watched it to see what it was doing. although it didn't delete the folders it did delete the file "root.disk" from the folder "disks".

i thank anyone who may be able to help me out.
cheers mambo801

---

### Post by bcbc on 2010-07-04
if chkdsk deleted the root.disk it's probably sitting in c:\found.000 (hidden folder). The [wubi guide]("https://wiki.ubuntu.com/WubiGuide") talks about this. So you'll have to copy it out of there. 

The root.disk itself may be corrupt. You can run a fsck on it - refer to the wubi guide for details.

What I do to manually boot wubi (assuming root.disk is on /dev/sda1):
```
insmod ntfs
set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot
```

PS you can check if the wubi files are on hd0,1 (/dev/sda1) by running the following and checking where ubuntu and wubildr are listed
```
ls (hd0,1)/
```

---

### Post by mambo801 on 2010-07-04
hi again

i forgot to mention earlier that i had checked the found.0000 folder, and that root.disk was not there. the only thing that was in the was a folder call "dir0000.chk" containing 4 files
_CACHE_001_
_CACHE_002_
_CACHE_003_
_CACHE_MAP_

I did however read that i can reset the root.disk file by doing a reinstall of wubi.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20reinstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20reinstall%20Wubi?)

But i'm not sure if this will erase the folders i'm trying to recover???

cheers and thankyou for your time and help

mambo801

---

### Post by bcbc on 2010-07-04
> **mambo801 said:**
> hi again

i forgot to mention earlier that i had checked the found.0000 folder, and that root.disk was not there. the only thing that was in the was a folder call "dir0000.chk" containing 4 files
_CACHE_001_
_CACHE_002_
_CACHE_003_
_CACHE_MAP_

I did however read that i can reset the root.disk file by doing a reinstall of wubi.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20reinstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20reinstall%20Wubi?)

But i'm not sure if this will erase the folders i'm trying to recover???

cheers and thankyou for your time and help

mambo801

The root.disk contains everything important(the ubuntu os and all your data and settings). Reinstalling will 'reset it' but your data will be gone. 

So your only option to get your data back is to recover the old root.disk.

In any of those files you mentioned, did any match the size of the old root.disk? Has your available space remained the same since the root.disk disappeared or have you gained 5gb (or whatever size the install was). This should give you a clue whether the file is still around.
If it is truly gone, then the only alternative would be some data recovery software. I suppose it depends on how important the data is to you.

---

### Post by mambo801 on 2010-07-06
cheers thanks for your help.

i'm still accessing how important the files are plus trying to remember what was on there as well.

can you tell me can this sort of thing happen to a normal install of Ubuntu?? instead of the wubi way.

and if it is possible to happen on a normal install, how can you back up the root.disk file or equivalent??

also im obviously considering doing a normal install, however the partition i'd like to install on is currently the XP operating system partition. when i run the installation cd, will it allow me to alter the partition to fit Ubuntu on it as well? I am running a 250gig hard drive. it is partitioned at the moment into three drives. the XP OS, which has about 55gig still free space. a drive for personal files and the third is for media files and work space for converting files and make .iso.

thank you for your time 

cheers mambo801

---

### Post by bcbc on 2010-07-06
> **mambo801 said:**
> cheers thanks for your help.

i'm still accessing how important the files are plus trying to remember what was on there as well.

can you tell me can this sort of thing happen to a normal install of Ubuntu?? instead of the wubi way.

and if it is possible to happen on a normal install, how can you back up the root.disk file or equivalent??

also im obviously considering doing a normal install, however the partition i'd like to install on is currently the XP operating system partition. when i run the installation cd, will it allow me to alter the partition to fit Ubuntu on it as well? I am running a 250gig hard drive. it is partitioned at the moment into three drives. the XP OS, which has about 55gig still free space. a drive for personal files and the third is for media files and work space for converting files and make .iso.

thank you for your time 

cheers mambo801

This problem is unique to wubi - since it's installed on a virtual disk that is a single file, and so a corruption on the file can be catastrophic. e.g. normally, if you are updating a file and the power goes out, there's a chance that you just lost your changes, or that the that file alone is corrupt and everything else is fine. With wubi, if the root.disk is corrupt, you can lose everything.

Even with a normal install, you still need to backup important data. The fact is your drive could fail at any time. If the data is important, back it up. There is a guide on backing up from ubuntu: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

To install on a partition that contains XP, you want to defrag from XP a at least twice. Then you can let the installer partition - or you can boot a live CD and use gparted to create your partitions. When I did it, I partitioned manually using gparted on a live cd and then rebooted into windows to make sure everything was fine, before installing. I don't know if that's necessary - there are a lot of guides out there about this.

Good luck

---

