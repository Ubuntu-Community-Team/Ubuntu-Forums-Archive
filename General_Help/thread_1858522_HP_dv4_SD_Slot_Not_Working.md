---
title: "HP dv4 SD Slot Not Working"
date: 2011-10-12
forum: General Help
---

### Post by Simeo on 2011-10-12
I've done the google search and haven't found a solution. 

I have an internal SD reader on my laptop and I'm trying to figure out how to get it to work. Help?

lspci output:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by Mark Phelps on 2011-10-13
I've found that, of all the devices contained in laptops, the two that tend NOT to work with Linux distros are the WiFi on/off switch and the SD card reader.

I don't see the card reader listed.  On mine, it says something like "OS2Micro MemoryCardBus Controller".

In Linux, the drivers are bound with the OS, so it's not a simple matter of sticking in a driver CD and installing drivers.

What I had to resort to on another laptop where the card reader wasn't seen was an external, USB-cabled card reader.  Yeah, it's clumsy to carry around, but it works.

---

### Post by stoneguy on 2011-10-13
Yes. I looked for a way to boot an Acer Aspire notebook from the SD card just like with my ASUS eeePC netbook, and was surprised to find I couldn't. No visibility of the card slot from the Boot Order BIOS setting either. I do full installs (with boot sector) to 16 GB SDHCs to test trial versions. Better realism then using a VM, and doesn't screw around with the disk.

There's another solution to adapting an SDHC to a USB port. It's a gizmo that's a bit longer than the length of a standard USB key, so it's easily pocketable. Unfortunately, it's nearly twice as wide, which means it'll block 2 ports when they're adjacent. There aren't any wires - the card slides in one side, and the other plugs into the slot. Mine caps closed, and they're cheap enough just leave an SDHC in one. That way you can just carry it around, and when a Win-friend yells for help, offer it in exchange for an hour on their machine to try their hardware and file launchpad reports ;)

Don't try plugging into a USB hub though. The electronics of the hub seem to get in the way of booting, although most other devices are just fine. That's how I do lappy and netbook testing off the same card.

---

