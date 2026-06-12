---
title: "Problems With Startup Disk Creator in 9.10"
date: 2009-11-11
forum: General Help
---

### Post by Plumtreed on 2009-11-11
I can't get a USB drive to boot after loading 9.04 to it. I used the USB Startup disk creator in 9.10 which asked me to format the fash drive before proceeding. It appears to load properly and all the usual files are there but when i try to boot it simply says 'BOOT FAILED'!

I have juggled the bios settings. The USB drive always performed well when used with the 9.04 Startup Disk Creator.

GParted tells me that the drive is FAT32, 4GB, Flags boot & Iba.

I haven't tried UNBootin or Pendrive 'cause I think I should be able to use Ubuntu's 'Creator' when I am loading another version of Ubuntu.

I would appreciate any ideas that I could try because I would like to go this route to develop a persistent USB drive??????

---

### Post by wilee-nilee on 2009-11-11
> **Plumtreed said:**
> I can't get a USB drive to boot after loading 9.04 to it. I used the USB Startup disk creator in 9.10 which asked me to format the fash drive before proceeding. It appears to load properly and all the usual files are there but when i try to boot it simply says 'BOOT FAILED'!

I have juggled the bios settings. The USB drive always performed well when used with the 9.04 Startup Disk Creator.

GParted tells me that the drive is FAT32, 4GB, Flags boot & Iba.

I haven't tried UNBootin or Pendrive 'cause I think I should be able to use Ubuntu's 'Creator' when I am loading another version of Ubuntu.

I would appreciate any ideas that I could try because I would like to go this route to develop a persistent USB drive??????

Did you reformat the thumb before loading it.

---

### Post by Plumtreed on 2009-11-11
Yes thanks Wilee, when I used the 9.10 Startup Disk Creator a 'popup' indicated that a format was essential so I clicked on the 'Format' button. The usb drive mounted and showed that the USB was clear. 

Did you think it essential to do it via GParted?

---

### Post by wilee-nilee on 2009-11-11
> **Plumtreed said:**
> Yes thanks Wilee, when I used the 9.10 Startup Disk Creator a 'popup' indicated that a format was essential so I clicked on the 'Format' button. The usb drive mounted and showed that the USB was clear. 

Did you think it essential to do it via GParted?

Probably not but that is what I do, any time I format a bootable thumb. I wonder if your download is corrupted or it was just a bad transfer to the thumb. Some thumb drives just don't cooperate as well. If you have an extra CD youcould try burking it and seeing if the problem persists, and also check the Md5 sum of the down load.

---

### Post by Plumtreed on 2009-11-11
I checked out the CD and it seems OK. In fact, it is the official Shipit version. 

I am starting to feel that Grub is interfering in some way. I get the error message 'Boot Failure' and if I hit enter Grub proceeds and boots to 9.10

Possible?

---

### Post by Plumtreed on 2009-11-11
I used my 9.04 live CD and selected the Startup Disk Creator within the live CD to create the USB drive.

It told me it was necessary to format, which we did, and from there it created a successful, bootable and persistent USB drive. No problems!

Clearly there is a malfunction with this facility in Karmic 9.10?  

(Good to have trusty, old 9.04 back to solve 9.10 problems:p)


BTW I did try UNetbootin but it had the same result as 9.10

---

