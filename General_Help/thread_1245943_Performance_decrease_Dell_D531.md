---
title: "Performance decrease Dell D531"
date: 2009-08-21
forum: General Help
---

### Post by Haarlem on 2009-08-21
Hi All,

I must say, Kubuntu is still aweing me daily after my migration from XP. It boots faster(even with the errors: [http://ubuntuforums.org/showthread.php?p=7821994#post7821994](http://ubuntuforums.org/showthread.php?p=7821994#post7821994)), works faster, more stable, no worries about viruses, open-source software, etc etc... All in all I love it.

Unfortunately this is no Utopia and also my Kubuntu experience is not without some struggle. 

For a reason unknown to me, after a while my laptop gets les reactive, the GUI buildup seems to slow down and everything get a kind of sluggishness over it. This is always solved by a reboot. It _*seems*_ like this performance drop occurs after using programs such as Wine/Pokerstars, YouTube/fullscreen motion picture, aMSN, Kontact, too much messing around with widgets or stuff which is graphically taxing.

I use:
- Dell Latitude D531
- Kubuntu 9.04/newest KDE desktop environment.

**sudo lshw:**
laptop                    
    description: Portable Computer
    product: Latitude D531        
    vendor: Dell Inc.             
    serial: xxxxxxx               
    width: 32 bits                
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=xxxxxxxxxxxxxxxxxxxxxxx
  *-core                                                                                 
       description: Motherboard                                                          
       product: 0XM006                                                                   
       vendor: Dell Inc.                                                                 
       physical id: 0                                                                    
       serial: .xxxxxxxxxxxxxxxxxxxxxx.                                                  
     *-firmware                                                                          
          description: BIOS                                                              
          vendor: Dell Inc.                                                              
          physical id: 0                                                                 
          version: A00 (04/23/2007)                                                      
          size: 64KiB                                                                    
          capacity: 960KiB                                                               
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot                                              
     *-cpu                                                                                                                        
          description: CPU                                                                                                        
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-60                                                                   
          vendor: Advanced Micro Devices [AMD]                                                                                    
          physical id: 400                                                                                                        
          bus info: cpu@0                                                                                                         
          version: 15.8.1                                                                                                         
          slot: Microprocessor                                                                                                    
          size: 2GHz                                                                                                              
          capacity: 2GHz                                                                                                          
          width: 64 bits                                                                                                          
          clock: 100MHz                                                                                                           
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq                                                                                                                        
        *-cache:0                                                                                                                 
             description: L1 cache                                                                                                
             physical id: 700                                                                                                     
             size: 128KiB                                                                                                         
             capacity: 128KiB                                                                                                     
             capabilities: internal write-back data                                                                               
        *-cache:1                                                                                                                 
             description: L2 cache                                                                                                
             physical id: 701                                                                                                     
             size: 512KiB                                                                                                         
             capacity: 1MiB                                                                                                       
             clock: 66MHz (15.0ns)                                                                                                
             capabilities: pipeline-burst internal varies unified                                                                 
     *-memory                                                                                                                     
          description: System Memory                                                                                              
          physical id: 1000                                                                                                       
          slot: System board or motherboard                                                                                       
          size: 2GiB                                                                                                              
        *-bank:0                                                                                                                  
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)                                                                   
             product: M4 70T2953EZ3-CE6                                                                                           
             vendor: CE00000000000000                                                                                             
             physical id: 0                                                                                                       
             serial: F404FB9D                                                                                                     
             slot: DIMM_A                                                                                                         
             size: 1GiB                                                                                                           
             width: 64 bits                                                                                                       
             clock: 667MHz (1.5ns)                                                                                                
        *-bank:1                                                                                                                  
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)                                                                   
             product: M4 70T2953EZ3-CE6                                                                                           
             vendor: CE00000000000000                                                                                             
             physical id: 1                                                                                                       
             serial: F404FBAF                                                                                                     
             slot: DIMM_B                                                                                                         
             size: 1GiB                                                                                                           
             width: 64 bits                                                                                                       
             clock: 667MHz (1.5ns)                                                                                                
     *-pci:0                                                                                                                      
          description: Host bridge                                                                                                
          product: RS690 Host Bridge                                                                                              
          vendor: ATI Technologies Inc                                                                                            
          physical id: 100                                                                                                        
          bus info: pci@0000:00:00.0                                                                                              
          version: 00                                                                                                             
          width: 32 bits                                                                                                          
          clock: 66MHz                                                                                                            
          configuration: latency=64                                                                                               
        *-pci:0                                                                                                                   
             description: PCI bridge                                                                                              
             product: RS690 PCI to PCI Bridge (Internal gfx)                                                                      
             vendor: ATI Technologies Inc                                                                                         
             physical id: 1                                                                                                       
             bus info: pci@0000:00:01.0                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: pci ht bus_master cap_list                                                                             
           *-display UNCLAIMED                                                                                                    
                description: VGA compatible controller                                                                            
                product: RS690M [Radeon X1200 Series]                                                                             
                vendor: ATI Technologies Inc                                                                                      
                physical id: 5                                                                                                    
                bus info: pci@0000:01:05.0                                                                                        
                version: 00                                                                                                       
                width: 64 bits                                                                                                    
                clock: 33MHz                                                                                                      
                capabilities: pm msi bus_master cap_list                                                                          
                configuration: latency=64                                                                                         
        *-pci:1                                                                                                                   
             description: PCI bridge                                                                                              
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)                                                                
             vendor: ATI Technologies Inc                                                                                         
             physical id: 5                                                                                                       
             bus info: pci@0000:00:05.0                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 33MHz                                                                                                         
             capabilities: pci pm pciexpress msi ht bus_master cap_list                                                           
             configuration: driver=pcieport-driver                                                                                
           *-network                                                                                                              
                description: Network controller                                                                                   
                product: BCM4312 802.11a/b/g                                                                                      
                vendor: Broadcom Corporation                                                                                      
                physical id: 0                                                                                                    
                bus info: pci@0000:0b:00.0                                                                                        
                version: 01                                                                                                       
                width: 32 bits                                                                                                    
                clock: 33MHz                                                                                                      
                capabilities: pm msi pciexpress bus_master cap_list                                                               
                configuration: driver=b43-pci-bridge latency=0 module=ssb                                                         
        *-pci:2                                                                                                                   
             description: PCI bridge                                                                                              
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)                                                                
             vendor: ATI Technologies Inc                                                                                         
             physical id: 6                                                                                                       
             bus info: pci@0000:00:06.0                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 33MHz                                                                                                         
             capabilities: pci pm pciexpress msi ht bus_master cap_list                                                           
             configuration: driver=pcieport-driver                                                                                
           *-network                                                                                                              
                description: Ethernet interface                                                                                   
                product: NetXtreme BCM5755M Gigabit Ethernet PCI Express                                                          
                vendor: Broadcom Corporation                                                                                      
                physical id: 0                                                                                                    
                bus info: pci@0000:09:00.0                                                                                        
                logical name: eth0                                                                                                
                version: 02                                                                                                       
                serial: xxxxxxxxxxxxxxx                                                                                         
                capacity: 1GB/s                                                                                                   
                width: 64 bits                                                                                                    
                clock: 33MHz                                                                                                      
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                                                                                                           
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5755m-v3.29 latency=0 link=no module=tg3 multicast=yes port=twisted pair                                                                                     
        *-storage                                                                                                                 
             description: SATA controller                                                                                         
             product: SB600 Non-Raid-5 SATA                                                                                       
             vendor: ATI Technologies Inc                                                                                         
             physical id: 12                                                                                                      
             bus info: pci@0000:00:12.0                                                                                           
             logical name: scsi0                                                                                                  
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: storage pm bus_master cap_list emulated                                                                
             configuration: driver=ahci latency=64 module=ahci                                                                    
           *-disk                                                                                                                 
                description: ATA Disk                                                                                             
                product: ST980811AS                                                                                               
                vendor: Seagate                                                                                                   
                physical id: 0.0.0                                                                                                
                bus info: scsi@0:0.0.0                                                                                            
                logical name: /dev/sda                                                                                            
                version: 3.CD                                                                                                     
                serial: 5LY770CS                                                                                                  
                size: 74GiB (80GB)                                                                                                
                capabilities: partitioned partitioned:dos                                                                         
                configuration: ansiversion=5 signature=41ab2316                                                                   
              *-volume:0                                                                                                          
                   description: Windows NTFS volume                                                                               
                   physical id: 1                                                                                                 
                   bus info: scsi@0:0.0.0,1                                                                                       
                   logical name: /dev/sda1                                                                                        
                   version: 3.1                                                                                                   
                   serial: 483ac7e1-5e13-a449-8364-50b987acb2a5                                                                   
                   size: 40GiB                                                                                                    
                   capacity: 40GiB                                                                                                
                   capabilities: primary bootable ntfs initialized                                                                
                   configuration: clustersize=4096 created=2008-03-25 15:08:56 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true **_state=dirty_** upgrade_on_mount=true                                                                   
              *-volume:1                                                                                                          
                   description: Extended partition                                                                                
                   physical id: 2                                                                                                 
                   bus info: scsi@0:0.0.0,2                                                                                       
                   logical name: /dev/sda2                                                                                        
                   size: 34GiB                                                                                                    
                   capacity: 34GiB                                                                                                
                   capabilities: primary extended partitioned partitioned:extended                                                
                 *-logicalvolume:0                                                                                                
                      description: Linux filesystem partition                                                                     
                      physical id: 5                                                                                              
                      logical name: /dev/sda5                                                                                     
                      logical name: /                                                                                             
                      capacity: 32GiB                                                                                             
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted     
                 *-logicalvolume:1                                                                                                
                      description: Linux swap / Solaris partition                                                                 
                      physical id: 6                                                                                              
                      logical name: /dev/sda6                                                                                     
                      capacity: 1482MiB                                                                                           
                      capabilities: nofs                                                                                          
        *-usb:0                                                                                                                   
             description: USB Controller                                                                                          
             product: SB600 USB (OHCI0)                                                                                           
             vendor: ATI Technologies Inc                                                                                         
             physical id: 13                                                                                                      
             bus info: pci@0000:00:13.0                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: bus_master                                                                                             
             configuration: driver=ohci_hcd latency=64                                                                            
        *-usb:1                                                                                                                   
             description: USB Controller                                                                                          
             product: SB600 USB (OHCI1)                                                                                           
             vendor: ATI Technologies Inc                                                                                         
             physical id: 13.1                                                                                                    
             bus info: pci@0000:00:13.1                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: bus_master                                                                                             
             configuration: driver=ohci_hcd latency=64                                                                            
        *-usb:2                                                                                                                   
             description: USB Controller                                                                                          
             product: SB600 USB (OHCI2)                                                                                           
             vendor: ATI Technologies Inc                                                                                         
             physical id: 13.2                                                                                                    
             bus info: pci@0000:00:13.2                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: bus_master                                                                                             
             configuration: driver=ohci_hcd latency=64                                                                            
        *-usb:3                                                                                                                   
             description: USB Controller                                                                                          
             product: SB600 USB (OHCI3)                                                                                           
             vendor: ATI Technologies Inc                                                                                         
             physical id: 13.3                                                                                                    
             bus info: pci@0000:00:13.3                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: bus_master                                                                                             
             configuration: driver=ohci_hcd latency=64                                                                            
        *-usb:4                                                                                                                   
             description: USB Controller                                                                                          
             product: SB600 USB (OHCI4)                                                                                           
             vendor: ATI Technologies Inc                                                                                         
             physical id: 13.4                                                                                                    
             bus info: pci@0000:00:13.4                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: bus_master                                                                                             
             configuration: driver=ohci_hcd latency=64                                                                            
        *-usb:5                                                                                                                   
             description: USB Controller                                                                                          
             product: SB600 USB Controller (EHCI)                                                                                 
             vendor: ATI Technologies Inc                                                                                         
             physical id: 13.5                                                                                                    
             bus info: pci@0000:00:13.5                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: pm debug bus_master cap_list                                                                           
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd                                                            
        *-serial                                                                                                                  
             description: SMBus                                                                                                   
             product: SBx00 SMBus Controller                                                                                      
             vendor: ATI Technologies Inc                                                                                         
             physical id: 14                                                                                                      
             bus info: pci@0000:00:14.0                                                                                           
             version: 14                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: ht cap_list                                                                                            
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4                                                         
        *-ide                                                                                                                     
             description: IDE interface                                                                                           
             product: SB600 IDE                                                                                                   
             vendor: ATI Technologies Inc                                                                                         
             physical id: 14.1                                                                                                    
             bus info: pci@0000:00:14.1                                                                                           
             logical name: scsi4                                                                                                  
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: ide bus_master emulated                                                                                
             configuration: driver=pata_atiixp latency=64                                                                         
           *-cdrom                                                                                                                
                description: DVD writer                                                                                           
                product: DVD+-RW TS-L632D                                                                                         
                vendor: TSSTcorp                                                                                                  
                physical id: 0.0.0                                                                                                
                bus info: scsi@4:0.0.0                                                                                            
                logical name: /dev/cdrom                                                                                          
                logical name: /dev/cdrw                                                                                           
                logical name: /dev/dvd                                                                                            
                logical name: /dev/dvdrw                                                                                          
                logical name: /dev/scd0                                                                                           
                logical name: /dev/sr0                                                                                            
                version: DE04                                                                                                     
                capabilities: removable audio cd-r cd-rw dvd dvd-r                                                                
                configuration: ansiversion=5 status=nodisc                                                                        
        *-multimedia                                                                                                              
             description: Audio device                                                                                            
             product: SBx00 Azalia (Intel HDA)                                                                                    
             vendor: ATI Technologies Inc                                                                                         
             physical id: 14.2                                                                                                    
             bus info: pci@0000:00:14.2                                                                                           
             version: 00                                                                                                          
             width: 64 bits                                                                                                       
             clock: 33MHz                                                                                                         
             capabilities: pm bus_master cap_list                                                                                 
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel                                                      
        *-isa                                                                                                                     
             description: ISA bridge                                                                                              
             product: SB600 PCI to LPC Bridge                                                                                     
             vendor: ATI Technologies Inc                                                                                         
             physical id: 14.3                                                                                                    
             bus info: pci@0000:00:14.3                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: isa bus_master                                                                                         
             configuration: latency=0                                                                                             
        *-pci:3                                                                                                                   
             description: PCI bridge                                                                                              
             product: SBx00 PCI to PCI Bridge                                                                                     
             vendor: ATI Technologies Inc                                                                                         
             physical id: 14.4                                                                                                    
             bus info: pci@0000:00:14.4                                                                                           
             version: 00                                                                                                          
             width: 32 bits                                                                                                       
             clock: 66MHz                                                                                                         
             capabilities: pci bus_master                                                                                         
           *-pcmcia                                                                                                               
                description: CardBus bridge                                                                                       
                product: Cardbus bridge                                                                                           
                vendor: O2 Micro, Inc.                                                                                            
                physical id: 1                                                                                                    
                bus info: pci@0000:03:01.0                                                                                        
                version: 21                                                                                                       
                width: 32 bits                                                                                                    
                clock: 33MHz                                                                                                      
                capabilities: pcmcia bus_master cap_list                                                                          
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket                       
           *-firewire                                                                                                             
                description: FireWire (IEEE 1394)                                                                                 
                product: Firewire (IEEE 1394)                                                                                     
                vendor: O2 Micro, Inc.                                                                                            
                physical id: 1.4                                                                                                  
                bus info: pci@0000:03:01.4                                                                                        
                version: 02                                                                                                       
                width: 32 bits                                                                                                    
                clock: 33MHz                                                                                                      
                capabilities: pm bus_master cap_list                                                                              
                configuration: driver=ohci1394 latency=64 module=ohci1394                                                         
     *-pci:1                                                                                                                      
          description: Host bridge                                                                                                
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration                                                  
          vendor: Advanced Micro Devices [AMD]                                                                                    
          physical id: 101                                                                                                        
          bus info: pci@0000:00:18.0                                                                                              
          version: 00                                                                                                             
          width: 32 bits                                                                                                          
          clock: 33MHz                                                                                                            
     *-pci:2                                                                                                                      
          description: Host bridge                                                                                                
          product: K8 [Athlon64/Opteron] Address Map                                                                              
          vendor: Advanced Micro Devices [AMD]                                                                                    
          physical id: 102                                                                                                        
          bus info: pci@0000:00:18.1                                                                                              
          version: 00                                                                                                             
          width: 32 bits                                                                                                          
          clock: 33MHz                                                                                                            
     *-pci:3                                                                                                                      
          description: Host bridge                                                                                                
          product: K8 [Athlon64/Opteron] DRAM Controller                                                                          
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-battery
       product: DELL xxxxxx
       vendor: SMP
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52000mWh
       configuration: voltage=11.1V
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: xxxxxxxxxxxx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=xxxxxxxxxxxx multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial:xxxxxxxxxxxxxx
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

[B]sudo lsmod:
[/B]Module                  Size  Used by                                                                                             
rfkill_input           12800  0                                                                                                   
binfmt_misc            16776  1                                                                                                   
radeon                342816  2                                                                                                   
drm                    96424  3 radeon                                                                                            
ppdev                  15620  0                                                                                                   
bridge                 56212  0                                                                                                   
stp                    10500  1 bridge                                                                                            
bnep                   20224  2                                                                                                   
lp                     17156  0                                                                                                   
parport                42220  2 ppdev,lp                                                                                          
arc4                    9856  2                                                                                                   
ecb                    10752  2                                                                                                   
snd_hda_intel         434100  4                                                                                                   
snd_pcm_oss            46336  0                                                                                                   
snd_mixer_oss          22656  1 snd_pcm_oss                                                                                       
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss                                                                         
snd_seq_dummy          10756  0                                                                                                   
snd_seq_oss            37760  0                                                                                                   
snd_seq_midi           14336  0                                                                                                   
b43                   131484  0                                                                                                   
snd_rawmidi            29696  1 snd_seq_midi                                                                                      
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi                                                                          
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              217592  1 b43
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 44748  0
snd                    62756  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 18496  0
cfg80211               38288  1 mac80211
soundcore              15200  1 snd
ati_agp                14988  0
agpgart                42696  2 drm,ati_agp
i2c_piix4              18448  0
video                  25360  0
shpchp                 40212  0
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
led_class              12036  1 b43
yenta_socket           32396  1
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                61972  0
dcdbas                 15264  0
pcspkr                 10496  0
serio_raw              13444  0
output                 11008  1 video
k8temp                 12416  0
input_polldev          11912  1 b43
btusb                  19608  2
usbhid                 42336  0
ohci1394               38576  0
ieee1394               94660  1 ohci1394
tg3                   131204  0
ssb                    41220  1 b43
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

[B]sudo lspci:
[/B]00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

---

### Post by Haarlem on 2009-08-21
I guess after the first question being the search for a preventive solution, the second question is: If a reboot fixes the issue. Is there something like a reboot that is quicker. Like a mem dump or something else?

---

### Post by bchurchill on 2009-08-21
I'm guessing there's some process that's hogging your system.  Try running

```
top
```

to see what's taking memory/CPU.  You can kill the process using

```
killall <processname>
```

I've found that flash player often slows things down a lot especially in firefox... so the Youtube might be the culprit.  Usually killing firefox has done the job for me in the past.  (Although I guess you're probably using Konqueror)

Personally I like GNOME because it's not quite as graphically taxing.

---

### Post by prshah on 2009-08-21
> **Haarlem said:**
> It _*seems*_ like this performance drop occurs after using programs such as Wine/Pokerstars, 

There are often-documented cases of wineserver taking 100% cpu usage on quit. Perhaps you should check the top output for wineserver when next you face such an issue.

Killing wineserver will get everything back to normal within 1-2 seconds; in any case, generally taking a look at top output should be your first step when faced with sluggishness.

---

### Post by Haarlem on 2009-08-21
Thanks for the responses guys.

I have been checking top regularly, though maybe not at the correct times. I'll try this more efficiently to find the culprit.

I am using Firefox, so maybe it is the flash player doing the damage. Thinking of it, this is highly likely.

I like to watch some anime during a break. Is there any way to avoid the performance stomp that Firefox/flash are most likely causing? Possibly other browser? Or a fix?

---

