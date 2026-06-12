---
title: "How can I load a module at boot?"
date: 2006-06-23
forum: General Help
---

### Post by Randomskk on 2006-06-23
So, I've installed Ubuntu server on an old machine I had lying around, planning to use it as a backup server. It's got a tape drive and a four-drive SCSI array in RAID5, but no IDE drives.

The install went perfectly, and no errors were reported. However, when I boot I get a long wait (on recovery mode I see it is "waiting for the root file system") and then an error that /dev/rd/c0d0p1 does not exist, and it drops me into a Busybox shell.

I can boot a live CD and once it's booted I can mount the array with no problems, so I can edit files on it.

I believe I need to get the system to load the DAC960 (the type of SCSI controller I have) module earlier than it currently does, however I've got no idea how to go about doing this!

I've tried changing the /boot/config-.... file, editing "CONFIG_BLK_DEV_DAC960=m" to =y, but this does nothing.

In [this thread](http://ubuntuforums.org/showthread.php?t=152731), the poster solved my problem by editing the initrd.img file to load the module, but I don't know how to do this.

I've also heard I should be able to get GRUB to load the module for me, and I've looked around but can't find out exactly how to do this for my module.
The module name is DAC960, and it is in /lib/modules/2.6.15-23-386/kernel/drivers/block/DAC960.ko

So, in short, how can I get this loading so that the system will boot properly?
Thanks for any help

---

### Post by zxee on 2006-06-23
/etc/rc.d/rc.local usually is the place for things to load at boot.
Someone correct me if I'm wrong but I think the line to add would be 
modprobe DAC960
I don't know if you need to add the .ko or not you could try it both ways.

---

### Post by Randomskk on 2006-06-23
If I boot the system and the busybox shell loads, I can not load the module - and /lib/modules is empty.
It seems the DAC960 module is stored in the array itself - catch 22 I guess, since I need the module to mount the array but I need the array to get the module.

I believe the /initrd.img contains the modules present before the file system is mounted; but how could I edit this to enable the DAC960 module?

edit: I've tried using module and modulenounzip in GRUB, both before and after the initrd line, with two different results:
Before initrd, it does not change anything
After, it causes a kernel panic because it couldn't mount at unknown block 0,0 or something

I guess my best bet is to get the DAC960 module into the initrd.img, but I've still got no idea how.

---

### Post by scxtt on 2006-06-23
i'm just gonna throw this out there, in case it's of any help:

i needed my sensor modules loaded @ startup to avoid a "failed" note when i boot my box (and to avoid having to do it myself) ... so i put "w83627hf" in /etc/modules (a text file) and it works perfectly ... so if this is something you'd have to "sudo modprobe <a module>" give that a try ...

---

### Post by Randomskk on 2006-06-24
Fixed this with this thread's help:
[http://www.ubuntuforums.org/archive/index.php/t-82466.html](http://www.ubuntuforums.org/archive/index.php/t-82466.html)

I added DAC960 to /etc/mkinitrd/modules then ran mkinitrd, and it boots fine :D

---

### Post by scxtt on 2006-06-24
just for my own curiousity, what's your /etc/modules look like now?

---

### Post by RavenOfOdin on 2006-06-24
[QUOTE=scxtt]just for my own curiousity, what's your /etc/modules look like now?[/QUOTE]

I was thinking the same thing.

---

### Post by Randomskk on 2006-06-24
/etc/modules has two non-commented lines:
lp
psmouse

I believe the /etc/modules file just contains things that'l be loaded after the hard disk mounts; the modules file I edited just tells mkinitrd what modules to put into the ramdisk (in this case, the DAC960 module so that the hard disk can be mounted)

---

### Post by scxtt on 2006-06-24
ahh, ok - thanks :)

---

