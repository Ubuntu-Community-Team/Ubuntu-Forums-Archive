---
title: "Trouble with LED  indicator  light on Laptop Exterior"
date: 2012-02-06
forum: General Help
---

### Post by V13 Noob on 2012-02-06
Hello Ubuntu Community,

I'm new to the Ubuntu forum site here, well actually I created an account several years back but wasn't active at all posting and just read the posts, which helped me out tremendously. I've been dual booting Ubuntu/Windows 7 for about two years now on an Acre Aspire 721 but have now removed Windows and had Ubuntu running alone for about two months. It's been an easy transition and all of the hardware has been working great except for one exterior LED. It is a light that indicates whether the wireless is on or not. The wireless adapter is working, I have internet running and the wireless indicator is always a high percentage. When I would dual boot into Windows the LED would start functioning again. I've looked for settings that could adjust it but haven't been able to find any.  I don't know if this would help but here is the lspci -v below. I know it really isn't all that important however its a bit annoying to see it off when I know the wireless is working. Any suggestions would be greatly appreciated and many thanks.

~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602 (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: d0000000-d01fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: d0200000-d02fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Memory behind bridge: d0300000-d03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 42
    I/O ports at 8440 [size=8]
    I/O ports at 8430 [size=4]
    I/O ports at 8420 [size=8]
    I/O ports at 8410 [size=4]
    I/O ports at 8400 [size=16]
    Memory at d0607c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d0607000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d0607400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8450 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=64

00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d0607800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 9000 [size=256]
    Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
    Memory at d0000000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Acer Incorporated [ALI] Device 0429
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d0110000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

03:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
    Subsystem: Acer Incorporated [ALI] Device 040d
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at d0200000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at a000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

06:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
    Subsystem: Foxconn International, Inc. Device e021
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d0300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: brcmsmac
    Kernel modules: wl, brcmsmac

---

### Post by Ubuntist on 2012-07-27
I don't have a solution, but I have a similar or identical problem and I'd like to commiserate.  It used to be that the blue wireless indicator on my laptop was illuminated whenever the wireless was switched on, and that's still how it works when I boot to Windows.

Since about 1 January 2012, however, the wireless indicator seems to indicate the amount of wireless activity rather than the state (i.e., on or off) of the wireless.  Thus, when I boot to Ubuntu (currently using 12.04 but previously noticed the same behaviour under 11.04), the indicator flashes intermittently.  If I do a big download, it's lit continuously.

I think the behaviour changed when I installed routine updates around 1 January of this year.  For a while, I though my wireless had stopped working.

I much prefer the the old behaviour of the wireless indicator:  continuously on whenever the wireless is switched on.  That way I can be sure when I'm on a plane, for example, that it's off.

If anybody has any ideas how to recover the old behaviour of the wireless indicator, I'm all ears.

---

### Post by V13 Noob on 2012-08-13
> **Ubuntist said:**
> I don't have a solution, but I have a similar or identical problem and I'd like to commiserate.  It used to be that the blue wireless indicator on my laptop was illuminated whenever the wireless was switched on, and that's still how it works when I boot to Windows.

Since about 1 January 2012, however, the wireless indicator seems to indicate the amount of wireless activity rather than the state (i.e., on or off) of the wireless.  Thus, when I boot to Ubuntu (currently using 12.04 but previously noticed the same behaviour under 11.04), the indicator flashes intermittently.  If I do a big download, it's lit continuously.

I think the behaviour changed when I installed routine updates around 1 January of this year.  For a while, I though my wireless had stopped working.

I much prefer the the old behaviour of the wireless indicator:  continuously on whenever the wireless is switched on.  That way I can be sure when I'm on a plane, for example, that it's off.

If anybody has any ideas how to recover the old behaviour of the wireless indicator, I'm all ears.

Hey, I just solved my LED indicator problem a few days ago by just updating and activating the wireless broadcom drivers. I had neglected to update them because my wireless was working fine and I've had so much trouble with the broadcom card before that I didn't even wasn't to mess with it. Luckily updating the drivers worked flawlessly.

Try updating your card's drivers and it might solve your issue too. Just in case, the settings can be found in System Settings > Hardware > Additional Drivers.

---

### Post by Ubuntist on 2012-11-05
Thanks very much, V13 Noob -- your fix solves a lot of my problem.  In some ways, it's actually better than before:  the wireless indicator light is basically on now but blinks when data is flowing.  So I get the best of both worlds: an indication that it's on *and* indication of data flow.

There is still one problem, though.  If I turn the wireless off, the light goes out, as it should.  The trouble is that when I switch the wireless back on, the light stays out until I have a wireless connection.  Thus, I could be sitting on a plane with no wifi connection but having my laptop's wireless on without me knowing it.

---

