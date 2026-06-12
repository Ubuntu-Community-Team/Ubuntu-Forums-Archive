---
title: "i thought HAL was no more in 10.04?"
date: 2010-04-30
forum: General Help
---

### Post by 51dusty on 2010-04-30
so, i assumed since the lucid release notes had this in it:
```
HAL removal
...full removal of HAL from the boot process, making Ubuntu faster to boot and faster to resume from suspend.
```

that the HAL components would have been removed with the other obsolete packages, but this is not the case(on my sys anyway). are they still being used?

---

### Post by happyhamster on 2010-04-30
It means that Lucid doesn't need the HAL daemon anymore to talk with the hardware, but there still are shared libraries that are needed (other programs use those as well).
You can check for hal-related processes with the command: 

ps aux | grep hal

Output from my Jaunty box:
```

106       2577  0.0  0.0  36416  4832 ?        Ss   00:02   0:00 /usr/sbin/hald
root      2643  0.0  0.0  15864  1260 ?        S    00:02   0:00 hald-runner
root      2672  0.0  0.0  28532  1976 ?        S    00:02   0:00 hald-addon-input: Listening on /dev/input/event0 /dev/input/event1 /dev/input/event3 /dev/input/event2
root      2732  0.0  0.0  28532  1980 ?        S    00:02   0:00 hald-addon-storage: polling /dev/sr1 (every 2 sec)
root      2733  0.0  0.0  28540  1976 ?        S    00:02   0:00 /usr/lib/hal/hald-addon-cpufreq
106       2734  0.0  0.0  32436  2036 ?        S    00:02   0:00 /usr/lib/hal/hald-addon-acpi
root      2736  0.0  0.0  28532  1976 ?        S    00:02   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
user12    3186  0.0  0.0  56184  4072 ?        S    00:02   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
user12    4528  0.0  0.0   7576   804 pts/1    S+   00:45   0:00 grep --color=auto hal

```

Output from my Lucid box:
```
user34    2758  0.0  0.0   7616   908 pts/2    S+   00:55   0:00 grep --color=auto hal

```

---

### Post by HappyTimeHarry on 2010-04-30
I'm sorry, Dave I'm afraid I can't do that. :P

---

### Post by nanog on 2010-04-30
Hal was removed from the boot process. Hal is still used by thousands of programs (if you have one of those it will be installed as a dependency).

---

### Post by 51dusty on 2010-04-30
thanks for the info guys!
:)

---

