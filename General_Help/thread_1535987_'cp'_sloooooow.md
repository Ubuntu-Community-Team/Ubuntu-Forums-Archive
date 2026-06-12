---
title: "'cp' sloooooow"
date: 2010-07-21
forum: General Help
---

### Post by janthes on 2010-07-21
Hi all,

I'm running a 10.4 server on my LAN which at one point, I was able to copy flac albums (for example) disk-to-disk in a matter of seconds, whereas now it's taking about 15-20 minutes. The 'w' command is showing a load of 2.* to 3.* on a single core Sempron during the transfers, and 'top' shows cp as using 0.1-10.0% cpu and 0.1% memory.

I have no idea were/how to proceed in diagnosing this (still relatively noobish). Help would be gratefully appreciated!!

Extra info:

uname -a:
```
Linux server 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
```

lshw:
```

server                    
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: N68-S
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.30 (04/10/2009)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor LE-1150
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.15.1
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm extapic cr8_legacy 3dnowprefetch
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:900(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:dc00(size=64) ioport:600(size=64) ioport:700(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fbcff000-fbcfffff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fbcfec00-fbcfecff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
          resources: ioport:e000(size=4096) memory:fbd00000-fbffffff memory:40000000-400fffff(prefetchable)
        *-network:0
             description: Ethernet interface
             product: 82557/8/9/0/1 Ethernet Pro 100
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:01:08.0
             logical name: eth1
             version: 08
             serial: 00:90:27:99:a8:c2
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A ip=192.168.0.1 latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
             resources: irq:19 memory:fbfff000-fbffffff ioport:ec00(size=64) memory:fbe00000-fbefffff memory:40000000-400fffff(prefetchable)
        *-network:1
             description: Wireless interface
             product: Atheros AR5001X+ Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: a
             bus info: pci@0000:01:0a.0
             logical name: wlan0
             version: 01
             serial: 00:1c:f0:9d:98:25
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
             resources: irq:18 memory:fbfe0000-fbfeffff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-disk
             description: ATA Disk
             product: Maxtor 6Y080P0
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: YAR4
             serial: Y22JPFFC
             size: 76GiB (81GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000e68dd
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: caf86412-1a9d-4ae0-9e13-7435bde87f8c
                size: 73GiB
                capacity: 73GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-07-13 16:30:29 filesystem=ext4 lastmountpoint=/&#65533;&#65533;+|&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p>&#65533;&#65533;&#65533;g &#65533;-]/&#65533;d>&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;>&#65533;&#65533;>&#65533;&#65533;j modified=2010-07-13 16:44:41 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-07-20 13:07:59 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2886MiB
                capacity: 2886MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2886MiB
                   capabilities: nofs
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW TS-H652M
             vendor: TSSTcorp
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 0414
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:19:66:cf:98:ca
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:27 memory:fbcfd000-fbcfdfff ioport:d480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=16) memory:fbcfc000-fbcfcfff
        *-disk:0
             description: ATA Disk
             product: SAMSUNG HD203WI
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1AN1
             serial: S1UYJ1MZ205822
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=1a84eb64-6a80-4d1d-b9d6-8f0de321a9eb
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/netshare
                version: 1.0
                serial: 55805edc-26eb-4c41-8836-7ce5bdbad493
                size: 1863GiB
                capacity: 1863GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-05-10 13:35:07 filesystem=ext4 lastmountpoint=/media/netshare&#65533;&#65533;&#65533;,&#65533;5&#65533;&#65533;(d&#65533;&#65533;&#65533;O&#65533;d6&#65533;&#65533;g &#65533;&#482;&#65533;@&#65533;&#65533; &#65533;&#65533; &#65533;&#65533; &#65533; modified=2010-07-20 13:08:00 mount.fstype=ext4 mount.options=rw,sync,nosuid,nodev,noexec,relatime,barrier=1,data=ordered mounted=2010-07-20 13:08:00 state=mounted
        *-disk:1
             description: ATA Disk
             product: ST31500341AS
             vendor: Seagate
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc
             version: SD19
             serial: 9VS0FA0V
             size: 1397GiB (1500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=44cb44ca
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/backups
                version: 1.0
                serial: 9eeacb9d-b602-4a2f-a8d0-02eeca4e947f
                size: 1397GiB
                capacity: 1397GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-02-21 16:51:16 filesystem=ext4 lastmountpoint=/media/torrentsa&#65533;8&#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;;&#65533;^=&#65533;&#65533;g &#65533;-]/&#65533;&#65533;^=&#65533;&#65533;!&#65533;&#65533;b&#560;b modified=2010-07-20 13:08:00 mount.fstype=ext4 mount.options=rw,sync,nosuid,nodev,noexec,relatime,barrier=1,data=ordered mounted=2010-07-20 13:08:00 state=mounted
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          logical name: scsi5
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=16) memory:fbcf7000-fbcf7fff
        *-disk
             description: ATA Disk
             product: ST3320833AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdd
             version: 3.AA
             serial: 9NF0FAWL
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=6160cd12
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/transmission
                version: 1.0
                serial: f1e37503-d27b-44a2-9982-d153cd05f2bf
                size: 298GiB
                capacity: 298GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-06-26 17:29:46 filesystem=ext4 lastmountpoint=/media/transmission5u&#65533;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;(0&#65533;9P&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;g &#65533;&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;c&#65533;&#65533;&#65533;$ modified=2010-07-20 13:08:01 mount.fstype=ext4 mount.options=rw,sync,nosuid,nodev,noexec,relatime,barrier=1,data=ordered mounted=2010-07-20 13:08:01 state=mounted
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 7025 / nForce 630a]
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:22 memory:fa000000-faffffff memory:e0000000-efffffff(prefetchable) memory:f9000000-f9ffffff memory:fbcc0000-fbcdffff(prefetchable)
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

```

---

### Post by prodigy_ on 2010-07-21
Probably something is wrong with your network connection so some diagnostics will be needed. First of all - do you use wired or wireless connection?

---

### Post by janthes on 2010-07-21
Thanks for the reply prodigy!

At the moment I'm using Ethernet (eth0). The extra NICs are planned for converting the server to a gateway / AP.

---

### Post by prodigy_ on 2010-07-21
Alright. Do some network copying now, then open terminal and use the following commands: ```
sudo ethtool eth0
sudo ethtool -S eth0
netstat -s eth0
```
Post the output here.

---

### Post by janthes on 2010-07-21
sudo ethtool eth0:

```
 
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

```

sudo ethtool -S eth0:

```
NIC statistics:
     tx_bytes: 11735724558
     tx_zero_rexmt: 10491528
     tx_one_rexmt: 0
     tx_many_rexmt: 0
     tx_late_collision: 0
     tx_fifo_errors: 0
     tx_carrier_errors: 0
     tx_excess_deferral: 0
     tx_retry_error: 0
     rx_frame_error: 0
     rx_extra_byte: 0
     rx_late_collision: 0
     rx_runt: 0
     rx_frame_too_long: 0
     rx_over_errors: 0
     rx_crc_errors: 0
     rx_frame_align_error: 0
     rx_length_error: 0
     rx_unicast: 8928664
     rx_multicast: 839
     rx_broadcast: 1311
     rx_packets: 8930814
     rx_errors_total: 0
     tx_errors_total: 0
     tx_deferral: 0
     tx_packets: 10491528
     rx_bytes: 4068884942
     tx_pause: 0
     rx_pause: 0
     rx_drop_frame: 70
     tx_unicast: 422650
     tx_multicast: 153512
     tx_broadcast: 509076735222

```

netstat -s eth0:

```
Ip:
    9045630 total packets received
    0 forwarded
    0 incoming packets discarded
    9045584 incoming packets delivered
    10608660 requests sent out
Icmp:
    5571 ICMP messages received
    591 input ICMP message failed.
    ICMP input histogram:
        destination unreachable: 2852
        timeout in transit: 60
        echo requests: 330
        echo replies: 2329
    25932 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
        destination unreachable: 23273
        echo request: 2329
        echo replies: 330
IcmpMsg:
        InType0: 2329
        InType3: 2852
        InType8: 330
        InType11: 60
        OutType0: 330
        OutType3: 23273
        OutType8: 2329
Tcp:
    90546 active connections openings
    143637 passive connection openings
    40222 failed connection attempts
    19565 connection resets received
    39 connections established
    9006261 segments received
    10239297 segments send out
    333160 segments retransmited
    109 bad segments received.
    116014 resets sent
Udp:
    10403 packets received
    23269 packets to unknown port received.
    21 packet receive errors
    10271 packets sent
UdpLite:
TcpExt:
    70263 invalid SYN cookies received
    220 resets received for embryonic SYN_RECV sockets
    621 packets pruned from receive queue because of socket buffer overrun
    9 ICMP packets dropped because they were out-of-window
    67981 TCP sockets finished time wait in fast timer
    895 packets rejects in established connections because of timestamp
    227191 delayed acks sent
    54 delayed acks further delayed because of locked socket
    Quick ack mode was activated 28493 times
    874 times the listen queue of a socket overflowed
    874 SYNs to LISTEN sockets dropped
    1145 packets directly queued to recvmsg prequeue.
    188561 bytes directly received in process context from prequeue
    2361019 packet headers predicted
    2446116 acknowledgments not containing data payload received
    2805476 predicted acknowledgments
    124 times recovered from packet loss due to fast retransmit
    61537 times recovered from packet loss by selective acknowledgements
    45 bad SACK blocks received
    Detected reordering 7 times using FACK
    Detected reordering 43 times using SACK
    Detected reordering 18 times using time stamp
    33 congestion windows fully recovered without slow start
    39 congestion windows partially recovered using Hoe heuristic
    119 congestion windows recovered without slow start by DSACK
    17254 congestion windows recovered without slow start after partial ack
    87324 TCP data loss events
    TCPLostRetransmit: 5452
    117 timeouts after reno fast retransmit
    14808 timeouts after SACK recovery
    8996 timeouts in loss state
    117063 fast retransmits
    2647 forward retransmits
    58590 retransmits in slow start
    66620 other TCP timeouts
    65 classic Reno fast retransmits failed
    9684 SACK retransmits failed
    66814 packets collapsed in receive queue due to low socket buffer
    32873 DSACKs sent for old packets
    76 DSACKs sent for out of order packets
    17945 DSACKs received
    613 DSACKs for out of order packets received
    37455 connections reset due to unexpected data
    2880 connections reset due to early user close
    26649 connections aborted due to timeout
    TCPSACKDiscard: 21
    TCPDSACKIgnoredOld: 2583
    TCPDSACKIgnoredNoUndo: 3987
    TCPSpuriousRTOs: 274
    TCPSackShiftFallback: 644884
IpExt:
    InMcastPkts: 430
    OutMcastPkts: 28
    InBcastPkts: 1325
    OutBcastPkts: 707
    InOctets: -356189466
    OutOctets: -1305563256
    InMcastOctets: 94059
    OutMcastOctets: 4763
    InBcastOctets: 236524
    OutBcastOctets: 162545

```

---

### Post by prodigy_ on 2010-07-21
I'd say everything looks normal...

Just to clarify: do you have a problem with copying files over the network (from one PC to another) or locally (from one HDD to another on the same PC)? Since you mentioned it's a server, I assumed the former.

---

### Post by janthes on 2010-07-21
It's disk-to-disk (internal). I login with ssh and do my CLI thing.

I started to think myself that it couldn't be a network connection because I'm able to access the server's services (smb, nfs, sshfs) with no noticeable impact on the server's load (0.17, 0.07, 0.06 ATM). 

I think it has something to do with cp, or perhaps a controller issue (hopefully the former).

---

### Post by prodigy_ on 2010-07-21
> **janthes said:**
> It's disk-to-disk (internal).
Sorry, my bad then.

In this case, can you provide more info about your server? Do you have any RAID setup there?

---

### Post by janthes on 2010-07-21
> **prodigy_ said:**
> Sorry, my bad then.

Don't sweat it. :)

I don't have RAID implemented:

```

james@server:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G  3.6G   66G   6% /
none                  489M  204K  489M   1% /dev
none                  494M     0  494M   0% /dev/shm
none                  494M  340K  493M   1% /var/run
none                  494M     0  494M   0% /var/lock
none                  494M     0  494M   0% /lib/init/rw
/dev/sdb1             1.9T  812G  1.1T  44% /media/netshare
/dev/sdc1             1.4T  985G  322G  76% /media/backups
/dev/sdd1             294G  278G   16G  95% /media/transmission

```

---

### Post by prodigy_ on 2010-07-21
Well, if there's no raid, you probably should start with checking the disks (source and target).

Go to the manufacturer website, download their official diagnostic tool and use it. There should be a bootable CD version - you will probably need this one.

---

