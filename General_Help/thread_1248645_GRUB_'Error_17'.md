---
title: "GRUB: 'Error 17'"
date: 2009-08-24
forum: General Help
---

### Post by doggitydogs on 2009-08-24
Um... hi.
I dual-booted Ubuntu with my Windows XP installation yesterday, following the instructions at this page:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
However, I had installed a bootscreen to XP. This created two entries in my boot.ini file.
As such, the GRUB installation, instead of creating a direct entry to XP, created an entry to the XP loader.
I booted into Ubuntu and messed around with it.
I then rebooted into XP.
Today, I installed several drivers in XP in hope to be able to read my ext3 Ubuntu partition, but to no avail. I didn't make much of this, and hard-rebooted (it doesn't matter why) to try to enter the Ubuntu installation.
However, it booted into a screen that said:
```
GRUB loading: stage1.5

GRUB [something]
Error 17
```This rendered my computer unbootable. (I am writing this from my Ubuntu live CD.)

Is there any way to fix this, or to bypass GRUB and boot directly from the first partition, with the XP loader?
(I do have a partitioning utility available, and I can burn CDs and make floppy disks (ha.))

HALP.

(I am double-posting this at [http://dynamicdrive.com/forums/showthread.php?p=203904#post203904](http://dynamicdrive.com/forums/showthread.php?p=203904#post203904).)

---

### Post by Bucky Ball on 2009-08-24
Wrong approach. Grub 17 error means you are trying to boot from the wrong drive. 

When you get to that error, try hitting ctl/alt/f1. That should take you to a CLI. Type this in:
```

sudo blkid
```That tells what's where. sda1 = first partition, first drive. Now, find your linux partition and note the sda?, sdb? whatever it might be. It will be an EXT3 partition. If you know where it is already, skip this bit. Next, type this:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```This backs up the file your about to work on. Then:
```

sudo nano /boot/grub/menu.lst
```Find the part that boots your Ubuntu. It will look something like this:

```
title             Ubuntu 8.04.1 Blend (kernel 2.6.24-19-generic)
root            (**hd0,5)**
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=36bd7710-ca84-48c9-90$
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

```The part in bold is the part that would be wrong on your machine (I'm figuring). Now, if Ubuntu is on sda1 this would be (hd0,0). Follow? So if Ubuntu was on sdb2 it would be (hd1,1). (hd*,*) starts counting from zero in other words. See how you go. If you blow it you always have your backup menu.lst

Let us know if you need any help and welcome. :)

Look here anyway for a description of error 17 and if your menu.lst uses UUID instead of (hd*,*):

[http://members.iinet.net.au/~herman546/p15.html#17]("http://members.iinet.net.au/%7Eherman546/p15.html#17")

---

### Post by P4man on 2009-08-24
> **Bucky Ball said:**
> Wrong approach. Grub 17 error means you are trying to boot from the wrong drive. 

When you get to that error, try hitting ctl/alt/f1. That should take you to a CLI. 

Hu? Are you saying you can use that when grub is failing to boot linux, you can go to a CLI and run nano and everything?

---

### Post by doggitydogs on 2009-08-24
Um... yeah... remember, I started with XP...
I'll try.

---

### Post by Bucky Ball on 2009-08-24
:)

Cool, so did I. It is a learning curve but go for it. That link I supplied will probably give a much better explanation of the problem than I did. You could probably also do this from the LIVE CD when I think about it now, sorry. The confusion there can be that you are working on the CD files when you think you are working on the ones on hard drive, but in this case, there wouldn't be a menu.lst on CD I don't think. Maybe try from the CD and I think when you see the menu.lst, you will know it is the right one (you will find your Windows boot at the bottom probably). 

Try that, much easier

---

### Post by Bucky Ball on 2009-08-24
> **P4man said:**
> Hu? Are you saying you can use that when grub is failing to boot linux, you can go to a CLI and run nano and everything?

Yup. This page will give you all the grub error numbers a bit further down:

[http://members.iinet.net.au/~herman546/p15.html#Common_Booting_Errors_and_Some_Possible]("http://members.iinet.net.au/%7Eherman546/p15.html#Common_Booting_Errors_and_Some_Possible")

In fact you can hit that key combo anytime and get a CLI. Can't remember the command for getting the desktop back at the moment though!

---

### Post by doggitydogs on 2009-08-24
Didn't see your post. I may try setting (hd0,0) to boot (the XP drive) rather than (hd0,2) (the GRUB drive)

---

### Post by doggitydogs on 2009-08-24
Okay, this thread is a mess in 5 minutes.

---

### Post by Bucky Ball on 2009-08-24
> **doggitydogs said:**
> Didn't see your post. I may try setting (hd0,0) to boot (the XP drive) rather than (hd0,2) (the GRUB drive)

Hmm, well if you do that there will be no way of booting Ubuntu. MS doesn't recognise EXT3 files. Someone might have a workaround. You should really try fixing your grub with the LIVE cd. You are probably one digit away from getting the dual-boot up.

Just keep asking questions if you get stuck. Other thing is if you do it with LIVE cd you can stay online while you are experimenting.

---

### Post by P4man on 2009-08-24
> **Bucky Ball said:**
> Yup. This page will give you all the grub error numbers a bit further down:

[http://members.iinet.net.au/~herman546/p15.html#Common_Booting_Errors_and_Some_Possible]("http://members.iinet.net.au/%7Eherman546/p15.html#Common_Booting_Errors_and_Some_Possible")

In fact you can hit that key combo anytime and get a CLI. Can't remember the command for getting the desktop back at the moment though!

We are misunderstanding each other, or you typed something else than you meant in your initial post. You can not access a terminal from grub that will let you copy files, run a nano text editor etc. Thats what your post implied. 

Control alt F1 works once your booted linux. And **then** you can enter all those commands, but not when grub fails to load linux with whatever error message. There is a tiny shell in grub that lets you do a few things, even repair grub, but not using cp or nano.

BTW, control alt+ F7 is what gets you back to X.

---

### Post by Bucky Ball on 2009-08-24
Run a file system check and that will probably fix it according to the first post I gave you. Really simple with the LIVE cd and here is how. Sounds like you are perhaps not reading what is there:

[http://members.iinet.net/~herman546/p10.html#Running_a_filesystem_check_with_GParted_](http://members.iinet.net/~herman546/p10.html#Running_a_filesystem_check_with_GParted_)

Too simple. If it doesn't fix, post back.

---

### Post by Bucky Ball on 2009-08-24
Yea, you're right. Getting late here, time for bed. 

> **P4man said:**
> 
BTW, control alt+ F7 is what gets you back to X.

There ya go. ;-)

---

### Post by P4man on 2009-08-24
@doggitydogs

sorry for contributing to thread mess, Ill try to make it up now :)

Its entirely unclear to me though, if we are looking at a wubi install, or not. Did you give ubuntu its own partition or did you install from inside windows ?

Your solution depends entirely on which of both approaches you used.

---

### Post by doggitydogs on 2009-08-24
The Ubuntu has its own partition, as a normal (non-Wubi) installation.

I don't need the Ubuntu to be bootable. I just need to get back to XP. Can somebody please tell me how to do that, in Windows Geek instead of Linux Geek, via the BIOS, the GRUB shell, or the Live CD?

---

### Post by P4man on 2009-08-24
well, for a windows geek not needing to be able to boot ubuntu, boot from the windows cd, recovery mode, and then run fixboot.

But lets fix grub instead, its not that hard :)

Boot from the live CD. Then go places > yourharddisk to make sure your disks are mounted. Do it for each. You probably dont need to, but to be safe.

Then open a terminal from applications > accessoires > terminal 
Type:

```
sudo grub
```

You will get a grub> prompt. Type

```
find /boot/grub/stage1
```

It will respond with something like (hdx,y)

Then type
```
root (hd**x,y**) 
```where x and y are the numbers you found ealier

then 

```
setup(hdx) 
```agan replace x with the number

finish with
```
quit
sudo reboot
```

That should at least fix ubuntu, and probably windows too. If windows is not working yet then, report back, and we'll add windows.

edit: should ubuntu not boot either, please open a terminal and type

> cat /boot/grub/menu.lst 

and post the output here.

---

### Post by doggitydogs on 2009-08-24
When I type:
```
find /boot/grub/stage1
```
at the
```
>grub
```
prompt, it returns
```
Error 15: File not found
```

---

### Post by doggitydogs on 2009-08-24
The contents of my
```
/boot/
```
folder on the ext3 partition is as follows:
> abi-2.6.28-11-generic
config-2.6.28-11-generic
memtest86+.bin
System.map-2.6.28-11-generic
vmcoreinfo-2.6.28-11-generic

---

### Post by P4man on 2009-08-24
you dont have grub on there at all?
hmm

ok, give me the output of

```
sudo fdisk -l
```

---

### Post by doggitydogs on 2009-08-24
```
ubuntu@ubuntu:~$ sudo fdisk -l
Warning: extra link pointer in partition table 5
omitting empty partition (6)

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0b6ae4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17847   143355996    7  HPFS/NTFS
/dev/sda2           17848       71242   428895337+   7  HPFS/NTFS
/dev/sda3           71243       77825    52877947+   5  Extended
/dev/sda5           77551       77825     2208937+   5  Extended

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45e7800d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


```

---

### Post by P4man on 2009-08-24
and where exactly did you think you installed ubuntu? There is no ext3 or 4 linux volume in that list! Are you REALLY sure you didn't do a wubi install? Or is there a drive missing from that list?

Oh and wait.. 2 extended volumes? That cant be right!

Im off for a bite, Ill be back later, but something is pretty messed up

---

### Post by doggitydogs on 2009-08-24
Okay... what I did when I installed Ubuntu was this:
I booted the live CD.
I selected 'Install Ubuntu.'
I set the user info.
It asked what I wanted to do with XP. It showed me a partition map of hda.
The map was as follows:
hda1 - Windows XP Professional - 136.71 GB
hda2 - (my data drive) - 459.46 GB
hda3 - Ubuntu - 0.0 GB
I clicked and dragged the little Ubuntu so the map was:
hda1 - Windows XP Professional - 136.71 GB
hda2 - (my data drive) - 408.66 GB
hda3 - Ubuntu - 50.8 GB
I clicked next.
It said that hda2 would be modified and that hda3 (Ubuntu) and hda4 (Ubuntu swap) would be created and that no partitions would be modified or removed.
I clicked OK.
It did its thing. I rebooted.
The GRUB menu came up. I chose 'Ubuntu 9.04' from the list.
Ubuntu loaded. I changed some basic settings and installed compiz-fusion. I then tweaked the compiz-fusion settings, then rebooted. I chose 'Microsoft Windows XP Professional' from the list. I loaded XP.
Blah.
Later, I did that driver thing mentioned in the first post. I then hard-rebooted, and it gave me:
```
GRUB loading stage1.5

GRUB loading, please wait...
Error 17

```

From the driver programs, I could browse the 'Linux' partition, and see, but not browse, the 'Linux swap' partition.
The only partitions shown in XP in those driver programs were:
> 
hda1: Salmon: NTFS
hda2: Data: NTFS
hda3: Linux: EXT3
hda4: Linux swap: swap
hdb1: Programs: NTFS

From the linux live CD, right now, I can see (in 'Computer'):
> 
CD-RW/CD-ROM Drive (contents: 'No media in drive' error)
CD-RW/DVD±RW Drive (contents: 'Cannot mount file' error) (the Live CD)
Data (contents: my stuff from XP - Documents, Videos, Pictures, and the like)
Floppy Drive (contents: none)
Programs (contents: some XP programs - Mozilla Firefox, CDBurnerXP, Adobe Photoshop CS3, and the like)
Salmon (contents: XP installation files - WINDOWS, Program Files, Documents and Settings, and the like)
Filesystem (contents: Linux installation files - boot, sys, usr, and the like)


---

### Post by P4man on 2009-08-24
thanks for the complete and clear explanation.
Looks like those Ext3 drivers wiped you ubuntu partitions, or least made them unreadable (for now?). That partition also contained /boot and /boot/grub which was needed to boot both ubuntu and windows. Im guessing one thing that may have led to this is using a windows Ext3 driver to read/write to an Ext4 volume, but thats not certain..

I guess you got a couple of options now. You can try to recover the ubuntu partitions with something like testdisk. Its in the repo's, so you can install it from the live cd by running:
```

sudo apt-get install testdisk
```

Or you can reinstall ubuntu to the same "spot" and let the installer sort out grub for dual boot. You will lose all changes to ubuntu.  Or you if you are getting nervous and / or in a hurry to get windows up and running again, boot a windows disc, and do the fixboot thing from the windows recovery console. then later on, we can still try to revive the ubuntu partitions or do a reinstall.

---

### Post by P4man on 2009-08-24
BTW the "Filesystem (contents: Linux installation files - boot, sys, usr, and the like) " you see in the live cd now, thats the livecd environment, not your harddisk. It also has a /boot, but that wont help us now. You would need a /media/disk/boot/ where "disk" is the Ext3 or Ext4 volume which has dissapeared.

---

### Post by doggitydogs on 2009-08-24
I'll try reinstalling to the same spot, as it can't find 'testdisk' in the repo.

---

### Post by doggitydogs on 2009-08-24
Nope, I can't, as it can't find XP, because the loader is gone. Even I did, GRUB wouldn't dual-boot an XP install that it doesn't think exists.
I'll go for the XP repair.

---

### Post by P4man on 2009-08-24
firing up a live cd now to check. perhaps you have to enable the "universe" repository first, gimme a minute.

Yep. do this: system > adminstration > software sources.

Check the "universe" and "multiverse" repo's (not sure which of both it is, so select them both :) ). Close, let it reload package information. Then you can install testdisk.

If you are going to reinstall, delete the 2 extended partitions first from the live cd. Then install in "unused space", thats probably the easiest approach.

---

