---
title: "Problems with visual effects"
date: 2009-08-14
forum: General Help
---

### Post by cookiedemkp on 2009-08-14
Hey everyone, having a slight problem here, I've tried enabling visual effects, but as soon as click on extra, my entire screen goes black and I have to ctrl + backspace to get back to login window, where I can login and everythings fine again, same thing happens when I try to start compiz.

Output of 
```
sudo lshw -C display:

```

```
*-display               
       description: VGA compatible controller
       product: GeForce 7150M
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

Any Help would be appreciated, as I would like some visual effects ;)

---

### Post by KhurramM on 2009-08-14
U will need to confirm the compatibility of compiz with your hardware.

Then only u can use compiz, else be compizless or get supported hardware.

Search the net for the compatiblity.............

---

### Post by P4man on 2009-08-14
seemes like a bug in the nvidia 180 drivers:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/325188](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/325188)

if you press control alt F1, and then back control alt F7, does it cure it for you too?

---

