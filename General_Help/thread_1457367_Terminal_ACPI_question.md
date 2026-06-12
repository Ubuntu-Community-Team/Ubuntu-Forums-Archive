---
title: "Terminal ACPI question"
date: 2010-04-18
forum: General Help
---

### Post by altjx on 2010-04-18
The command "acpi -V" shows these results
```
Battery 0: Charging, 25%, 02:29:42 until charged
Battery 0: design capacity 7800 mAh, last full capacity 6427 mAh = 82%
Adapter 0: on-line
Thermal 0: ok, 56.5 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 105.0 degrees C
Cooling 0: LCD 0 of 15
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10

```

what exactly does the second line mean?
```
Battery 0: design capacity 7800 mAh, last full capacity 6427 mAh = 82%
```
A few days ago it was 85%

---

### Post by altjx on 2010-04-18
hmm

---

### Post by rnerwein on 2010-04-18
hi
for a techincal explanation have a look at: [http://en.wikipedia.org/wiki/Ampere-hour](http://en.wikipedia.org/wiki/Ampere-hour)

in short: your battery has, when it is full loaded, only 82%. this value is going down as older your
battery is. it's a normal behavior.
ciao

---

### Post by altjx on 2010-04-18
> **rnerwein said:**
> hi
for a techincal explanation have a look at: [http://en.wikipedia.org/wiki/Ampere-hour](http://en.wikipedia.org/wiki/Ampere-hour)

in short: your battery has, when it is full loaded, only 82%. this value is going down as older your
battery is. it's a normal behavior.
ciao

oh ok. in other words, when it's close to 0% it'll be time for a new battery?

---

