---
title: "Dual boot Win XP 12.04  Boot Repair partially successful"
date: 2012-05-19
forum: General Help
---

### Post by sea_dawg on 2012-05-19
Following a fresh install of 12.04 on a dual HDD dual boot system first boot brought up Grub Rescue.

I installed Boot Repair in a live CD and ran the recommended repair.  Boot Repair indicated a successful repair.

Upon reboot there is no entry for Win XP.  

Gparted shows sda as full as it was before installing 12.04.  Nautilus shows Win XP files intact.

I don't think this is a hardware problem.  This dual HDD, dual boot system has successfully booted grub under 10.10, 10.04 and 11.10.

Boot Repair produced the URL  [http://paste.ubuntu.com/996608](http://paste.ubuntu.com/996608)

---

### Post by wilee-nilee on 2012-05-19
> **sea_dawg said:**
> Following a fresh install of 12.04 on a dual HDD dual boot system first boot brought up Grub Rescue.

I installed Boot Repair in a live CD and ran the recommended repair.  Boot Repair indicated a successful repair.

Upon reboot there is no entry for Win XP.  

Gparted shows sda as full as it was before installing 12.04.  Nautilus shows Win XP files intact.

I don't think this is a hardware problem.  This dual HDD, dual boot system has successfully booted grub under 10.10, 10.04 and 11.10.

Boot Repair produced the URL  [http://paste.ubuntu.com/996608](http://paste.ubuntu.com/996608)

Have you run in Ubuntu?

```
sudo update-grub
```

This should add XP to the grub menu.

---

### Post by sea_dawg on 2012-05-19
@wilee-nilee

That did the trick.  Thank you!

---

### Post by wilee-nilee on 2012-05-19
> **sea_dawg said:**
> @wilee-nilee

That did the trick.  Thank you!

 
Cool, enjoy. :)

---

