---
title: "cpu temps"
date: 2009-10-24
forum: General Help
---

### Post by sdowney717 on 2009-10-24
curious why cpu temps are being reported so differently from vista to ubuntu.
for example even in vista there is a difference of 5 to 6 degrees c and on to ubuntu it is showing up even warmer in the low to mid 50's.

I would expect these programs to get the same info from the same sensors on the board. This is a resting temp where the pc is not doing anything.

actually running sensors shows about the same as vista. but gkrellm is showing higher readings! like 51 to 55
> scott@scott-desktop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +50.0°C  (high = +78.0°C, crit = +100.0°C)  

scott@scott-desktop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +50.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +50.0°C  (high = +78.0°C, crit = +100.0°C)  

scott@scott-desktop:~$ 


---

### Post by QLee on 2009-10-24
> **sdowney717 said:**
> curious why cpu temps are being reported so differently from vista to ubuntu.
for example even in vista there is a difference of 5 to 6 degrees c and on to ubuntu it is showing up even warmer in the low to mid 50's.

I would expect these programs to get the same info from the same sensors on the board. This is a resting temp where the pc is not doing anything.

actually running sensors shows about the same as vista. but gkrellm is showing higher readings! like 51 to 55

If you are fairly confident that the Vista and sensors reading are correct since they agree, then you can set an offset in gkrellm so that it reports the same as sensors. Make sure they track as the core heats up too.

---

