---
title: "Fan control"
date: 2011-05-23
forum: General Help
---

### Post by lbozzay on 2011-05-23
I installed lm_sensors and it's giving me the following when running sensors in terminal

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +39.0°C  (crit = +100.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +35.0°C  (high = +82.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 2:       +33.0°C  (high = +82.0°C, crit = +100.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 3:       +33.0°C  (high = +82.0°C, crit = +100.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 1:       +35.0°C  (high = +82.0°C, crit = +100.0°C)
```

I however always have to start the modules manually.

When I run sudo pwmconfig I get

```
There are no pwm-capable sensor modules installed
```

Any idea how to fix this? Thanks!

---

