---
title: "WiFi is not working on a fresh install of 11.04 (32bit)"
date: 2011-08-23
forum: General Help
---

### Post by WarrenSH on 2011-08-23
I just got done with a fresh install of 11.04

So far I like the new update and face lift. The only thing I do not like is that I can not use my laptops WiFi :confused: I have a Compaq Presario V5101US

Below info is from doing lspci command in the terminal...

```
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```Please help me I need the WiFi for school & work :wink: 

Thanks <3

---

### Post by kiddykoff on 2011-08-23
Is this an older wireless card (laptop?)

you might have to use ndiswrapper.

---

### Post by kiddykoff on 2011-08-23
you also might want to look into this thread [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by IWantFroyo on 2011-08-23
Install b43-fwcutter and the b43-firmware-installer packages from synaptic.

I don't remember the exact package names, so search 'b43' in Synaptic and read the descriptions.

---

### Post by WarrenSH on 2011-08-23
> **kiddykoff said:**
> Is this an older wireless card (laptop?)

you might have to use ndiswrapper.

I got the laptop back in 2004 or 2005 so I guess yes being 6 years old is older :lolflag:

> **kiddykoff said:**
> you also might want to look into this thread [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Thanks for the link. I looked into it and I got super lost on how to do this. WOW I n00b flashback for me. If there any other ways of getting around my issue? The wireless card looks to be installed on my laptop thanks to doing this. **lspci | grep Broadcom\ Corporation** This is the outcome ```
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by WarrenSH on 2011-08-23
Thank you I got those installed now. So should I reboot and unplug my Ethernet cable to see if the wifi works or do I need to run a command in the terminal? 

> **IWantFroyo said:**
> Install b43-fwcutter and the b43-firmware-installer packages from synaptic.

I don't remember the exact package names, so search 'b43' in Synaptic and read the descriptions.

---

### Post by IWantFroyo on 2011-08-23
Did a bit more research:

Your card needs special firmware from Synaptic. I'm not at a natty computer, but you need to search 'b43' in synaptic, and read through the descriptions of the ~5 packages there. One will have support for the bcm4318 (I think its the only package that supports just one card).

No use messing with ndiswrapper. That thread kiddykoff posted is out of date.

---

### Post by WarrenSH on 2011-08-23
Nice thank you i'll do some soul searching in Synaptic. I will post back what I fin in a while. :D

> **IWantFroyo said:**
> Did a bit more research:

Your card needs special firmware from Synaptic. I'm not at a natty computer, but you need to search 'b43' in synaptic, and read through the descriptions of the ~5 packages there. One will have support for the bcm4318 (I think its the only package that supports just one card).

No use messing with ndiswrapper. That thread kiddykoff posted is out of date.

---

### Post by WarrenSH on 2011-08-23
So it looks like I have that one installed. But how do I get it to work? 

.
.
.
.
.

[IMG]http://i52.tinypic.com/2m3k1v9.png[/IMG]

---

### Post by IWantFroyo on 2011-08-23
It should go into action automatically. Unplug your ethernet, and if it still doesn't come on, reboot.

---

### Post by WarrenSH on 2011-08-24
Still not work :( 

> **IWantFroyo said:**
> It should go into action automatically. Unplug your ethernet, and if it still doesn't come on, reboot.

---

### Post by kiddykoff on 2011-08-24
I was asking about the age of the computer, because i remember a while back that broadcom agreed to something that would have made all of their further cards compatible with linux natively.

anyways, what do you get when you run, ifconfig

---

### Post by IWantFroyo on 2011-08-24
> **kiddykoff said:**
> I was asking about the age of the computer, because i remember a while back that broadcom agreed to something that would have made all of their further cards compatible with linux natively.

anyways, what do you get when you run, ifconfig

They did, but it isn't integrated in the kernel yet. b43-fwcutter and b43-firmware-installer should've fixed it.

I have the same card and II've had this issue before, and those two packages would always fix it.

---

### Post by WarrenSH on 2011-08-24
```
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:ff:b8:34  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:feff:b834/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:657815 (657.8 KB)  TX bytes:128576 (128.5 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65982 (65.9 KB)  TX bytes:65982 (65.9 KB)

```

> **kiddykoff said:**
> I was asking about the age of the computer, because i remember a while back that broadcom agreed to something that would have made all of their further cards compatible with linux natively.

anyways, what do you get when you run, ifconfig

---

### Post by bkratz on 2011-08-24
As I asked in one of your other threads, did you ever try to install the STA driver??  If so, you may have blacklisted the correct b43 drivers. What is the output of

egrep -e b43 -e ssb  /etc/modprobe.d/*

---

### Post by WarrenSH on 2011-08-24
```
-e b43 -e ssb /etc/modprobe.d/*
/etc/modprobe.d/blacklist-bcm43.conf:blacklist b43
/etc/modprobe.d/blacklist-bcm43.conf:blacklist b43legacy
/etc/modprobe.d/blacklist-bcm43.conf:blacklist ssb
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.

```

> **bkratz said:**
> As I asked in one of your other threads, did you ever try to install the STA driver??  If so, you may have blacklisted the correct b43 drivers. What is the output of

egrep -e b43 -e ssb  /etc/modprobe.d/*

---

### Post by WarrenSH on 2011-08-24
I also did this command in terminal 


```
[    0.132612] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.132689] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.132748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.132804] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.132853]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.134678] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.134727] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.134772] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.134823] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.134868] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.134914] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.134959] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.135004] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.135144] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.135149] vgaarb: loaded
[    0.135416] SCSI subsystem initialized
[    0.135505] libata version 3.00 loaded.
[    0.135575] usbcore: registered new interface driver usbfs
[    0.135593] usbcore: registered new interface driver hub
[    0.135625] usbcore: registered new device driver usb
[    0.135912] wmi: Mapper loaded
[    0.135915] PCI: Using ACPI for IRQ routing
[    0.135921] PCI: pci_cache_line_size set to 64 bytes
[    0.136031] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.136034] reserve RAM buffer: 0000000077ea0000 - 0000000077ffffff 
[    0.136170] NetLabel: Initializing
[    0.136173] NetLabel:  domain hash size = 128
[    0.136175] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.136191] NetLabel:  unlabeled traffic allowed by default
[    0.145357] AppArmor: AppArmor Filesystem Enabled
[    0.145404] pnp: PnP ACPI init
[    0.145428] ACPI: bus type pnp registered
[    0.146074] pnp 00:00: [bus 00-ff]
[    0.146078] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.146081] pnp 00:00: [mem 0x000c0000-0x000c1fff window]
[    0.146085] pnp 00:00: [mem 0x000c2000-0x000c3fff window]
[    0.146087] pnp 00:00: [mem 0x000c4000-0x000c5fff window]
[    0.146090] pnp 00:00: [mem 0x000c6000-0x000c7fff window]
[    0.146093] pnp 00:00: [mem 0x000c8000-0x000c9fff window]
[    0.146096] pnp 00:00: [mem 0x000ca000-0x000cbfff window]
[    0.146099] pnp 00:00: [mem 0x000cc000-0x000cdfff window]
[    0.146102] pnp 00:00: [mem 0x000ce000-0x000cffff window]
[    0.146105] pnp 00:00: [mem 0x000d0000-0x000d1fff window]
[    0.146108] pnp 00:00: [mem 0x000d2000-0x000d3fff window]
[    0.146111] pnp 00:00: [mem 0x000d4000-0x000d5fff window]
[    0.146113] pnp 00:00: [mem 0x000d6000-0x000d7fff window]
[    0.146116] pnp 00:00: [mem 0x000d8000-0x000d9fff window]
[    0.146119] pnp 00:00: [mem 0x000da000-0x000dbfff window]
[    0.146122] pnp 00:00: [mem 0x000dc000-0x000ddfff window]
[    0.146125] pnp 00:00: [mem 0x000de000-0x000dffff window]
[    0.146128] pnp 00:00: [mem 0x000e0000-0x000e1fff window]
[    0.146131] pnp 00:00: [mem 0x000e2000-0x000e3fff window]
[    0.146134] pnp 00:00: [mem 0x000e4000-0x000e5fff window]
[    0.146137] pnp 00:00: [mem 0x000e6000-0x000e7fff window]
[    0.146139] pnp 00:00: [mem 0x000e8000-0x000e9fff window]
[    0.146142] pnp 00:00: [mem 0x000ea000-0x000ebfff window]
[    0.146145] pnp 00:00: [mem 0x000ec000-0x000edfff window]
[    0.146148] pnp 00:00: [mem 0x000ee000-0x000effff window]
[    0.146151] pnp 00:00: [mem 0x80000000-0xffffffff window]
[    0.146154] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.146157] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.146160] pnp 00:00: [io  0x0d00-0xffff window]
[    0.146220] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.146243] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.146246] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.146249] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.146306] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.146310] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.146313] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.146318] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.146535] pnp 00:02: [io  0x0000-0x001f]
[    0.146538] pnp 00:02: [io  0x0080-0x008f]
[    0.146541] pnp 00:02: [io  0x00c0-0x00df]
[    0.146544] pnp 00:02: [dma 4]
[    0.146582] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.146592] pnp 00:03: [io  0x00f0-0x00fe]
[    0.146608] pnp 00:03: [irq 13]
[    0.146639] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.146651] pnp 00:04: [io  0x0070-0x0071]
[    0.146658] pnp 00:04: [irq 8]
[    0.146691] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.146701] pnp 00:05: [io  0x0061]
[    0.146736] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.146747] pnp 00:06: [io  0x0060]
[    0.146750] pnp 00:06: [io  0x0064]
[    0.146755] pnp 00:06: [irq 1]
[    0.146786] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.146799] pnp 00:07: [irq 12]
[    0.146832] pnp 00:07: Plug and Play ACPI device, IDs SYN0121 SYN0100 SYN0002 PNP0f13 (active)
[    0.146848] pnp 00:08: [io  0x0072-0x0073]
[    0.146851] pnp 00:08: [io  0x1080]
[    0.146854] pnp 00:08: [io  0x00b0-0x00b1]
[    0.146856] pnp 00:08: [io  0x0092]
[    0.146858] pnp 00:08: [io  0x040b]
[    0.146861] pnp 00:08: [io  0x04d0-0x04d1]
[    0.146863] pnp 00:08: [io  0x04d6]
[    0.146866] pnp 00:08: [io  0x0870-0x087f]
[    0.146868] pnp 00:08: [io  0x0c00-0x0c01]
[    0.146871] pnp 00:08: [io  0x0c14]
[    0.146873] pnp 00:08: [io  0x0c50-0x0c52]
[    0.146876] pnp 00:08: [io  0x0c6c]
[    0.146878] pnp 00:08: [io  0x0c6f]
[    0.146880] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.146883] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.146886] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.146888] pnp 00:08: [io  0x8000-0x805f]
[    0.146891] pnp 00:08: [io  0x8100-0x81ff window]
[    0.146897] pnp 00:08: [io  0x0f40-0x0f47]
[    0.146899] pnp 00:08: [io  0x0280-0x0293]
[    0.146969] system 00:08: [io  0x1080] has been reserved
[    0.146972] system 00:08: [io  0x040b] has been reserved
[    0.146975] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.146978] system 00:08: [io  0x04d6] has been reserved
[    0.146982] system 00:08: [io  0x0870-0x087f] has been reserved
[    0.146986] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.146989] system 00:08: [io  0x0c14] has been reserved
[    0.146992] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.146995] system 00:08: [io  0x0c6c] has been reserved
[    0.146999] system 00:08: [io  0x0c6f] has been reserved
[    0.147002] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.147005] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.147008] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.147012] system 00:08: [io  0x8000-0x805f] has been reserved
[    0.147015] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.147019] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.147022] system 00:08: [io  0x0280-0x0293] has been reserved
[    0.147027] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.147091] pnp 00:09: [mem 0x000e0000-0x000fffff]
[    0.147095] pnp 00:09: [mem 0xfff80000-0xffffffff]
[    0.147097] pnp 00:09: [mem 0x00000000-0x00000fff]
[    0.147113] pnp 00:09: disabling [mem 0x00000000-0x00000fff] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.147153] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.147157] system 00:09: [mem 0xfff80000-0xffffffff] has been reserved
[    0.147161] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.168042] pnp: PnP ACPI: found 10 devices
[    0.168045] ACPI: ACPI bus type pnp unregistered
[    0.168049] PnPBIOS: Disabled by ACPI PNP
[    0.204659] Switching to clocksource acpi_pm
[    0.204723] pci 0000:01:05.0: BAR 6: assigned [mem 0xc0120000-0xc013ffff pref]
[    0.204728] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.204731] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.204736] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
[    0.204740] pci 0000:00:01.0:   bridge window [mem 0xc8000000-0xcfffffff 64bit pref]
[    0.204745] pci 0000:00:05.0: PCI bridge to [bus 02-03]
[    0.204747] pci 0000:00:05.0:   bridge window [io  disabled]
[    0.204751] pci 0000:00:05.0:   bridge window [mem disabled]
[    0.204754] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.204759] pci 0000:00:14.4: PCI bridge to [bus 06-07]
[    0.204763] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.204772] pci 0000:00:14.4:   bridge window [mem 0xc0200000-0xc02fffff]
[    0.204778] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.204798] pci 0000:00:05.0: setting latency timer to 64
[    0.204809] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.204812] pci_bus 0000:00: resource 5 [mem 0x80000000-0xefffffff]
[    0.204815] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.204818] pci_bus 0000:00: resource 7 [mem 0xf0000000-0xffffffff]
[    0.204822] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.204825] pci_bus 0000:01: resource 1 [mem 0xc0100000-0xc01fffff]
[    0.204828] pci_bus 0000:01: resource 2 [mem 0xc8000000-0xcfffffff 64bit pref]
[    0.204831] pci_bus 0000:06: resource 0 [io  0xa000-0xafff]
[    0.204834] pci_bus 0000:06: resource 1 [mem 0xc0200000-0xc02fffff]
[    0.204838] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
[    0.204841] pci_bus 0000:06: resource 5 [mem 0x80000000-0xefffffff]
[    0.204844] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.204847] pci_bus 0000:06: resource 7 [mem 0xf0000000-0xffffffff]
[    0.204899] NET: Registered protocol family 2
[    0.204968] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.205313] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.206483] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.207054] TCP: Hash tables configured (established 131072 bind 65536)
[    0.207058] TCP reno registered
[    0.207066] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.207087] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.207202] NET: Registered protocol family 1
[    0.207217] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.207224] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.207311] pci 0000:01:05.0: Boot video device
[    0.207321] PCI: CLS 32 bytes, default 64
[    0.207617] cpufreq-nforce2: No nForce2 chipset.
[    0.207792] audit: initializing netlink socket (disabled)
[    0.207810] type=2000 audit(1314222931.204:1): initialized
[    0.207810] Switched to NOHz mode on CPU #0
[    0.218535] Trying to unpack rootfs image as initramfs...
[    0.236213] highmem bounce pool size: 64 pages
[    0.236221] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.244395] VFS: Disk quotas dquot_6.5.2
[    0.244487] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.245276] fuse init (API version 7.16)
[    0.245391] msgmni has been set to 1681
[    0.252473] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.252519] io scheduler noop registered
[    0.252522] io scheduler deadline registered
[    0.252542] io scheduler cfq registered (default)
[    0.252734] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.252769] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.254386] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.256118] ACPI: AC Adapter [ACAD] (on-line)
[    0.256224] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.256274] ACPI: Lid Switch [LID]
[    0.256321] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.256326] ACPI: Power Button [PWRB]
[    0.256389] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.256393] ACPI: Power Button [PWRF]
[    0.256450] input: Sleep Button as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input3
[    0.256454] ACPI: Sleep Button [SLPF]
[    0.256554] ACPI: acpi_idle registered with cpuidle
[    0.256589] Marking TSC unstable due to TSC halts in idle
[    0.288865] ACPI: Invalid active0 threshold
[    0.290959] thermal LNXTHERM:00: registered as thermal_zone0
[    0.290964] ACPI: Thermal Zone [THRM] (0 C)
[    0.291045] ERST: Table is not found!
[    0.291178] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.292466] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.292477] serial 0000:00:14.6: PCI INT B disabled
[    0.292674] Linux agpgart interface v0.103
[    0.294320] brd: module loaded
[    0.295012] loop: module loaded
[    0.295172] i2c-core: driver [adp5520] using legacy suspend method
[    0.295174] i2c-core: driver [adp5520] using legacy resume method
[    0.295378] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.295431] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.295885] Fixed MDIO Bus: probed
[    0.295934] PPP generic driver version 2.4.2
[    0.300091] tun: Universal TUN/TAP device driver, 1.6
[    0.300095] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.300260] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.300307] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.300332] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.300386] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.300467] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[    0.300522] isapnp: Scanning for PnP cards...
[    0.349727] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.349943] hub 1-0:1.0: USB hub found
[    0.349949] hub 1-0:1.0: 8 ports detected
[    0.350066] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.350088] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.350111] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.350176] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.350206] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[    0.452116] hub 2-0:1.0: USB hub found
[    0.452128] hub 2-0:1.0: 4 ports detected
[    0.452229] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.452254] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.452318] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.452348] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[    0.556140] hub 3-0:1.0: USB hub found
[    0.556153] hub 3-0:1.0: 4 ports detected
[    0.556254] uhci_hcd: USB Universal Host Controller Interface driver
[    0.556372] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.574333] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.574409] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.574540] mousedev: PS/2 mouse device common for all mice
[    0.574781] rtc_cmos 00:04: RTC can wake from S4
[    0.574837] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.574872] rtc0: alarms up to one month, 114 bytes nvram
[    0.574982] device-mapper: uevent: version 1.0.3
[    0.575090] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.575859] device-mapper: multipath: version 1.2.0 loaded
[    0.575862] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.575975] EISA: Probing bus 0 at eisa.0
[    0.575978] EISA: Cannot allocate resource for mainboard
[    0.575981] Cannot allocate resource for EISA slot 1
[    0.575984] Cannot allocate resource for EISA slot 2
[    0.575986] Cannot allocate resource for EISA slot 3
[    0.575989] Cannot allocate resource for EISA slot 4
[    0.575992] Cannot allocate resource for EISA slot 5
[    0.575994] Cannot allocate resource for EISA slot 6
[    0.575997] Cannot allocate resource for EISA slot 7
[    0.576045] Cannot allocate resource for EISA slot 8
[    0.576048] EISA: Detected 0 cards.
[    0.576162] cpuidle: using governor ladder
[    0.576226] cpuidle: using governor menu
[    0.576528] TCP cubic registered
[    0.576677] NET: Registered protocol family 10
[    0.577371] NET: Registered protocol family 17
[    0.577404] Registering the dns_resolver key type
[    0.577439] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3300+ (1 cpu cores) (version 2.20.00)
[    0.582137] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xa
[    0.582142] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xc
[    0.582145] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0xe
[    0.582147] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x13
[    0.582194] powernow-k8: ph2 null fid transition 0xc
[    0.582232] Using IPI No-Shortcut mode
[    0.582411] PM: Hibernation image not present or could not be loaded.
[    0.582426] registered taskstats version 1
[    0.582637]   Magic number: 7:934:955
[    0.582764] rtc_cmos 00:04: setting system clock to 2011-08-24 21:55:32 UTC (1314222932)
[    0.582768] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.582770] EDD information not available.
[    0.674848] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.674867] ACPI: Battery Slot [BAT1] (battery present)
[    0.723736] isapnp: No Plug & Play device found
[    0.761801] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.986527] Freeing initrd memory: 12548k freed
[    1.001157] Freeing unused kernel memory: 700k freed
[    1.001974] Write protecting the kernel text: 5192k
[    1.002013] Write protecting the kernel read-only data: 2148k
[    1.036055] <30>udev[61]: starting version 167
[    1.112072] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    1.307272] scsi0 : pata_atiixp
[    1.310100] scsi1 : pata_atiixp
[    1.310908] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    1.310912] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    1.322435] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.322465] 8139cp 0000:06:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.473190] ata2.00: ATAPI: PHILIPS CD-RW/DVD-ROM SCB5265, TH16, max MWDMA2
[    1.488543] ata2.00: configured for MWDMA2
[    1.490416] ata1.00: ATA-8: WDC WD3200BEVE-00A0HT0, 11.01A11, max UDMA/100
[    1.490419] ata1.00: 625142448 sectors, multi 16: LBA48 
[    1.505474] ata1.00: configured for UDMA/100
[    1.505623] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVE-0 11.0 PQ: 0 ANSI: 5
[    1.505857] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.506116] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.506171] sd 0:0:0:0: [sda] Write Protect is off
[    1.506175] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.506198] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.507247] scsi 1:0:0:0: CD-ROM            PHILIPS  CDRW/DVD SCB5265 TH16 PQ: 0 ANSI: 5
[    1.510759] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    1.510767] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.510948] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.511043] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.550134]  sda: sda1 sda2 < sda5 >
[    1.550537] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.568074] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.568150] 8139too 0000:06:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.573064] 8139too 0000:06:06.0: eth0: RealTek RTL8139 at 0xa000, 00:0f:b0:ff:b8:34, IRQ 22
[    1.589228] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input5
[    1.589600] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:13.1-2/input0
[    1.589909] usbcore: registered new interface driver usbhid
[    1.589914] usbhid: USB HID core driver
[    1.898843] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.621923] Adding 1963004k swap on /dev/sda5.  Priority:-1 extents:1 across:1963004k 
[   15.664956] <30>udev[271]: starting version 167
[   15.772541] lp: driver loaded but no devices found
[   15.829572] cfg80211: Calling CRDA to update world regulatory domain
[   15.979704] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.988453] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.996119] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[   15.996131] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[   15.996143] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[   15.996152] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[   16.027168] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   16.037281] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[   16.070883] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   16.136228] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   16.136233] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136237] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   16.136240] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136243] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   16.136246] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136249] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   16.136252] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136255] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   16.136258] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136261] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   16.136264] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136267] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   16.136270] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136273] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   16.136276] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136279] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   16.136282] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136285] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   16.136288] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136291] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   16.136294] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136297] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   16.136300] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136303] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   16.136306] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.136309] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   16.136312] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[   16.228563] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   16.229297] Registered led device: b43-phy0::radio
[   16.229321] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   16.303642] type=1400 audit(1314222948.216:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=498 comm="apparmor_parser"
[   16.318557] type=1400 audit(1314222948.232:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=498 comm="apparmor_parser"
[   16.318842] type=1400 audit(1314222948.232:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=498 comm="apparmor_parser"
[   16.388338] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.923584] acpi device:11: registered as cooling_device1
[   16.923774] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0f/LNXVIDEO:00/input/input6
[   16.923918] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.472673] [drm] Initialized drm 1.1.0 20060810
[   17.785845] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.785853] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785856] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.785859] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785862] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.785865] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785868] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.785871] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785874] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.785877] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785880] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.785883] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785886] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.785889] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785892] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.785895] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785898] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.785901] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785904] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.785907] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785910] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.785913] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785916] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   17.785919] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785922] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   17.785925] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785928] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   17.785931] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.785936] cfg80211: World regulatory domain updated:
[   17.785938] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.785941] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.785944] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.785947] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.785950] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.785953] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.863429] input: HP WMI hotkeys as /devices/virtual/input/input7
[   17.888902] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000/0x0
[   17.954735] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   18.148185] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   18.200459] [drm] radeon defaulting to kernel modesetting.
[   18.200465] [drm] radeon kernel modesetting enabled.
[   18.200569] radeon 0000:01:05.0: power state changed by ACPI to D0
[   18.200573] radeon 0000:01:05.0: power state changed by ACPI to D0
[   18.200583] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.204168] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.228194] b43-phy0: Radio hardware status changed to DISABLED
[   18.252139] [drm] initializing kernel modesetting (RS480 0x1002:0x5955).
[   18.252177] [drm] register mmio base: 0xC0100000
[   18.252180] [drm] register mmio size: 65536
[   18.252392] [drm] Generation 2 PCI interface, using max accessible memory
[   18.252401] radeon 0000:01:05.0: VRAM: 128M 0x0000000078000000 - 0x000000007FFFFFFF (128M used)
[   18.252405] radeon 0000:01:05.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[   18.252438] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.252440] [drm] Driver supports precise vblank timestamp query.
[   18.252473] [drm] radeon: irq initialized.
[   18.252556] [drm] Detected VRAM RAM=128M, BAR=128M
[   18.252561] [drm] RAM width 128bits DDR
[   18.262366] [TTM] Zone  kernel: Available graphics memory: 437176 kiB.
[   18.262370] [TTM] Zone highmem: Available graphics memory: 964860 kiB.
[   18.262372] [TTM] Initializing pool allocator.
[   18.262400] [drm] radeon: 128M of VRAM memory ready
[   18.262403] [drm] radeon: 512M of GTT memory ready.
[   18.262437] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   18.281801] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   18.294041] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   18.434915] type=1400 audit(1314222950.348:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=786 comm="apparmor_parser"
[   18.456266] type=1400 audit(1314222950.372:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=788 comm="apparmor_parser"
[   18.460679] type=1400 audit(1314222950.376:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=788 comm="apparmor_parser"
[   18.460969] type=1400 audit(1314222950.376:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=788 comm="apparmor_parser"
[   18.465541] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.465641] radeon 0000:01:05.0: WB enabled
[   18.473499] [drm] Loading R300 Microcode
[   18.486487] [drm] radeon: ring at 0x0000000080001000
[   18.486511] [drm] ring test succeeded in 1 usecs
[   18.486656] [drm] radeon: ib pool ready.
[   18.488186] type=1400 audit(1314222950.404:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=789 comm="apparmor_parser"
[   18.488518] [drm] ib test succeeded in 0 usecs
[   18.500378] type=1400 audit(1314222950.416:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=789 comm="apparmor_parser"
[   18.502529] [drm] Panel ID String: QDS                     
[   18.502536] [drm] Panel Size 1280x800
[   18.504772] [drm] Radeon Display Connectors
[   18.504778] [drm] Connector 0:
[   18.504780] [drm]   VGA
[   18.504784] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   18.504786] [drm]   Encoders:
[   18.504788] [drm]     CRT1: INTERNAL_DAC2
[   18.504790] [drm] Connector 1:
[   18.504791] [drm]   LVDS
[   18.504794] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   18.504796] [drm]   Encoders:
[   18.504798] [drm]     LCD1: INTERNAL_LVDS
[   18.504800] [drm] Connector 2:
[   18.504802] [drm]   S-video
[   18.504803] [drm]   Encoders:
[   18.504805] [drm]     TV1: INTERNAL_DAC2
[   18.516424] type=1400 audit(1314222950.432:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=789 comm="apparmor_parser"
[   18.579028] MC'97 0 converters and GPIO not ready (0x1)
[   18.582617] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.683756] [drm] radeon: power management initialized
[   19.022186] [drm] fb mappable at 0xC8040000
[   19.022191] [drm] vram apper at 0xC8000000
[   19.022193] [drm] size 4096000
[   19.022195] [drm] fb depth is 24
[   19.022197] [drm]    pitch is 5120
[   19.022519] fbcon: radeondrmfb (fb0) is primary device
[   19.026692] Console: switching to colour frame buffer device 160x50
[   19.026738] fb0: radeondrmfb frame buffer device
[   19.026740] drm: registered panic notifier
[   19.026753] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
[   19.207244] ppdev: user-space parallel port driver
[   22.739870] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   27.844208] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   28.384039] eth0: no IPv6 routers present
[   61.213309] eth0: link down
[   86.812244] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  958.773771] exe (1970): /proc/1970/oom_adj is deprecated, please use /proc/1970/oom_score_adj instead.
```

---

### Post by WarrenSH on 2011-08-24
BUMP BUMP BUMP....

Still not working for me. How do I remove the blacklist?

---

### Post by bkratz on 2011-08-25
> **WarrenSH said:**
> BUMP BUMP BUMP....

Still not working for me. How do I remove the blacklist?



Just woke up.

-e b43 -e ssb /etc/modprobe.d/*
[COLOR="Red"]/etc/modprobe.d/blacklist-bcm43.conf:blacklist b43[/COLOR]
/etc/modprobe.d/blacklist-bcm43.conf:blacklist b43legacy
/etc/modprobe.d/blacklist-bcm43.conf:blacklist ssb
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.


There it is!

```
gksudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```

add the # sign in front of blacklist b43 and # in front of blacklist ssb so they look like
#blacklist b43
#blacklist ssb



To guarantee that the module is added at boot time. Do

```
sudo su
echo b43 >> /etc/modules
exit

```

It then should reload at boot time. This step may not be necessary, but will guarantee that it happens.

Reboot and enjoy!

---

### Post by ArgusVision on 2011-08-25
Hey Bkratz and IWantFroyo,
    Just wanted to say thank you. Your tips worked great for me. Didn't they have a 'thank' button at one time?

I had the same issue, worked fine before upgrade to 11.04, then broke after upgrade. 
FYI: appending b43 to /etc/modules wasn't needed. But not a bad suggestion.

---

### Post by bkratz on 2011-08-25
Glad to hear you got it sorted out. congratulations and enjoy your wireless!

SORRY, just noticed that you are not the original poster--but congrats anyway!

---

### Post by WarrenSH on 2011-08-26
Thank you I just did this and i'm going to reboot now. I so hope this works thanks for the info <3 :KS:KS:KS

> **bkratz said:**
> Just woke up.

-e b43 -e ssb /etc/modprobe.d/*
[COLOR="Red"]/etc/modprobe.d/blacklist-bcm43.conf:blacklist b43[/COLOR]
/etc/modprobe.d/blacklist-bcm43.conf:blacklist b43legacy
/etc/modprobe.d/blacklist-bcm43.conf:blacklist ssb
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.


There it is!

```
gksudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```

add the # sign in front of blacklist b43 and # in front of blacklist ssb so they look like
#blacklist b43
#blacklist ssb



To guarantee that the module is added at boot time. Do

```
sudo su
echo b43 >> /etc/modules
exit

```

It then should reload at boot time. This step may not be necessary, but will guarantee that it happens.

Reboot and enjoy!

---

### Post by WarrenSH on 2011-08-26
Still not working for me... :(

PLZ see the images below & let me know what I might have done wrong. 

The last screenshot is to show you that the wifi is still not working. My high speed only works when plugged in :confused:

.
.
.
.
.

[IMG]http://img402.imageshack.us/img402/8259/screenshot1od.png[/IMG]
[IMG]http://img685.imageshack.us/img685/4966/screenshot2yn.png[/IMG]
[IMG]http://img718.imageshack.us/img718/6832/screenshot3fp.png[/IMG]
.
.
.
.
.
.

> **bkratz said:**
> Just woke up.

-e b43 -e ssb /etc/modprobe.d/*
[COLOR="Red"]/etc/modprobe.d/blacklist-bcm43.conf:blacklist b43[/COLOR]
/etc/modprobe.d/blacklist-bcm43.conf:blacklist b43legacy
/etc/modprobe.d/blacklist-bcm43.conf:blacklist ssb
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.


There it is!

```
gksudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```

add the # sign in front of blacklist b43 and # in front of blacklist ssb so they look like
#blacklist b43
#blacklist ssb



To guarantee that the module is added at boot time. Do

```
sudo su
echo b43 >> /etc/modules
exit

```

It then should reload at boot time. This step may not be necessary, but will guarantee that it happens.

Reboot and enjoy!

---

### Post by bkratz on 2011-08-26
> **WarrenSH said:**
> Still not working for me... :(

PLZ see the images below & let me know what I might have done wrong. 

The last screenshot is to show you that the wifi is still not working. My high speed only works when plugged in :confused:

.
.
.
.
.

[IMG]http://img402.imageshack.us/img402/8259/screenshot1od.png[/IMG]
[IMG]http://img685.imageshack.us/img685/4966/screenshot2yn.png[/IMG]
[IMG]http://img718.imageshack.us/img718/6832/screenshot3fp.png[/IMG]
.
.
.
.
.
.



Actually you did do it right, it was me that forgot that we also need to remove the wl driver, the b43 and wl don't like each other very much, they are probably fighting right now. Anyway,look at

```
 lsmod 
```

(that is an L not a 1) and see if you see all of the following (plus a lot more) wl, b43 and ssb now. If we remove wl you should be golden.

```
sudo apt-get remove –purge bcmwl-kernel-source
```

this will remove wl (STA) may require a reboot. You might also want to post the following:

```
rfkill list all
```

and look for any hard or soft blocks.

---

### Post by Dr_U on 2011-08-26
Hi,

I too am having problems with WiFi not working on fresh install. However, my hardware is a **Ralink** (see below).

My set up: an MSI notebook that also has Mint 9 Fluxbox edition (completely  up-to-date and **without** the problems described below). Here are some  outputs that I gathered when logged in:

from: lspci | grep Net

04:09.0 Network controller: Ralink corp. RT2561/RT61 rev B 802.11g

---
from the wireless.kernel.org page: the correct driver to use is rt61pci

---
from: lsmod | grep rt61pci

rt61pci                27265  0
rt2x00pci              13986  1 rt61pci
rt2x00lib              39075  2 rt61pci,rt2x00pci
eeprom_93cx6           12653  1 rt61pci
crc_itu_t              12627  2 rt61pci,firewire_core

---
from: iwconfig

lo          no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any
             Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated
             Tx-Power=20 dBm
             Retry  long limit:7   RTS thr: off   Fragment thr: off
             Power Management: on
---
from: iwlist wlan0 scanning

wlan0   No scan results
---
**Using Mint 9 Fluxbox I have no problems** at all connecting to my wireless AP at home or the APs at work.

With11.04  the situation is confusing: After the initial install (which  I just did about 4 days ago) and reboot the wireless connection worked  fine. I updated everything with synaptic and everything worked well. I  think it did this for the first day, maybe the second day as well. After  that I have been unable to connect using wireless.

The signal  strength (in conky) is 100% and in the nm-applet it appears as well and  is also strong. After the initial password prompt for the keyring, it  just does not connect. After a while it will pop-up a prompt for the  WPA/WPA2 key (which is correctly stored). It then tries again to  connect. After a while the prompt for the WPA/WPA2 key appears again.

This  repeats itself for a while. After about 5-6 tries, the nm-applet pops  up a message that the wireless connection is disconnected. Checking the  nm-applet I no longer see any wireless signals listed.

I can still connect with a cable to eth0 (which I am currently using to write this).

Another  observation: a few days before installing, I installed  Lubuntu 11.04. The exact same problems occurred (which is why I deleted  Lubuntu).

Could it be that  the newer kernel, the newer nm-applet or the rt61pci driver are somehow  no longer working? I guess that I could go back to using Mint 9 Fluxbox,  but 11.04 is very nice ...

Any help would be greatly appreciated !!

Thanks in advance,

-- Dr. U

---

### Post by WarrenSH on 2011-08-26
I do not see w1 or wl <-- wL looks like a one but it's a L.  I only see ssb & b43 when doing the lsmod command. I also got this when doing sudo apt-get remove &#8211;purge bcmwl-kernel-source

```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
radeon                900494  4 
snd_atiixp             19400  2 
snd_atiixp_modem       18624  0 
snd_ac97_codec        105614  2 snd_atiixp,snd_atiixp_modem
joydev                 17322  0 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ttm                    65184  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
drm                   184164  6 radeon,ttm,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
video                  18951  0 
snd                    55295  12 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12872  0 
arc4                   12473  2 
shpchp                 32345  0 
b43                   296610  0 
soundcore              12600  1 snd
i2c_piix4              13095  0 
snd_page_alloc         14073  3 snd_atiixp,snd_atiixp_modem,snd_pcm
ati_agp                13202  0 
ssb                    45942  1 b43
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
8139too                23208  0 
hid                    77084  1 usbhid
8139cp                 22497  0 
pata_atiixp            12968  2 
```

```
wls@Presario_V5101US:~$ sudo apt-get remove &#8211;purge bcmwl-kernel-source
[sudo] password for wls: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package &#8211;purge

```

> **bkratz said:**
> Actually you did do it right, it was me that forgot that we also need to remove the wl driver, the b43 and wl don't like each other very much, they are probably fighting right now. Anyway,look at

```
 lsmod 
```

(that is an L not a 1) and see if you see all of the following (plus a lot more) wl, b43 and ssb now. If we remove wl you should be golden.

```
sudo apt-get remove &#8211;purge bcmwl-kernel-source
```

this will remove wl (STA) may require a reboot. You might also want to post the following:

```
rfkill list all
```

and look for any hard or soft blocks.

---

### Post by bkratz on 2011-08-26
That is good, since we don't see wl the is no need to remove it!  The next thing now would be to see the output of

rfkill list all


and look for blocks--hard or soft, we may be having the problem with hp-wmi module but the above should tell us.

---

### Post by WarrenSH on 2011-08-26
Looks like we have a few blocks. 

```
wls@Presario_V5101US:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```


> **bkratz said:**
> That is good, since we don't see wl the is no need to remove it!  The next thing now would be to see the output of

rfkill list all


and look for blocks--hard or soft, we may be having the problem with hp-wmi module but the above should tell us.

---

### Post by bkratz on 2011-08-27
The other problem might be the module hp-wmi. Laptops require a small module to translate key presses, primarily Function keys, to useful information, such as, "Please turn on the wireless". In Hp's that is usually contrl F12.

As an experiment we can try (this would be just temporary, so don't reboot)

sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all

and see if it works better. If so we can make it permanent. Here are some relevant posts about exactly the same problem where the poster later discovered that alt F12 actually worked on his rather than Cntrl F12. Probably some good clues here.


[http://ubuntuforums.org/showthread.php?t=1793994](http://ubuntuforums.org/showthread.php?t=1793994)
[http://ubuntuforums.org/showpost.php?p=10026302&postcount=20](http://ubuntuforums.org/showpost.php?p=10026302&postcount=20)
[http://ubuntuforums.org/showthread.php?t=1706731](http://ubuntuforums.org/showthread.php?t=1706731)



If you do experiment with other key combinations it will be necessary to either reboot or execute

sudo modprobe hp-wmi

to put the module back in first. During experimentation just keep trying

rfkill list all

until you see the hardblock dissapear.

---

