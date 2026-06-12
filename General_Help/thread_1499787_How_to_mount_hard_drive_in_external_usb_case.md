---
title: "How to mount hard drive in external usb case ?"
date: 2010-06-02
forum: General Help
---

### Post by le1 on 2010-06-02
I have some documents that I need to copy from my old disk that has Fedora 9 on it. I bought external usb case for 2'5" disk but when I connect it through usb cable I can only hear it running but there's not much of the auto-detection. Pls help me mount it manually. Thanks.

---

### Post by VCoolio on 2010-06-02
"sudo fdisk -l" (that is a small L, not capital i) to check whether it is recognized, then use the mount command: "sudo mount /dev/??? /media/whatevermountpoint -t <filesystem-type> -o user,rw" something like that.

---

### Post by dino99 on 2010-06-02
check into synaptic that pmount and usbmount are installed

mountmanager is the easy way to deal with partitions and devices, install it and set your prefs into "system admin mountmanager"

---

### Post by le1 on 2010-06-02
**fdisk -l** does not detect it, **mountmanager** does as sdb 0 bytes disk

---

### Post by dino99 on 2010-06-02
ckeck that usb is activated into bios

its strange that fdisk -l dont see it, does that case need external power ?  which usb it is ? usb2 or usb3 (see manual hardware)

---

### Post by le1 on 2010-06-02
usb is activated in bios, 
usb 2.0, 
external case powered through usb

I bought it on ebay but I looks like working I can hear it etc

---

### Post by dino99 on 2010-06-02
> **le1 said:**
> usb is activated in bios, 
usb 2.0, 
external case powered through usb

I bought it on ebay but I looks like working I can hear it etc

i hope you bought a real hardware, not a fake.

---

### Post by le1 on 2010-06-02
if it was fake mount manager wouldn't detect it, right ?

Though it might be the reason why doesn't work, any other way around ? or this is it ?

---

### Post by dino99 on 2010-06-02
if you can really identify this box with manufacturer, name, model, number, googling around might help

(have you an idea why this box was on ebay ?)

---

### Post by le1 on 2010-06-02
if anybody knows any other way of mounting it (the way that can't be found on google) drop a line, thanks

---

