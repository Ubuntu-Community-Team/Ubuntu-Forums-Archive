---
title: "poweroff does not work"
date: 2010-11-09
forum: General Help
---

### Post by jandom29 on 2010-11-09
hi,
I install Ubuntu 10.10 and the poweroff (command, button in GUI)does not work, the power supply does not switch off, I must press the power button of the PC to switch off.
When i remove the tuner TNT card (PCI-E) from the PC, the poweroff works.
Anybody have an idea to solve this problem?
I also try with Ubuntu 10.04 and I have the same problem. :confused:
Thank.

---

### Post by TeoBigusGeekus on 2010-11-09
You can shutdown via terminal
```
sudo shutdown -h now
```

---

### Post by jandom29 on 2010-11-10
This command does not work if the tuner card is plugged in the pci-e slot. If this tuner card is un-plugged the command works fine.

---

