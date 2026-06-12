---
title: "battery power not recognized"
date: 2010-12-05
forum: General Help
---

### Post by urur on 2010-12-05
Hello Ubuntu Users,

when I boot without the AC cable plugged in the Power Applet says I am on AC power (but the notebook is of course running on battery power). Which is bad because I don't know how much battery time still remains.

Strangely, when I boot on AC Power and then remove the AC cable both the fact that battery power is used and the remaining battery time is shown correctly.

Also when I boot into battery power and then plug in the AC cable it correctly shows that the battery is charging and how long it takes until fully charged.

Please help me?

I use Ubuntu 10.10, 32bit on an Acer Aspire One 751 if that helps. The problem has also existed in Ubuntu 10.04 and I hoped the update would solve it but it did not.

If you need more Information please ask.

---

### Post by urur on 2010-12-06
Anyone?

---

### Post by linux-hack on 2010-12-06
Take a look at this : [http://linux.die.net/man/8/laptop-mode.conf](http://linux.die.net/man/8/laptop-mode.conf)
[http://www.linux-on-laptops.com/battery-powered/linux-power-management.html](http://www.linux-on-laptops.com/battery-powered/linux-power-management.html)

---

### Post by urur on 2010-12-09
Thanks for the links, linux-hack.
I found a solution, here it is in case someone has the same problem:

1) install the acpi package with
```
sudo apt-get install acpi
```

2) everytime the battery is not shown correctly type
```
cat /proc/acpi/battery/BAT1/state
```

this will make the system recognize it is running on battery power

---

