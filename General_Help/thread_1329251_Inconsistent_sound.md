---
title: "Inconsistent sound"
date: 2009-11-17
forum: General Help
---

### Post by Gavagai80 on 2009-11-17
This is with Kubuntu 9.10.

Most of the last week, I haven't been getting any sound in any program. Yet sometimes everything randomly decides to work in every program after a reboot. Sometimes that sticks through a suspend/resume, sometimes it doesn't. When the sound dies, rebooting doesn't normally help. Sometimes I hear the KDE startup sound, but no further sound after that. I've yet to detect any patterns. 

I've tried xine and gstreamer phonon backends, makes no difference.

alsamixer originally showed it muted and fixing that helped it work one time, but now it's failing again while alsamixer shows it's at full volume.

"HDA Intel MID (ALC272 Analog)" is the only one of the output devices that seems to occasionally work, though as stated it usually doesn't. The pulseaudio and esound options never do.

Some checks:
```

pgk@pgk-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

pgk@pgk-laptop:~$ sudo lshw                                         
pgk-laptop                                               
    description: Computer                                           
    product: AO751h                                                 
    vendor: Acer                                                    
    version: Not Applicable                                         
    serial: LUS850B239928161BC2500                                  
    width: 32 bits                                                  
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp                    
    configuration: administrator_password=disabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=40FA01D2-5935-DE11-98F8-00238BF08AA6                                          
  *-core                                                                        
       description: Motherboard                                                 
       product: JV11-ML                                                         
       vendor: Acer                                                             
       physical id: 0                                                           
       version: Not Applicable                                                  
       serial: 925JVJMBQTF08E62                                                 
     *-firmware                                                                 
          description: BIOS                                                     
          vendor: Acer                                                          
          physical id: 0                                                        
          version: V0.3206 (06/23/2009)                                         
          size: 100KiB                                                          
          capacity: 960KiB                                                      
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification                                                     
     *-cpu                                                                      
          description: CPU                                                      
          product: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz                       
          vendor: Intel Corp.                                                   
          physical id: 4                                                        
          bus info: cpu@0                                                       
          version: 6.12.2                                                       
          serial: 0001-06C2-0000-0000-0000-0000                                 
          slot: U3E1                                                            
          size: 1333MHz                                                         
          capacity: 1333MHz                                                     
          width: 32 bits                                                        
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 xtpr pdcm movbe lahf_lm tpr_shadow vnmi flexpriority cpufreq                      
          configuration: id=0                                                   
        *-cache:0                                                               
             description: L1 cache                                              
             physical id: 5                                                     
             slot: L1 Cache                                                     
             size: 64KiB                                                        
             capacity: 64KiB                                                    
             capabilities: asynchronous internal write-back                     
        *-cache:1                                                               
             description: L2 cache                                              
             physical id: 6                                                     
             slot: L2 Cache                                                     
             size: 512KiB                                                       
             capacity: 512KiB                                                   
             capabilities: burst external write-back                            
        *-logicalcpu:0                                                          
             description: Logical CPU                                           
             physical id: 0.1                                                   
             width: 32 bits                                                     
             capabilities: logical                                              
        *-logicalcpu:1                                                          
             description: Logical CPU                                           
             physical id: 0.2                                                   
             width: 32 bits                                                     
             capabilities: logical                                              
     *-memory                                                                   
          description: System Memory                                            
          physical id: 13                                                       
          slot: System board or motherboard                                     
          size: 1GiB                                                            
          capacity: 1GiB                                                        
        *-bank                                                                  
             description: SODIMM DDR2 Synchronous                               
             physical id: 0                                                     
             slot: DIMM0 J6D1                                                   
             size: 1GiB                                                         
             width: 32 bits                                                     
     *-pci                                                                      
          description: Host bridge                                              
          product: System Controller Hub (SCH Poulsbo)                          
          vendor: Intel Corporation                                             
          physical id: 100                                                      
          bus info: pci@0000:00:00.0                                            
          version: 07                                                           
          width: 32 bits                                                        
          clock: 33MHz                                                          
        *-display                                                               
             description: VGA compatible controller                             
             product: System Controller Hub (SCH Poulsbo) Graphics Controller   
             vendor: Intel Corporation                                          
             physical id: 2                                                     
             bus info: pci@0000:00:02.0                                         
             version: 07                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm msi bus_master cap_list rom                       
             configuration: driver=psb latency=0                                
             resources: irq:16 memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:b0000000-b003ffff                                   
        *-multimedia                                                            
             description: Audio device                                          
             product: System Controller Hub (SCH Poulsbo) HD Audio Controller   
             vendor: Intel Corporation                                          
             physical id: 1b                                                    
             bus info: pci@0000:00:1b.0                                         
             version: 07                                                        
             width: 64 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm pciexpress bus_master cap_list                    
             configuration: driver=HDA Intel latency=0                          
             resources: irq:22 memory:b0050000-b0053fff                         
        *-pci:0                                                                 
             description: PCI bridge                                            
             product: System Controller Hub (SCH Poulsbo) PCI Express Port 1    
             vendor: Intel Corporation                                          
             physical id: 1c                                                    
             bus info: pci@0000:00:1c.0                                         
             version: 07                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pci pciexpress pm bus_master cap_list                
             configuration: driver=pcieport-driver                              
             resources: irq:17 ioport:2000(size=4096) memory:40000000-400fffff memory:d0100000-d01fffff(prefetchable)                                           
           *-network                                                            
                description: Ethernet interface                                 
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
                vendor: Realtek Semiconductor Co., Ltd.                         
                physical id: 0                                                  
                bus info: pci@0000:02:00.0                                      
                logical name: eth0                                              
                version: 02                                                     
                serial: 00:23:8b:f0:8a:a6                                       
                size: 10MB/s                                                    
                capacity: 100MB/s                                               
                width: 64 bits                                                  
                clock: 33MHz                                                    
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation           
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s                                                                         
                resources: irq:24 ioport:2000(size=256) memory:d0110000-d0110fff(prefetchable) memory:d0100000-d010ffff(prefetchable) memory:d0120000-d012ffff(prefetchable)                                                                    
        *-pci:1                                                                 
             description: PCI bridge                                            
             product: System Controller Hub (SCH Poulsbo) PCI Express Port 2    
             vendor: Intel Corporation                                          
             physical id: 1c.1                                                  
             bus info: pci@0000:00:1c.1                                         
             version: 07                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pci pciexpress pm bus_master cap_list                
             configuration: driver=pcieport-driver                              
             resources: irq:16 memory:d0000000-d00fffff                         
           *-network                                                            
                description: Wireless interface                                 
                product: AR5001 Wireless Network Adapter                        
                vendor: Atheros Communications Inc.                             
                physical id: 0                                                  
                bus info: pci@0000:03:00.0                                      
                logical name: wmaster0                                          
                version: 01                                                     
                serial: 00:26:5e:1f:af:0f                                       
                width: 64 bits                                                  
                clock: 33MHz                                                    
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless                                                     
                configuration: broadcast=yes driver=ath5k ip=172.16.1.33 latency=0 multicast=yes wireless=IEEE 802.11bg                                         
                resources: irq:17 memory:d0000000-d000ffff                      
        *-usb:0                                                                 
             description: USB Controller                                        
             product: System Controller Hub (SCH Poulsbo) USB UHCI #1           
             vendor: Intel Corporation                                          
             physical id: 1d                                                    
             bus info: pci@0000:00:1d.0                                         
             version: 07                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: bus_master                                           
             configuration: driver=uhci_hcd latency=0                           
             resources: irq:23 ioport:1820(size=32)                             
        *-usb:1                                                                 
             description: USB Controller                                        
             product: System Controller Hub (SCH Poulsbo) USB UHCI #2           
             vendor: Intel Corporation                                          
             physical id: 1d.1                                                  
             bus info: pci@0000:00:1d.1                                         
             version: 07                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: bus_master                                           
             configuration: driver=uhci_hcd latency=0                           
             resources: irq:19 ioport:1840(size=32)                             
        *-usb:2                                                                 
             description: USB Controller                                        
             product: System Controller Hub (SCH Poulsbo) USB UHCI #3           
             vendor: Intel Corporation                                          
             physical id: 1d.2                                                  
             bus info: pci@0000:00:1d.2                                         
             version: 07                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: bus_master                                           
             configuration: driver=uhci_hcd latency=0                           
             resources: irq:18 ioport:1860(size=32)                             
        *-usb:3                                                                 
             description: USB Controller                                        
             product: System Controller Hub (SCH Poulsbo) USB EHCI #1           
             vendor: Intel Corporation                                          
             physical id: 1d.7                                                  
             bus info: pci@0000:00:1d.7                                         
             version: 07                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm debug bus_master cap_list                         
             configuration: driver=ehci_hcd latency=0                           
             resources: irq:21 memory:b0054000-b00543ff                         
        *-isa                                                                   
             description: ISA bridge                                            
             product: System Controller Hub (SCH Poulsbo) LPC Bridge            
             vendor: Intel Corporation                                          
             physical id: 1f                                                    
             bus info: pci@0000:00:1f.0                                         
             version: 07                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: isa                                                  
             configuration: driver=isch_smbus latency=0                         
             resources: irq:0                                                   
        *-ide                                                                   
             description: IDE interface                                         
             product: System Controller Hub (SCH Poulsbo) IDE Controller        
             vendor: Intel Corporation                                          
             physical id: 1f.1                                                  
             bus info: pci@0000:00:1f.1                                         
             logical name: scsi0                                                
             version: 07                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: ide bus_master emulated                              
             configuration: driver=pata_sch latency=0                           
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)                                                  
           *-disk                                                               
                description: ATA Disk                                           
                product: TOSHIBA MK1655GS                                       
                vendor: Toshiba                                                 
                physical id: 0.0.0                                              
                bus info: scsi@0:0.0.0                                          
                logical name: /dev/sda                                          
                version: FG01                                                   
                serial: 7921F4BXS                                               
                size: 149GiB (160GB)                                            
                capabilities: partitioned partitioned:dos                       
                configuration: ansiversion=5 signature=1647b2fc                 
              *-volume:0                                                        
                   description: Windows NTFS volume                             
                   physical id: 1                                               
                   bus info: scsi@0:0.0.0,1                                     
                   logical name: /dev/sda1                                      
                   version: 3.1                                                 
                   serial: 7448-3978                                            
                   size: 8190MiB                                                
                   capacity: 8GiB                                               
                   capabilities: primary bootable boot ntfs initialized         
                   configuration: clustersize=4096 created=2009-07-10 05:52:27 filesystem=ntfs label=PQSERVICE state=clean                                      
              *-volume:1                                                        
                   description: Windows NTFS volume                             
                   physical id: 2                                               
                   bus info: scsi@0:0.0.0,2                                     
                   logical name: /dev/sda2                                      
                   version: 3.1                                                 
                   serial: d602e119-a040-5248-b0cf-e88ad05419e9                 
                   size: 25GiB                                                  
                   capacity: 25GiB                                              
                   capabilities: primary ntfs initialized                       
                   configuration: clustersize=4096 created=2009-07-10 06:11:19 filesystem=ntfs label=ACER modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true                                    
              *-volume:2                                                        
                   description: Extended partition                              
                   physical id: 3                                               
                   bus info: scsi@0:0.0.0,3                                     
                   logical name: /dev/sda3                                      
                   size: 115GiB                                                 
                   capacity: 115GiB                                             
                   capabilities: primary extended partitioned partitioned:extended                                                                              
                 *-logicalvolume:0                                              
                      description: Linux filesystem partition                   
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 74GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1906MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /
                      capacity: 39GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound


```

I'm running the psb 2D (not 3D) video driver, if that's relevant.

---

### Post by Gavagai80 on 2009-11-17
Maybe the error realplayer gives on trying to play a file gives someone an idea:
```
Opening ALSA PCM device default
/usr/bin/realplayer: line 57:  2877 Floating point exception$HELIX_LIBS/realplay.bin "$@"
```

It doesn't crash at times when the sound works.

---

### Post by penguin10916 on 2009-11-29
it's because of the timer line in the alsa-base.conf file. You have to split the line and comment out the 2nd half... I'm having a problem similar to what mac users are having now... headphones don't mute the ext. speakers, and strangely, I get audio out of the right headphone.

...I'm going to try out opensuse.

---

### Post by Gavagai80 on 2009-11-30
What line? There isn't a line 57 in /etc/modprobe.d/alsa-base.conf, nor does the word "timer" appear in the file. This bit looks suspicious though: ```
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```
Maybe it could be an idle timeout killing it occasionally when in powersave mode, that fits the facts as far as I've noticed. But there's no clear halves to that line. I'll try just changing 10 to 100000.

---

### Post by penguin10916 on 2009-12-01
lol, sorry, wasn't thinking. I meant power_save. That line you posted is the one you have to split.

---

