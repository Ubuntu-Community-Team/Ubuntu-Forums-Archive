---
title: "lm-sensors and i5 processor"
date: 2011-07-05
forum: General Help
---

### Post by An Sanct on 2011-07-05
Hello there!

As mentioned in the title, I have a Intel i5-750 processor and am using lm-sensors to check on the temperature.

The results are amazing, this is the output of
```

an@drak:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +0.86 V  (min =  +0.80 V, max =  +1.60 V)
+3.3V Voltage:      +3.39 V  (min =  +2.97 V, max =  +3.63 V)
+5V Voltage:        +5.04 V  (min =  +4.50 V, max =  +5.50 V)
+12V Voltage:      +11.98 V  (min = +10.20 V, max = +13.80 V)
CPU Fan Speed:     1962 RPM  (min =  600 RPM)
Chassis1 Fan Speed:   0 RPM  (min =  600 RPM)
Chassis2 Fan Speed:   0 RPM  (min =  600 RPM)
Power Fan Speed:      0 RPM  (min =    0 RPM)
CPU Temperature:    +39.5°C  (high = +45.0°C, crit = +45.5°C)  
MB Temperature:     +30.0°C  (high = +45.0°C, crit = +46.0°C)  

```I'm mostly interested in the CPU temperature. Currently the machine is not *"under stress*" - thus 40C. Also it states there, that 45.5C is critical (???) but the sensors show temperatures of up to 70C+ (!!!) while under heavy load (several VMs + LAMP + Firefox + ....)

Has anybody had any experience with lm-sensors in combination with i5? Maybe the sensor value multiplier is wrong (currently at the default *1.000*) ?

---

### Post by Mark Phelps on 2011-07-05
Noticed that you're running 10.10.  If you downloaded lm-sensors from the repos with that, you could be using an older version.

The link below is to the Debian package search tool, and shows the latest lm-sensors packages:

[http://packages.debian.org/search?keywords=lm-sensors&searchon=names&suite=all&section=all]("http://packages.debian.org/search?keywords=lm-sensors&searchon=names&suite=all&section=all")

You could try using one of the newer versions, instead.

---

### Post by An Sanct on 2011-07-05
Yes, the info in my avatar is correct :) maybe I should have pointed it out more directly ...

Well ... I'm losing myself around that deb-package web place ... what should I do?

lenny/squeeze/wheezy/sid?

---

### Post by An Sanct on 2011-07-05
Okay :) I clicked something, upgraded the packages and now I have temperature for every core ... yet still I'm interested ... What are normal working temperatures for an i5 type processor? Should I be concerned about 70 deg.C?

---

### Post by pqwoerituytrueiwoq on 2011-07-05
is it under load?
it it in a laptop
my AMD Phenom II X4 965 runs at 33C idle SHSF in my desktop
using a side air duct (home made)

---

### Post by jorok_tupur on 2011-07-05
I'm using i5-430M.

```

someuser@somedomain:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +56.0°C  (high = +95.0°C, crit = +105.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +47.0°C  (high = +95.0°C, crit = +105.0°C)

```

Is this normal? My laptop does feel hot to the touch from time to time.

---

### Post by An Sanct on 2011-07-05
Well, I get this readings now

```
an@drak:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +0.86 V  (min =  +0.80 V, max =  +1.60 V)
+3.3V Voltage:       +3.39 V  (min =  +2.97 V, max =  +3.63 V)
+5V Voltage:         +5.06 V  (min =  +4.50 V, max =  +5.50 V)
+12V Voltage:       +12.04 V  (min = +10.20 V, max = +13.80 V)
CPU Fan Speed:      1916 RPM  (min =  600 RPM)
Chassis1 Fan Speed:    0 RPM  (min =  600 RPM)
Chassis2 Fan Speed:    0 RPM  (min =  600 RPM)
Power Fan Speed:       0 RPM  (min =    0 RPM)
CPU Temperature:     +40.5°C  (high = +45.0°C, crit = +45.5°C)
MB Temperature:      +31.0°C  (high = +45.0°C, crit = +46.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +40.0°C  (high = +83.0°C, crit = +99.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +38.0°C  (high = +83.0°C, crit = +99.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +37.0°C  (high = +83.0°C, crit = +99.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +37.0°C  (high = +83.0°C, crit = +99.0°C)


```

The thing I don't get is: a cores max temp can be +99.0°C and the processors +45.5°C :) I consider it funny ...

By the way, the temperature, that should not exceed 45.5°C is still jumping up to 70+

pqwoerituytrueiwoq: My computer is a "normal" desktop and due to the fact, that it is summer right now, with normal temperatures around 35°C so the case is opened. My case has a lot of vents, but temperature readings from my CPU made me nervous, so I opened it ...

---

