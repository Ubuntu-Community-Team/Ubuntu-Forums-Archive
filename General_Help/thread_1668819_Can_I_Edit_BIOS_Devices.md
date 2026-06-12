---
title: "Can I Edit BIOS Devices?"
date: 2011-01-16
forum: General Help
---

### Post by sKRiBEL on 2011-01-16
I want to know if i can change the amount of devices, because I bought a 7 port usb hub, and i have a few storage devices i would like to be able to boot from but they're boot letters don't show up in the BIOS boot menu, does anyone know how I can add more? :]

---

### Post by psusi on 2011-01-16
Letters are a Windows thing only.

Most BIOS says something like press F9 for boot menu where you can choose which device to boot from.

---

### Post by grahammechanical on 2011-01-16
I do not know. I would guess that you would need to set the BIOS to boot from USB before booting from hard disc. 

Alternatively you could let GRUB do the work. There is a GRUB command that tells it to look for all Operating Systems and list them in the GRUB menu. You should do some research on the GRUB commands. I do not want to give wrong directions.

I think that the commands that you need are update-grub  or update-grub2. This then edits all the configuration files.

Regards.

---

### Post by sKRiBEL on 2011-01-16
> **psusi said:**
> Letters are a Windows thing only.

Most BIOS says something like press F9 for boot menu where you can choose which device to boot from.
ya i know, thats one thing i hate, im trying to find a way that it would label the devices like it does on ubuntu (i.e sda, sda1, sda2, sdb, sdb1, sdb2, ect.), im not sure how im going to change the BIOS though :/

---

### Post by efflandt on 2011-01-16
Depending upon your BIOS, it may either give you a list of connected USB devices by model to boot from, or will just give you a choice of booting from USB and boot from the (1st) device it finds there, which may not be the order you want.  In the latter case, you may have to only connect the USB device you want to boot from, and connect other USB storage devices after it boots.

---

