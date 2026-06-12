---
title: "Reducing CPU Usage"
date: 2010-05-25
forum: General Help
---

### Post by Hunter Morrell on 2010-05-25
I noticed earlier that my CPU usage is hovering around 70% when I'm just on FF, not doing much of anything. Yet, when I try to watch Hulu, it shoots up around 90%, even going as high as 98%. I'm a bit concerned about that, so is there any way I can significantly lower my CPU usage?

---

### Post by linuxman94 on 2010-05-25
Do you know the specs on your machine?  If so, post them here.  Also post the results of this command.

```
top
```

---

### Post by cmileto on 2010-05-25
turn off the extra effects for the window manager if you need to save cpu, although imo if its not lagging or skipping why bother?

---

### Post by s3a on 2010-05-25
Are you using flash?

---

### Post by jerenept on 2010-05-25
Flash = plenty CPU. Try the youtube html5 beta. It will surprise you.

---

### Post by linuxman94 on 2010-05-25
> **jerenept said:**
> Flash = plenty CPU. Try the youtube html5 beta. It will surprise you.

You can't use the HTML5 beta with firefox because of the codec youtube uses.

---

### Post by Hunter Morrell on 2010-05-25
> **linuxman94 said:**
> Do you know the specs on your machine?  If so, post them here.  Also post the results of this command.

```
top
```

@linuxman94: I'm a bit new to Ubuntu (been using it for about a month and a half, if even that much) so I don't exactly know how to get my specs.

```
top - 22:30:50 up 11:54,  1 user,  load average: 1.12, 1.45, 1.64
Tasks: 171 total,   1 running, 169 sleeping,   0 stopped,   1 zombie
Cpu(s): 16.6%us,  7.0%sy,  0.3%ni, 75.8%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   2311968k total,  2002024k used,   309944k free,   122604k buffers
Swap:   610428k total,      720k used,   609708k free,  1323716k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 1787 hunter    20   0  508m 173m  38m S 10.9  7.7 311:19.49 firefox-bin                                                     
  878 root      20   0 74460  37m  22m S  6.6  1.6  52:38.83 Xorg                                                            
 1340 hunter    20   0 65416  22m  12m S  2.7  1.0   0:03.79 python                                                          
 1330 hunter    20   0 91504  26m 9380 S  1.7  1.2  12:11.77 compiz                                                          
10259 hunter    20   0  2544 1208  900 R  0.7  0.1   0:00.04 top                                                             
 1522 hunter    20   0 16528  11m 3884 S  0.3  0.5   1:20.74 desktopcouch-se                                                 
 1568 hunter    20   0 31780  18m 4164 S  0.3  0.8   1:31.45 ubuntuone-syncd                                                 
 1688 hunter    30  10 17032  10m 2380 S  0.3  0.5   1:15.09 desktopcouch-se                                                 
    1 root      20   0  2804 1536 1164 S  0.0  0.1   0:00.56 init                                                            
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0                                                     
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.27 events/0                                                        
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset                                                          

```

@cmileto: I have most of the effects turned off because I'm not really into all that eye-candy anyway. The main stuff I kept was for practicality.


@s3a: I downloaded two plug-ins for FF earlier. Flashblock and Adblock Plus is what they were, I believe.

---

### Post by linuxman94 on 2010-05-25
Is the top result from when you have hulu playing?

---

### Post by Hunter Morrell on 2010-05-25
No. I don't even have Hulu open at the moment.

---

### Post by linuxman94 on 2010-05-25
Could you post the result while you have hulu playing?

Post the output of this command please.

```
sudo lshw
```

---

### Post by Hunter Morrell on 2010-05-25
```
top - 22:54:32 up 12:18,  1 user,  load average: 1.68, 1.36, 1.33
Tasks: 170 total,   2 running, 167 sleeping,   0 stopped,   1 zombie
Cpu(s): 85.5%us, 12.5%sy,  0.3%ni,  0.7%id,  0.0%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:   2311968k total,  2050600k used,   261368k free,   124408k buffers
Swap:   610428k total,      720k used,   609708k free,  1343064k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
10338 hunter    20   0  593m 210m  40m R 72.8  9.3   3:45.35 firefox-bin                                                     
  878 root      20   0 92288  41m  26m S 13.2  1.8  54:20.47 Xorg                                                            
 1330 hunter    20   0 91504  26m 9380 S  5.6  1.2  12:37.03 compiz                                                          
 1340 hunter    20   0 65580  22m  13m S  3.0  1.0   0:06.24 python                                                          
 1375 hunter     9 -11  148m 5476 4296 S  3.0  0.2  22:28.65 pulseaudio                                                      
  657 mysql     20   0  142m  17m 5440 S  0.7  0.8   0:24.08 mysqld                                                          
10619 hunter    20   0  2544 1208  900 R  0.7  0.1   0:00.05 top                                                             
   19 root      20   0     0    0    0 S  0.3  0.0   0:15.91 ata/0                                                           
   36 root      20   0     0    0    0 S  0.3  0.0   0:57.31 scsi_eh_0                                                       
 1477 hunter    20   0 25300  11m 9464 S  0.3  0.5   0:44.00 multiload-apple                                                 
 1522 hunter    20   0 16528  11m 3884 S  0.3  0.5   1:23.11 desktopcouch-se                                                 
 1688 hunter    30  10 17032  10m 2380 S  0.3  0.5   1:17.54 desktopcouch-se                                                 
    1 root      20   0  2804 1536 1164 S  0.0  0.1   0:00.57 init                                                            
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     

```


```
hunter                    
    description: Mini Tower Computer
    product: 8195A1U
    vendor: IBM
    serial: KCW0XTG
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific chassis=mini-tower cpus=1 keyboard_password=enabled power-on_password=disabled uuid=E6A3B928-497C-2612-B4ED-A0B445D88650
  *-core
       description: Motherboard
       product: IBM
       vendor: IBM
       physical id: 0
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 2AKT31AUS (10/07/2003)
          size: 110KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot edd acpi usb agp ls120boot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: WMT478/NWD
          size: 2400MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 8KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 2304MiB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: J4
             size: 128MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             physical id: 1
             slot: J5
             size: 128MiB
             width: 64 bits
        *-bank:2
             description: DIMM DDR Synchronous
             physical id: 2
             slot: J15
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM DDR Synchronous
             physical id: 3
             slot: J16
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:ec000000-efffffff(prefetchable)
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff(prefetchable) memory:e8000000-e807ffff ioport:1800(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e8080000-e80803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:2000(size=4096) memory:e8100000-e81fffff
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth0
                version: 02
                serial: 00:09:6b:af:9e:19
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.100 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:20 memory:e8110000-e8110fff ioport:2000(size=64)
           *-communication UNCLAIMED
                description: Communication controller
                product: Conexant Systems, Inc.
                vendor: Conexant Systems, Inc.
                physical id: a
                bus info: pci@0000:03:0a.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: memory:e8100000-e810ffff ioport:2040(size=8)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:90000000-900003ff
           *-cdrom:0
                description: DVD-RAM writer
                product: DVD Writer 840d
                vendor: HP
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HPD5
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio cd-r cd-rw
                configuration: status=nodisc
           *-disk
                description: ATA Disk
                product: QUANTUM FIREBALL
                vendor: Quantum
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: A3F.
                serial: 134916070305
                size: 12GiB (13GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00056e39
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: b2df690d-8b12-453a-a75c-8dd018cd343d
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-04-22 17:22:56 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Z&#65533;&#65533;&#65533;&#2001;&#65533;p^&#65533;&#65533;u^ &#65533;U/&#65533;d^&#65533;&#65533;~!&#65533;&#65533;I&#65533;&#65533;&#65533;I&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^&#65533;&#65533;^&#65533;&#65533;a modified=2010-05-22 10:00:15 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-25 10:36:34 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 596MiB
                   capacity: 596MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 596MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:1c00(size=256) ioport:18c0(size=64) memory:e8080c00-e8080dff memory:e8080800-e80808ff
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound

```

---

### Post by linuxman94 on 2010-05-25
Yeah, that's what I expected.  The problem is that flash uses a LOT of processing power and memory.  You can have a look [here]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html") and that may help.

---

