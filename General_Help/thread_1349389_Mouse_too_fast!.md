---
title: "Mouse too fast!"
date: 2009-12-08
forum: General Help
---

### Post by ManDay on 2009-12-08
Can anyone tell me how to reduce mouse speed even further if it's already turned to the lowest setting in the mouse settings??

---

### Post by ManDay on 2009-12-08
I've looked almost everywhere and many people seem to have this problem, although no one seems to have any solution!

For me this is really a reason to throw ubuntu into the garbage! If I cannot even use my mouse because it cannot be configured correctly in Version 9.10, what is that?!

---

### Post by ManDay on 2009-12-08
Can any one tell me where to set my mouse speed beyond the standard GUI? Some config file maybe?

---

### Post by ManDay on 2009-12-12
I managed to slow it down by configuring it with HAL in one of its FDI files. I simply found out about the device with lshal - wrote down a distinct property - in this case the info.product string - and made a match for it, setting x11_options.ConstantDeceleration. See bugtracker on launchpad, thats where I found it.

---

### Post by tka.lee on 2009-12-23
> **ManDay said:**
> I managed to slow it down by configuring it with HAL in one of its FDI files. I simply found out about the device with lshal - wrote down a distinct property - in this case the info.product string - and made a match for it, setting x11_options.ConstantDeceleration. See bugtracker on launchpad, thats where I found it.

Hi I'm a newbie, can somebody decipher this for me? :confused: HAL? FDI? Ishal? etc...

---

