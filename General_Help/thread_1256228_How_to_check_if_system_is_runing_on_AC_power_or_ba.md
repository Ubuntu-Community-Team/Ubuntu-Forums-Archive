---
title: "How to check if system is runing on AC power or baterry?"
date: 2009-09-02
forum: General Help
---

### Post by hmfernandes on 2009-09-02
Hello all,

I'm developing an application in C to run in a laptop, and I need to be able to know when the AC power is unplugged. Does any one know a system signal that is sent when the AC power plug is disconnected.

My program will need to know that in order to send an alert to the user, so I need to monitor a "file" or "signal" where that information is frequently updated.

Basically I want to be able to know when AC power is down or a AC plug is disconnected, just as gnome power manager does to reduce dim, etc...

Thanks in advance,
Helder Matos Fernandes

---

### Post by asmoore82 on 2009-09-02
Not sure where to go from here, but:

```
cat /proc/acpi/ac_adapter/AC/state
```

---

### Post by philinux on 2009-09-02
> **hmfernandes said:**
> Hello all,

I'm developing an application in C to run in a laptop, and I need to be able to know when the AC power is unplugged. Does any one know a system signal that is sent when the AC power plug is disconnected.

My program will need to know that in order to send an alert to the user, so I need to monitor a "file" or "signal" where that information is frequently updated.

Basically I want to be able to know when AC power is down or a AC plug is disconnected, just as gnome power manager does to reduce dim, etc...

Thanks in advance,
Helder Matos Fernandes

Install the app acpi

Then acpi -b should show batter state.

```
OPTIONS
       -b | --battery
                 show battery information

       -B | --without-battery
                 suppress battery information

       -i | --capacity
                 show battery capacity information if available

       -a | --ac-adapter
                 show ac adapter information

       -A | --without-ac-adapter
                 suppress ac-adapter information

       -t |  --thermal
                 show thermal information

       -T | --without-thermal
                 suppress thermal information

       -c | --cooling
                 show cooling device information

       -C | --without-cooling
                 suppress cooling device information

       -V | --everything
                 show every device, overrides above options

       -s | --show-empty
                 show non-operational devices

       -S | --hide-empty
                 hide non-operational devices

       -f | --fahrenheit
                 use fahrenheit as the temperature unit instead of default celsius

       -k | --kelvin
                 use kelvin as the temperature unit instead of default celsius

       -p | --proc
                 use the old /proc interface, default is the new /sys one

       -d | --directory <dir>
                 path to ACPI info (either /proc/acpi or /sys/class)

       -h | --help
                 display help and exit

       -v | --version

```

---

### Post by hmfernandes on 2009-09-02
Thank you both for your fast replies.

Best Regards,
Helder Matos Fernandes

---

