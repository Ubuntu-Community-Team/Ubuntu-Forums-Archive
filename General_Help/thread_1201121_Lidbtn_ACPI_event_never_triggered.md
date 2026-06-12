---
title: "Lidbtn ACPI event never triggered"
date: 2009-06-30
forum: General Help
---

### Post by speaker219 on 2009-06-30
I'm having a problem with my laptop lid in Ubuntu 9.04. The lidbtn event is never triggered when the lid is closed. /proc/acpi/button/lid/LID0/state reports the proper states (open or closed), but the lid.sh script is never executed.

I can confirm this because my backlight does not turn off when I close my lid, but if I have this running:
```
while [ 1 ]; do /etc/acpi/lid.sh; sleep 1; done
```
The backlight turns off when the lid is closed, and back on when I open it. Any ideas? making me crazy :[

---

