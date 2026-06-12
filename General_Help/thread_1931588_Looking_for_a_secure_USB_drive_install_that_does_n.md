---
title: "Looking for a secure USB drive install that does not use the host HD"
date: 2012-02-25
forum: General Help
---

### Post by ubuntu1sttimer on 2012-02-25
I think I have seen this before and it may have been on this site but I can't find it.

Is there a way to install Ubuntu on a USB thumb drive so that it does not use the host hard drive when run? All "disk writes" are made to the USB drive.

Any help would be most appreciated.

---

### Post by dcstar on 2012-02-26
> **ubuntu1sttimer said:**
> I think I have seen this before and it may have been on this site but I can't find it.

Is there a way to install Ubuntu on a USB thumb drive so that it does not use the host hard drive when run? All "disk writes" are made to the USB drive.

Any help would be most appreciated.

You mean **exactly** like the Live USB currently works?

---

### Post by ubuntu1sttimer on 2012-02-26
According to Wikipedia, "A live USB is a USB flash drive or a USB external hard disk drive containing a full operating system that can be booted. Live USBs are closely related to live CDs, but sometimes have the ability to persistently save settings and permanently install software packages back onto the USB device."

This includes both the operating systems installed on a USB device that writes to the computer hard drive and the version that uses the USB device only for storage of data. 

The later is what I am looking for. I have seen a item about a version that ran Ubuntu and used only the USB device without leaving any trace on the hard drive but can't find information about it now.

---

### Post by ottosykora on 2012-02-26
well, normal bootable usb live system has no reason to write anything to any hard drive unless you deliberately mount a hard drive partition and write to it. If you do not mount it, it is not existent.
There is however the swap partition, this could be used if present, but otherwise live system with persistent partition will even keep setting etc on the usb stick.
It will also work without any hard disk at all as it will boot from the usb media.

---

### Post by Gremlinzzz on 2012-02-26
You want to use a thumb drive as a portable hard drive?
I dont think that would work,mostly because of the heat:popcorn:


then again i could be wrong
How to Use a Flash Drive As a Hard Drive

[http://www.wikihow.com/Use-a-Flash-Drive-As-a-Hard-Drive](http://www.wikihow.com/Use-a-Flash-Drive-As-a-Hard-Drive)

---

### Post by mcduck on 2012-02-26
> **ubuntu1sttimer said:**
> 
The later is what I am looking for. I have seen a item about a version that ran Ubuntu and used only the USB device without leaving any trace on the hard drive but can't find information about it now.
You don't need any special version for that, just the normal Ubuntu Desktop version, and then use Ubuntu's own Startup Disc Creator or Unetbootin to create the bootable drive, both tools give you option to reserve some of the space on the drive for persistence file.

...and of course you can also just make a regular install into the thumb drive. Just make sure you'll install the bootloader to the thumbdrive instead of your hard drive. (this approach might not work as well when switching between different computers, but in general should be just fine)

---

### Post by Gremlinzzz on 2012-02-26
Those thumb drives do more than i thought:popcorn:

45 Free Useful Thumb Drive Applications

[http://www.hongkiat.com/blog/45-free-useful-thumb-drive-applications/](http://www.hongkiat.com/blog/45-free-useful-thumb-drive-applications/)

---

### Post by oldfred on 2012-02-26
I have a full install of 12.04 in a 8GB partition on a 16GB flash drive. I installed just like any install to a second drive. I also used gpt partitioning just to learn about the new gpt partitioning. I do not use it a lot so not sure about life but you should make settings similar to a SSD to minimize writes. That also helps speed a bit as writes to flash are slow.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

Lighter weight systems may be better:
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

