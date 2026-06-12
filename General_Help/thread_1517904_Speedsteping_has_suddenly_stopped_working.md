---
title: "Speedsteping has suddenly stopped working"
date: 2010-06-25
forum: General Help
---

### Post by dasy2k1 on 2010-06-25
My cpu has multiple supported levels of speed stepping,
1GHz 1.8GHz  2GHz 2.2GHz and 2.4GHz

with the frequecny monitoring applet set to ondemand previously the cpu has scalled up and down as required..

but now for some reason this is nolonger happening, all the levels are still shown on the applet but the cpu remains at full speed all the time (casuing the fan to remain at high speed and high noise)

/proc/acpi/processor/CPU0/thottling 
is just showing 
<not supported>

and the speedstepping profile that was previously vissible in proc dosent appear anymore, 

booting into the previous kernel dosent seem to make any differace either (along with giving me low graphics mode warning, but i think thats to do with the graphics card driver kernel module)

this is with ubuntu 10.04 X86_64 kernel 
2.6.32-22-generic

---

