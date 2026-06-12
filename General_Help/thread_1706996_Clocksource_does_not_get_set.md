---
title: "Clocksource does not get set"
date: 2011-03-14
forum: General Help
---

### Post by mdeen on 2011-03-14
I have two clocksources available: hpet and acpi_pm. hpet is set as current_clocksource, but since ntp can't keep proper time and the cpu clock is being changed because of power saving, I want to try acpi_pm. I've changed GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub to "quiet splash clocksource=acpi_pm" and ran update-grub. The boot option is listed in /boot/grub/grub.cfg
After booting, the clocksource option is also listed in /proc/cmdline, but the current_clocksource is stil set to hpet.

What am I doing wrong here?
System is 10.04.2 desktop on an Athlon XP 64 5050e.

---

