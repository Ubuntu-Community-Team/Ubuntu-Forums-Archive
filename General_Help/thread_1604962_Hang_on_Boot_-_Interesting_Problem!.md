---
title: "Hang on Boot - Interesting Problem!"
date: 2010-10-24
forum: General Help
---

### Post by IMSargon on 2010-10-24
I'm working on a server that dual boots Windows 7 64-bit and Ubuntu 10.10 Desktop 64-bit. There are three partitions on one hard disk: A boot partition for Ubuntu, the Ubuntu partition, and the Windows partition. 

A windows bootloader is in the MBR. It can load Windows, or it can call the Grub2 bootloader which is installed to the Ubuntu boot partition (rather than installing itself on the MBR). I am committed to this particular configuration.

Here's where it gets interesting. 
If I boot to Windows, I have no problem. If I then reboot, I can boot to Ubuntu with no problems. 
If I boot from power-off, Ubuntu hangs at this line:
[    0.710004] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0280 (mask 00ff)
If I hit the reset button on the server, I am able to boot Ubuntu the second time around. However, if I were to power-off instead, I would be unable to boot Ubuntu.
If I boot from power-off, wait until I get to the windows bootloader, then hit the reset button, I am able to boot to Ubuntu.
If I boot from power-off, go through the windows bootloader to Grub and just wait there for a few minutes before loading Ubuntu, it will not work.

Here are some helpful hints.
When Ubuntu is not able to load. I see this:
```
[    0.709158] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.709208] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.709256] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.709315] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.709374] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xffffffff]
[    0.710118] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH6 ACPI/GPIO/TCO
[    0.710180] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
[    0.710230] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0280 (mask 00ff)

```

When Ubuntu loads properly, the same section of the log looks like this:
```
[    0.676098] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.676101] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.676103] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.676105] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.676107] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xffffffff]
[    0.676164] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.676167] pci 0000:00:01.0: PME# disabled
[    0.676236] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.676239] pci 0000:00:1c.0: PME# disabled
[    0.676293] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.676296] pci 0000:00:1c.1: PME# disabled
[    0.676351] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.676354] pci 0000:00:1c.2: PME# disabled
[    0.676407] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.676410] pci 0000:00:1c.3: PME# disabled
[    0.676464] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.676467] pci 0000:00:1c.4: PME# disabled
[    0.676522] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.676525] pci 0000:00:1c.5: PME# disabled
[    0.676563] pci 0000:00:1d.0: reg 20: [io  0x7000-0x701f]
[    0.676603] pci 0000:00:1d.1: reg 20: [io  0x7080-0x709f]
[    0.676643] pci 0000:00:1d.7: reg 10: [mem 0xf96ff800-0xf96ffbff]
[    0.676685] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.676689] pci 0000:00:1d.7: PME# disabled
[    0.676784] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH6 ACPI/GPIO/TCO
[    0.676788] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
[    0.676791] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0280 (mask 00ff)
```

"Ah HA!", you say, "The part with the PME# is missing!". Well, yes, but what does that indicate and what can I do about it?

---

### Post by das_lox on 2010-12-07
I have the same problem on a different system. It is WinXp which is installed parallel and I use Grub2.

I found out that a PME# is a Power Management Event and as far as I understood this posts

[http://markmail.org/message/vk4z74afn3mzzaqj]("http://markmail.org/message/vk4z74afn3mzzaqj"),

it seems like one of our pci devices powers done during the pci scan process. This action can be avoided by disabling PME# before the scan as it is done after the reset (so it seems to me).

The fact that this behaviour is related to the Power Management would explain why the ***nolapic*** Kernel option on boot was a well working workaround for the last kernel version. (power management was not working with this option)

Unfortunately, ***noapm*** boot option, which should deactivate the power management, does not do the job.

Currently I have no idea what else to do than hoping for help.

---

### Post by das_lox on 2011-01-08
UPDATE:

my machine is running fine for 2 weeks now with ***pcie_aspm=off*** boot option.

I figured out that the problem must be related to pci express devices since they were not detected during pci probing on a fail- boot. (As you can see in the log above and with help of ***lspci*** to identify the missing devices)

for further reference see:
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt")

I hope that will help also others who have the same issue. This might also be helpful:
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

Cheers,
das_lox

---

### Post by ic3man5 on 2011-09-14
> my machine is running fine for 2 weeks now with ***pcie_aspm=off*** boot option.

Thanks! Booting into Clonezilla Live had the same issue.

---

