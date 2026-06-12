---
title: "Battery power information from CLI"
date: 2010-09-15
forum: General Help
---

### Post by e24ohm on 2010-09-15
Folks:
I am running a cli only based laptop for a special project; however, is there any terminal based simple text or GUI applications that will give me power remaining and other information about the battery? Looking for: power remaining, total power, WATTS, AMPS, etc... just the basic items and some other items, nothing to fancy.


Thanks.

---

### Post by solar george on 2010-09-15
Install [acpi]("apt://acpi") for the basic % remaining or [acpitool]("apt://acpitool") for more details, or you could just;
```

george-laptop~&#9774;:cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         47520 mWh
last full capacity:      45824 mWh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 918 mWh
design capacity low:     0 mWh
capacity granularity 1:  10 mWh
capacity granularity 2:  10 mWh
model number:            G71C0001R11E
serial number:           0000000000
battery type:            Li-ION  


```

---

