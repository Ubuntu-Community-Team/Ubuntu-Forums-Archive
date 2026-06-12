---
title: "eth0 gone after resume from standby"
date: 2011-03-25
forum: General Help
---

### Post by mswade on 2011-03-25
Hello,

On resume from suspend my wireless interface is gone. A restart does not restore it, I need to cold reboot.

eth0 is the logical name of my Intel PRO/Wireless 2200BG Network Connection network controller.
From what I've been reading it seems the device is powered down on suspend and on resume it is not powered-up and the firmware cannot be reloaded.

After resume, dmesg:

[   34.134061] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   34.134067] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   34.905219] intel8x0_measure_ac97_clock: measured 55423 usecs
[   34.905224] intel8x0: clocking to 48000
[   34.906405] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   34.906922] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   36.985782] ipw2200: Parity error.  Retrying init.
[   37.032820] ipw2200: Parity error.  Retrying init.
[   37.079840] ipw2200: Parity error.  Retrying init.
[   37.126840] ipw2200: TODO: Handle parity error -- schedule restart?
[   37.126868] ipw2200: Unable to load firmware: -5
[   37.128438] ipw2200: failed to register network device
[   37.128524] ACPI: PCI interrupt for device 0000:02:03.0 disabled
[   37.128550] ipw2200: probe of 0000:02:03.0 failed with error -5

and lshw -C network:

  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=24 mingnt=3

after shutdown then start, demsg:

[   35.231670] ieee80211_crypt: registered algorithm 'NULL'
[   35.262708] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   35.262713] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   35.298489] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   35.298494] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   35.323026] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[   35.323031] Socket status: 30000006
[   35.323035] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   35.323042] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   35.323046] cs: IO port probe 0xd000-0xefff: clean.
[   35.323633] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   35.334926] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011e]
[   35.346727] udev: renamed network interface eth0 to eth1
[   35.463035] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[   35.463040] Socket status: 30000410
[   35.463043] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   35.463051] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   35.463055] cs: IO port probe 0xd000-0xefff: clean.
[   35.463642] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   35.482485] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   35.530419] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   36.122370] pccard: PCMCIA card inserted into slot 1
[   37.879013] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   38.386125] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
[   38.399279] pcmcia: registering new device pcmcia1.0

and lshw -C network:

  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 05
       serial: 00:0e:35:16:5d:10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.0.8 latency=32 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11b


My install is 8.04  2.6.24-28-generic

I believe if I can power-up that device then I can:

modprobe -r ipw2200
modprobe ipw2200
/etc/init.d/networking restart

And I would have my wireless back but I don't know how to go about it.  Anyone with an idea how to accomplish that?

I can't update to a newer distribution, after 9.04 the ipw2200 driver compiled in the kernel won't connect to wep protected access points, same thing in openSUSE 11.4, and right now I need to do that.

-- Mark Wade

---

### Post by mswade on 2011-03-28
[quote]

On resume from suspend my wireless interface is gone. A restart does not restore it, I need to cold reboot.

eth0 is the logical name of my Intel PRO/Wireless 2200BG Network Connection network controller.
From what I've been reading it seems the device is powered down on  suspend and on resume it is not powered-up and the firmware cannot be  reloaded.

[\quote]

Using the hardware suspend, on this machine Fn-Esc,it seems resume from suspend works okay so it would seem that the software suspend implementation is at fault.

As long as I can sleep this thing I can live with that. A portable that can't suspend is kind of useless.

Now I need to find a fix for the well known ipw2200/wep bug no one acknowledges.

-- Mark

---

