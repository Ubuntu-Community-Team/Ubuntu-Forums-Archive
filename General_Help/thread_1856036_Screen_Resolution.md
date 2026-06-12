---
title: "Screen Resolution"
date: 2011-10-07
forum: General Help
---

### Post by galacticaboy on 2011-10-07
I cannot change my screen resolution, right now it is 1024*768 I know I can go more but Ubuntu does not give me the options, in Windows XP I could go way more. How can I do this?

---

### Post by TeoBigusGeekus on 2011-10-07
Have you checked the Additional Drivers (or Hardware Drivers, can't remember) for any available proprietary drivers for your graphics card?

---

### Post by galacticaboy on 2011-10-07
I have and there are none.

---

### Post by TeoBigusGeekus on 2011-10-07
What's your graphics card?
```
lshw -C display
```

---

### Post by galacticaboy on 2011-10-07
After entering that I get this...

david@David-Ubuntu:~$ sudo lshw -C display
[sudo] password for david: 
  *-display               
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f0000000-f7ffffff memory:ffa80000-ffafffff ioport:ec00(size=8)
david@David-Ubuntu:~$

---

### Post by TeoBigusGeekus on 2011-10-08
Some googling revealed that the Intel 82865G chip has been problematic in the past and it is obviously now.
From what I could make out, there are no drivers for it; ubuntu should recognise and take care of it automatically.
Almost all the threads/pages I found described an update as their solution.
Unless you want to wait in case an update or an upgrade to Oneiric (brrr...) fixes this, you could buy a super cheapo (10~20 dollars) old nvidia card.

---

