---
title: "Extended Desjtop with dual monitors"
date: 2010-04-18
forum: General Help
---

### Post by conradin on 2010-04-18
Hi all, I have a thinkpad T43 with a dock and a 19" Dell monitor attached. Im trying to get an extended desktop. 
Using the default display program (using ubuntu 9.10) I can mirror the screens just fine. But, when I click the radio button to enable the extended desktop, the monitors (both of them) go black. Some times it doesn't come out of this. (yes, I'm waiting more than 25 seconds) 

What can I do to make the extended desktop work?

here is my display info from the command lshw:
*-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:90080000-900fffff ioport:1800(size=8) memory:b0000000-bfffffff(prefetchable) memory:90000000-9003ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:40000000-4007ffff

---

### Post by conradin on 2010-04-18
So then, I looked on intel's website for Mobile 915GM/GMS/910GML Express Graphics Controller and found that they had an rpm. I downloaded that, and converted it to a .deb file with alien, but it also failed to give me any useful new options. I want to note, that in my WinXp partition, the extended desktop works fine.

---

