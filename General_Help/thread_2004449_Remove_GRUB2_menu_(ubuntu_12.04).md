---
title: "Remove GRUB2 menu (ubuntu 12.04)"
date: 2012-06-15
forum: General Help
---

### Post by abimael08 on 2012-06-15
I want ubuntu to automatically boot, i dont want to see the grub menu to choose between the Linux or Memtest options, prefer to do this thru terminal, no programs please. Thank You

---

### Post by wilee-nilee on 2012-06-15
> **abimael08 said:**
> I want ubuntu to automatically boot, i dont want to see the grub menu to choose between the Linux or Memtest options, prefer to do this thru terminal, no programs please. Thank You

Do you have more then one OS on the computer, that is  only when you will see the grub menu, unless you trigger it with the shift key at powering on, or grub is borked.

If you only have one OS try runing in ubuntu
```
sudo update-grub
```

---

### Post by drs305 on 2012-06-15
```
sudo sed "s/GRUB_TIMEOUT=[0-9]*/GRUB_TIMEOUT=0/g" -i /etc/default/grub
sudo update-grub
```
This will replace any GRUB_TIMEOUT of [0-9]* seconds (0+) to 0, although I'd recommend 1 so you can interrupt it if you need to.

---

### Post by abimael08 on 2012-06-15
> **wilee-nilee said:**
> Do you have more then one OS on the computer, that is  only when you will see the grub menu, unless you trigger it with the shift key at powering on, or grub is borked.

If you only have one OS try runing in ubuntu
```
sudo update-grub
```

  No, i only have UBUNTU 12.04

---

### Post by wilee-nilee on 2012-06-15
> **abimael08 said:**
> No, i only have UBUNTU 12.04

Try drs305's solution.

---

### Post by abimael08 on 2012-06-15
> **drs305 said:**
> ```
sudo sed &quot;s/GRUB_TIMEOUT=[0-9]*/GRUB_TIMEOUT=0/g&quot; -i /etc/default/grub
sudo update-grub
```This will replace any GRUB_TIMEOUT of 1 to 10 seconds to 0, although I'd recommend 1 so you can interrupt it if you need to.

  Worked, THANKS

---

