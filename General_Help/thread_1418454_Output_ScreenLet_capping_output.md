---
title: "Output ScreenLet capping output"
date: 2010-02-28
forum: General Help
---

### Post by azzid on 2010-02-28
I just tried activating the "output screenlet" to have the output from 'dmesg' and 'sensors -A' available on my desktop.

It seems however that there is something wrong with the way that the output get parsed, some of the first characters are just dropped.

[IMG]http://azzid.sytes.net/output_scrlet.png[/IMG]

Anyone know why this might be? Or what one could do about it?

The actual output when I run the commands is:
```
[154056.324047] input input4: event field not found
[154056.508035] input input4: event field not found
[154056.724022] input input4: event field not found
[154056.740019] input input4: event field not found
[154056.820010] input input4: event field not found
[154057.667960] input input4: event field not found
```
and:
```
coretemp-isa-0000
Core 0:      +77.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0001
Core 1:      +75.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0002
Core 2:      +72.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0003
Core 3:      +73.0°C  (high = +82.0°C, crit = +100.0°C)
```

---

### Post by crazy ivan on 2011-03-13
Same problem here and still waiting for an answer from the developers:

[https://answers.launchpad.net/screenlets/+question/58968]("https://answers.launchpad.net/screenlets/+question/58968")

---

### Post by azzid on 2011-03-14
I tried adding my own description to launchpad to get some activity on the issue, it had been marked inactive by the launchpad janitor.

---

