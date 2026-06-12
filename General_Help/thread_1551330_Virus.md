---
title: "Virus?"
date: 2010-08-12
forum: General Help
---

### Post by Feilin on 2010-08-12
I've been experiencing a few problems with my Ubuntu 10.04, and I'm suspecting a virus in my system (if such things do exist?). The main issues I've discovered so far are;

Very high use of CPU for seemingly no reason. When I'm just browsing the net or something, it starts buzzing and everything slows down and responds after a few seconds (clicking a link etc). Oddly enough, when I bring up the system monitor, it seems to go away, so I don't know if or what program is the cause. Sometimes when I leave it on though, I can follow the curve going up and down from 0-100, but at those times, it seems like it's the monitor itself that uses the CPU.

My kMess starts receiving messages with virus links from offline contacts (different, but same messages).

iBus and VLC are also behaving weird and freezes at times. Usually they wont respond to just right clicking and exiting, so I have to do it through the system manager and kill the processes.

For some reason, Java is not working properly either, and when I want to watch youtube, it sometimes doesn't show anything, sometimes it's dark and flashes with some picture, and sometimes I get only sound.

(Granted, the three last ones aren't necessarily a virus, maybe just faulty programming or integration, or simply not correctly installed, I don't know, but they‘re still problems for me. As for the first one, I don't know why it takes up all the CPU)

What should I do to heal my computer?

---

### Post by elliotn on 2010-08-12
FireFox
Java
Flash
This may coz hi cpu usage

---

### Post by Rubi1200 on 2010-08-12
Hi,
in all honesty nothing you have described sounds like the work of a virus.

What is more likely; not enough RAM, issues with Flash or Java, Compiz running etc.

Go to Applications > Accessories > Terminal and type this in
```
top
```
Post the results back here please.

---

### Post by DrMelon on 2010-08-12
It's highly unlikely you have a virus, as there aren't very many for Linux, and most are targeted at businesses and servers and also you would have to enter your password to allow it to do some serious damage.

It sounds more likely to be a driver issue or hardware incompatibility. 

Additionally, did you update to Ubuntu 10.04 from 9.10? This sometimes causes problems.

Messages that include virus links are more likely to be from infected contacts rather than from your own computer - generally, they attempt to spread through your contacts list, but as long as you haven't managed to find one that runs on Linux you should be okay.

If you're still worried about it, install ClamAV from the Ubuntu repositories and scan for viruses using it. I think there is a GUI version available.

I've had instability issues with VLC before - make sure you have the latest version, and that the video/audio files you're playing aren't broken or anything. Look for patterns in the crashes, and you might be able to find the problem. Also, you can try running it from a terminal - this will print error messages and such to the terminal while VLC is running, and will help you to diagnose the problem.

As for youtube's problems, make sure you have the latest version of whichever flash player you're using.

All I can really suggest for Java is, once again, check it's fully updated.


If problems persist and get really bad, and there is no virus, it may be best to reinstall Ubuntu (an extreme solution, as it may be) or check your hardware for malfunctions.


Could you give us your specs also?

---

### Post by Feilin on 2010-08-12
I don't know what the reason is, maybe it's something I've failed to realise during installation or something. Though the problems have come gradually, they seldom happen at the same time. I'm thinking about just reinstalling my system to make sure it's clean and nice.

Still, here's the top command punched into Terminal:


top - 12:26:53 up  4:52,  2 users,  load average: 0.63, 0.62, 0.61
Tasks: 179 total,   1 running, 178 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.3%us,  3.8%sy,  0.0%ni, 82.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3092048k total,  1558820k used,  1533228k free,   161648k buffers
Swap:  7735256k total,        0k used,  7735256k free,   706688k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3754 fredrik   20   0 55676  15m  10m S   12  0.5   0:02.09 gnome-terminal     
  972 root      20   0 84276  69m  14m S    9  2.3  25:56.81 Xorg               
 2791 fredrik   20   0  450m 175m  32m S    7  5.8  25:18.79 firefox-bin        
 3010 fredrik   20   0  201m  51m  23m S    4  1.7   8:31.71 skype              
 1467 fredrik   20   0 72912  54m  16m S    3  1.8   5:15.54 compiz             
 1246 rtkit     21   1 22904 1220 1020 S    0  0.0   0:00.04 rtkit-daemon       
    1 root      20   0  2804 1664 1200 S    0  0.1   0:00.66 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.13 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      20   0     0    0    0 S    0  0.0   0:01.71 events/0           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr          
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm

---

### Post by dino99 on 2010-08-12
keep in mind that errors logged can be usefull to tweak your system

goto system admin logviewer and into /home: .xsession-errors (ctrl+h to unhide it)

---

### Post by Feilin on 2010-08-12
Yeah, I kinda suspected it might've been the update from 9.10. Actually, it was from 9.04->9.10->10.04 (since I only have a live CD for 9.04). I should probably download 10.04 and burn a live CD.

I'm not quite sure what specs exactly, but in the systems tab in the system monitor it says:
10.04 (lucid)
Linux 2.6.32-24-generic
GNOME 2.30.2

2,9 GiB
Pentium(R) Dual-Core CPU T4200 @ 2.00GHz
Pentium(R) Dual-Core CPU T4200 @ 2.00GHz

---

### Post by Rubi1200 on 2010-08-12
You can get information on your hardware using this command in the terminal:

```
lshw
```

In many instances, a fresh install is better than upgrading simply because it means you start with a fresh slate (no old issues lurking in the background).

Make sure you backup any important files before taking the step of a fresh install.

---

### Post by Feilin on 2010-08-12
Yes, I follow that logic. Hopefully I'll be able to remember to backup before eventual reinstallation. Why does it say I only have 32 bits btw? and 3019 MiB memory? I was told that with ubuntu it doesn't matter how much memory and CPU speed you have, the system will adapt... Maybe the problem has something to do with me having installed the wrong version in the first place?

    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3019MiB
     *-cpu
          product: Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:f0000000-f2ffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G98M [GeForce G 105M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f2000000-f2ffffff memory:d0000000-dfffffff(prefetchable) memory:f0000000-f1ffffff ioport:2000(size=128)
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1820(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:f3404800-f3404bff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:21 memory:f3400000-f3403fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:f3000000-f30fffff memory:c0000000-c01fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: NetLink BCM5784M Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: 00:1f:16:ab:6d:2b
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v2.19 ip=213.66.11.166 latency=0 multicast=yes
                resources: irq:30 memory:f3000000-f300ffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:5000(size=4096) memory:c0200000-c03fffff memory:c0400000-c05fffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:6000(size=4096) memory:f3100000-f31fffff memory:c0600000-c07fffff(prefetchable)
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: 00:17:c4:99:c5:c4
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 memory:f3100000-f310ffff
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:3000(size=4096) memory:f4000000-f5ffffff ioport:f6000000(size=33554432)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1840(size=32)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1860(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1880(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18a0(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f3404c00-f3404fff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:18f0(size=8) ioport:18e4(size=4) ioport:18e8(size=8) ioport:18e0(size=4) ioport:18c0(size=32) memory:f3404000-f34047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0800000-c08000ff ioport:1c00(size=32)

---

