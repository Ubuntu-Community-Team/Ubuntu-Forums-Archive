---
title: "Skippy sound in 9.04"
date: 2009-06-29
forum: General Help
---

### Post by Tomash on 2009-06-29
Yesterday I did a dist-upgrade of Kubuntu 8.10 to 9.04 on my laptop. All went pretty good, but now I have a serious issue with audio.

When playing (music or videos) the sound is choppy/skippy, i.e. a given second (sometimes it's every second, sometimes it's one of 2-5) plays faster than it should (lasts less than a full second should). It results in the sound being sped up and chopped to fit in this partial-second.

I've googled a lot and followed a tutorial on this forum on setting PulseAudio (by removing old asound config files and installing PulseAudio tools) and it didn't help at all.

Issue tested with Songbird (my only music player), Audacity and various MPlayer frontends. Audacity seems to be handling it after a few initial choppy seconds, while Songbird seems to be worst affected: music is completely un-hearable.

The issue actually affects also video playback: youtube videos are stuttery the same way, with video following the audio (i.e. also being choppy and seconds are shorter than they really are).

My laptop is Asus F80S

lspci output:
```
tomek@tomek-asus-f80s:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
        Subsystem: ASUSTeK Computer Inc. Device 1847       
        Flags: bus master, medium devsel, latency 64       
        Kernel modules: sis-agp                            

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
        Flags: bus master, fast devsel, latency 0                     
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0  
        I/O behind bridge: 0000d000-0000dfff                          
        Memory behind bridge: fde00000-fdefffff                       
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>                                       
        Kernel driver in use: pcieport-driver                               
        Kernel modules: shpchp                                              

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
        Flags: bus master, medium devsel, latency 0                                   

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Device 1847                                             
        Flags: bus master, medium devsel, latency 128                                            
        I/O ports at 01f0 [size=8]                                                               
        I/O ports at 03f4 [size=1]                                                               
        I/O ports at 0170 [size=8]                                                               
        I/O ports at 0374 [size=1]                                                               
        I/O ports at fff0 [size=16]                                                              
        Capabilities: <access denied>                                                            
        Kernel driver in use: pata_sis                                                           

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 1847                                             
        Flags: bus master, medium devsel, latency 64, IRQ 20                                     
        Memory at fddff000 (32-bit, non-prefetchable) [size=4K]                                  
        Kernel driver in use: ohci_hcd                                                           

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 1847                                             
        Flags: bus master, medium devsel, latency 64, IRQ 21                                     
        Memory at fddfe000 (32-bit, non-prefetchable) [size=4K]                                  
        Kernel driver in use: ohci_hcd                                                           

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20)
        Subsystem: ASUSTeK Computer Inc. Device 1847                                    
        Flags: bus master, medium devsel, latency 64, IRQ 22                            
        Memory at fddfd000 (32-bit, non-prefetchable) [size=4K]                         
        Capabilities: <access denied>                                                   
        Kernel driver in use: ehci_hcd                                                  

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
        Subsystem: ASUSTeK Computer Inc. Device 1815                                               
        Flags: bus master, medium devsel, latency 0, IRQ 19                                        
        Memory at fddfcc00 (32-bit, non-prefetchable) [size=128]                                   
        I/O ports at cc00 [size=128]                                                               
        Capabilities: <access denied>                                                              
        Kernel driver in use: sis190                                                               
        Kernel modules: sis190                                                                     

00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])                                                                                                   
        Subsystem: ASUSTeK Computer Inc. Device 1847                                                                
        Flags: bus master, medium devsel, latency 64, IRQ 17                                                        
        I/O ports at c800 [size=8]                                                                                  
        I/O ports at c400 [size=4]                                                                                  
        I/O ports at c000 [size=8]                                                                                  
        I/O ports at bc00 [size=4]                                                                                  
        I/O ports at b800 [size=16]                                                                                 
        I/O ports at b400 [size=128]                                                                                
        Capabilities: <access denied>                                                                               
        Kernel driver in use: sata_sis                                                                              

00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
        Flags: bus master, fast devsel, latency 0                     
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0  
        Memory behind bridge: fdf00000-fdffffff                       
        Capabilities: <access denied>                                 
        Kernel driver in use: pcieport-driver                         
        Kernel modules: shpchp                                        

00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
        Flags: bus master, fast devsel, latency 0                     
        Bus: primary=00, secondary=03, subordinate=06, sec-latency=0  
        I/O behind bridge: 0000e000-0000efff                          
        Memory behind bridge: fe000000-febfffff                       
        Prefetchable memory behind bridge: 00000000fa000000-00000000fcffffff
        Capabilities: <access denied>                                       
        Kernel driver in use: pcieport-driver                               
        Kernel modules: shpchp                                              

00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
        Subsystem: ASUSTeK Computer Inc. Device 19c3                          
        Flags: bus master, medium devsel, latency 0, IRQ 18                   
        Memory at fddf4000 (32-bit, non-prefetchable) [size=16K]              
        Capabilities: <access denied>                                         
        Kernel driver in use: HDA Intel                                       
        Kernel modules: snd-hda-intel

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
        Subsystem: ASUSTeK Computer Inc. Device 19e2
        Flags: bus master, fast devsel, latency 0, IRQ 2300
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at d800 [size=256]
        Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fdec0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
        Subsystem: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fdeec000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Device 1a3b:1067
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```

EDIT: adding myself to pulse-rt group doesn't help at all (and has actually borked KDE system sounds like the welcome one)

---

### Post by Hilko on 2009-07-25
Same problem here. I have a fresh install of 9.04 on an ext4 partition and my sound is terrible. It skips every second.
Before this i had 9.04 on ext3, that was upgraded from 8.04 to 8.10 to 9.04 and i didn't have problems with sound at all.

---

