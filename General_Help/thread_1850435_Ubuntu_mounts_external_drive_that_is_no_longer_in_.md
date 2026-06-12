---
title: "Ubuntu mounts external drive that is no longer in /etc/fstab"
date: 2011-09-26
forum: General Help
---

### Post by kristo5747 on 2011-09-26
About a month ago, I configured my /etc/fstab and added an external drive. I don't need it anymore so I edited my /etc/fstab and removed the declaration line.


  This morning I rebooted my development server and GRUB stopped with a  warning that this drive was not available: do I wait, skip and manually  recover?
  

What am I missing? Why is it still seeing my external drive?


On Ubuntu 11.04.

---

### Post by matt_symes on 2011-09-26
Hi

If it's stopping at GRUB, try updating GRUB. From the terminal...

```
sudo update-grub
```

Enter your password. It will not be displayed on the screen.

Kind regards

---

### Post by kristo5747 on 2011-09-26
> **matt_symes said:**
> Hi

If it's stopping at GRUB, try updating GRUB. From the terminal...

```
sudo update-grub
```Enter your password. It will not be displayed on the screen.

Kind regards


((red face))I removed the wrong line in my fstab. Solved it: thank God for backups.

---

