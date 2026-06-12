---
title: "lomoco not working in 9.10 Karmic"
date: 2010-03-19
forum: General Help
---

### Post by craetech on 2010-03-19
Hi, I've just upgraded to Kubuntu Karmic and lomoco is no longer working - no effect on sensitivity, and device scan has no feedback. Is lomoco no longer supported, or is a known issue?

I'm using a Logitech MX300 and invoke lomoco with:

```
sudo lomoco -8
```

I'd appreciate any help provided. Thanks!

---

### Post by craetech on 2010-04-04
Solved!

Edited /boot/grub/menu.lst to load the latest kernel - I forgot that during dist-upgrade, I had selected to keep currently installed menu.lst and wasn't aware of the new kernel files. My bad!

---

