---
title: "Grub loading problem in ubuntu 9.10"
date: 2009-12-27
forum: General Help
---

### Post by mak.ripon on 2009-12-27
1. I use Ubuntu 9.10 including Win 7 in different partition. Grub loading from bios takes too long time(almost 40-45 sec),definitely irritating. how do i solve this?
2. How do i make win 7 default? there are total 7 options in grub including two recovery mode.

---

### Post by zvacet on 2009-12-27
That 7 options are kernels,recovery mode memtest and Windows boot option.Look if you have more then two kernels remove one with lower number from synaptic.You will find kernewls in synaptic by typing in search box **linux-image**.

If you want to make Windows default install from synaptic startup manager and with it choose witch OS you want to be default.

---

### Post by colau on 2010-01-25
> **mak.ripon said:**
> 1. I use Ubuntu 9.10 including Win 7 in different partition. Grub loading from bios takes too long time(almost 40-45 sec),definitely irritating. how do i solve this?
2. How do i make win 7 default? there are total 7 options in grub including two recovery mode.
Can you post:
```

cat /boot/grub/grub.cfg

```

---

