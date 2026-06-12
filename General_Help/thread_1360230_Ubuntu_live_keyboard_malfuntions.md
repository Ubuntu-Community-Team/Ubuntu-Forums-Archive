---
title: "Ubuntu live keyboard malfuntions"
date: 2009-12-20
forum: General Help
---

### Post by Gemu on 2009-12-20
I made an Ubuntu 8.10 USB flash drive and it works fine. I got it like I wanted, saved all my settings and all from my desktop. When I boot it in a small Acer laptop the keyboard loads wrong unless I turn persistence off. All the blue buttons show up as numbers.


 Is there a work around for this like a cheat code or something? 


 Thanks

---

### Post by dcstar on 2009-12-20
> **Gemu said:**
> I made an Ubuntu 8.10 USB flash drive and it works fine. I got it like I wanted, saved all my settings and all from my desktop. When I boot it in a small Acer laptop the keyboard loads wrong unless I turn persistence off. All the blue buttons show up as numbers.

Is there a work around for this like a cheat code or something? 


Persistence means that configuration settings are kept, and once it is configured for your desktop 8.10 is not going to reconfigure itself for different hardware.

9.04 or 9.10 would probably be better as they always reconfigure this sort of thing on every boot.

---

### Post by Gemu on 2009-12-20
Thanks, that helps a bunch. Im not sure I like the way the newer Ubuntu 9.10 mounts drives as /media/UUID12345678 yet but I guest its better for networking folks.

 What about fstab? obviously Ubuntu has a program working in the background to automatically detect and at least present all the hard drives on the machine. Should I just leave fstab alone on the USB live and let it mount those drives automatically since I want to boot it on several different computers? 

I actually might install it on the lap top with the USB because it doesn't have a cdrom drive.

---

