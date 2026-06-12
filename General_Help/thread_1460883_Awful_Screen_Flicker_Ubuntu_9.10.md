---
title: "Awful Screen Flicker Ubuntu 9.10"
date: 2010-04-23
forum: General Help
---

### Post by opethfan89 on 2010-04-23
Hi all,

Until now, I never used Ubuntu 9.10 on my Desktop (HP Pavillion 753n) because of a HORRIBLE screen flicker problem I have with my integrated Intel chipset

Relevant lshw output as follows:
```
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff(prefetchable)
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0000000-e7ffffff(prefetchable) memory:ec100000-ec17ffff

```I tried reading [this sticky]("http://ubuntuforums.org/showthread.php?t=1130582") but I'm afraid I may make some irreversable changes to my install. The instructions are just a bit over my current knowledge level at the moment.

I have tried using the 'auto-tune' setting on my monitor to no avail, and setting the refresh rate to 75hZ does not help. I don't know if it is relevant or not, but in my monitor's on-screen menu, it is showing the Horizontal (rate?) to be 79 KHZ and Vertical to be 75HZ...is this perhaps the cause of my problem, two different rates on my monitor?

To be more specific about the flicker, it is apparent in any text I am reading, as well as certain dark features on light colored backgrounds. 

Thanks for any help, and I'm going to go lay down and try to alleviate this headache I have from staring at this monitor *pops Advil pills*

Thanks,
Opethfan89

---

### Post by opethfan89 on 2010-04-24
bump?

---

### Post by opethfan89 on 2010-04-27
I think this ended up just being a monitor issue, because I switched monitors and now there is no screen flicker, and since there were no replies I'm requesting this thread be closed. 
 
Thanks, 
Opethfan89

---

