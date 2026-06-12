---
title: "Renaming of cryptsetup LUKS USB-Device"
date: 2011-02-18
forum: General Help
---

### Post by Andreas Riedel on 2011-02-18
Hello Forum.

I've some problem with my encyrpted LUKS USB device.

At plugin the USB-device, the device is automount to:
/media/0e5beef7-6781-46c8-83c1-a525d074587b

This is not an intuitiv name. So, I wan't to rename it to something more easy like:
/media/USB_Backup_Device

But the way to do this will not be this easy. All instruction I read tells something about /etc/crypttab and /etc/fstab.

But the device is not fix. Sometimes it's mount to /dev/sdd2, sometimes /dev/sdc2 or /dev/sde2.

So the most reason thing to do is to rename the device itself or give it some name. But I'm not able to do this with gparted.

The question is:
- What's to do, do give an encrypted USB-Device an fix Name that it will be (auto-) mounted to an fix device name like /media/USB_Backup_Device


TIA
  Andreas

---

