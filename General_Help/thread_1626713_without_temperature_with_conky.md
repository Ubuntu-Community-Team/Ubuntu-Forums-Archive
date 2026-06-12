---
title: "without temperature with conky"
date: 2010-11-20
forum: General Help
---

### Post by davidtuti on 2010-11-20
Hi,
I've installed lm-sensors Ok but I cant get the CPU temperature, always shows me 0.


```
sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.21 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.20 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +4.94 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.04 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     2556 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:   0 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:   0 RPM  (min =  600 RPM)
POWER FAN Speed:    577 RPM  (min =  600 RPM)
CPU Temperature:    +29.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:     +42.0°C  (high = +45.0°C, crit = +95.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +50.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +49.0°C  (high = +78.0°C, crit = +100.0°C)  


.conkyrc

..........
.........


[ number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT

${font Goudy Bookletter 1911:style=Bold}SYSTEM${font} ${hr 2}
${alignc 17}${font Sniglet:size=16}googly${font}

${alignc}${font Comfortaa:size=10}fly, you fools${font}
${voffset 2}${font StyleBats:size=16}i${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}l${font}  Temperatura: ${alignr}${acpitemp}C
${font StyleBats:size=16}l${font}  Temperatura: ${alignr}${acpifan}C

```

Any help please?
Many thanks and sorry for my english!

---

### Post by Hippytaff on 2010-11-20
not sure of how conky deals with this but acpi -t outputs the temp
should it be
```
{font StyleBats:size=16}l${font}  Temperatura: ${alignr}${acpi -t}C
```this is a wild guess btw :-)

also did you mean to type temperatura rather than temperature?

---

### Post by stinkeye on 2010-11-20
Have a look at this page from conky-pitstop.
[**_[COLOR="DarkRed"]http://conky-pitstop.wikidot.com/programs#toc2[/COLOR]_**]("http://conky-pitstop.wikidot.com/programs#toc2")

---

### Post by davidtuti on 2010-11-20
> **Hippytaff said:**
> not sure of how conky deals with this but acpi -t outputs the temp
should it be
```
{font StyleBats:size=16}l${font}  Temperatura: ${alignr}${acpi -t}C
```this is a wild guess btw :-)

also did you mean to type temperatura rather than temperature?

If I write:
${font StyleBats:size=16}l${font}  Temperatura: ${alignr}${acpi -t}C

in conky it shows me:
Temperatura:         $[acpi]C
Temperatura:         nofans?C

Any help?

---

### Post by Hippytaff on 2010-11-20
Then ignore me and my ignorance - check out stinkeye's link :-)

---

### Post by Girya on 2010-11-20
Not sure from your post if you configured lm-sensors. If you didn't configure try this page to configure lm-sensors: 

[http://http://www.cyberciti.biz/faq/howto-linux-get-sensors-information/]("http://www.cyberciti.biz/faq/howto-linux-get-sensors-information/")

---

### Post by stinkeye on 2010-11-20
```
${execi 8 sensors | grep "CPU Temperature:" | cut -c22-23}
```
From your first post this should give your temp.


I prefer to use the core temps though
```
${execi 8 sensors | grep "Core 0:" | cut -c15-16}
${execi 8 sensors | grep "Core 1:" | cut -c15-16}
```

---

