---
title: "run command lines on boot?"
date: 2010-09-11
forum: General Help
---

### Post by JaizEdelmann on 2010-09-11
Hey everyone im using a minimal install of ubuntu without gnome.

And i would like to know how i run the following lines onboot

```
/media$ sudo mount /dev/sdb1 /media/mediaStorage1
/media$ sudo mount /dev/sdc1 /media/mediaStorage2

```

I'm sorry if this has been posted before but i triede googling abit and couldent find the right answer.

---

### Post by cj13579 on 2010-09-11
You just need to edit you fstab. It is located in:

/etc/fstab

This is a [great guide]("http://ubuntuforums.org/showthread.php?t=283131") to fstab.

---

### Post by sigmarhophi on 2010-09-11
Hi,

I am guessing you want to mount the two devices every time you start your system.  You really do not need to run any command, rather simply add the devices to /etc/fstab

gksudo gedit /etc/fstab

then add 

/dev/sdb1 /media/mediaStorage1 auto auto,exec,rw,user 0

repeat with necessary changes for your second device.

---

### Post by sigmarhophi on 2010-09-11
silly me,

you are not running gnome, so the gksudo command will not work


try sudo nano /etc/fstab

---

### Post by JaizEdelmann on 2010-09-11
> **sigmarhophi said:**
> Hi,

I am guessing you want to mount the two devices every time you start your system.  You really do not need to run any command, rather simply add the devices to /etc/fstab

gksudo gedit /etc/fstab

then add 

/dev/sdb1 /media/mediaStorage1 auto auto,exec,rw,user 0

repeat with necessary changes for your second device.

Cheers, worked like a charm obviously with nano instead for the editation of fstab file :)

---

### Post by JaizEdelmann on 2010-09-15
> **JaizEdelmann said:**
> Cheers, worked like a charm obviously with nano instead for the editation of fstab file :)

And then again it didnt work as inted'd as it sometimes swaps around with the naming convention of the harddrives however i found the solution with using instead

```
LABEL=MyHarddriveLabel /media/myhdd ....
```

---

