---
title: "bootable USB"
date: 2009-09-22
forum: General Help
---

### Post by BarefootSoul83 on 2009-09-22
I'm messing around and put "Slax" on USB so I can take Linux anywhere... how do I make it bootable? 

note: I already have USB boot capability from F12

---

### Post by gordintoronto on 2009-09-23
Gparted can set the bootable flag.

---

### Post by Carl Hamlin on 2009-09-23
> **BarefootSoul83 said:**
> I'm messing around and put "Slax" on USB so I can take Linux anywhere... how do I make it bootable? 

note: I already have USB boot capability from F12

As an aside - flash can only sustain a finite number or write/erase cycles before becoming a fairly ineffective paperweight.

Running an operating system on flash eats those up pretty quickly, so the long and the short of it is that if you want bootable flash, your device is going to have it's potential lifespan shortened *considerably*.

---

### Post by Darkwing-Duck on 2009-09-23
If you want to "burn" an ISO image onto a thumbdrive then it's actually quite simple. 

```
sudo apt-get install usb-creator
```

Hope this works for ya!

---

### Post by BarefootSoul83 on 2009-09-23
I got the ISO image on the thumb drive but no dice on getting it to boot....:confused:

---

### Post by Darkwing-Duck on 2009-09-23
Did you copy it to the drive or did you use the USB creator?

Do you have your BIOS setup to boot the thumb drive (USB) before the HD?

---

### Post by Plumtreed on 2009-09-23
Not all USB drives will boot linux. Apparently some need 'doctoring' to allow them to work properly with linux. Others just don't!

---

### Post by BarefootSoul83 on 2009-09-23
OK...I got Slax to boot from a USB on my Ubuntu machine... but when I tried it on a Windows PC it froze up right before login?

---

