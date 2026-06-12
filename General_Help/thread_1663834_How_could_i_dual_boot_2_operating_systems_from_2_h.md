---
title: "How could i dual boot 2 operating systems from 2 hard drives?"
date: 2011-01-10
forum: General Help
---

### Post by JohneG on 2011-01-10
Is there any easy way of doing this? For example i want to have lucid on one hard drive and another distro set up on another hard drive. Is there any way i can set this up so that i can boot up my computer and choose which hard drive to boot from? The easier the better

---

### Post by niteling on 2011-01-10
If the hard drives are part of the same pc I would think that grub will automatically find the two os's.

---

### Post by TeoBigusGeekus on 2011-01-10
Nothing particularly difficult with this. Just install the other distro wherever you want and the bootloader will take care of the rest.
Just make sure to install the bootloader on your boot hard drive.

---

### Post by pricetech on 2011-01-10
Another option you may have; Some BIOSes will let you choose a particular drive to boot from.  Each drive would have its own bootloader and would be able to function even in the absence of any other drive.  This may be what you're looking for.  Check your BIOS to see if it will let you choose one specific device.

---

