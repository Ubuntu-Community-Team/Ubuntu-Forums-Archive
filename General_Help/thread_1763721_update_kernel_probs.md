---
title: "update kernel probs???"
date: 2011-05-20
forum: General Help
---

### Post by gene simmons on 2011-05-20
hi guys,i wanted to upgrade the kernel to .39 and i folowed the instructions and in terminal it showed it installed,i rebooted and it didnt show it upon boot and when  i looked once booted it showed old one still,i opended termainal and tried to reinstall and it said i had the newest version which is .39 but its not installed when i boot and when i look in system monitor,is there anther way to install the new kernel.thanx guys

---

### Post by 4Orbs on 2011-05-20
In the terminal:
```
sudo update-grub
```
then reboot and maybe it will show up.

---

