---
title: "ACPI resource conflicts with ACPI region"
date: 2009-08-08
forum: General Help
---

### Post by heluani on 2009-08-08
Hi there, I am running 2.6.29.5 on a Asus P5Q3 and wanted to check out the new fancontrol support. I need the kernel module w83627ehf but the version from 2.6.30 or later. 

So I replaced the new w83627ehf.c in my kernel source tree, recompiled and got the module working and I can see fan speeds in 2.6.29 

I get this message on dmesg though:
```

[   28.246687] w83627ehf: Found W83667HG chip at 0x290
[   28.246854] ACPI: I/O resource w83627ehf [0x295-0x296] conflicts with ACPI region HWRE [0x290-0x299]
[   28.247106] ACPI: Device needs an ACPI driver
```
should I be worried?

R.

---

### Post by alukin on 2009-10-20
Generally speaking you should not. Read this:
[http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31)

And try to load module asus_atk0110 - it works with ACPI and slows down coolers a little bit. Though, if you want your sensors back, pass "acpi_enforce_resources=lax" to kernel in some appropriate place (depends on grub version), see /boot/grub

---

