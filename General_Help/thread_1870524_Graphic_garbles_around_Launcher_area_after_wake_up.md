---
title: "Graphic garbles around Launcher area after wake up from hibernate"
date: 2011-10-27
forum: General Help
---

### Post by koreaheart on 2011-10-27
I installed ubuntu 11.10 to my HP dv9700. After waking up from hibernate, the graphic of just Launcher area becomes weird-looking (garbles or broken) while the other area is just fine. Would you know the problem and solutions?

---

### Post by 2F4U on 2011-10-27
Would you please tell us your hardware specs and what graphics driver you are using?

---

### Post by mjuhasz on 2011-10-27
Refreshing the launcher after wake-up has been on the developer's todo list and as far as I know it's still not resolved. I also experience this issue.
A simple workaround is to hover your mouse over the launcher and it will get repainted.

---

### Post by koreaheart on 2011-10-27
Thanks a lot for your comments.

Yes, I am touching the launcher every time as well to get rid of the broken graphic.
Hopefully, the problem gets solved.
Anyways, the spec of my laptop is following:

   id:shin-hp-pavilion-dv9730ca-kc332ua
       description: Notebook     version: Rev 1     width: 32 bits     capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp      configuration: boot=oem-specific chassis=notebook cpus=2 family=103C_5335KV sku=KC332UA#ABC uuid=434E4638-3034-334B-4243-001E680C6F53  
                 id:core
          description: Motherboard        product: 30DA        vendor: Quanta        physical id: 0
        version: 85.26        serial: None2      
                          id:firmware
             description: BIOS           vendor: Hewlett-Packard           physical id: 0
           version: F.32           date: 03/03/2009           size: 101KiB           capacity: 960KiB           capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery          
        
                          id:cpu:0
             description: CPU           product: AMD Turion(tm) 64 X2 Mobile Technology TL-60           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 4
           bus info: cpu@0
           version: 15.8.2           slot: Socket S1           size: 800MHz           capacity: 2GHz           width: 64 bits           clock: 200MHz           capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq          
                                   id:cache:0
                description: L1 cache              physical id: 5
              slot: L1 Cache              size: 128KiB              capabilities: asynchronous internal write-back             
           
                                   id:cache:1
                description: L2 cache              physical id: 6
              slot: L2 Cache              size: 512KiB              capacity: 1MiB              capabilities: synchronous internal write-through unified             
           
        
                          id:memory:0
             description: System Memory           physical id: 3
           slot: System board or motherboard           size: 4GiB         
                                   id:bank:0
                description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)              physical id: 0
              slot: DIMM 1              size: 2GiB              width: 64 bits              clock: 667MHz (1.5ns)            
           
                                   id:bank:1
                description: DIMM DDR2 667 MHz (1.5 ns)              physical id: 1
              slot: DIMM 2              size: 2GiB              width: 64 bits              clock: 667MHz (1.5ns)            
           
        
                          id:cpu:1
             physical id: 5
           bus info: cpu@1
           version: 15.8.2           size: 800MHz           capacity: 800MHz           capabilities: cpufreq          
                                   id:cache:0
                description: L1 cache              physical id: 0
              size: 128KiB            
           
                                   id:cache:1
                description: L2 cache              physical id: 1
              size: 512KiB            
           
        
                          id:memory:1
             description: RAM memory           product: MCP65 Memory Controller           vendor: nVidia Corporation           physical id: b
           bus info: pci@0000:00:00.0
           version: a3           width: 32 bits           clock: 66MHz (15.2ns)           capabilities: ht bus_master cap_list            configuration: latency=0         
        
                          id:isa
             description: ISA bridge           product: MCP65 LPC Bridge           vendor: nVidia Corporation           physical id: 1
           bus info: pci@0000:00:01.0
           version: a3           width: 32 bits           clock: 66MHz           capabilities: isa bus_master            configuration: latency=0           resources: ioport:1d00(size=256)         
        
                          id:serial
             description: SMBus           product: MCP65 SMBus           vendor: nVidia Corporation           physical id: 1.1
           bus info: pci@0000:00:01.1
           version: a1           width: 32 bits           clock: 66MHz           capabilities: pm cap_list            configuration: driver=nForce2_smbus latency=0           resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)         
        
                          id:processor
             description: Co-processor           product: MCP65 SMU           vendor: nVidia Corporation           physical id: 1.3
           bus info: pci@0000:00:01.3
           version: a1           width: 32 bits           clock: 66MHz           capabilities: bus_master            configuration: latency=0 maxlatency=1 mingnt=3           resources: memory:f2200000-f227ffff         
        
                          id:usb:0
             description: USB Controller           product: MCP65 USB Controller           vendor: nVidia Corporation           physical id: 2
           bus info: pci@0000:00:02.0
           version: a3           width: 32 bits           clock: 66MHz           capabilities: pm ohci bus_master cap_list            configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3           resources: irq:18 memory:f2486000-f2486fff         
        
                          id:usb:1
             description: USB Controller           product: MCP65 USB Controller           vendor: nVidia Corporation           physical id: 2.1
           bus info: pci@0000:00:02.1
           version: a3           width: 32 bits           clock: 66MHz           capabilities: debug pm ehci bus_master cap_list            configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3           resources: irq:17 memory:f2488000-f24880ff         
        
                          id:network
             description: Ethernet interface           product: MCP65 Ethernet           vendor: nVidia Corporation           physical id: 6
           bus info: pci@0000:00:06.0
           logical name: eth0
           version: a3           serial: 00:1e:68:0c:6f:53           capacity: 1Gbit/s           width: 32 bits           clock: 66MHz           capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation            configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII           resources: irq:20 memory:f2487000-f2487fff ioport:30e0(size=         
        
                          id:multimedia
             description: Audio device           product: MCP65 High Definition Audio           vendor: nVidia Corporation           physical id: 7
           bus info: pci@0000:00:07.0
           version: a1           width: 32 bits           clock: 66MHz           capabilities: pm msi ht bus_master cap_list            configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2           resources: irq:21 memory:f2480000-f2483fff         
        
                          idci:0
             description: PCI bridge           product: MCP65 PCI bridge           vendor: nVidia Corporation           physical id: 8
           bus info: pci@0000:00:08.0
           version: a1           width: 32 bits           clock: 66MHz           capabilities: pci ht subtractive_decode bus_master cap_list            resources: memory:f2100000-f21fffff         
                                   id:firewire
                description: FireWire (IEEE 1394)              product: R5C832 IEEE 1394 Controller              vendor: Ricoh Co Ltd              physical id: 5
              bus info: pci@0000:07:05.0
              version: 05              width: 32 bits              clock: 33MHz              capabilities: pm ohci bus_master cap_list               configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2              resources: irq:5 memory:f2100000-f21007ff            
           
                                   id:generic:0
                description: SD Host controller              product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter              vendor: Ricoh Co Ltd              physical id: 5.1
              bus info: pci@0000:07:05.1
              version: 22              width: 32 bits              clock: 33MHz              capabilities: pm bus_master cap_list               configuration: driver=sdhci-pci latency=64              resources: irq:7 memory:f2100800-f21008ff            
           
                                   id:generic:1
                description: System peripheral              product: R5C592 Memory Stick Bus Host Adapter              vendor: Ricoh Co Ltd              physical id: 5.2
              bus info: pci@0000:07:05.2
              version: 12              width: 32 bits              clock: 33MHz              capabilities: pm bus_master cap_list               configuration: latency=64              resources: memory:f2101000-f21010ff            
           
                                   id:generic:2
                description: System peripheral              product: xD-Picture Card Controller              vendor: Ricoh Co Ltd              physical id: 5.3
              bus info: pci@0000:07:05.3
              version: 12              width: 32 bits              clock: 33MHz              capabilities: pm bus_master cap_list               configuration: driver=r852 latency=64              resources: irq:7 memory:f2101400-f21014ff            
           
        
                          id:ide:0
             description: IDE interface           product: MCP65 IDE           vendor: nVidia Corporation           physical id: 9
           bus info: pci@0000:00:09.0
           logical name: scsi4
           version: a1           width: 32 bits           clock: 66MHz           capabilities: ide pm bus_master cap_list emulated            configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3           resources: irq:0 ioport:1f0(size= ioport:3f6 ioport:170(size= ioport:376 ioport:30c0(size=16)         
                                   id:cdrom
                description: DVD-RAM writer              product: DVDRW  DR-KD08HB              vendor: PIONEER              physical id: 0.0.0
              bus info: scsi@4:0.0.0
              logical name: /dev/cdrom
              logical name: /dev/cdrw
              logical name: /dev/dvd
              logical name: /dev/dvdrw
              logical name: /dev/scd0
              logical name: /dev/sr0
              version: 1K09              capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram               configuration: ansiversion=5 status=nodisc            
           
        
                          id:ide:1
             description: IDE interface           product: MCP65 SATA Controller           vendor: nVidia Corporation           physical id: a
           bus info: pci@0000:00:0a.0
           logical name: scsi0
           version: a3           width: 32 bits           clock: 66MHz           capabilities: ide pm bus_master cap_list emulated            configuration: driver=ahci latency=0 maxlatency=1 mingnt=3           resources: irq:23 ioport:30f8(size= ioport:30ec(size=4) ioport:30f0(size= ioport:30e8(size=4) ioport:30d0(size=16) memory:f2484000-f2485fff         
                                   id:disk
                description: ATA Disk              product: FUJITSU MHZ2320B              vendor: Fujitsu              physical id: 0.0.0
              bus info: scsi@0:0.0.0
              logical name: /dev/sda
              version: 8909              serial: K618T8528DF0              size: 298GiB (320GB)              capabilities: partitioned partitioned:dos               configuration: ansiversion=5 signature=0001fb91            
                                            id:volume:0
                   description: EXT4 volume                 vendor: Linux                 physical id: 1
                 bus info: scsi@0:0.0.0,1
                 logical name: /dev/sda1
                 logical name: /
                 version: 1.0                 serial: a51e92f6-ca4e-4073-b808-d818436f200a                 size: 294GiB                 capacity: 294GiB                 capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized                  configuration: created=2011-10-21 09:15:02 filesystem=ext4 lastmountpoint=/ modified=2011-10-21 09:23:23 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-10-25 21:02:42 state=mounted               
              
                                            id:volume:1
                   description: Extended partition                 physical id: 2
                 bus info: scsi@0:0.0.0,2
                 logical name: /dev/sda2
                 size: 3934MiB                 capacity: 3934MiB                 capabilities: primary extended partitioned partitioned:extended                
                                                     id:logicalvolume
                      description: Linux swap / Solaris partition                    physical id: 5
                    logical name: /dev/sda5
                    capacity: 3934MiB                    capabilities: nofs                   
                 
              
           
        
                          idci:1
             description: PCI bridge           product: nVidia Corporation           vendor: nVidia Corporation           physical id: 100
           bus info: pci@0000:00:0b.0
           version: a1           width: 32 bits           clock: 33MHz           capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list            configuration: driver=pcieport           resources: irq:40         
        
                          idci:2
             description: PCI bridge           product: MCP65 PCI Express bridge           vendor: nVidia Corporation           physical id: c
           bus info: pci@0000:00:0c.0
           version: a1           width: 32 bits           clock: 33MHz           capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list            configuration: driver=pcieport           resources: irq:41 memory:f2000000-f20fffff ioport:f2500000(size=1048576)         
                                   id:network
                description: Wireless interface              product: BCM4321 802.11a/b/g/n              vendor: Broadcom Corporation              physical id: 0
              bus info: pci@0000:03:00.0
              logical name: eth2
              version: 03              serial: 00:21:00:23:a3:0d              width: 64 bits              clock: 33MHz              capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless               configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.2.11 latency=0 multicast=yes wireless=IEEE 802.11abgn              resources: irq:16 memory:f2000000-f2003fff memory:f2500000-f25fffff            
           
        
                          idci:3
             description: PCI bridge           product: MCP65 PCI Express bridge           vendor: nVidia Corporation           physical id: d
           bus info: pci@0000:00:0d.0
           version: a1           width: 32 bits           clock: 33MHz           capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list            configuration: driver=pcieport           resources: irq:42 ioport:4000(size=4096) memory:cc000000-ceffffff ioport:d0000000(size=268435456)         
                                   id:display
                description: VGA compatible controller              product: G86 [GeForce 8400M GS]              vendor: nVidia Corporation              physical id: 0
              bus info: pci@0000:05:00.0
              version: a1              width: 64 bits              clock: 33MHz              capabilities: pm msi pciexpress vga_controller bus_master cap_list rom               configuration: driver=nvidia latency=0              resources: irq:19 memory:ce000000-ceffffff memory:d0000000-dfffffff memory:cc000000-cdffffff ioport:4000(size=12            
           
        
                          idci:4
             description: PCI bridge           product: MCP65 PCI Express bridge           vendor: nVidia Corporation           physical id: e
           bus info: pci@0000:00:0e.0
           version: a1           width: 32 bits           clock: 33MHz           capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list            configuration: driver=pcieport           resources: irq:43 ioport:5000(size=4096) memory:f0000000-f1ffffff ioport:f2600000(size=2097152)         
        
                          idci:5
             description: Host bridge           product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 101
           bus info: pci@0000:00:18.0
           version: 00           width: 32 bits           clock: 33MHz         
        
                          idi:6
             description: Host bridge           product: K8 [Athlon64/Opteron] Address Map           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 102
           bus info: pci@0000:00:18.1
           version: 00           width: 32 bits           clock: 33MHz         
        
                          idci:7
             description: Host bridge           product: K8 [Athlon64/Opteron] DRAM Controller           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 103
           bus info: pci@0000:00:18.2
           version: 00           width: 32 bits           clock: 33MHz         
        
                          idci:8
             description: Host bridge           product: K8 [Athlon64/Opteron] Miscellaneous Control           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 104
           bus info: pci@0000:00:18.3
           version: 00           width: 32 bits           clock: 33MHz           configuration: driver=k8temp           resources: irq:0

---

