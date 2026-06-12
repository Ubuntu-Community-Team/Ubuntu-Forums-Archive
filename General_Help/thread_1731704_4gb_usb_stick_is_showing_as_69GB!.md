---
title: "4gb usb stick is showing as 69GB!"
date: 2011-04-17
forum: General Help
---

### Post by Tosho on 2011-04-17
I was trying to make a Startup Usb Disk but after I press Erase the Disk I interrupt it and try to format the usb stick from Disk Utility and then I saw that the stick is 69GB instead of 4GB. Now I can't format the drive or anything.
How to change the size again to 4GB or the usb stick is dead?

---

### Post by TeoBigusGeekus on 2011-04-17
Post us the output of 
```
sudo fdisk -l
```
while the flash drive is plugged in.

---

### Post by Jack Brown on 2011-04-17
easiest would be to just get another 4gb usb, they're quite common nowadays.

if you really want to,
there's also some software that can enable you to repair the usb flash firmware.  But first you might need to find what kind of chip is inside the flash drive by opening it up.

search and you shall find

but be careful to use only safe programs.

---

