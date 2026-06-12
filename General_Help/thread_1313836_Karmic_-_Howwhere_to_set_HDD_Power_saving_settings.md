---
title: "Karmic - How/where to set HDD Power saving settings ?"
date: 2009-11-04
forum: General Help
---

### Post by Nick Rhodes on 2009-11-04
In Intrepid this was done with laptop-mode.
I've been told that pm-utils now handles this, but I can't work out where to adjust hdd spindown times in particular.

I've also tried adding settings to hdparm.conf, but this seems to have no effect on reboot.

I need to know how to do this because one of my machines runs without a GUI.

Cheers, Nick

---

### Post by Nick Rhodes on 2009-11-06
I still not have had any luck getting hdparm.conf to work, which would be my preference.

But I have got Laptop-mode working. Having looking through the pm-utils scripts there are checks in there for using Laptop-mode, so I consider this a fix rather than a 

From [https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement) I worked out for Karmic the following need to be done:

1. Create an empty "laptop-tools" file using the command:
```
sudo touch /etc/pm/power.d/laptop-tools
```

2. ENABLE_LAPTOP_MODE=true in /etc/default/acpi-support

3. Enable CONTROL_HD_POWERMGMT=1 in /etc/laptop-mode/laptop-mode.conf 

Edit, after a few days of testing, seems stable, will update the Wiki and report bugs when I am happy.

Cheers, Nick

---

