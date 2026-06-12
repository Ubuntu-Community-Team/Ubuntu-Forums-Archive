---
title: "landscape-sysinfo not displaying temperature"
date: 2010-06-30
forum: General Help
---

### Post by CharlesA on 2010-06-30
Hi there,

I am running Lucid x64 on an Gigabyte Mobo with an Intel E6500 CPU.

I think this script pulls the temperature from /proc/acpi/thermal_zone. However, that directory is empty.

I can get the cpu temp by using lm-sensors or by running this:

```
cat /sys/class/hwmon/hwmon0/device/temp1_input
```

Any ideas on how to get landscape-sysinfo to display the temperature?

Thanks.

---

### Post by CharlesA on 2010-07-01
Anyone?

---

### Post by CharlesA on 2010-07-04
Did a clean install of Lucid Server x64 on another machine with an Asus mobo, installed lm-sensors and ran sensors-detect. It displayed the correct CPU and mobo temp from ACPI, but /proc/acpi/thermal_zone was empty and landscape-sysinfo still didn't display the temperature.

Oh well, I guess I shall have to stick with using sensors to check the temps.

---

### Post by beruic on 2013-01-16
I have the same problem now, except I don't seem to have /proc/acpi/thermal_zone at all.

---

### Post by oldos2er on 2013-01-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

