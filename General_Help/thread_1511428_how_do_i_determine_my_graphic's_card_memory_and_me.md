---
title: "how do i determine my graphic's card memory and memory type?"
date: 2010-06-16
forum: General Help
---

### Post by princeofnam on 2010-06-16
i tried lscpi and lshw, but both don't really get into the specifics

---

### Post by wojox on 2010-06-16
What does **lspci** say?

---

### Post by fragos on 2010-06-16
If your card uses an Nvidia chip set run "NVIDIA X Server Settings" from System-> Administration. It will tell you which Nvidia card you have, the amount of memory allocated and numerous other technical details. Once you have the model name you can Google the card for it's specs, including memory type. "lspci |grep VGA" will also tell the model of your video card or on board chip set. On board video shares your system memory and the amount can be changed in your BIOS setup.

---

### Post by wojox on 2010-06-16
Next time you run lspci look for some numbers in front of VGA and then run:

```
lspci -v -s 00:02.0
```

Remember to change the numbers to yours.

---

### Post by princeofnam on 2010-06-17
--

VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at f8000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915
	Kernel modules: i915

--

is it possible for me to figure out whether it's GDDR3 or 2? and what distinction is there between prefetchable and non-prefetchable?

---

### Post by princeofnam on 2010-06-17
i'm also a little confused
according to

--

  description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:f8000000-f80fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)

---

and GPU-Z i have 8Mb of RAm while on the other lspci readign i got 256?

---

### Post by fragos on 2010-06-17
GM965/GL960 is an Intel chip set which is probably on the mother board of your laptop. The amount of memory used is a BIOS parameter and the type of memory is what your system is using.

---

### Post by princeofnam on 2010-06-17
wait, so let me see if understand you correctly. integrated graphics cards don't use their own memory? they use the system's memory? is that fundamentally slower?

why is it that some sources tell me it has 8mb while others tell me it has 256 mb of memory?

---

### Post by fragos on 2010-06-17
> **princeofnam said:**
> wait, so let me see if understand you correctly. integrated graphics cards don't use their own memory? they use the system's memory? is that fundamentally slower?

why is it that some sources tell me it has 8mb while others tell me it has 256 mb of memory?

Integrated cards don't have separate memory and allocated part of the systems memory in the BIOS setup.

Separate VGA card memory can be faster than your system memory.

Some sources may be wrong, the allocated video memory can only be changed by the BIOS. I'd ignore the 8mb report.

---

