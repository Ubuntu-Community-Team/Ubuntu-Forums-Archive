---
title: "Newbie, Need some help"
date: 2012-10-04
forum: General Help
---

### Post by aremat1989 on 2012-10-04
Well, I installed ubuntu through wubi, and I've already migrated it to my other HDD.... However I'm still having a problem of getting a blank screen when selecting normal mood.  It literally stays like this, forcing me to hard reboot, which I know is bad.   The only way my screen doesn't go blank is if I boot via recovery mode.   If it has anything to do with graphics, ubuntu says that mine is VESA: Intel(r)Cantiga Graphics.

---

### Post by madinc on 2012-10-04
i think is a graphics problem i had a problem like that one time after an update for me the solution was this:

```
sudo apt-get install --reinstall nvidia-current
```but  i use nvidia and i have no idea about intel, also your problem could be different .

---

### Post by spaceshipguy on 2012-10-04
> **aremat1989 said:**
>   It literally stays like this, forcing me to hard reboot, which I know is bad.
Ubuntu seems very stable after hard reboots - I tinker and inflict a lot of them on my system - while they seem to quite quickly kill a Windows install. 

Just my subjective experience, nothing scientific, but I don't hesitate to reach for the power button when I need to.

---

### Post by apochry on 2012-10-04
It seems to be a graphics problem. If you provide the model of your adapter people could help better.
You can type ```
lspci -v
``` and look for the part, which lists your graphics card.
It should look something like that:
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 04c5
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at e0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```Do you have double graphics, integrated and discrete one?

---

### Post by aremat1989 on 2012-10-04
> **apochry said:**
> It seems to be a graphics problem. If you provide the model of your adapter people could help better.

Like this?

```
tamera@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4110 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, fast devsel, latency 0
    Memory at 93400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 40e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 40c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at 96704c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 96700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 95700000-966fffff
    Prefetchable memory behind bridge: 0000000090400000-00000000913fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 94600000-956fffff
    Prefetchable memory behind bridge: 0000000091400000-00000000923fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 93500000-945fffff
    Prefetchable memory behind bridge: 0000000092400000-00000000933fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 40a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 4080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 4060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 4040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at 96704800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at 4108 [size=8]
    I/O ports at 411c [size=4]
    I/O ports at 4100 [size=8]
    I/O ports at 4118 [size=4]
    I/O ports at 4020 [size=32]
    Memory at 96704000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 048a
    Flags: medium devsel, IRQ 11
    Memory at 96705000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4000 [size=32]
    Kernel modules: i2c-i801

04:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Lite-On Communications Inc Device 6603
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 94600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 0139
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at 93500000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

tamera@ubuntu:~$ 
```


> Do you have double graphics, integrated and discrete one?

I have no clue what that means o.o

---

### Post by Bashing-om on 2012-10-04
Looking at your "lspci" output, I do not see where a driver is loaded. The "Kernel driver in use" line being blank.

This guide to load the i915 driver upon booting:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

The workaround should work for any version.

I had another method in mind, ran across this one, like better...
Try this and post back with the results.
[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by aremat1989 on 2012-10-04
> **Bashing-om said:**
> Looking at your "lspci" output, I do not see where a driver is loaded. The "Kernel driver in use" line being blank.

This guide to load the i915 driver upon booting:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

The workaround should work for any version.

I had another method in mind, ran across this one, like better...
Try this and post back with the results.[INDENT]just try'n to help <==BDQ

[/INDENT]

Um, I'm assuming I run those commands in the terminal, right?

---

