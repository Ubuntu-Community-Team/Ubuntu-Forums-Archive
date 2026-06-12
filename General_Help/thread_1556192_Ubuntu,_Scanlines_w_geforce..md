---
title: "Ubuntu, Scanlines w geforce."
date: 2010-08-19
forum: General Help
---

### Post by dek8 on 2010-08-19
I have noticed that there are some tiny white scanlines over the screen in linux, is this something known? specific graphics cards? just an issue with my setup?

Its hard to explain but its even horizontal scanlines, like small white lines over the screen, like every 3 line... was wondering if its my geforce 8800 or what it is?

anyone got any ideas?



.

---

### Post by BbUiDgZ on 2010-08-19
> **dek8 said:**
> I have noticed that there are some tiny white scanlines over the screen in linux, is this something known? specific graphics cards? just an issue with my setup?

Its hard to explain but its even horizontal scanlines, like small white lines over the screen, like every 3 line... was wondering if its my geforce 8800 or what it is?

anyone got any ideas?



.

make sure your using the nvidia drivers, under administator menu, hardware drivers button

---

### Post by dek8 on 2010-08-19
i am using the current 195.36.24, also tried the older 173 or something. same thing. 

its the same thing without drivers too...

---

### Post by cascade9 on 2010-08-19
Thats something I've seen with 'cooked' or overheating nVidia cards before. (ATI and others for that matter)

Notr sayign that your card is cooked or overheating for sure, it could be somethign else. I'd try taking the side of teh case off, gettign a nice, big desktop fan, pointing it into the case and setting it to 'small huricane' and then booting the computer. If the card is overheating, the extra air from the fan should make the scanlines disappear.

---

### Post by dek8 on 2010-08-19
its fine in win7.... doesnt look like a graphical error... like a broken card or something- it looks more like a bad monitor driver, like the monitor is not configured properly. i havent installed any monitor drivers in linux, im not sure about that.

the scanlines are very very small. its not like its a broken display or adapter, but it degrades picture quality and im wondering if im missing out on something, maybe something i need to configure, ive tried several resolutions and refresh rates and its the same on them all, the monitor is a samsung 120hz lcd (2233RZ).

---

### Post by dek8 on 2010-09-02
basically putting in

Option "UseEdidFreqs" "no" under the display adapter and VertRefresh 120.0 under the monitor settings in xorg.conf fixed this for me with the new 256 drivers.

---

