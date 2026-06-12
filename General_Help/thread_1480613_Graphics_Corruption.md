---
title: "Graphics Corruption"
date: 2010-05-11
forum: General Help
---

### Post by lvleph on 2010-05-11
I have read a few bug reports that seem related to this, but I wasn't completely sure based on the description. I also, didn't completely understand the work around, so I figured I would post here to get help.

I am having a weird graphics corruption issue. The desktop becomes scrambled. Ctl+alt+backspace will fix the issue. This seems to be a kernel issue, since 2.31.20 doesn't have the issue, but all the current Lucid kernels do and the latest 2.34 has the same issue. I have attached a screen shot so that you can see the issue. Currently, I am running 2.31.20 so that I don't have to worry about this, but I would like to use a more up to date kernel.

**lspci -v**
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
	Subsystem: Acer Incorporated [ALI] Device 028c
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 9000 [size=256]
	Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 2
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel modules: radeon
```

---

### Post by GSF1200S on 2010-05-11
I have not had this issue at all and ive been running Lucid on 2.6.32 since beta 2. I had an issue where killing gdm would shut off my monitor, but the latest nvidia driver from the X ppa fixed that. This is the only difference between our setups- im on nvidia and you are on an ATI card. I remember seeing a few other threads dealing with this problem, and if I remember correctly, they were ATI users as well. What driver are you using? Could you perhaps try a different driver (the open source one for instance) or try using the X ppa located at:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid)
I see an update for nvidia drivers (which I am using) and an update for intel, but not for intel. Perhaps the xorg-xserver update will help..

Sorry I cant suggest anymore- I dont have any ATI cards and I havent had this issue myself..

---

### Post by lvleph on 2010-05-11
I am using the open source driver, since my card is in Legacy.

EDIT: Even tried placing radeon.modeset=1 in grub and it didn't help

EDIT2: Switching to radeon.modeset=0 seems to be helping. I am not having any issues yet.

EDIT: I think radeon.modeset=0 has fixed the issue.

---

### Post by efflandt on 2010-05-12
**nomodeset** should work as well as **radeon.modeset=0**.

It is just that the radeon.modeset=0 is specific to ATI (like if you had an external drive that boots on multiple computers), and nomodeset deactivates the kernel mode driver (KMS) for any card.  Then instead of using KMS by default, it would use the user space module (like 9.10 did).

---

### Post by lvleph on 2010-05-12
> **efflandt said:**
> **nomodeset** should work as well as **radeon.modeset=0**.

It is just that the radeon.modeset=0 is specific to ATI (like if you had an external drive that boots on multiple computers), and nomodeset deactivates the kernel mode driver (KMS) for any card.  Then instead of using KMS by default, it would use the user space module (like 9.10 did).
Thanks for the explanation. I am still up and running on the newest kernel, so everything seems to be working.

---

