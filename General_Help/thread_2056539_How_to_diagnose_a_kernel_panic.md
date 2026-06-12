---
title: "How to diagnose a kernel panic?"
date: 2012-09-11
forum: General Help
---

### Post by dpapathanasiou on 2012-09-11
I have a [Hauppauge WinTV-HVR-1250 tv capture card]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250") which I've used for over a year in an AMD64 machine running both 11.04 then 11.10 without any problems.

Recently, I moved that card to another AMD64 machine, but suddenly I started getting kernel panics when the capture was in use, recording tv.

Unfortunately, the panics don't leave any traces in /var/log/kern.log or any other log I could find, but I did capture the screen output with a camera (both shots are of the same screen, just at slightly different angles):

[http://i.imgur.com/cpghah.jpg]("http://i.imgur.com/cpghah.jpg")
[http://i.imgur.com/Ho0gth.jpg]("http://i.imgur.com/Ho0gth.jpg")

People have suggested that the problem is an interrupt conflict with the capture card, but I'm not sure how to go about confirming that, and resolving it.

The Hauppauge card is a PCI-e type, and on this new machine, there is only one PCI-e slot.

The bios menu seems to assume that the PCI-e slot will be used for a video card, because in the only option where it's mentioned, the PCI-e slot can be switched on/off as the default video output.

Since the motherboard has a built-in video card, I set that as the default, so that the bios doesn't try to use the PCI-e slot for video output.

Unfortunately, that seems unrelated/nothing to do with the problem.

I ran the lshw command, and below is an excerpt of the output.

If anyone can recommend what to change or upgrade, please let me know.

```
id:	
core
description:	Motherboard
product:	09AC
vendor:	MSI
physical id:	
0
```

```
id:	
firmware
description:	BIOS
vendor:	Phoenix Technologies, LTD
physical id:	
0
version:	1.18
date:	08/01/2006
size:	128KiB
capacity:	448KiB
capabilities:	pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
```

```
id:	
cpu:0
description:	CPU
product:	AMD Athlon(tm) 64 Processor 3000+
vendor:	Hynix Semiconductor (Hyundai Electronics)
physical id:	
4
bus info:	
cpu@0
version:	AMD Athlon(tm) 64 Processor 3000+
slot:	Socket 939
size:	1800MHz
capacity:	3GHz
width:	64 bits
clock:	199MHz
capabilities:	fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up rep_good nopl pni lahf_lm cpufreq
```

---

