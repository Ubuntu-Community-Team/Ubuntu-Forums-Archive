---
title: "Cannot boot live CD from USB"
date: 2009-10-19
forum: General Help
---

### Post by falkenberg_cph on 2009-10-19
Hey
I´m suddenly having problems creating a bootable live CD USB.
This is the first time I´m having problems with this, and I´m totally out of ideas. Maybe you can give me some inputs.

Here´s what i´ve done:
1. Reformatted a USB stick using "HP USB Disk Storage Format Tool".
(Not checking "Create a DOS startup disk")
This particular USB has been used to create live CDs many times before.

2. Installed the latest Ubuntu ISO with Unetbootin (Ubuntu 9.04 desktop 32 & 64, Ubuntu 9.10 Beta 32).

3. Rebooted with the USB plugged in the computer

4. Edited the Boot Order in BIOS, to first go with USB-HDD

This is ignored and the computer just goes right into Grub

5. Tried different USB plugs (I guess thats what they are called)

6. Tried resetting BIOS to optimized defaults

It is just not working
Hope you can give me input
Thanks Carsten

PS: I have a Windows 7 x64 partition and a Ubuntu x64 partition. I have tried Unetbootin from both partitions.

[EDIT]: Sorry if this has been posted before. I thought the "check if thread has allready been posted". Would prompt me a pre-post result. It didnt.

---

### Post by grafted_scion on 2009-10-19
Try formatting to ext2 with gparted (system/administration/partitionmanager).
Instead of downloading iso manually just choose ubuntu in the unetbootin droplist
I just made a bootstick like that few days ago it worked just fine.

If you still cant make it work with unetbootin.
There is also the usb startupdisk creator (system/administration/usbstartupdiskcreator.

---

### Post by falkenberg_cph on 2009-10-19
Hey
Thanks for the input. I tried doing as you suggested.
It didn´t work but it do something unexpected.

When the USB is plugged in, it locks up the computer when the BIOS initializes. I had this same problem on my other computer with the same USB stick. I´m starting to think it is somehow damaged.

BTW. I noticed Unetbootin was hanging an awful long on 0% when it was installing the bootloader.

Oh. Just remembered  - I still have not tried your other suggestion (startup disk creator).

---

