---
title: "Format a USB flash drive?"
date: 2010-06-17
forum: General Help
---

### Post by PDA1 on 2010-06-17
How do I format a USB flash drive?

---

### Post by TeoBigusGeekus on 2010-06-17
With gparted.
Install it if you haven't already
```
sudo apt-get install gparted
```
and run it as administrator
```
gksu gparted
```
Select your flash drive, unmount it and format it (fat32).

---

### Post by hansdown on 2010-06-17
Hi PDA1.

You can install gparted.

```
sudo apt-get gparted
```

Or go to synaptic.

This should be helpful.

[http://www.ehow.com/how_4963426_format-usb-flash-drive-ubuntu.html](http://www.ehow.com/how_4963426_format-usb-flash-drive-ubuntu.html)

---

### Post by C.S.Cameron on 2010-06-17
Nowadays you can right click the drive in Nautilus and select "Format...".

---

### Post by howefield on 2010-06-17
The above (gparted posts) will certainly work, but you might be able to simply right click on the Desktop icon for your flash drive, then select Format.

Not sure if all Ubuntu versions supports this, what version are you running ?

---

### Post by bodhi.zazen on 2010-06-17
mkfs.ext2 /dev/sdxy

where /dev/sdxy is your USB device.

change the "ext2" to vfat, ntfs, ext4, jfs as desired.

See man mkfs.ext2 for options (such as setting a label).

---

