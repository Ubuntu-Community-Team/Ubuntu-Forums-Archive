---
title: "whats Dvd ROM directory"
date: 2011-08-10
forum: General Help
---

### Post by ofox25 on 2011-08-10
hi i need to mount my dvd rom in a program(abgx360) but when i select  my dvd rom program show this message :

For Unix based operating systems: Devices are files!
Select "File(s)" as Input and enter the device name.
Linux Example: /dev/cdrom (requires read permissions).
Writes are automatically disabled for block devices.

i dont know what this message mean i tried /dev/DVD_ROM but its not working plz anybody can help what should i do?

---

### Post by Bubble32 on 2011-08-10
Hey!
if you've already mounted your dvd, you can address it in the program with /media/[YOUR_ROM] (which I think you already knew!)
But for finding your devices' **files** you can open your terminal, **cd** to your **/dev** and do a:
```
find . | grep dvd
```
and check which one suits your need. Then try to mount the files you've found! ;)\.

---

