---
title: "Change trip points"
date: 2011-03-02
forum: General Help
---

### Post by Vistz on 2011-03-02
Lately, I've been noticing that my laptop seems to get very hot. When I'm looking at the sensor's applet, it says my CPU temp reaches up to 80 degrees C. When I run
```
cat/proc/acpi/thermal_zone/THM/trip_points
```this is what I see

```
critical (S5):           126 C
```I've tried changing the trip point by using this command
```
gksudo echo -n "100:0:80:70:60:50:" > /proc/acpi/thermal_zone/THM/trip_points 
```but I end up getting
```
bash: /proc/acpi/thermal_zone/THM/trip_points: Permission denied
```

Is there another way I can change the trip point?

---

