---
title: "Random shutdown"
date: 2010-08-23
forum: General Help
---

### Post by grumpy.biatch on 2010-08-23
I've a dual boot system with Windows 7 x64 ultimate and Ubuntu 10.04 x86. I added 2 GB ram a couple of days ago and installed Server Kernel (PAE) in order to get Ubuntu recognize 4 GB DDR2 memory.

The Ubuntu now shuts down randomly, I have checked the smart fan function from BIOS and found it correct. I have not observed any shut down issues from windows. I've tried running Linux Mint amd64 live cd and that fails as well.

---

### Post by john newbuntu on 2010-08-23
Have you put it through a thorough memtest86+ with one stick of RAM at a time. When in Ubuntu monitor the CPU temps.

---

### Post by grumpy.biatch on 2010-08-23
> **john newbuntu said:**
> Have you put it through a thorough memtest86+ with one stick of RAM at a time. When in Ubuntu monitor the CPU temps.

Yeah, I ran memtest for 4 chips, I ran those from windows (memory test) and ubuntu, it didnt return any error. I am now using Ubuntu, checking crashme for last half an hour but it didnt crash yet. I guess this is mobo(msi sucks) issue, will like to check whats killing it and get a replacement in case of fault. 

The temps normal -

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +124.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +47.0°C                                    
Core0 Temp:  +46.0°C                                    
Core1 Temp:  +50.0°C                                    
Core1 Temp:  +42.0°C
```

---

### Post by grumpy.biatch on 2010-08-23
I've discovered the problem with regards to random shut down.

1. dmesg shows - [   92.504023] Clocksource tsc unstable (delta = -184895675 ns)

2. 'sudo cat /sys/devices/system/clocksource/clocksource0/available_clocksource' shows options with - hpet acpi_pm 

3. 'sudo cat /sys/devices/system/clocksource/clocksource0/current_clocksource' shows hpet

Should I turn off ACPI in BIOS or what should I do in order to resolve this.

---

### Post by john newbuntu on 2010-08-23
It appears like you might have solved the problem yourself.  I haven't encountered the clock running away problem nor the shutoff one and so am not qualified to give you the right advice.

But on Googling, it appears like using one of the following kernel parameters: noacpi or acpi=off or notsc has helped some people. If none work, try turning off ACPI in BIOS.  tsc for sure is bad.  A few others have used acpi_pm instead of hpet for the clocksource.

---

### Post by grumpy.biatch on 2010-08-24
I have tried resetting all parameters in BIOS but none worked as yet. I cant even boot a livecd, guess this is a hardware issue, will like to know what causes it. I dont trust the vendor, I guess if i get to know what keeps it from booting, will help me chew butt at acer.

---

