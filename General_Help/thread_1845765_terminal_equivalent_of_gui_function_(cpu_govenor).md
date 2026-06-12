---
title: "terminal equivalent of gui function (cpu govenor)"
date: 2011-09-17
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-09-17
i know this script will do it but it needs root the applet does not need my password


~# cpuGovenor preformance
```
    for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n "$1" > $CPUFREQ
    done
```

---

