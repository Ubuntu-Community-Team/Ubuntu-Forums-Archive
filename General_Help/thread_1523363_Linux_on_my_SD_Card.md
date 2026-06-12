---
title: "Linux on my SD Card"
date: 2010-07-03
forum: General Help
---

### Post by shardvexspangler on 2010-07-03
Okay, I want to boot ubuntu from a 4 GB SD-card that I have. I have been doing this from a usb sd-card reader. I want to be able to boot the sd-card right from the sd card slot in my computer, instead of the usb sd-card reader. Obviously the boot menu doesn't have this option. How would I go about doing this? And yes, I will accept bios hacks as an option. Any help????????????

---

### Post by -humanaut- on 2010-07-03
You could create a boot floppy or cd like if you where going to flash the bios. that `might` work. Theres no way for you to select the SD card from "removable" my usb pendrive likes to show up as a USB Zip drive but it boots fine.

---

### Post by shardvexspangler on 2010-07-03
So is there no way to get my SD-card to show up in the "select boot device menu?"  There's gotta be some hack I can do..........

---

### Post by efflandt on 2010-07-03
What type of dev does the SD card show up as when inserted directly into your computer?  Many card slots in laptops are NOT USB (some other type of block dev) and the computer BIOS has no option to boot from that.

For example my Toshiba laptop has a card reader, which it has no option to boot from and Startup Disk Creator will not write to that.  But I can put the same SD in a USB card reader, put a live/install iso on the card and boot from the USB card reader (even microSD).  Even a bootable SD created on USB will not boot from the laptop's own card slot.

The multi-card reader in my desktop is apparently connected via USB internally.  So with that I can create or boot from a bootable system on SD (or microSD with an SD adapter).

---

### Post by holycow131415 on 2010-07-03
get something like this:

[http://www.amazon.com/Mini-Memory-Card-Reader-Writer/dp/B000FNDWLQ/ref=sr_1_1?ie=UTF8&s=electronics&qid=1278195790&sr=8-1](http://www.amazon.com/Mini-Memory-Card-Reader-Writer/dp/B000FNDWLQ/ref=sr_1_1?ie=UTF8&s=electronics&qid=1278195790&sr=8-1)

then boot from usb when you put your sd card in the adapter

---

### Post by v1ad on 2010-07-03
some bios's consider that as removable media. see if you can set removable media as first boot device.

---

### Post by sgosnell on 2010-07-03
You might have to have the card in the slot before you get the option to boot from it.

---

### Post by MooPi on 2010-07-03
My flash drives and SD cards show as hard drive in bios, maybe you've just missed the selection ? Check and see if you have a hard drive priority selection.

---

