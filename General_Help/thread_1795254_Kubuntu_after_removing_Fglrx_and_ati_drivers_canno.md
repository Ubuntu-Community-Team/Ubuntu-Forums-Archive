---
title: "Kubuntu: after removing Fglrx and ati drivers cannot login"
date: 2011-07-02
forum: General Help
---

### Post by avary on 2011-07-02
hello  i was running kubuntu 10.10 with ati drivers (11-5) . for some problems s, i reinstalled ati-drivers to install lastest version (11-6) but before install the new driver i reinstalled Fglrx as described here ([https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch)) then rebooted. now when i start my computer it boots up and later show kubuntu progress bar then shade off with random colors and goes black completey ..  how i can fix this without needing to reinstall the whole system?


edit : fixed it, i booted from a live cd and mounted my linux partion than chroot, finally install ati drivers and problem gone.

---

