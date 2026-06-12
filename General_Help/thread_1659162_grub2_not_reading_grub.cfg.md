---
title: "grub2 not reading grub.cfg"
date: 2011-01-03
forum: General Help
---

### Post by adambot on 2011-01-03
Greetings,

I installed grub2 into a usb flash drive, the system loads grub fine, but then dumps me to the grub> prompt. The only way i can get the system to continue on is to type in

```
configfile /boot/grub/grub.cfg
```

does anyone know how to get grub to auto-load the grub.cfg file?

Thanks!!

---

### Post by lithopsian on 2011-01-03
Do you have a separate /boot partition?

---

### Post by adambot on 2011-01-03
yes and no...

when i am booted off the live cd, the /boot is on a different partition than the CD, but as far as the flash drive goes, there is only 1 partition

---

