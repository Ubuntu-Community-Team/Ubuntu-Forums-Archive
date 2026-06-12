---
title: "After enabling NVDIA Accelerated Graphics Driver Problems shutting Down Ubuntu"
date: 2009-07-09
forum: General Help
---

### Post by Stoneface on 2009-07-09
I have activated NVDIA Accelerated Graphics Driver version 180. After that I could not shut down properly anymore. Every time I shut down Ubuntu I see 6 command lines and prompts and it all just freezes. Then I just need to push the power button for a few seconds to get my Acer Aspire Laptop to really shutdown. Any ideas what is going on and how I can solve this?

---

### Post by Stoneface on 2009-07-17
I started this thread a week ago. No replies so far. If extra intel is needed tel me know. If this is the wrong section move my thread.

Here some more information that might help you help me:

```
uname -a
Linux me-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

```

```
lspci -v | grep nvidia
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

```
```

dmesg | grep nvidia
[   16.993247] nvidia: module license 'NVIDIA' taints kernel.
[   17.249061] nvidia 0000:02:00.0: PCI INT A -> Link[LK2E] -> GSI 19 (level, low) -> IRQ 19
[   17.249069] nvidia 0000:02:00.0: setting latency timer to 64
```

```
lspci -v

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)
	Subsystem: Acer Incorporated [ALI] Device 0121
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 4000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

```

---

### Post by akshay.sulakhe on 2009-07-17
How did u installed the driver..by downloading it from Nvidia site or from Hardware drivers...if from Hardware drivers..then this shud not happen...now remove the driver...install a different version from hardware drivers..if u have already done from hardware drivers...

---

### Post by Stoneface on 2009-07-17
I installed it from  System > Administration > Hardware Drivers. I chose the recommended version 180. Do you suggest I use NVIDIA AGD version 173? Those are the two only propriety ones showing in the hardware drivers list. 
Question two. Is NVIDIA AGD 180 causing the shut down issues (9 command prompts blinking)? The errors I posted don't make sense to me so I don't know..

---

