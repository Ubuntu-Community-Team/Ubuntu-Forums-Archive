---
title: "ATI Mobility"
date: 2010-09-25
forum: General Help
---

### Post by jjakspaw6 on 2010-09-25
Hi, 

I have an old laptop, HP ze460. This system has the ATI Mobility U1 chip. I noticed that the system is using a generic, xorg driver instead of the ATI. I remember that the ATI chip worked in Gusty But I can not seem to locate a driver now.... Any tips on this?

Thanks,
Jason

---

### Post by lukeiamyourfather on 2010-09-25
Use the "hardware drivers" utility in the administration menu at the top of GNOME. Note that the graphics chipset in that machine might be too old and not be maintained by AMD/ATi anymore. In that case you'll either have to manually install a legacy binary driver or just use the open source driver.

---

### Post by jjakspaw6 on 2010-09-25
I tried the hardware drivers utility... that finds my broadcom43legacy (it doesn't work right either).... I will look into the open source drivers.

Thanks

---

### Post by lukeiamyourfather on 2010-09-26
The open source drivers are probably already being used. Is there something in particular that is not working, or why are you trying to do? If I remember correctly you can use "lsmod" to show what kernel modules are loaded, and there should be one for the graphics chipset.

---

