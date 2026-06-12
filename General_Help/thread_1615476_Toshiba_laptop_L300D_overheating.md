---
title: "Toshiba laptop L300D overheating"
date: 2010-11-07
forum: General Help
---

### Post by Kr0nZ on 2010-11-07
Hi,
i been trying to deal with this problem for awhile now but every google search leads to dead ends.
when my laptop running ubuntu 10.10 is doing something resource intensive it tends to overheat and shutdown, ive never had this problem in windows
the fan in my laptop is running but it runs at the same speed all the time(when i am in windows you can hear the fan change speeds depending on what im doing)
ive also tried appending acpi_osi=Linux to the end of the kernel line in the grub menu but i dont think this changed anything

If anyone has any ideas on able to fix my fan issue or atleast be able to increase the speed of it it would be greatly appreciated

---

### Post by P4man on 2010-11-07
Have you installed lm-sensors (if not, install it from software center, then run ```
sudo sensors-detect
``` from the terminal, confirm every question. THen reboot and what does sensors report?

You could also try adding ```
acpi.power_nocheck
``` as boot option or ```
acpi_osi=
``` (nothing behind the equal sign).

---

### Post by Kr0nZ on 2010-11-07
thanks i tried the 'acpi_osi=' and i think it made a difference, correct me if im wrong but this disables linux acpi support right? and only allows the bios to control my fan
anyways, i think my fan speed is now actually changing speeds, and i can now crack my own wep without my laptop failing

i tried installing lm-sensors but i could only get it to detect my temperature sensor (module k10temp-pci-00c3), currently reading 65.5 witch is better than it was before when it was reading 80+

thanks again

---

### Post by P4man on 2010-11-08
> **Kr0nZ said:**
> thanks i tried the 'acpi_osi=' and i think it made a difference, correct me if im wrong but this disables linux acpi support right? 

No it doesnt (acpi=off would do that). It just prevents the kernel from responding to osi requests, which is the bios asking the OS for identification. Using that switch only prevents the bios from executing commands for specific windows versions.

See the link in my sig for more details

---

