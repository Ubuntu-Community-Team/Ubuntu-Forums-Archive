---
title: "Help with Persistent USB"
date: 2009-12-25
forum: General Help
---

### Post by Cuco3 on 2009-12-25
I've tried making a persistent LiveUSB drive using a [Toshiba 8GB Flash Drive]("http://www.officemax.com/technology/drives-memory-storage/hard-drives-usb-drives/usb-flash-drives/product-prod1120027") and "USB Startup Disk Creator" but it doesn't save my settings. On shutdown/restart, it gives some error messages about I/O and buffer overflow pertaining to the USB drive but I don't have enough time to write down exactly what it is cuz it happens pretty fast.

Anybody experienced anything like this?

---

### Post by Cuco3 on 2009-12-25
Ok, so I'm in the live usb right now. I checked somethings out and found this:

1. When looking through "Computer", I tried double clicking the USB drive but it says "Unable to mount location."
2. Using GParted, it says the USB drive is mounted as /cdrom.

I think that's my problem there.

WTF is going on here. :p

---

### Post by Cuco3 on 2009-12-25
Anybody?

I'm using the "USB Startup Creator Disk" program found in System > Administration

For the setting **"When starting up from this disk, documents and settings will be"**, I chose "Stored in reserved extra space" and slid the bar all the way to the right. Doesn't this mean to use the max disk space for persistent settings?

---

### Post by efflandt on 2009-12-26
Did the USB Startup Disk Creator actually complete properly?  With 4 GB USB I had difficulty getting it to complete if I put the slider all the way to the right.  But it worked one click down from max.  This may be because it estimates space it needs from file sizes, but all files do not necessarily end up on sector boundaries, so they take a bit more space than estimated and it runs out of space.

But I thought there was also a 4 GB limit on the persistent file (casper-rw).  Not sure if that is just when using FAT16 or if it applies to FAT32.  Anyway, try a persistent file not larger than 4 GB and see how that works.  You can still use the rest of the USB flash for storage of files accessible to Linux or Windows.  You can add packages, but I would not try to remove packages or do updates, since that will not change what boots from the iso files.

Or with 8 GB you could do a regular install with Linux filesystem (ext3 or ext4).  If you do that, during the summary just before actual installation proceeds, pay attention to the **Advanced** button and use that to put grub2 on the mbr of the USB, instead of default to your main hard drive.  And use tmpfs for /tmp like the USB startup disk does.

---

### Post by Cuco3 on 2009-12-26
> **efflandt said:**
> Did the USB Startup Disk Creator actually complete properly?  With 4 GB USB I had difficulty getting it to complete if I put the slider all the way to the right.  But it worked one click down from max.  This may be because it estimates space it needs from file sizes, but all files do not necessarily end up on sector boundaries, so they take a bit more space than estimated and it runs out of space.

But I thought there was also a 4 GB limit on the persistent file (casper-rw).  Not sure if that is just when using FAT16 or if it applies to FAT32.  Anyway, try a persistent file not larger than 4 GB and see how that works.  You can still use the rest of the USB flash for storage of files accessible to Linux or Windows.  You can add packages, but I would not try to remove packages or do updates, since that will not change what boots from the iso files.Yeah, it appeared to complete properly. I also tried setting a persistent space less than 4GB but nothing. 

I think LiveUSB Persistent is just broken in 9.04. 

> **efflandt said:**
> 
Or with 8 GB you could do a regular install with Linux filesystem (ext3 or ext4).  If you do that, during the summary just before actual installation proceeds, pay attention to the **Advanced** button and use that to put grub2 on the mbr of the USB, instead of default to your main hard drive.  And use tmpfs for /tmp like the USB startup disk does.I'm doing just that as I type this. Thanks for the advice on this. One thing I need to know is how to use "tmpfs" for /tmp so it stores tmp files in memory rather than on the USB. I was reading this in "LiveUsbPersistent" from the UbuntuWiki but it never gives directions on how to go about this.

---

### Post by Cuco3 on 2009-12-26
Ok, so after doing a little research, I figured out that you have to mount tmpfs and configure it to use a directory.


I used:

> ```
gksudo gedit /etc/fstab
```and added the line:
```

tmpfs /tmp tmpfs rw 0 0
```[Link]("http://ubuntuforums.org/showthread.php?t=119975")

How can I verify that tmpfs is working and using the ram to store /tmp ???
[COLOR=SeaGreen](So I researched and found out that mount can be used to manually mount partitions [derp!], so I did "man mount" and saw that you can use "mount -a" to mount everything in /etc/fstab". Then I did "mount -v" and it showed that my /tmp directory was mounted using tmpfs!)[/COLOR]

Also, is there any other directories that should be mounted using tmpfs ???

I'm really looking to improve performance and reduce the wear-n-tear on my USB drive. This Ubuntu runs a little slower than the LiveUSB version and i'm guessing it has something to do with TMPFS.

---

### Post by sgosnell on 2009-12-26
If you really want persistence, you need to use the liveUSB version to install Ubuntu to a USB  drive.  There is really no persistence I've seen using a liveUSB.  You need to boot from the liveUSB, select Install, and do a full install to another USB drive.  I regularly do that to install to SD cards.  With a full install, you have a complete portable Ubuntu system, usable on any computer which will boot from a USB drive.

---

### Post by Cuco3 on 2009-12-26
> **sgosnell said:**
> If you really want persistence, you need to use the liveUSB version to install Ubuntu to a USB  drive.  There is really no persistence I've seen using a liveUSB.  You need to boot from the liveUSB, select Install, and do a full install to another USB drive.  I regularly do that to install to SD cards.  With a full install, you have a complete portable Ubuntu system, usable on any computer which will boot from a USB drive.That would explain a lot. I wish they'd make it more clear about that. Thanks man.

Instead, I choose to install Ubuntu on a USB instead and it works.

My next concern is TMPFS. I used the command in my previous post but performance seems to have degraded. I noticed that source I used is from 2006 so I'm pretty sure things have changed so if someone has a recommended string for TMPFS in FSTAB please post. I'll be searching google in the mean time to see if I can get my answer.

---

### Post by sgosnell on 2009-12-27
I've never bothered with tmpfs, I just use the drive.  USB drives are so cheap I don't worry about wearing them out.  It will take years, and by that time they'll be too small to use for anything, just like the 16-128MB stuff from a few years ago are useless now.  The speed you gain by using RAM isn't really significant, IMO, and it increases the odds that the system will need to use the disk swap, which will slow everything down.

---

