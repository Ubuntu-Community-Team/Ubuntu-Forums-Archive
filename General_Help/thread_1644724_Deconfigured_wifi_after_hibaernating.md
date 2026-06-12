---
title: "Deconfigured wifi after hibaernating"
date: 2010-12-13
forum: General Help
---

### Post by HotForLinux on 2010-12-13
After hibernating a laptop with Hardy Heron installed, I boot and a little message tells me that the boot process wasn't clean (or something like that), but it doesn't tell me what kind of problem there has been.

I have repeatedly detected that, at least, the wifi interface is corrupted (deconfigured or lost), and seems inexistent to the system.

I would like to know whether this is a bug or something is misconfigured in the system and how to fix the problem without having to reboot again.

Here's the output of some commands, in chronological order, after touching around (not much) trying to see if I could fix the problem.

Normally I boot with
eth0 as the wired interface and eth1 as the wifi interface.

```
==============================

**$ lshw**
....
 *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Ethernet interface
                product: 88E8036 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth1_rename
                version: 10
                serial: 00:a0:d1:bb:ae:17
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes

...

 *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:05:04.0
                logical name: eth0
                version: 05
                serial: 00:0e:35:e4:21:84
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

===========================

**$ sudo /etc/init.d/networking force-reload**
 * Reconfiguring network interfaces...                                                                                          eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
=================================

**$ ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:0e:35:e4:21:84  
          inet6 addr: fe80::20e:35ff:fee4:2184/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116 errors:0 dropped:1 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:696238 (679.9 KB)  TX bytes:1120616 (1.0 MB)
          Interrupt:11 Base address:0x2000 Memory:b800b000-b800bfff 

eth1_rename Link encap:Ethernet  HWaddr 00:a0:d1:bb:ae:17  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          LOOPBACK  MTU:16436  Metric:1
          RX packets:16775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:981054 (958.0 KB)  TX bytes:981054 (958.0 KB)

===================================

**$ iwconfig**
lo        no wireless extensions.

eth0      IEEE 802.11g  ESSID:"WebSTAR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:C6:DE:85:3D   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/100  Signal level=-69 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:3

eth1_rename  no wireless extensions.
================================

**$ cat /proc/net/wireless **
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
  eth0: 0000   53.  -69.  -90.       0      0      0      0      1        6

========================

**$ sudo ifdown eth1**
ifdown: interface eth1 not configured

=================

[B]$ sudo ifconfig eth0 up
$ sudo ifconfig eth1 up[/B]
eth1: ERROR while getting interface flags: No such device

=====================================

**$ cat /etc/network/interfaces **
auto lo
  iface lo inet loopback
  address 127.0.0.1
  netmask 255.0.0.0

#auto eth0
  iface eth0 inet dhcp

auto eth1
  iface eth1 inet dhcp
  wireless-essid $my_essid
  wireless-key $mykey

====================================
```Below is the output of **dmesg** after the hibernation and before the reboot that reestablished the interfaces.

```

**$ dmesg**
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-27-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Wed Mar 24 10:04:52 UTC 2010 (Ubuntu 2.6.24-27.69-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f7dfffc (usable)
[    0.000000]  BIOS-e820: 000000005f7dfffc - 000000005f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000005f7fffc0 - 000000005f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 631MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 391135) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   391135
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   391135
[    0.000000] On node 0 totalpages: 391135
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1263 pages used for memmap
[    0.000000]   HighMem zone: 160496 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E5010 checksum 0
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 TOSINV)
[    0.000000] ACPI: RSDT 5F7F86C7, 0034 (r1 INSYDE RSDT_000      100 ABCD    10200)
[    0.000000] ACPI: FACP 5F7FFB30, 0074 (r1 TOSINV FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 5F7F8D10, 6E13 (r1 TOSINV SONOMA       1004 INTL  2002036)
[    0.000000] ACPI: FACS 5F7FFFC0, 0040
[    0.000000] ACPI: MCFG 5F7FFBC0, 003C (r1 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 5F7F88B5, 0237 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
[    0.000000] ACPI: SSDT 5F7F86FB, 01BA (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5f800000:a0700000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 388080
[    0.000000] Kernel command line: root=UUID=101d90ae-ebe6-48a2-b01b-51421c9cbfc7 ro vga=791
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01c01000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.040 MHz processor.
[   16.571827] Console: colour dummy device 80x25
[   16.571832] console [tty0] enabled
[   16.572321] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.572797] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.647842] Memory: 1538440k/1564540k available (2182k kernel code, 24904k reserved, 1005k data, 368k init, 647036k highmem)
[   16.647865] virtual kernel memory layout:
[   16.647866]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   16.647867]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.647869]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.647870]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.647871]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   16.647873]       .data : 0xc03218ca - 0xc041cdc4   (1005 kB)
[   16.647874]       .text : 0xc0100000 - 0xc03218ca   (2182 kB)
[   16.647899] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.647965] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.648029] Calibrating delay loop (skipped), using tsc calculated value.. 3192.08 BogoMIPS (lpj=6384160)
[   16.648076] Security Framework initialized
[   16.648090] SELinux:  Disabled at boot.
[   16.648112] AppArmor: AppArmor initialized
[   16.648120] Failure registering capabilities with primary security module.
[   16.648134] Mount-cache hash table entries: 512
[   16.648306] Initializing cgroup subsys ns
[   16.648320] Initializing cgroup subsys cpuacct
[   16.648337] CPU: After generic identify, caps: afe9f9ff 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[   16.648350] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.648355] CPU: L2 cache: 2048K
[   16.648362] CPU: After all inits, caps: afe9f9ff 00000000 00000000 00042040 00000180 00000000 00000000 00000000
[   16.648374] Compat vDSO mapped to ffffe000.
[   16.648392] Checking 'hlt' instruction... OK.
[   16.664396] SMP alternatives: switching to UP code
[   16.666391] Freeing SMP alternatives: 11k freed
[   16.666523] Early unpacking initramfs... done
[   17.068260] ACPI: Core revision 20070126
[   17.068343] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.071251] ACPI: setting ELCR to 0200 (from 0c20)
[   17.142482] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[   17.142500] SMP motherboard not detected.
[   17.142504] Local APIC not detected. Using dummy APIC emulation.
[   17.142553] Brought up 1 CPUs
[   17.142572] CPU0 attaching sched-domain:
[   17.142575]  domain 0: span 01
[   17.142577]   groups: 01
[   17.142767] net_namespace: 64 bytes
[   17.142778] Booting paravirtualized kernel on bare hardware
[   17.143264] Time: 11:43:37  Date: 12/10/10
[   17.143294] NET: Registered protocol family 16
[   17.143496] EISA bus registered
[   17.143520] ACPI: bus type pci registered
[   17.143654] PCI: PCI BIOS revision 2.10 entry at 0xea7d4, last bus=5
[   17.143660] PCI: Using configuration type 1
[   17.143671] Setting up standard PCI resources
[   17.146277] ACPI: EC: Look up EC in DSDT
[   17.153631] ACPI: Interpreter enabled
[   17.153637] ACPI: (supports S0 S3 S4 S5)
[   17.153654] ACPI: Using PIC for interrupt routing
[   17.174493] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   17.174500] ACPI: EC: driver started in poll mode
[   17.174544] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.175303] Force enabled HPET at base address 0xfed00000
[   17.175309] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   17.175317] PCI quirk: region 1300-133f claimed by ICH6 GPIO
[   17.176142] PCI: Transparent bridge - 0000:00:1e.0
[   17.176229] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.176640] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   17.176817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   17.177009] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   17.203762] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[   17.203932] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[   17.204043] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *11)
[   17.204153] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[   17.204262] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 11)
[   17.204372] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 10) *0, disabled.
[   17.204523] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[   17.204632] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[   17.204768] ACPI: Power Resource [PFA1] (off)
[   17.204812] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.204846] pnp: PnP ACPI init
[   17.204855] ACPI: bus type pnp registered
[   17.212909] pnp: PnP ACPI: found 9 devices
[   17.212915] ACPI: ACPI bus type pnp unregistered
[   17.212920] PnPBIOS: Disabled by ACPI PNP
[   17.213149] PCI: Using ACPI for IRQ routing
[   17.213154] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.213193] PCI: Cannot allocate resource region 0 of device 0000:05:06.0
[   17.235450] NET: Registered protocol family 8
[   17.235455] NET: Registered protocol family 20
[   17.235635] hpet clockevent registered
[   17.235642] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   17.235649] hpet0: 3 64-bit timers, 14318180 Hz
[   17.236684] AppArmor: AppArmor Filesystem Enabled
[   17.239636] Time: tsc clocksource has been installed.
[   17.247667] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   17.247674] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[   17.247681] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[   17.247687] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[   17.247693] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[   17.247699] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[   17.247706] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[   17.247712] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[   17.247722] system 00:05: ioport range 0x300-0x36f has been reserved
[   17.247728] system 00:05: ioport range 0x800-0x80f has been reserved
[   17.247734] system 00:05: ioport range 0x1000-0x107f has been reserved
[   17.247740] system 00:05: ioport range 0x1300-0x133f has been reserved
[   17.247746] system 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[   17.247752] system 00:05: iomem range 0xf0008000-0xf000bfff has been reserved
[   17.247759] system 00:05: iomem range 0xfed14000-0xfed17fff has been reserved
[   17.247765] system 00:05: iomem range 0xfed18000-0xfed18fff has been reserved
[   17.247771] system 00:05: iomem range 0xfed19000-0xfed19fff has been reserved
[   17.278165] PCI: Bridge: 0000:00:1c.0
[   17.278171]   IO window: c000-dfff
[   17.278179]   MEM window: cc000000-cfffffff
[   17.278185]   PREFETCH window: 9c000000-9fffffff
[   17.278193] PCI: Bridge: 0000:00:1c.1
[   17.278198]   IO window: a000-bfff
[   17.278206]   MEM window: c8000000-cbffffff
[   17.278213]   PREFETCH window: 98000000-9bffffff
[   17.278228] PCI: Bus 6, cardbus bridge: 0000:05:06.0
[   17.278232]   IO window: 00008000-000080ff
[   17.278240]   IO window: 00008400-000084ff
[   17.278247]   PREFETCH window: 88000000-8bffffff
[   17.278255]   MEM window: bc000000-bfffffff
[   17.278262] PCI: Bridge: 0000:00:1e.0
[   17.278267]   IO window: 8000-9fff
[   17.278274]   MEM window: b8000000-c7ffffff
[   17.278281]   PREFETCH window: 88000000-97ffffff
[   17.278478] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   17.278484] PCI: setting IRQ 10 as level-triggered
[   17.278489] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   17.278501] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.278679] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   17.278685] PCI: setting IRQ 11 as level-triggered
[   17.278690] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.278701] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.278715] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.278887] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   17.278892] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   17.278912] NET: Registered protocol family 2
[   17.315627] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.315854] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.316657] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.317124] TCP: Hash tables configured (established 131072 bind 65536)
[   17.317131] TCP reno registered
[   17.327716] checking if image is initramfs... it is
[   17.739177] Switched to high resolution mode on CPU 0
[   18.112457] Freeing initrd memory: 7717k freed
[   18.113054] audit: initializing netlink socket (disabled)
[   18.113076] audit(1291981418.396:1): initialized
[   18.113283] highmem bounce pool size: 64 pages
[   18.115335] VFS: Disk quotas dquot_6.5.1
[   18.115421] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.115584] io scheduler noop registered
[   18.115589] io scheduler anticipatory registered
[   18.115594] io scheduler deadline registered
[   18.115608] io scheduler cfq registered (default)
[   18.115625] Boot video device is 0000:00:02.0
[   18.115829] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.115882] assign_interrupt_mode Found MSI capability
[   18.115932] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.115975] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.116071] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.116123] assign_interrupt_mode Found MSI capability
[   18.116168] Allocate Port Service[0000:00:1c.1:pcie00]
[   18.116202] Allocate Port Service[0000:00:1c.1:pcie02]
[   18.116453] isapnp: Scanning for PnP cards...
[   18.470056] isapnp: No Plug & Play device found
[   18.498058] Real Time Clock Driver v1.12ac
[   18.498182] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.499247] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[   18.499255] PCI: setting IRQ 5 as level-triggered
[   18.499260] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   18.499276] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   18.499927] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.500006] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.500110] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.503642] i8042.c: Detected active multiplexing controller, rev 1.1.
[   18.505566] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.505573] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.505578] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.505583] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.505588] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.510497] mice: PS/2 mouse device common for all mice
[   18.510614] EISA: Probing bus 0 at eisa.0
[   18.510624] Cannot allocate resource for EISA slot 1
[   18.510651] Cannot allocate resource for EISA slot 8
[   18.510656] EISA: Detected 0 cards.
[   18.510661] cpuidle: using governor ladder
[   18.510665] cpuidle: using governor menu
[   18.510764] NET: Registered protocol family 1
[   18.510795] Using IPI No-Shortcut mode
[   18.510834] registered taskstats version 1
[   18.510954]   Magic number: 6:637:731
[   18.511050] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.511055] EDD information not available.
[   18.511258] Freeing unused kernel memory: 368k freed
[   18.511290] Write protecting the kernel read-only data: 803k
[   18.517276] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   18.606575] vesafb: framebuffer at 0xa0000000, mapped to 0xf8880000, using 3072k, total 7872k
[   18.606591] vesafb: mode is 1024x768x16, linelength=2048, pages=4
[   18.606596] vesafb: scrolling: redraw
[   18.606600] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[   18.606717] Console: switching to colour frame buffer device 128x48
[   18.622066] fb0: VESA VGA frame buffer device
[   18.734564] fuse init (API version 7.9)
[   18.746972] ACPI: Transitioning device [FAN1] to D3
[   18.747121] ACPI: Transitioning device [FAN1] to D3
[   18.747266] ACPI: Fan [FAN1] (off)
[   18.753409] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.753603] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.753804] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.818229] ACPI: Thermal Zone [TZCR] (40 C)
[   18.826214] ACPI: Thermal Zone [TZCL] (18 C)
[   19.233707] Clocksource tsc unstable (delta = -4679290018 ns)
[   19.237696] Time: hpet clocksource has been installed.
[   19.429990] usbcore: registered new interface driver usbfs
[   19.430184] usbcore: registered new interface driver hub
[   19.437542] usbcore: registered new device driver usb
[   19.444357] USB Universal Host Controller Interface driver v3.0
[   19.450262] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   19.455895] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   19.461683] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.461688] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.497850] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.503837] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[   19.537674] usb usb1: configuration #1 chosen from 1 choice
[   19.549747] hub 1-0:1.0: USB hub found
[   19.555774] hub 1-0:1.0: 2 ports detected
[   19.689635] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   19.695735] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   19.701997] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.702002] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.708249] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.714528] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[   19.720861] usb usb2: configuration #1 chosen from 1 choice
[   19.727109] hub 2-0:1.0: USB hub found
[   19.734384] hub 2-0:1.0: 2 ports detected
[   19.753454] SCSI subsystem initialized
[   19.827777] libata version 3.00 loaded.
[   19.841262] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   19.847355] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.847360] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.853378] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.859383] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[   19.865422] usb usb3: configuration #1 chosen from 1 choice
[   19.871400] hub 3-0:1.0: USB hub found
[   19.877279] hub 3-0:1.0: 2 ports detected
[   19.985100] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   19.991153] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   19.991158] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   19.997212] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   20.003312] uhci_hcd 0000:00:1d.3: irq 11, io base 0x00001260
[   20.009564] usb usb4: configuration #1 chosen from 1 choice
[   20.015755] hub 4-0:1.0: USB hub found
[   20.021884] hub 4-0:1.0: 2 ports detected
[   20.129084] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[   20.135907] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   20.142025] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.142030] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.148564] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   20.158700] ehci_hcd 0000:00:1d.7: debug port 1
[   20.164851] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   20.164858] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[   20.184793] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.191152] usb usb5: configuration #1 chosen from 1 choice
[   20.197476] hub 5-0:1.0: USB hub found
[   20.203689] hub 5-0:1.0: 8 ports detected
[   20.313182] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 6
[   20.319364] PCI: setting IRQ 6 as level-triggered
[   20.319369] ACPI: PCI Interrupt 0000:05:06.2[C] -> Link [LNKG] -> GSI 6 (level, low) -> IRQ 6
[   20.375505] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   20.392620] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   20.399517] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.399532] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   20.412124] ahci 0000:00:1f.2: version 3.0
[   20.412136] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   20.419043] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   20.425852] ahci: probe of 0000:00:1f.2 failed with error -22
[   20.435844] ata_piix 0000:00:1f.2: version 2.12
[   20.435849] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   20.594438] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   20.601425] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.601503] scsi0 : ata_piix
[   20.608507] scsi1 : ata_piix
[   20.616194] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[   20.623126] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[   20.633286] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OAD4A, max UDMA/100
[   20.640101] ata1.00: 156301488 sectors, multi 16: LBA48 
[   20.646801] ata1.00: applying bridge limits
[   20.654985] ata1.00: configured for UDMA/100
[   20.667033] ata2.00: ATAPI: MATSHITADVD-RAM UJ-830S, 1.00, max UDMA/33
[   20.676595] ata2.00: configured for UDMA/33
[   20.683328] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
[   20.690822] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-830S  1.00 PQ: 0 ANSI: 5
[   20.707824] Driver 'sd' needs updating - please use bus_type methods
[   20.714737] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   20.723218] sd 0:0:0:0: [sda] Write Protect is off
[   20.729990] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.730451] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.739724] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   20.746665] Driver 'sr' needs updating - please use bus_type methods
[   20.754077] sd 0:0:0:0: [sda] Write Protect is off
[   20.761076] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.761478] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.768873]  sda:<7>ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d1bbae17]
[   20.780681]  sda1 sda2 < sda5 sda6 sda7 sda8 > sda3
[   20.788510] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.799113] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   20.806231] Uniform CD-ROM driver Revision: 3.20
[   20.813346] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   20.821971] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   20.829170] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   20.977885] Attempting manual resume
[   20.985044] swsusp: Resume From Partition 8:6
[   20.985046] PM: Checking swsusp image.
[   20.985185] PM: Resume from disk failed.
[   21.008361] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[   21.015635] ReiserFS: sda5: using ordered data mode
[   21.023484] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   21.038810] ReiserFS: sda5: checking transaction log (sda5)
[   21.046888] ReiserFS: sda5: Using r5 hash to sort names
[   24.681323] Linux agpgart interface v0.102
[   24.965036] iTCO_vendor_support: vendor-support=0
[   25.053032] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   25.128879] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.343942] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   25.350694] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   25.357678] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.440607] agpgart: Detected an Intel 915GM Chipset.
[   25.447660] agpgart: Detected 7932K stolen memory.
[   25.472719] agpgart: AGP aperture is 256M @ 0xa0000000
[   25.536676] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.590861] input: Power Button (FF) as /devices/virtual/input/input3
[   25.628389] ACPI: Power Button (FF) [PWRF]
[   25.634852] input: Lid Switch as /devices/virtual/input/input4
[   25.656476] ACPI: Lid Switch [LID0]
[   25.662939] input: Power Button (CM) as /devices/virtual/input/input5
[   25.692322] ACPI: Power Button (CM) [PWRB]
[   25.780609] ACPI: AC Adapter [AC] (on-line)
[   25.856425] ACPI: Battery Slot [BAT1] (battery present)
[   25.936528] Yenta: CardBus bridge found at 0000:05:06.0 [1179:ff10]
[   25.942810] Yenta: Enabling burst memory read transactions
[   25.949039] Yenta: Using CSCINT to route CSC interrupts to PCI
[   25.955360] Yenta: Routing CardBus interrupts to PCI
[   25.961640] Yenta TI: socket 0000:05:06.0, mfunc 0x01aa1b22, devctl 0x66
[   26.018386] ieee80211_crypt: registered algorithm 'NULL'
[   26.055962] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   26.062302] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.208376] Yenta: ISA IRQ mask 0x0098, PCI irq 11
[   26.214646] Socket status: 30000006
[   26.220841] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   26.227203] pcmcia: parent PCI bridge I/O window: 0x8000 - 0x9fff
[   26.233528] cs: IO port probe 0x8000-0x9fff: clean.
[   26.240299] pcmcia: parent PCI bridge Memory window: 0xb8000000 - 0xc7ffffff
[   26.246592] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x97ffffff
[   26.487506] intel_rng: FWH not detected
[   26.937820] ACPI: PCI Interrupt 0000:05:06.3[D] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   27.033172] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   27.039446] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   27.046227] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   27.094893] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   27.130862] sdhci: Secure Digital Host Controller Interface driver
[   27.137536] sdhci: Copyright(c) Pierre Ossman
[   27.301186] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   27.334668] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   27.537514] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[   27.544694] synaptics: Toshiba Satellite M45 detected, limiting rate to 40pps.
[   27.607515] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   29.324104] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   29.331636] sdhci: SDHCI controller found at 0000:05:06.4 [104c:8034] (rev 0)
[   29.339290] ACPI: PCI Interrupt 0000:05:06.4[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   29.347030] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   29.356265] mmc0: SDHCI at 0xb800a000 irq 11 DMA
[   29.363986] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it.
[   29.373871] mmc1: SDHCI at 0xb800a100 irq 11 DMA
[   29.381664] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it.
[   29.408723] mmc2: SDHCI at 0xb800a200 irq 11 DMA
[   29.416659] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   29.424783] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   29.424812] sky2 0000:01:00.0: v1.20 addr 0xcc000000 irq 11 Yukon-FE (0xb7) rev 1
[   29.498685] udev: renamed network interface eth0 to eth1
[   29.525282] sky2 0000:01:00.0: No interrupt generated using MSI, switching to INTx mode.
[   29.533857] sky2 eth0: addr 00:a0:d1:bb:ae:17
[   29.542189] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   29.550665] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   29.555132] cs: IO port probe 0x100-0x3af: clean.
[   29.564928] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   29.573949] cs: IO port probe 0x820-0x8ff: clean.
[   29.589884] cs: IO port probe 0xc00-0xcf7: clean.
[   29.601959] cs: IO port probe 0xa00-0xaff: clean.
[   29.621830] ieee80211_crypt: registered algorithm 'WEP'
[   29.766049] intel8x0_measure_ac97_clock: measured 55451 usecs
[   29.774045] intel8x0: clocking to 48000
[   29.924231] lp: driver loaded but no devices found
[   30.141526] Adding 1277128k swap on /dev/sda6.  Priority:-1 extents:1 across:1277128k
[   30.202523] NET: Registered protocol family 17
[   30.635899] device-mapper: uevent: version 1.0.3
[   30.635931] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   31.671127] NET: Registered protocol family 10
[   31.671351] lo: Disabled Privacy Extensions
[   32.608815] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.663199] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   32.758349] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   33.585560] ACPI: Error installing notify handler
[   33.585622] No dock devices found.
[   34.288955] sky2 eth0: enabling interface
[   34.292774] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.320685] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   34.320707] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[   34.624106] ppdev: user-space parallel port driver
[   34.669026] audit(1291977881.203:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5750 profile="/usr/sbin/cupsd" namespace="default"
[   34.746265] eth1: no IPv6 routers present
[   34.798996] sky2 eth0: disabling interface
[   34.863432] apm: BIOS not found.
[   34.887410] spurious 8259A interrupt: IRQ7.
[   35.015305] sky2 eth0: enabling interface
[   35.019337] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   53.818619] Marking TSC unstable due to: cpufreq changes.
[   37.536823] [drm] Initialized drm 1.1.0 20060810
[   75.154626] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   75.154642] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   75.154757] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  291.411910] ACPI: EC: non-query interrupt received, switching to interrupt mode
[  228.069240] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  228.069254] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  228.069256]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  228.069257]          res 41/04:00:00:04:eb/00:00:00:00:00/a0 Emask 0x1 (device error)
[  228.069261] ata2.00: status: { DRDY ERR }
[  228.070832] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  228.070841] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  228.070843]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  228.070844]          res 41/04:00:00:04:eb/00:00:00:00:00/a0 Emask 0x1 (device error)
[  228.070848] ata2.00: status: { DRDY ERR }
[  228.070933] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[  228.070940] sr: Sense Key : Aborted Command [current] [descriptor]
[  228.070944] sr: Add. Sense: No additional sense information
[  228.072909] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  228.072919] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  228.072920]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  228.072922]          res 41/04:00:00:04:eb/00:00:00:00:00/a0 Emask 0x1 (device error)
[  228.072925] ata2.00: status: { DRDY ERR }
[  228.072942] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[  228.072944]    : Sense Key : Aborted Command [current] [descriptor]
[  228.072948]    : Add. Sense: No additional sense information
[  228.233390] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  228.233402] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  228.233404]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  228.233405]          res 41/04:00:00:04:eb/00:00:00:00:00/a0 Emask 0x1 (device error)
[  228.233409] ata2.00: status: { DRDY ERR }
[  228.241912] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[  228.241929] sr: Sense Key : No Sense [current] 
[  228.241932] sr: Add. Sense: No additional sense information
[ 8382.676326] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 8382.676342] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 8382.676343]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 8382.676345]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[ 8382.676349] ata2.00: status: { DRDY }
[ 8382.676386] ata2: soft resetting link
[ 8382.754531] ata2.01: NODEV after polling detection
[ 8382.830615] ata2.00: NODEV after polling detection
[ 8382.830622] ata2.00: revalidation failed (errno=-2)
[ 8382.830627] ata2: failed to recover some devices, retrying in 5 secs
[ 8385.376910] ata2: soft resetting link
[ 8385.615343] ata2.00: configured for UDMA/33
[ 8385.615375] ata2: EH complete
[ 8398.610071] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 8398.610086] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 8398.610088]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 8398.610089]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[ 8398.610093] ata2.00: status: { DRDY }
[ 8398.610130] ata2: soft resetting link
[ 8398.707231] ata2.01: NODEV after polling detection
[ 8398.793048] ata2.00: NODEV after polling detection
[ 8398.793055] ata2.00: revalidation failed (errno=-2)
[ 8398.793060] ata2: failed to recover some devices, retrying in 5 secs
[ 8401.467526] ata2: soft resetting link
[ 8401.719968] ata2.00: configured for UDMA/33
[ 8401.719999] ata2: EH complete
[28302.013736] file-roller[14751]: segfault at 00000130 eip 08077393 esp bf988b80 error 4
[29169.634984] file-roller[16838]: segfault at 00000008 eip 080749f0 esp bffe8f50 error 4
[34179.608603] gnome-panel[7013]: segfault at 6f59bfb2 eip b6f1dbec esp bfb2ac40 error 4
[37672.438570] ipw2200: Firmware error detected.  Restarting.
[59572.322749] ipw2200: Firmware error detected.  Restarting.
[44043.397902] ipw2200: Firmware error detected.  Restarting.
[50529.932730] file-roller[15627]: segfault at 00000130 eip 08077393 esp bf85f470 error 4
[52443.740040] evince[19326]: segfault at 00000008 eip 08084879 esp bf8297f8 error 6
[55172.977985] ipw2200: Firmware error detected.  Restarting.
[57511.368279] file-roller[19307]: segfault at 00000130 eip 08077393 esp bfbd6750 error 4
[58544.603767] audit(1292203833.282:3): type=1503 operation="capable" name="dac_override" pid=15621 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
[58544.603779] audit(1292203833.282:4): type=1503 operation="capable" name="dac_read_search" pid=15621 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
[119260.965316] sky2 eth0: disabling interface
[119260.993629] ACPI: PCI interrupt for device 0000:01:00.0 disabled
[59584.098888] ACPI: PCI interrupt for device 0000:05:04.0 disabled
[59585.089856] PM: suspend-to-disk mode set to 'platform'
[59585.090237] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
[59585.090243] swsusp: Basic memory bitmaps created
[59585.090245] Syncing filesystems ... done.
[59585.096024] Freezing user space processes ... (elapsed 0.00 seconds) done.
[59585.097183] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[59585.097222] Shrinking memory...  -\|/-\|/-\|/-\|/-done (215469 pages freed)
[59587.442463] Freed 861876 kbytes in 13.06 seconds (65.99 MB/s)
[59587.442466] Suspending console(s)
[59587.445296] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[59587.445626] ACPI handle has no context!
[59587.445693] ACPI handle has no context!
[59587.445720] ACPI: PCI interrupt for device 0000:05:06.4 disabled
[59587.445727] ACPI handle has no context!
[59587.445933] ACPI handle has no context!
[59587.445950] ACPI: PCI interrupt for device 0000:05:06.3 disabled
[59587.445957] ACPI handle has no context!
[59587.446176] ACPI handle has no context!
[59587.446625] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[59587.446802] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[59587.447192] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
[59587.447304] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[59587.447508] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[59587.447540] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[59587.447572] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[59587.447603] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[59587.472052] Disabling non-boot CPUs ...
[59587.472246] swsusp: critical section: 
[59587.526975] swsusp: Need to copy 125296 pages
[59587.526979] swsusp: Normal pages needed: 44419 + 1024 + 32, available pages: 184854
[   68.284596] Force enabled HPET at resume
[   68.322621] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   68.322631] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   68.322704] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   68.322766] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   68.322775] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   68.322782] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   68.322831] usb usb1: root hub lost power or was reset
[   68.322851] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   68.322857] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   68.322905] usb usb2: root hub lost power or was reset
[   68.322924] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   68.322931] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   68.322976] usb usb3: root hub lost power or was reset
[   68.322994] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   68.323001] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   68.323047] usb usb4: root hub lost power or was reset
[   68.323672] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   68.323679] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   68.323722] usb usb5: root hub lost power or was reset
[   68.327627] ehci_hcd 0000:00:1d.7: debug port 1
[   68.327633] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   68.327660] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 20050500, writing 20090500)
[   68.327687] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   68.327720] PM: Writing back config space on device 0000:00:1e.2 at offset 1 (was 2900007, writing 2900003)
[   68.327737] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   68.327744] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   68.339263] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   68.339271] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[   68.349227] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b80001, writing 2b00005)
[   68.349246] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   68.349253] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   68.350747] PM: Writing back config space on device 0000:01:00.0 at offset 1 (was 40100007, writing 100003)
[   68.350807] PM: Writing back config space on device 0000:05:04.0 at offset 1 (was 2900006, writing 2900002)
[   68.350835] PM: Writing back config space on device 0000:05:06.0 at offset f (was 3c001ff, writing 5c001ff)
[   68.350861] PM: Writing back config space on device 0000:05:06.0 at offset 3 (was 824000, writing 82a820)
[   68.351189] PM: Writing back config space on device 0000:05:06.2 at offset f (was 4020300, writing 402030b)
[   68.351211] PM: Writing back config space on device 0000:05:06.2 at offset 5 (was 0, writing b8004000)
[   68.351218] PM: Writing back config space on device 0000:05:06.2 at offset 4 (was 0, writing b8000000)
[   68.351224] PM: Writing back config space on device 0000:05:06.2 at offset 3 (was 800000, writing 808004)
[   68.351232] PM: Writing back config space on device 0000:05:06.2 at offset 1 (was 2100000, writing 2100006)
[   68.400842] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   68.401272] ACPI: PCI Interrupt 0000:05:06.3[D] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   68.401492] ACPI: PCI Interrupt 0000:05:06.4[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   68.447235] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[   68.447239] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[   68.452824] ata1.00: configured for UDMA/100
[   68.452862] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   68.452875] sd 0:0:0:0: [sda] Write Protect is off
[   68.452878] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   68.452895] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   68.458437] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[   68.458440] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[   68.460850] ata2.00: configured for UDMA/33
[   68.527315] sd 0:0:0:0: [sda] Starting disk
[   68.532249] PM: Image restored successfully.
[   68.581902] Restarting tasks ... done.
[   68.596866] swsusp: Basic memory bitmaps freed
[  140.394415] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  140.394424] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  140.436558] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  140.436567] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  140.437340] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  140.439203] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   70.269451] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  140.789610] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  140.789638] PCI: Setting latency timer of device 0000:01:00.0 to 64
[  140.789679] sky2 0000:01:00.0: v1.20 addr 0xcc000000 irq 11 Yukon-FE (0xb7) rev 1
[  140.801678] sky2 0000:01:00.0: No interrupt generated using MSI, switching to INTx mode.
[  140.802949] sky2 eth1: addr 00:a0:d1:bb:ae:17
[   71.884644] eth0: no IPv6 routers present
[  380.289856] eth0: no IPv6 routers present
[  623.761642] eth0: no IPv6 routers present
[  637.516791] eth0: no IPv6 routers present
[  654.848016] eth0: no IPv6 routers present
[  678.027909] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[  678.203582] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  678.236926] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  681.057740] eth0: no IPv6 routers present
[  687.231779] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[  343.429284] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  343.465870] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  691.399393] eth0: no IPv6 routers present
[  756.584682] eth0: no IPv6 routers present
[  997.855684] eth0: no IPv6 routers present
[ 1000.323007] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1002.502679] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 1002.738098] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1005.918656] eth0: no IPv6 routers present
[ 1054.692776] eth0: no IPv6 routers present
[ 1066.040917] eth0: no IPv6 routers present
[ 1106.352419] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  831.741712] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  661.393688] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  679.210600] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  679.210607] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  679.210611] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[ 1420.598975] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 1420.801605] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1078.483667] eth0: no IPv6 routers present
[ 1859.909151] eth0: no IPv6 routers present
[ 1877.424222] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1878.719002] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 1878.885036] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1882.655423] eth0: no IPv6 routers present
```

---

### Post by HotForLinux on 2010-12-19
*bump*

---

