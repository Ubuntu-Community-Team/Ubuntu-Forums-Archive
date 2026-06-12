---
title: "how to patition a usb drive??"
date: 2011-10-13
forum: General Help
---

### Post by dude599 on 2011-10-13
how to patition a usb drive with a 32 FAT system??

---

### Post by mikejonesey on 2011-10-13
fdisk, gparted... any disk util...

sudo apt-get install gparted
system->admin->gparted

select usb (prob /dev/sdb)
wipe n add partitions as you please

if you dont't want to partition then just right click and select format one of the options is fat...

---

