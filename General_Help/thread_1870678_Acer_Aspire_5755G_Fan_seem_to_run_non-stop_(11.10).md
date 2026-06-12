---
title: "Acer Aspire 5755G Fan seem to run non-stop (11.10)"
date: 2011-10-27
forum: General Help
---

### Post by Mobidoy on 2011-10-27
I have a new Acer Aspire 5755Gthat i have manage to have Optimus to work (IronHide) and the brightness control too. 

The only issue I still seem to have to save has much energy has possible would be to be able to control the fan. It looks like it is running constantly. Anyone has a fix for it ?

---

### Post by Aragant on 2012-03-21
So, you found one or not?

---

### Post by Markone1 on 2012-03-25
How did you set the brightness? Are you use x64 of ubuntu? I haven't got problem with the cpu fan i use bumblebee (the latest) and the optimus and the cpu fan is working fine.

---

### Post by keskival on 2012-09-21
It seems with Ace Aspire 5755G the temperature sensors work fine, but fan control doesn't. Booting the kernel with the parameter acpi=off leaves the fans to be controlled by the BIOS, meaning that they actually work. However, this also disables all kinds of things from hyperthreading to HDMI control. Booting with acpi=ht does not help, because that also disables the fan control by BIOS.

The newest, Linux Mint Debian Edition tells me in dmesg:

[135006.801954] acerhdf: Acer Aspire One Fan driver, v.0.5.24
[135006.802553] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 5755G/V1.20, please report, aborting!

I have update the BIOS firmware and everything to newest versions, and I can't find any way to manually or automatically control the fan, which is set at a constant (not full) speed. For me, the speed is too low, and the computer overheats.

If anyone has any solutions to this, please answer. This is a common issue, and no one has found a workable solution.

---

