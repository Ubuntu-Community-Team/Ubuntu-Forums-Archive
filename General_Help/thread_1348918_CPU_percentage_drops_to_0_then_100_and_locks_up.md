---
title: "CPU percentage drops to 0 then 100 and locks up"
date: 2009-12-07
forum: General Help
---

### Post by ghostandmachine on 2009-12-07
Hello,

I've been having a problem with lock ups on my Ubuntu 8.04 for the past month or so. Only lately has it really become an unbearable issue.

Linux ubuntu 2.6.24-26-rt #1 SMP PREEMPT RT Tue Dec 1 20:53:25 UTC 2009 i686 GNU/Linux


I've completely updated my system as of one hour ago. The lock ups usually occoure while using VLC or Firefox. Every once in a while it'll happen on my Ktorrent app.

Using VLC, after about ten to twenty minutes, the CPU usage will drop to 0% then rise to 100% causing the computer to lock up. The computer will lock up (playing the last sound over and over completely annoying) without any keyboard or mouse action. The lock up usually lasts about five minutes then returns to normal. It seems to last longer on VLC (or mplayer and totem) than with Firefox and Ktorrent.

No other programs are running (other than system apps)

With Firefox I thought it was flash that was causing the lock ups. After reinstalling flash many times, it started to lock up while using VLC. So I ruled out my flash idea.

Any help would be great. Thanks in advance. Below are my sys specs.

p.s. My computer locked up three times trying to type this message. :(

```
 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 2897MiB
     *-cpu
          product: AMD Sempron(tm) Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 6
          bus info: cpu@0
          version: 15.15.2
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up pni cx16 lahf_lm extapic cr8_legacy ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: vga_controller bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
        *-network:0 DISABLED
             description: Ethernet interface
             product: BCM4401-B0 100Base-TX
             vendor: Broadcom Corporation
             physical id: 7
             bus info: pci@0000:04:07.0
             logical name: eth0
             version: 02
             serial: 00:13:72:30:f1:89
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
        *-network:1
             description: Wireless interface
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications Inc.
             physical id: 8
             bus info: pci@0000:04:08.0
             logical name: wifi0
             version: 01
             serial: 00:11:50:d5:2b:6f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci ip=192.168.11.8 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-firewire
             description: FireWire (IEEE 1394)
             product: IEEE 1394 Host Controller
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@0000:04:09.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage

```

---

### Post by u.b.u.n.t.u on 2009-12-07
Just a casual observation, why is your RAM being reported as "UNCLAIMED"?

---

### Post by ghostandmachine on 2009-12-07
That's strange. It's Kingston memory. I installed it about a year ago.

---

### Post by ghostandmachine on 2009-12-20
Update

So i've been doing some testing and here's what i've discovered.

1. Having either Ktorrent or Deludge open while playing a video will cause the computer to lock up

2. If I completely close the torrent app, computer does not lock up.

3. If Ktorrent or Deludge is open, while I try to either delete torrents or configure some other options, the computer will lock up.

4. If I'm on Firefox or Chrome, and downloading a file with no other apps open, the computer will lock up.

So I've come to the conclusion that there has to be a connect between upload/download speed to the rest of my computer. I've never had this problem before and have always been up to date.

Any ideas would be great for a work around. How am I suppose to watch my DVDs and upload Ubuntu isos at the same time?!

---

### Post by zackiv31 on 2009-12-20
I have a similar lockup issue with Karmic Koala and Deluge freezing... no idea why...

---

### Post by ghostandmachine on 2009-12-20
> **zackiv31 said:**
> I have a similar lockup issue with Karmic Koala and Deluge freezing... no idea why...

I'm sorry to hear that you're having similar problems but relieved that I'm not the only one. 

If you're running Koala then it's not a kernel issue. What version of deluge are you running?

I'm running 0.5.8.9 which is the only available version for Hardy.

---

### Post by ghostandmachine on 2009-12-24
bump

---

### Post by chewearn on 2009-12-24
I have a similar system as yours, AMD+NVIDIA GeForce6150 motherboard.  Over the years, I have experienced random lock-ups; total system freeze which require power unplug.

I finally traced to problem to either:
1. a faulty motherboard integrated network port (hardware defect).
2. a strange incompatibility between linux driver of the network port.
3. network hardware overheating.

Whenever there is a large amount of network traffic, the computer would eventually freeze mid-transfer.

Temporarily, I found a USB-to-Ethernet dongle.  I turned off the BIOS switch for motherboard integrated network port.  Since this change, the problem has not recurred, which confirmed the source of the problem (but not the root cause).

Since then, I have bought a PCI network card to serve as the network port (the USB dongle is only 10BaseT), and the computer has been rock solid.

---

### Post by ghostandmachine on 2010-01-04
thank you so much for your advice and fix

i'll be purchasing a new network pci card soon in hopes it will also fix my problem.

will return with update.

---

### Post by ghostandmachine on 2010-01-06
i bought a new wireless card for my desktop and i'm still having problems with lock ups. i tried a different pci slot with no luck. 

So i'm thinking its the motherboard (oh no) or a bug in ubuntu that is hardware specific. 

any other ideas or advice is welcome

---

