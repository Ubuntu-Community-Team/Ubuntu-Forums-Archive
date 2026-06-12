---
title: "AMD Athlon XP 3200+ consistently at 99% usage"
date: 2011-06-12
forum: General Help
---

### Post by hellhounds88 on 2011-06-12
Hi all,

I've Googled the heck out of this problem, but I can't seem to find a solution that works for me. I have a desktop PC that I built back when I was a teenager, running Ubuntu 10.04 LTS and nothing else. I love it, but for one thing: the dang CPU usage hits at least 99% whenever any application besides Xorg is open and running. This doesn't affect performance too much, but if Windows XP Home Edition never gets close to 100% usage, then I figure there's something going on.

sudo lshw returns:
```
dan-desktop               
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: MS-6570E
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (08/16/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 2200MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MiB
        *-bank:2
             description: DIMM
             physical id: 2
             slot: A2
             size: 512MiB
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia
          resources: irq:0 memory:e4000000-e7ffffff(prefetchable)
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP2A ISA bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP2A SMBus
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:3 ioport:c400(size=32)
        *-usb:0
             description: USB Controller
             product: MCP2A USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:eb001000-eb001fff
        *-usb:1
             description: USB Controller
             product: MCP2A USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:eb002000-eb002fff
        *-usb:2
             description: USB Controller
             product: MCP2A USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:eb003000-eb0030ff
        *-bridge
             description: Ethernet interface
             product: MCP2A Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: a3
             serial: 00:11:09:8f:84:ee
             size: 100000000
             capacity: 1000000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.5 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
             resources: irq:20 memory:eb000000-eb000fff ioport:c000(size=8)
        *-multimedia
             description: Multimedia audio controller
             product: MCP2S AC'97 Audio Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
             resources: irq:21 ioport:b800(size=256) ioport:bc00(size=128) memory:eb004000-eb004fff
        *-pci:0
             description: PCI bridge
             product: MCP2A PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=4096) memory:e8000000-e8ffffff
           *-network UNCLAIMED
                description: Network controller
                product: ACX 111 54Mbps Wireless Interface
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: memory:e8020000-e8021fff memory:e8000000-e801ffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32
                resources: irq:19 memory:e8022000-e80227ff ioport:9000(size=128)
        *-ide:0
             description: IDE interface
             product: MCP2A IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: scsi1
             logical name: scsi2
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-cdrom:0
                description: DVD writer
                product: DVDRW SOHW-1673S
                vendor: LITE-ON
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: JS02
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW SOHR-5238S
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 4S06
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: ST380011A
                vendor: Seagate
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 8.01
                serial: 5JVL3MV5
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00004167
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 6a9d7b95-9282-47c6-bd86-fdca8b485848
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-04-29 22:54:10 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;&#65533;&#65533;3&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V&#65533;&#65533;&#65533;>&#65533;&#65533;E&#65533; &#65533;&#65533;&#65533;^&#65533;&#65533;/&#65533;&#65533;>&#65533;&#65533;&#65533;XY&#65533;XY&#65533;&#65533;3&#65533;&#65533;>&#65533;&#65533;&#65533;>&#65533;&#65533; modified=2011-06-12 11:37:03 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-12 11:37:19 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 2935MiB
                   capacity: 2935MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2935MiB
                      capabilities: nofs
        *-ide:1
             description: IDE interface
             product: nForce2 Serial ATA Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:22 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:ac00(size=16) ioport:b000(size=128)
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:e9000000-eaffffff memory:e0000000-e3ffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV28 [GeForce4 Ti 4800 SE]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:e9000000-e9ffffff memory:e0000000-e3ffffff(prefetchable) memory:ea000000-ea01ffff(prefetchable)
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sdb
             size: 3815MiB (4GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=00012380
           *-volume
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/Daniel Bott
                version: FAT32
                serial: ee73-af7a
                size: 3812MiB
                capacity: 3812MiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=Daniel Bott mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

---

### Post by Yellow Pasque on 2011-06-12
See what process is using all of the CPU:
```
sudo apt-get install htop
htop
```

---

### Post by hellhounds88 on 2011-06-12
PS, sudo top returns:
```
top - 12:04:50 up 23 min,  2 users,  load average: 2.21, 1.16, 0.69
Tasks: 140 total,   1 running, 139 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.7%us,  2.6%sy,  0.2%ni, 83.0%id,  3.3%wa,  0.2%hi,  0.1%si,  0.0%st
Mem:   1026464k total,   548592k used,   477872k free,    65724k buffers
Swap:  3005432k total,        0k used,  3005432k free,   246288k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  993 root      20   0 70128  29m  10m S  2.0  3.0   0:50.44 Xorg               
 1978 root      20   0  2540 1068  792 R  2.0  0.1   0:00.02 top                
    1 root      20   0  2768 1604 1164 S  0.0  0.2   0:00.41 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.04 events/0           
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr          
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                 
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers        
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default        
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.06 kblockd/0          
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpid     
```

This is what top returns even when I have cpu-sucking applications (like Google Chrome) open.

---

### Post by hellhounds88 on 2011-06-12
Maybe I shouldn't believe what System Monitor tells me about my CPU usage? Neither top nor htop show any troublesome processes.

---

### Post by cbowman57 on 2011-06-12
Yep, if your system isn't sluggish & unresponsive I'd believe what htop is telling you & assume system monitor has a bug regarding your cpu or another piece of your hardware.

---

### Post by hellhounds88 on 2011-06-12
My system does become sluggish (but NOT unresponsive) at times, especially when Adobe Flash is running, or when I have a multimedia application like an emulator running. I do, however, only have 1 Gb total RAM so that might be the cause for sluggish multitasking? Also, System Monitor itself seems to take up a huge %cpu by its own reckoning, never dipping below 37%.

---

### Post by Yellow Pasque on 2011-06-12
> especially when Adobe Flash is running, or when I have a multimedia application like an emulator running
Yeah, those things take CPU (especially Flash) and you only have a single core.

---

### Post by cbowman57 on 2011-06-12
That sluggishness with Adobe Flash & 1Gb RAM is probably just the result of files being swapped to disk.  Ordinarily I'd recommend you see what system monitor tells you when it does that, but in this case htop probably also shows swap file usage.  You might be able to tweak vm.swappiness to raise the point at which it begins to swap, but it's hard telling if it would work or not.  The discussion of changing vm.swappiness can raise some controversy & get varying responses.  Personally I always add vm.swappiness=1 to my sysctl.conf file but some would disagree with that. :)

---

### Post by hellhounds88 on 2011-06-12
What could I do to improve performance? I know that the Athlon XP series was designed to be overclocked. I just have no idea how to do something like that. Do you know of any resources (preferably aimed at the beginner, yet not glossing over the technical side) about how to overclock a cpu like mine on an Ubuntu machine?

---

### Post by hellhounds88 on 2011-06-12
Hey thanks for the advice! I'll research what you mentioned!

---

### Post by cbowman57 on 2011-06-12
For some tips on overclocking I'd start here [http://www.overclock.net/amd-cpus/70267-need-help-overclocking-3200-venice.html](http://www.overclock.net/amd-cpus/70267-need-help-overclocking-3200-venice.html)

---

### Post by Yellow Pasque on 2011-06-12
> **cbowman57 said:**
> For some tips on overclocking I'd start here [http://www.overclock.net/amd-cpus/70267-need-help-overclocking-3200-venice.html](http://www.overclock.net/amd-cpus/70267-need-help-overclocking-3200-venice.html)
That's a guide for a Venice (AMD64) chip. Athlon XP is a bit different (uses a traditional FSB instead of HyperTransport). [http://www.sharkyextreme.com/guides/hwGuides/article.php/1009731/Athlon-XP-Overclocking-Guide.htm](http://www.sharkyextreme.com/guides/hwGuides/article.php/1009731/Athlon-XP-Overclocking-Guide.htm)

BTW, the XP 3200 was the fastest in the XP line. You probably won't get too much out of OC'ing: [http://www.xbitlabs.com/articles/cpu/display/athlonxp-3200_5.html](http://www.xbitlabs.com/articles/cpu/display/athlonxp-3200_5.html)

---

### Post by cbowman57 on 2011-06-12
Good catch, I just remembered that overclock.net was a good resource.

---

### Post by topclip001 on 2011-06-12
Thanks for the information. :)

---

### Post by hellhounds88 on 2011-06-12
Actually, I just found something interesting. htop is telling me that this process is taking up 99% cpu: "/usr/bin/python /usr/share/checkbox/backend /tmp/checkboxLv1uE0/input /tmp/checkboxLv1uE0/output" The user is root.

Also, nice catch on the XP 3200. Good thing I didn't try it. I've only ever installed a cpu ONCE, so I'm not eager to seek out and install a new one. At least I can get the most out of what I have: I'll head off to the store to double my RAM later today.

---

### Post by Yellow Pasque on 2011-06-12
Good find. This is an issue in Lucid: [https://bugs.launchpad.net/checkbox/+bug/553328](https://bugs.launchpad.net/checkbox/+bug/553328)
Use this PPA to fix it: [https://launchpad.net/~checkbox-dev/+archive/ppa](https://launchpad.net/~checkbox-dev/+archive/ppa)

---

