---
title: "Command trigger Safely Remove Drive"
date: 2010-01-31
forum: General Help
---

### Post by ubfu on 2010-01-31
I wanted to know command to triggered "Safely Remove Drive".So I could implement it on Hardy 8.04
[http://ubuntuforums.org/showthread.php?p=8674988#post8674988](http://ubuntuforums.org/showthread.php?p=8674988#post8674988)


Hope for it, and thank you

---

### Post by rnerwein on 2010-01-31
hi
i think you can do follwing at command line (you must run the commands with root account):
#sync;sync
# unmount /your_mount_point
ciao

---

### Post by ubfu on 2010-01-31
> **rnerwein said:**
> hi
i think you can do follwing at command line (you must run the commands with root account):
#sync;sync
# unmount /your_mount_point
ciao

I know about mount but , it's about safely remove drive.It will power down + umount.
I just wanted to power down usb drive before taking out

---

### Post by ubfu on 2010-02-03
I really hope to have this command , anyone know what command for power down hard drive ?

---

### Post by ubfu on 2010-02-05
I can't find any information for powerdown on hardy 8.04

---

### Post by ushills on 2010-02-05
> **ubfu said:**
> I really hope to have this command , anyone know what command for power down hard drive ?

with modern hardrives there is no requirement to power down the spinning of platters, on a cut of power the heads automatically park safely using a weak spring or magnetic attraction with the heads.  modern drives are not as sensitive to correct parking as older sytle drives so unmounting is sufficient.  same with usb flash drives, once unmounted you can just unplug.   if you google hard drive head parking you will get confirmation.

---

### Post by bab1 on 2010-02-05
> **ubfu said:**
> I can't find any information for powerdown on hardy 8.04

It is 2 separate commands.

First you unmount the filesystem (partition).```
[FONT="Courier New"][_[COLOR="Navy"]umount [options] filesystem[/COLOR]_]("http://www.linfo.org/umount.html")[/FONT]
```

Then you *could *power down the drive```
[FONT="Courier New"][_[COLOR="Navy"]hdparm [ flags ] [device][/COLOR]_]("http://linux.die.net/man/8/hdparm")[/FONT]
```For some perspective on *hdparam *see [**[B]_[COLOR="Navy"]here[/COLOR]_**[/B]]("http://ubuntuforums.org/showthread.php?t=179074").

But frankly you do not need to worry about the power down part.  Disconnecting the USB cable is the same as spinning down the drive.  All it does is disconnect the power at a specified time.

The *safely disconnect *you are looking for is the un-mounting of the filesystem (partition).  At times if you disconnect the device before the filesystem cache is written to disk (e.g. using *umount filesystem*) you can corrupt files.

In short un-mount the partition(s) on the drive  and then just disconnect the USB cable.  I have several external drives that I use this way.  I have written scripts to do this so my command is: *extunmnt [drivename]*.  Of course I also have a mount script : *extmnt [drivename]*.

Another way to handle the dismount is to turn off the machine the dismount and the power down is part of the shutdown routine of the OS.

EDIT: As @ushills has said.  :D

---

