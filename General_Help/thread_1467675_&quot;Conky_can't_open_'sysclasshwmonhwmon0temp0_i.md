---
title: "&quot;Conky: can't open '/sys/class/hwmon/hwmon0/temp0_input': No such file or directory&quot;"
date: 2010-04-30
forum: General Help
---

### Post by Hund on 2010-04-30
I upgraded from Hardy to Lucid today. I thought it would solve the problem, but it didnt.

> Conky: can't open '/sys/class/hwmon/hwmon0/temp0_input': No such file or directory
please check your device or remove this var from Conky

The part from my Conky config:

> CPU1: ${alignr} ${hwmon 1 temp 1}°C
CPU2: ${alignr} ${hwmon 2 temp 1}°C

Dunno what to do?

---

### Post by Hund on 2010-05-01
Since I couldnt get it to work, I came up with another solution to print the temp:

```
${execi 30 sensors | grep 'Core0' | awk '{print $3}' | cut -c2-3}°C
```

:)

---

