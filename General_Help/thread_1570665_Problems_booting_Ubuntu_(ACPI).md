---
title: "Problems booting Ubuntu (ACPI)"
date: 2010-09-08
forum: General Help
---

### Post by AldoAxel on 2010-09-08
Hi, guys! First of all, thank you for taking the time to read and try to help me solve my problem.

I've installed Ubuntu 10.04.1 32 bits from a USB flash drive, but when I restarted the laptop for the first time, it could't boot into the system, it just stayed with a blinking underscore at the left of the screen. So, in order to see what was happening, I removed the 'quiet' argument form the GRUB, and now I see that hangs with 'ACPI: Core revision 20090903'. I've read that using  'acpi=off noapic nolapic' could work, but when I do that, it hangs at 'NET: Registered protocol family 1'. I've also tried using Ubuntu amd64 and even the 10.10 beta, but the results are the same. I've been dealing with this problem for days, and I really don't want to go back to Windows.

My notebook's specifications:
HP Pavillion DV6951LA
AMD Turion 64 X2 TL-62 2,1 GHz
4Gb RAM
Graphics NVIDIA GeForce Go 7150M
HDD 250 GB (5400 RPM)
Bios: F.32

I've read that some HP's have a problem with ACPI, and a solution is upgrading the kernel to 2.6.35, but even with the  
kernel form Maverick beta, I get the same problems.

---

