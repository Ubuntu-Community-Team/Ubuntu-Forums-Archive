---
title: "CPU Temps Show Twice"
date: 2010-12-23
forum: General Help
---

### Post by frustratednerd on 2010-12-23
When I do the 'sensors' command in Terminal, this is what shows up:

apple@fruit-bowl:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +52.0°C                                    
Core0 Temp:  +49.0°C                                    
Core1 Temp:  +51.0°C                                    
Core1 Temp:  +48.0°C  

Both Core0 and Core1's temperatures are shown twice with nearly identical temperatures and it looks like that the temps are switched around.

Is there anyway I can fix this?

---

### Post by dcstar on 2010-12-24
> **frustratednerd said:**
> When I do the 'sensors' command in Terminal, this is what shows up:

apple@fruit-bowl:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +52.0°C                                    
Core0 Temp:  +49.0°C                                    
Core1 Temp:  +51.0°C                                    
Core1 Temp:  +48.0°C  

Both Core0 and Core1's temperatures are shown twice with nearly identical temperatures and it looks like that the temps are switched around.

Is there anyway I can fix this?

There is probably nothing to "fix". It is simply reporting what your hardware has.

---

### Post by TWK1a4 on 2010-12-24
Judging that they are different readings for each core, I would assume that there are two temperature sensors per CPU core.  CPU's can have multiple 'Hot spots' where they are prone to overheating (IR cameras in clean-rooms are wicked!).  Two sensors per core could be a failsafe if one died.   

Enough speculating though...
1) What Processor are you running? 
2) Are you perhaps running a dual CPU, dual-core system? Ie 2 sockets for two dual-core-processors. Ie, NOT a single processor dual core.  That would give four readings.

     -TWeaK

---

### Post by frustratednerd on 2010-12-24
@TWK1a4:

1. I am using a laptop that is running on a 2.0GHz AMD Turion 64 X2 processor.
2. No, there is just one dual-core processor.

Edit: I forgot to add in... as a result of the 'sensors' showing 2 temps for each core, conky does not show my CPU temps.

---

### Post by frustratednerd on 2010-12-25
bump

Anyone else?

---

### Post by dino99 on 2010-12-25
actual kernels give the temps (builtin features). If users maketweaks with packages like sensord, well, readings are made several times and reported as well.

---

