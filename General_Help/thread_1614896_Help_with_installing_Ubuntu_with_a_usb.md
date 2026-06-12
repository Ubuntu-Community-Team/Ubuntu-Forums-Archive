---
title: "Help with installing Ubuntu with a usb"
date: 2010-11-06
forum: General Help
---

### Post by ringo14 on 2010-11-06
Well i wanna give  Ubuntu a try i read on how to install  the os with  a 2gb pen drive  and i have a  SanDisk cruzer micro 2gb pen drive and i went and downloaded the Universal USB Installer for the usb. now i have a few questions 
1. do i need the usb to boot up/ use  ubuntu again?
2. my has 2 important files and i don't won't to take it of my usb , if i do keep it will this affect the installation?
3. i am running vista os and i am wondering if i can install ubuntu so i can have a dual boot , is that possibly with  a usb pen drive? 

Thanks in  advance

---

### Post by I'mGeorge on 2010-11-06
> **ringo14 said:**
> Well i wanna give  Ubuntu a try i read on how to install  the os with  a 2gb pen drive  and i have a  SanDisk cruzer micro 2gb pen drive and i went and downloaded the Universal USB Installer for the usb. now i have a few questions 
1. do i need the usb to boot up/ use  ubuntu again?
2. my has 2 important files and i don't won't to take it of my usb , if i do keep it will this affect the installation?
3. i am running vista os and i am wondering if i can install ubuntu so i can have a dual boot , is that possibly with  a usb pen drive? 

Thanks in  advance

I believe you have to configure bios so it would boot from usb. If your BIOS doesn't has this option and you want it that bad you should consider doing a BIOS upgrade, though it's not something I would really recomend it. Almost all linux distros have light installers that would fit on a regular CD and as far as I know Ubuntu always was known for the lightness of it's installing kit.

---

### Post by m4tic on 2010-11-06
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sanderd17 on 2010-11-06
1. Once you installed ubuntu, you don't need to use the USB again. 

2. you probably will need to repartition your usb, so all files will be deleted. Once you put ubuntu on your usb, you can place files in the /home/[user]/Documents folder inside your USB. But I don't guarantee you that those files will be safe.

3. The default option when installing ubuntu (if you have enough space) is a dual boot.

---

### Post by sanderd17 on 2010-11-06
> **I'mGeorge said:**
> I believe you have to configure bios so it would boot from usb. If your BIOS doesn't has this option and you want it that bad you should consider doing a BIOS upgrade, though it's not something I would really recomend it. Almost all linux distros have light installers that would fit on a regular CD and as far as I know Ubuntu always was known for the lightness of it's installing kit.

All computes I know that are younger than 5 years can boot from USB without some BIOS settings changing. The only thing you need to do is to press a key (try ESC, F1-F4, F11 or F12 if your computer doesn't say which one) to choose to boot from USB.

---

### Post by I'mGeorge on 2010-11-06
> **sanderd17 said:**
> All computes I know that are younger than 5 years can boot from USB without some BIOS settings changing. The only thing you need to do is to press a key (try ESC, F1-F4, F11 or F12 if your computer doesn't say which one) to choose to boot from USB.

My ASUS motherboard it's 3 years old and didn't had this option from the beginning

---

### Post by sanderd17 on 2010-11-06
> **I'mGeorge said:**
> My ASUS motherboard it's 3 years old and didn't had this option from the beginning

Ok, sorry, so there are computers where you need to adapt a BIOS setting.

---

### Post by ringo14 on 2010-11-06
I know how to boot from  a  usb  i have to change  the boot order  and i have enough gb  to run a other os  i have 500 gb so thats enough.

How do i repartition  my usb ? and the files  that are in my usb are  only  2 documents don;t think they will take alot of space

---

### Post by m4tic on 2010-11-06
> **sanderd17 said:**
> Ok, sorry, so there are computers where you need to adapt a BIOS setting.

I have a gigabyte mobo from 2006, i had to flash the damn thing.

---

### Post by sanderd17 on 2010-11-06
> **ringo14 said:**
> I know how to boot from  a  usb  i have to change  the boot order  and i have enough gb  to run a other os  i have 500 gb so thats enough.

How do i repartition  my usb ? and the files  that are in my usb are  only  2 documents don;t think they will take alot of space

If you use the Universal USB Installer, and your USB stick doesn't have a good format (I think it should be FAT), he will propose to repartition it. It's not about taking space, it's about the format used to store files on the USB stick.

---

