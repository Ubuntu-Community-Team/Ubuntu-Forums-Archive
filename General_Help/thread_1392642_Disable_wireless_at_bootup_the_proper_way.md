---
title: "Disable wireless at bootup the proper way"
date: 2010-01-28
forum: General Help
---

### Post by Andreas1 on 2010-01-28
When my Laptop is booted, wireless is activated automatically. I don't want that because i rarely need it, so i want it to be off by default.
I found that if i do ```
echo 0 > /sys/devices/platform/acer-wmi/wireless
``` it has the same effect as flicking the radio switch.
i have 2 questions:

is the above the proper way to do this?
if so: where do i place this command? rc.local? (is executed very late during bootup, i'd rather have it sooner). do i make a new script in init.d? (fairly complicated as is has to have a certain structure, like start and stop and such).

---

