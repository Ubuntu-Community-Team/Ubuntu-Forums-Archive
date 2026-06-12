---
title: "Random complete freezes"
date: 2012-09-07
forum: General Help
---

### Post by supersatellite on 2012-09-07
I just bought a new Toshiba Satellite R945-P440, and installed Xubuntu 12.04.1 with Compiz. Every so often (maybe once every few hours of use), the entire system will freeze up completely. The cursor disappears, the screen becomes static, and if there was sound playing, the last second or so of the sound repeats indefinitely. Nothing on the keyboard works, including ctrl-F1 to switch to a tty, or REISUB; the only thing I can do is to hold the power button.

Memtest returned no errors. I've checked several log files and didn't see anything hopeful (although I'll post them here if necessary). The thing is, it is totally random. The only pattern I've been able to detect is that several times it's happened when the cursor moved over the XFCE panel. Based on that and the vanishing cursor I suspect it's a graphics issue, but I don't know how to tell for sure. Anyone have insights or experienced something similar?

---

### Post by Epodx64 on 2012-09-07
I had an identical problem with Kubuntu 12.04 x86 I never figured out  exactly what it was but I suspect it had something to do with the integrated Nvidia card. After 10.04 I had nothing but problems with Nvidia hardware (I had a Jetway MCP 61 mobo integrated Nvidia GeForce 6150se Nforce 430) It finally got to the point where I replaced my entire setup in favor of an Intel processor (core2duo) over AMD(athlon x2 6000+) and Intel GMA over Nvidia I've had zero problems since I switched.

---

### Post by 2F4U on 2012-09-08
It could probably be useful if you post your hardware specifications as well as graphics card and graphics driver. Am I right in assuming that overheating is not a problem?
Did you look into the log file .xsession-errors in your home folder?

---

### Post by Epodx64 on 2012-09-08
> **2F4U said:**
> It could probably be useful if you post your hardware specifications as well as graphics card and graphics driver. Am I right in assuming that overheating is not a problem?
Did you look into the log file .xsession-errors in your home folder?

over heating could be the issue when I was having that identical problem the Amd Athlon x2 6000+ was running idle at 56 c at stock speeds.

---

### Post by supersatellite on 2012-09-08
I don't think it's overheating, since it's happened within 15 seconds of booting (read: before I've had time to open anything) and I keep the office very cool.

The graphics card is a Mobile Intel HD. I hope these are the right commands for drivers...

$ lshw -class display
```
  *-display               
       description: VGA compatible controller
       product: Ivy Bridge Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:2000(size=64)
```

$ lspci -v -s 02
```
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device 0002
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at e0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 2000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
```

I attached .xsession-errors. Everything looked ok but maybe I missed something. The last freeze was ~16 hours ago... I don't know if it goes back that far or if/when it gets overwritten.

---

### Post by Chris Ahlstrom on 2012-09-09
I had the same issue when I installed Debian Wheezy (updated immediately to "unstable") on that Toshiba Satellite R945-P440 laptop.  I run the Fluxbox window manager.  I wasn't able to determine what was happening, though I have seen hints related to wpa-supplicant (wireless connection).  So I took a shot in the dark that worked.

I downloaded the source code for Linux 3.5.2 from kernel.org and used Debian's "kernel-package" application to configure, build, and install it.  No problems at all now.

Not sure what the "Ubuntu Way" is for installing updated kernels, but you could always do it the good old-fashioned way.

Chris

---

### Post by SeriousBeans on 2012-09-10
Install the new kernel, 3.5 :) worked for me.

---

### Post by supersatellite on 2012-09-10
Alright, I've upgraded to 3.5. I'll report back if it freezes again, or if after a few days it looks ok.

---

### Post by supersatellite on 2012-09-20
Well, it's been a week and no more freezes :D

So I'm marking this as solved. Thanks everyone for your help!

---

