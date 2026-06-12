---
title: "Bizarre network problems"
date: 2006-04-30
forum: General Help
---

### Post by crayzeepete on 2006-04-30
Recently made another attempt at entering the linux world, and so far so good... but I'm having problems now with networking on my fujitsu-siemens laptop.
It's incredibly bizarre, because I'm getting incredibly inconsistant problems.

I tried to run 'Automatix' on my system, to install a few things, but most of it failed. On further investigation, i found that the wget command was getting nowhere.
I fails on any host outside of the LAN, with 'No route to host'.
ping also fails, to any host outside of my LAN, with a timeout error.
Sound Juicer also has problems connecting to the internet, and my attempts at updating to the dapper beta also seem to be network related (although, i haven't properly investigated it, so it could easily be unrelated).

The strange thing, is that with a lot of other programs, it's all fine. Firefox and Thunderbird run fine. Synaptics/apt-get run fine. The update manager in general also runs fine.

Network-wise, it's DHCP, and running on a university LAN (not sure if that makes a difference or not...?)

(Network's running on standard ethernet port eth0)

dmesg
---------------------------------

[4294669.776000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294669.776000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294669.776000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294669.776000] TCP: Hash tables configured (established 8192 bind 8192)
[4294669.776000] NET: Registered protocol family 8
[4294669.776000] NET: Registered protocol family 20
[4294669.776000] ACPI wakeup devices:
[4294669.776000]  LID LANC MODM
[4294669.776000] ACPI: (supports S0 S3 S4 S5)
[4294676.070000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0a:e4:21:ca:e
[4294693.131000] NET: Registered protocol family 10
[4294693.132000] Disabled Privacy Extensions on device c02eb280(lo)
[4294693.132000] IPv6 over IPv4 tunneling driver
[4294693.215000] wbsd: Winbond W83L51xD SD/MMC card interface driver, 1.2
[4294693.215000] wbsd: Copyright(c) Pierre Ossman
[4294693.227000] mmc0: W83L51xD id 7112 at 0x248 irq 10 dma 2
[4294693.717000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[4294693.720000] input: SynPS/2 Synaptics TouchPad on isa0060/serio4
[4294694.097000] ts: Compaq touchscreen protocol output
[4294702.618000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.2
[4294702.618000] ipw2100: Copyright(c) 2003-2005 Intel Corporation
[4294702.622000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[4294702.622000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[4294702.622000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[4294703.429000] eth1: Radio is disabled by RF switch.
[4294703.627000] Linux Kernel Card Services
[4294703.627000]   options:  [pci] [cardbus] [pm]
[4294703.632000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[4294703.632000] Yenta: CardBus bridge found at 0000:02:09.0 [1734:1033]
[4294703.632000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294703.632000] Yenta: Routing CardBus interrupts to PCI
[4294703.632000] Yenta TI: socket 0000:02:09.0, mfunc 0x01001002, devctl 0x64
[4294703.730000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[03e40a0017042048][4294703.853000] Yenta: ISA IRQ mask 0x0078, PCI irq 10
[4294703.853000] Socket status: 30000007
[4294705.182000] Real Time Clock Driver v1.12
[4294706.104000] NET: Registered protocol family 17
[4294707.087000] b44: eth0: Link is down.
[4294711.087000] b44: eth0: Link is up at 10 Mbps, half duplex.
[4294711.087000] b44: eth0: Flow control is off for TX and off for RX.
[4294716.530000] eth0: no IPv6 routers present

---

### Post by dmizer on 2006-04-30
try disabling ipv6 per this wiki: [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29)

also, it sounds like your university may have a firewall in place to prevent downloading music and such.  you may be able to circumvent it by trying a proxy.

---

### Post by crayzeepete on 2006-04-30
disabled ipv6, problem still seems to be there...

i'm not sure about the firewall... there's lots of filesharing going on and, anyway, why on earth would they block the port for PING? and wget? wget uses port 80... the same port as firefox, right? (maybe my understanding of ports is a little off).
it doesn't add up to me.
also - i know there's a lot of active filesharing on this network.
currently, the network proxy option (System > Prefs > Proxy) is set up to go through a proxy config file... the same as firefox.

i guess the best thing to do would be to try it on an alternative network...

---

### Post by crayzeepete on 2006-05-01
For those of you still interested, it really looks like that anything outside of the terminal can use my network connection, and anything inside it can't.
Example, Synaptic can use the connection, sudo apt-get can't.
WHY?!?!?

---

### Post by crayzeepete on 2006-05-07
**##UPDATE##**

After looking around the net for a few more articles, I ran the following programs  to try to diagnose my problem...

```
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x000000ff (255)
        Link detected: yes
peter@rpc-pjw26:~$ sudo mii-tool eth0
eth0: no autonegotiation, 10baseT-HD, link ok
```

There's differences between the outputs of the two monitors... is this significant?

---

