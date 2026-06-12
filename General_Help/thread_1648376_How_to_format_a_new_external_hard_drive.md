---
title: "How to format a new external hard drive"
date: 2010-12-18
forum: General Help
---

### Post by jereece on 2010-12-18
I just bought a new 320gb laptop hard drive and mounted it into an external enclosure.  The hard drive has never been formatted.  I plugged it into my computer running Ubuntu 10.10 and nothing happens.  I expected something to popup and say the drive has not been formatted and give me formatting choices.  I looked in Places>Computer and it's not there.  I even looked in Gparted and it does not show it.  So how on earth do I format a new external hard drive?

Thanks,
Jim

---

### Post by fatal_ERROR777 on 2010-12-18
Have you turned it on? I have a Connectland hard drive which has a switch. Maybe you have it turned off.

Fatal_Error

---

### Post by jereece on 2010-12-18
It's a laptop hard drive so when you plug it into the USB cord the green light comes on and you can feel that it's running.

---

### Post by noah++ on 2010-12-18
So the laptop hard drive doesn't spin up until you connect the enclosure's USB cable? And the enclosure is powered only by USB -- no power cord? As for the laptop hard drive, are there separate connections to the enclosure for power and data? (Is it possible power is connected but data isn't?)

At any time, for diagnostic purposes, do an **fdisk -l** as root. If nothing resembling the external drive appears, try **lsusb**. If the device doesn't appear even there, I'd say there's no hope of using the disk until something gets corrected outside of the operating system.

---

### Post by argedion on 2010-12-18
Make sure the drive is connected straight to the computer and not to a Hub. I ran into that same problem a while back after getting a new hard drive. I hooked it up to the hub so I could see the power light coming on but no disk in the OS or in the Bios. Only when I connected straight to the laptop did it work.

---

### Post by noah++ on 2010-12-18
> **argedion said:**
> Make sure the drive is connected straight to the computer and not to a Hub. I ran into that same problem a while back after getting a new hard drive. I hooked it up to the hub so I could see the power light coming on but no disk in the OS or in the Bios. Only when I connected straight to the laptop did it work.
I'm curious -- was the USB hub AC-powered or just USB-powered?

---

### Post by argedion on 2010-12-18
> **noah++ said:**
> I'm curious -- was the USB hub AC-powered or just USB-powered?

the hub was usb powered so there wasn't enough power to get it to fully come on

---

### Post by akakingess on 2010-12-18
I don't mean to seem condescending, but when you look in GParted, are you looking up in the top right-hand corner where it says /dev/sda and made sure there is not a drop-down menu that would allow you to select /dev/sdb?  I only ask because I have personally made that mistake myself.

---

### Post by wilee-nilee on 2010-12-18
Was this used?

What is the exact model and manufacturer of the HD?

Did it come with a dual usb one power one HD, one plug-in on the HD but 2 usb to plug into the computer.

---

### Post by jereece on 2010-12-19
Well now I am wondering if the hard drive is defective.  The hard drive spins up and I get a green light on the unit, so I know it has power but can't find it listed anywhere so I can format.  I also tried it in Windows and got the same result.  In Windows I also get a notification balloon that the drivers have been installed, so my computer is definitely seeing the drive is there. I also connected it using an SATA to USB adapter and it still did not work.  Before I return it, the last thing I may try is to actually install it in my laptop and see if I can get it formatted from a boot disk.

---

### Post by jereece on 2010-12-19
Well I finally installed the drive into a laptop and used Ubuntu to partition format it.  You would think it could be easier than this.

So this problem is solved but now I have another problem but I will post that separately.

Jim

---

