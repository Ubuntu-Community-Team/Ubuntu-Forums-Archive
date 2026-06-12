---
title: "backlight brightness doesn't dim on netbook when running on battery"
date: 2011-09-18
forum: General Help
---

### Post by rezbd on 2011-09-18
I have installed Lubuntu 11.04 on my ***SAMSUNG NF108-A01*** netbook. when my lappy runs on battery, backlight brightness suppose to reduce. but it stays same as it's running on AC power. Win XP was installed before I came to Lubuntu. This problem didn't happen there.

I've checked out "Power Menagemant Preference". Things are ok there. "Reduce Backlight brightness" is ticked for battery power.


What can I do now?  Battery discharge fast with full brightness.

---

### Post by rezbd on 2011-09-18
anybody knows what can I do for it? please?

---

### Post by rezbd on 2011-09-19
I have solved this problem by adding acpi_backlight=vendor after quiet splash in the grub entry ```
sudo leafpad /boot/grub/grub.cfg

```

But when I turn off AC power , brightness doesn't go off dim automatically. I have to restart my laptop on battery to get the dim brightness. Then if I connect AC power, it doesn't go automatically to full brightness. I have to restart again on AC power to get the full brightness!

---

### Post by raja.genupula on 2011-09-19
> **rezbd said:**
> I have installed Lubuntu 11.04 on my ***SAMSUNG NF108-A01*** netbook. when my lappy runs on battery, backlight brightness suppose to reduce. but it stays same as it's running on AC power. Win XP was installed before I came to Lubuntu. This problem didn't happen there.

I've checked out "Power Menagemant Preference". Things are ok there. "Reduce Backlight brightness" is ticked for battery power.


What can I do now?  Battery discharge fast with full brightness.
i think there will be a brightness applet in ubuntu , but i dont know about lubuntu . in the panel options at add to panel menu i have got that brightness applet on <11 versions , i think it should be there , check for it in lubuntu panel menu . 
all the best .

---

