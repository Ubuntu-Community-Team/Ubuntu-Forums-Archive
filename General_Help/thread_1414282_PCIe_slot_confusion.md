---
title: "PCIe slot confusion"
date: 2010-02-23
forum: General Help
---

### Post by jon.mithe on 2010-02-23
Hi,

Is it possible to run a box with 2 graphics cards in it with one card being a PCIe x16 and the other being a PCIe x1?

Unsure whether this would cause all sorts of problems with ubuntu and/or the nvidia drivers (2 quatro NVS 290's).

Any help would be most appreciated, thanks,
Jon.

---

### Post by jon.mithe on 2010-03-03
For anyone else having the same troubles, turns out the answer is yes it is possible.  

I used two nvidia quadro NVS195's with the cheap passive display port adaprters (the nvs190 PCI x1 card only has a max resolution of 1920x1200 so needed the 195 for 2048x1152)

NVidia settings made it easy, I just enabled the screens in a separate X screen each then combined them with xinerama.  Only difficulties I had was uninstalling the ati driver and saving the nvidia configuration (it moaned about parse errors all the time (even when run as root), so I did a preview of the xorg.conf then just cut n copied that in)

Only one thing I will say is there has been a slight performance drop but my pc still runs well, its a decent spec pc with alot of ram, so I be slightly worried running these screens on a low spec pc. 

I think there are some better ways to do the multiscreen using twinview + ximerama and/or xrandr (I hear that now has multi gpu support). Another fight for another day tho... :P

---

