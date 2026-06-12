---
title: "making a live cd in ubuntu"
date: 2009-08-20
forum: General Help
---

### Post by blur xc on 2009-08-20
Hey- I needed to boot up my live cd last night for some work I needed to do on my system, but had forgotten that I loaned it out.  So- I thought I'd just make a new one.  First thing I tried, was to make a usb start up flash drive.  That was easy enough, but for some reason I can't get my computer to boot off of the usb drive, no matter what I selected for my first boot device in my bios.

so, then I thought I'd just burn a cd.  First fail- I burned the iso to the disk, so, all I had was a data disk w/ an iso on it.  No good.

2nd, 3rd, and 4th, fails- I right clicked he image, and selected burn to disk.  Each time, even selecting the slow 4x setting, it burned w/ erorrs.  Finally, I booted up vista in virtual box, downloaded and installed power-iso, and burned a successful live cd in one try.

Why didn't it work in ubunut?

thanks,
BM

---

### Post by P4man on 2009-08-21
First about the USB stick not working.. I had that once too, and I solved it by wiping it completely,  zero filling it:

```
dd if=/dev/zero of=/dev/yourusbstick
```

Then I reran the usb creator, and it did produce a bootable stick.

As for the cd, you just copied the iso file to  the cd, thats not gonna work.  Just open the iso with disk burner or brasero to burn it. Even double clicking afaik, would prompt you to burn the image.  Im guessing you dragged and dropped it on the cd instead ?

edit: guess you figured that out already. As to why it produces errors.. Im not sure :s

---

### Post by blur xc on 2009-08-21
I'll try that trick to fix my usb stick- but even so, my bios doesn't have a "boot from usb flash drive option".  It lists, usb cdrom, usb fdd, usb hdd, etc.., and I tried all off them...  

Yeah, and the first time I dragged and dropped, but then I figured out that I needed to burn the image to the disk.  This was my fisrt time burning a disk in Ubuntu.

Previously, I've always used power iso and nero in windows for my disk burning needs.

Each time, it told me that there were burn errors and files were corrupted (or something along those lines).

BM

---

