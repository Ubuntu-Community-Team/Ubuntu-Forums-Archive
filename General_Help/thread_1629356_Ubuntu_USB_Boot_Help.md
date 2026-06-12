---
title: "Ubuntu USB Boot Help"
date: 2010-11-23
forum: General Help
---

### Post by ngrieb on 2010-11-23
I have Ubuntu 10.04 x 64 desktop edition currently installed on my netbook, but I was curious to see how the 10.10 NB edition would be. Thus, I downloaded the Ubuntu 10.10 NB edition directly from the Ubuntu website, and used the gnome-usb-creator to make a usb start disk as I always have done for many multiple installs on many multiple computers. I rebooted, checked the BIOS boot priorities and made sure the FDD was first in line...no luck. I tried a different FDD, disabling all bootable devices but the FDD, creating the FDD using Windows 7, downloading earlier and different versions of Ubuntu for FDD, totally reformatting the FDD, etc, etc.

Needless to say nothing has worked, which is a huge problem on a netbook with no CD/DVD drive (and no I don't have an external DVD/CD drive sadly). This has obviously worked before because that is how I installed 10.04 on this netbook in the first place. Both Windows and Ubuntu see and autoboot the FDD after I login.

What could be causing this? I mean I have tried everything I know.(I'm thinking it must be a BIOS problem.) Does anyone know how to fix this?

---

### Post by Quackers on 2010-11-23
Doesn't FDD in bios refer to floppy drive? Not sure.

---

### Post by nl4m on 2010-11-23
Try using "unetbootin". If that does not work you can install Ubuntu 10.10 NB on the USB and use it through the USB port on your netbook. Or you can download Ubuntu's ISO, download Lubi, install the ISO through Lubi, partition the HDD, copy Lubi's file onto the second partition, and if you want you can delete the first partition.

---

### Post by C.S.Cameron on 2010-11-23
Check the MD5SUM of the downloaded iso.
I know from personal experience that working with a bad iso can be very frustrating.

---

### Post by ngrieb on 2010-11-24
Thanks for all of the replies. 

FDD I thought now refers to Flash Drive Disk, now that floppy's are dead anyways(I mean how long has it been since you have seen a computer come with a floppy drive? 10 years maybe more?).

I was just wanting to do a live boot from the disk to check it out. What is unetboot? (I shall look it up).

I was getting checksum errors on one of the flash drives I was using. If there are errors in the iso itself how do I ensure that I download all of the data? I mean I tried downloading the 10.10 NB edition twice (figuring some transfer protocol had gone wrong) and both times I had no luck...

---

### Post by nl4m on 2010-11-24
"Unetbootin" takes an ISO and "burns" the image to the USB flash drive. That way you can boot from the USB. If the program you originally use caused the problem using "unetbootin" may help.

---

### Post by Quackers on 2010-11-24
> **ngrieb said:**
> Thanks for all of the replies. 

FDD I thought now refers to Flash Drive Disk, now that floppy's are dead anyways(I mean how long has it been since you have seen a computer come with a floppy drive? 10 years maybe more?).



Last week when somebody else had this problem ;)

---

### Post by C.S.Cameron on 2010-11-24
MD5SUM:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by lohphat on 2010-11-24
My netbook won't boot from a live USB of UNE 10.10. I made it with the Universal USB Installer. If I put Linux Mint on it, it will boot, and this version of UNE on a USB will boot on my laptop. On my netbook however, it sits at "syslinux 4.02 copyright, etc.." with a blinking prompt and accepts no input.

[edit] Tried a different USB port and it booted.

---

### Post by ngrieb on 2010-11-24
Ah I found the one BIOS option that I had missed, Legacy USB was disabled. Thanks for all of the help anyways. I hope it might help someone else that is having problems.

[SOLVED]

---

### Post by liamfmfl on 2010-12-15
I have ubuntu 10.10 on a live usb. The live usb boots only if I hit enter. However, my home computer who has only a **usb keyboard **(no serial connections) stops working when I want to hit enter while I see on the screen:
 
boot:_
 
After a while, my computer gets stuck and I only see "boot:" with a flashing dash/line.
Is there a way to configure the booting options on my liveusb so I can boot directly without using my keyboard (once fully loaded, I hope the keyboard works).
 
My computer is an old Gateway desktop (built in 2001) with native usb keyboard support, its bios does not support booting from usb (use plpt.iso bootmanager), 512mb ram.

---

