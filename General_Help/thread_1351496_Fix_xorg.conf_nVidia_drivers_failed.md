---
title: "Fix xorg.conf? nVidia drivers failed?"
date: 2009-12-10
forum: General Help
---

### Post by BikeHelmet on 2009-12-10
Hi. :)

I have an Ubuntu 9.10 computer with a GeForce 6100 IGP. I tried installing nVidia drivers, but now X just complains about an invalid configuration every time it starts, and I have to run it in low-graphics mode.

All the options to re-generate xorg.conf fail, so... what do I do to fix this?

I don't care about acceleration. I just want my desktop back! :D

---

### Post by Physical Hook on 2009-12-10
I'm in the same situation - FX 5200 ( nvidia-glx-173 ) drivers are not working.

---

### Post by BikeHelmet on 2009-12-10
That's the version I tried, too. Maybe I should look for earlier versions? I think I remember seeing a v96.xx.

---

### Post by Physical Hook on 2009-12-10
Not really - your card seems to fall under nvidia-glx-173 ( [SUPPORTED PRODUCTS]("http://www.nvidia.com/object/linux_display_ia32_173.14.22.html") ).

---

### Post by BikeHelmet on 2009-12-10
Then why does it keep saying No Device Detected when I boot? :P

---

### Post by Physical Hook on 2009-12-10
> **BikeHelmet said:**
> Then why does it keep saying No Device Detected when I boot? :P

I've the same question and would be very nice if someone would know how to fix it :rolleyes:

---

### Post by ST3ALTHPSYCH0 on 2009-12-10
Have you tried deactivating the proprietary drivers and rebooting with the generic driver?

---

### Post by BikeHelmet on 2009-12-10
> **ST3ALTHPSYCH0 said:**
> Have you tried deactivating the proprietary drivers and rebooting with the generic driver?

How would I go about doing this?

Because I have tried the Drivers thing from the Administration menu. It just tells me that the nVidia driver isn't active. (Duh)

How do I tell xserver to go back to the working generic driver?

---

### Post by ST3ALTHPSYCH0 on 2009-12-10
If the Nvidia driver is inactive then you are running the generic driver. You might try my workaround in the link in my sig, if you have a little time and a spare CD laying around.

---

