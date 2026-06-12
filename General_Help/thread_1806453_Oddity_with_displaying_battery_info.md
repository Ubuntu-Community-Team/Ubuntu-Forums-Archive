---
title: "Oddity with displaying battery info"
date: 2011-07-17
forum: General Help
---

### Post by Vamirr on 2011-07-17
I'm having an issue with my Toshiba L745 where the battery is not being detected unless certain events happen.  This is under 64 bit Natty.

The power management application is set to Always display an icon.  There is no "On Battery Power" tab.

The power management icon displays the "on ac" lightning bolt unless one of following events occur: the battery's charge falls below 10% or I plug the laptop into the AC source.

If the battery monitor does not display the battery, issuing the ACPI command at the terminal returns nothing.  After I plug the laptop in, ACPI returns battery information and the battery monitor displays the current charge. From here, I am able to see the battery's charge and ACPI returns info until the next time I reboot.

At no point does the power management application display an on battery power tab.

---

