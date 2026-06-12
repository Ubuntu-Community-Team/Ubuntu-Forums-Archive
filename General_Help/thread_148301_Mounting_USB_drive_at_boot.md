---
title: "Mounting USB drive at boot"
date: 2006-03-21
forum: General Help
---

### Post by megadodo on 2006-03-21
I have an external usb hard drive that is pretty much always connected, and i would like it to be mounted at boot time. 

At the moment, the drive is mounted automatically at /media/lacie (its a lacie drive presumably) when i plug it in, but not if it is already plugged in while booting. Its a bit annoying to have to keep unplugging and replugging it every time!

Ive switched from gentoo, where i had a line in fstab which mounted /dev/sda1 (sda1 was the device it came up as mostly) However when i look in /dev of my newly installed kubuntu 5.10 amd64, there are no sd* devices, or in fact any hd* devices either. Where are they? 
Thanks in advance
Rich

---

### Post by fatsamurai on 2006-03-21
I'm not sure why you don't have any hda or sda devices in /dev.. I do..

Anyway, if you want to find out what the device name is - type 'mount' in  a terminal. Then create a matching fstab entry.

---

