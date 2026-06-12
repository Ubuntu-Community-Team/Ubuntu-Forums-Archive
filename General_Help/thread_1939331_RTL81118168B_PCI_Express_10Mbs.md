---
title: "RTL8111/8168B PCI Express 10Mb/s"
date: 2012-03-11
forum: General Help
---

### Post by bibble235 on 2012-03-11
Hi,

I have googled, changed my kernel, rebuilt the driver and unplugged the PC for 15 minutes but still with not joy.

I am trying to get my card to run at 1000 gigabyte.

I have tried
1/ building the driver .28 from Realtek for 8168 (including checking the ko is the one I built with modinfo)
2/ forcing the 8169 to work
3/ switch the PC off and taking the mains out
4/ Switching to kernal 3.2

Yes I have disabled r8169 when using r8168
Yes I do have a cat 6 cable
Yes the switch does support gigabyte connections (PS/3 and two other PC connect ok)

lspci gives
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

Any help appreciated.

Thanks,
Iain

---

### Post by bibble235 on 2012-03-13
Still trying to make progress with this.

A machine that does work has 

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full
	                        100baseT/Half 100baseT/Full
	                        1000baseT/Half 1000baseT/Full
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full
	                        100baseT/Half 100baseT/Full
	                        1000baseT/Half 1000baseT/Full
	[B]Advertised pause frame use: No
[/B]	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full
	                                     100baseT/Half 100baseT/Full
	                                     1000baseT/Full
	**Link partner advertised pause frame use: No**
	Link partner advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

 modinfo r8169
filename:      
/lib/modules/2.6.32-37-generic-pae/kernel/drivers/net/r8169.ko
version:        2.3LK-NAPI
license:        GPL
description:    RealTek RTL-8169 Gigabit Ethernet driver
author:         Realtek and the Linux r8169 crew <netdev@vger.kernel.org>
srcversion:     741D80D73655DA31EBC1103
alias:          pci:v00000001d00008168sv*sd00002410bc*sc*i*
alias:          pci:v00001737d00001032sv*sd00000024bc*sc*i*
alias:          pci:v000016ECd00000116sv*sd*bc*sc*i*
alias:          pci:v00001259d0000C107sv*sd*bc*sc*i*
alias:          pci:v00001186d00004300sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008169sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008168sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008167sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008136sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008129sv*sd*bc*sc*i*
depends:        mii
vermagic:       2.6.32-37-generic-pae SMP mod_unload modversions 586TSC
parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)

modinfo mii
filename:       /lib/modules/2.6.32-37-generic-pae/kernel/drivers/net/mii.ko
license:        GPL
description:    MII hardware support library
author:         Jeff Garzik <jgarzik@pobox.com>
srcversion:     0AC37502D4358344E7C3F7B
depends:
vermagic:       2.6.32-37-generic-pae SMP mod_unload modversions 586TSC

Where as I use the r8168 and blacklist the r8169.

But this has done zero good for me. The search continues ...

I am now looking at putting Windows 7 on just to change the settings on the NIC.

I have again tried turning the PC off with everything unplug but still no green light on the card.

Sigh...

---

