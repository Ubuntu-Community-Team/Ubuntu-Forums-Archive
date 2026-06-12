---
title: "Fancontrol / pwmconfig"
date: 2010-10-23
forum: General Help
---

### Post by CyberRascal on 2010-10-23
Hi. I have run into a small problem. sensors-detect rightly detect the sensors for my motherboard. However, then pwmconfig tells me I have no PWM compatible sensors.

I have an Asus P6T SE motherboard.

Then I ran across this:

[http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31)

and added acpi_enforce_resources=lax. This fixes my problem, but seems less than ideal. For one it seems dangerous,  and for one it seems that it disabled all labels for my temps.

Does anyone know what I should do, is there an ACPI interface driver or whatever I need for the motherboard I have (P6T SE).

Thanks!

---

### Post by CyberRascal on 2010-10-24
I'm sorry, I see no option but bumping this thread..!

---

### Post by P4man on 2010-10-24
DOnt know really, but have you checked if asus_atk0110 is loaded? You could try loading it manually

```
sudo modprobe asus_atk0110
```

and see if that helps.

---

