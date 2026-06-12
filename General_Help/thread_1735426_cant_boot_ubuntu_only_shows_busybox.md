---
title: "cant boot ubuntu only shows busybox"
date: 2011-04-21
forum: General Help
---

### Post by marwin on 2011-04-21
hello there mylaptop crashed due to extensive heat and i cant boot back to my ubuntu system. every time i try to boot back i get an error message and it only shows BusyBox :(
this happened to me before but one day it just miraculously boot back, now that it happened again im afraid that ill have to reinstall so i went here...

here's the error im gettin

mount: mounting /dev on root/dev failed: No such file or directory
mount: mounting /sys on root/sys failed: No such file or directory
mount: mounting /proc on root/proc failed: No such file or directory
Target filesystemdoesnt have requested /sbin/init
No init found. Try passing init= bootarg.


Busybox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for alist of built-in commands

(initramfs)

---

### Post by dino99 on 2011-04-21
boot on recovery mode and choose to repair package

---

### Post by marwin on 2011-04-22
i really cant :( even recovery mode shows the same thing

---

### Post by drs305 on 2011-04-22
Try booting a LiveCd and doing an fsck check. I use the following command. Make sure the Ubuntu partition is not mounted (it shouldn't be if you are using the LiveCD). Substitute your actual drive/partition for XY (i.e.sda1, sda5, etc).
```
sudo e2fsck -f -y -v /dev/sdXY
```

---

### Post by wilee-nilee on 2011-04-22
> **marwin said:**
> i really cant :( even recovery mode shows the same thing

Is this a wubi install?

---

### Post by marwin on 2011-04-22
@ drs305 can i use a diffrent distro for that :confused: 
 the only live cd i have right now is puppy :(
@wi-lee ni-lee nope, i installed it on a partition

---

### Post by drs305 on 2011-04-22
> **marwin said:**
> @ drs305 can i use a diffrent distro for that :confused: 
 the only live cd i have right now is puppy :(

Yes you can, as long as it has e2fsck on it, which I would expect it to.

---

### Post by ghost25 on 2011-04-22
Hey, I'm having much the same problem. I don't know why my hard drive would have gone belly-up, but I'm getting similar error messages.

I tried running fsck -f -y -v on sda, and when I opened Disk Utility to get the device name, the SMART Status told me that the disk has a few bad sectors. I thought that was the problem!

However, upon running fsck with the given options, it gave me the following error message:

e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?

I got the same error after closing Disk Utility. I tried to run Check Filesystem and got a pop-up window saying that "File system check on "244 GB Filesystem" (Partition 1 of ATA Samsung HM250HI) completed <break> file system is NOT clean."

Are there any other options there? I spoke with HP about it, as my laptop is still under warranty, and they said it might be either the controller board or BIOS having an issue too... but to me, this doesn't sound like that, it sounds like the hard drive is corrupted and getting ready to die. It may not be making the click of death, but when bad sectors start popping up, that's usually not a good sign.

Got any advice for me on that front? Thanks in advance.

---

### Post by drs305 on 2011-04-22
ghost25,

Are you specifying a partition (sda1, for instance). You run the check on a partition, not the drive. Trying to do it on 'sda' will give the messages you posted.

---

### Post by marwin on 2011-04-22
it worked! thanks :D i just ran fsck on my partition ("/dev/sda5") and it fixed it :P

@ghost25 yeah you should specify your partition, mine is @ "sda5" you should put in yours in order for fsck to work :)

---

