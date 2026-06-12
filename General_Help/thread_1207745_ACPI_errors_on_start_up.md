---
title: "ACPI errors on start up"
date: 2009-07-08
forum: General Help
---

### Post by 6205 on 2009-07-08
I'm getting these ACPI errors on Ubuntu 9.04, right after grub and before usplash.

[COLOR="DarkRed"][     0.875341] ACPI: Invalid PBLK length [7]
[     0.875968] ACPI: Invalid PBLK length [7]
[/COLOR]
Any idea what may those be? Also LiveCD shows them. Older Ubuntu 8.10 don't was OK. Anyway, it doesn't seems to affect anything so hopefully it's safe to ignore it...

My desktop is HP dc7900SFF with Intel Q45/Q43 chipset, X4500 graphics.

---

### Post by ivanvajar on 2009-07-08
It's OK. A lot of people ask about that.

---

### Post by ivanvajar on 2009-07-08
ACPI is related to power management. You get that message 'cause ACPI is looking for session to restore on boot. Since you shut down your computer, there is no session to resume.

---

