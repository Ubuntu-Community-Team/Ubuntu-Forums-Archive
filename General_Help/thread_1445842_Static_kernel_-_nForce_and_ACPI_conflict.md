---
title: "Static kernel - nForce and ACPI conflict"
date: 2010-04-03
forum: General Help
---

### Post by Arch Linux on 2010-04-03
I'm unable to use my "builtin" forcedeth (nForce ethernet card) driver because it conflicts with some of my "builtin" ACPI features. Anybody know what that is so that I don't need to test?

```
&#9492;&#9484;(%:~)&#9484;- dmesg |grep Force
forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
i2c i2c-0: nForce2 SMBus adapter at 0x600
**ACPI: I/O resource nForce2_smbus [0x700-0x73f] conflicts with ACPI region SM00 [0x700-0x73f]**
nForce2_smbus 0000:00:01.1: Error probing SMB2.
```

---

### Post by Arch Linux on 2010-04-03
Bump. Static kernel compilation people, I need you.

---

### Post by Intrepid Ibex on 2010-04-04
Did you try with "acpi_enforce_resources=lax" yet?

Btw. Nice avatar :D.

---

### Post by Arch Linux on 2010-04-08
Yes, but doesn't work.. I also tried all the possible ACPI features as modules while the forcedeth driver still being builtin but no luck.

---

### Post by Intrepid Ibex on 2010-04-08
Found this: [http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31). If you have a ASUS motherboard, did you try building the asus_atk0110 driver too? From the kernel docs:
```
ASUS ATK0110 (SENSORS_ATK0110)

CONFIG_SENSORS_ATK0110:

If you say yes here you get support for the ACPI hardware
monitoring interface found in many ASUS motherboards. This
driver will provide readings of fans, voltages and temperatures
through the system firmware.

This driver can also be built as a module. If so, the module
will be called asus_atk0110.

Symbol: SENSORS_ATK0110 [=n]
Prompt: ASUS ATK0110
Defined at drivers/hwmon/Kconfig:1083
Depends on: HWMON [=m] && ACPI [=y] && X86 [=y] && EXPERIMENTAL [=y]
Location:
-> Device Drivers
-> Hardware Monitoring support (HWMON [=m])
```

---

