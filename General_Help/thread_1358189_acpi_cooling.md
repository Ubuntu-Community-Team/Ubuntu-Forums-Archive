---
title: "acpi cooling"
date: 2009-12-18
forum: General Help
---

### Post by bkmfs on 2009-12-18
I am running a Dell Inspiron 530 with Ubuntu Studio 9.04.

My cooling fans do not speed up or slow down they just move at a constant slow speed.  Here is a snapshot of my terminal:

:~$ cat /proc/acpi/thermal_zone/THRM/cooling_mode
0 - Active; 1 - Passive
:~$ cat /proc/acpi/thermal_zone/THRM/polling_frequency
<polling disabled>
:~$ cat /proc/acpi/thermal_zone/THRM/state
state:                   ok
:~$ cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             40 C
:~$ cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           120 C
passive:                 50 C: tc1=4 tc2=3 tsp=60 devices=CPU0
active[0]:               50 C: devices= FAN
:~$

I can't seem to get permissions to change my 'polling_frequency' no matter what sudo method I try.  My 'cat /proc/acpi/thermal_zone/THRM/temperature' always comes up at 40 no matter how much I seem to pushing my machine and yet I do not hear my fans working any harder.  I assume that my cooling_mode is passive but I can't seem to change that. 

Can somebody help me figure out how to set my cooling fans up to be in active mode and with variable speeds?

---

### Post by bkmfs on 2012-05-28
F U acpi!

---

