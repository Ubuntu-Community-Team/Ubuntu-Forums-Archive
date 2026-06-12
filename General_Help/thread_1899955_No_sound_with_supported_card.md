---
title: "No sound with supported card?"
date: 2011-12-24
forum: General Help
---

### Post by chip616 on 2011-12-24
I have a fresh install of Kubuntu 11.10 with all current updates on an older IBM / Lenovo desktop.  The internal sound card is disabled in the BIOS.  I have installed a [PPA International sound card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829126005") which uses the VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller chipset.  This device uses the ICE1724 kernel module, which appears to be installed.

I am getting no sound.

I have all the channels unmuted in alsamixer, and have most of them either fully up, or partway up.  I will try to attach a screenshot of ALSA, but I've not had a lot of success posting graphics in this forum.

Below that are the outputs from aplay and lspci.

AFAIK, everything is in place.  What am I doing wrong?  What settings do I need in alsamixer to get this going?

I am trying to use the S/PDIF optical output on the card, and I have an external DAC feeding an input on my stereo.  I know the hardware works, as I installed WinXP on this machine to test it.  It works fine.  Can't make it go in Kubuntu 11.10

Any help appreciated.  I've been through the forum, and gone through the Comprehensive Sound Problems...  steps just short of recompiling alsa.  AFAIK, this card should work out of the box, so it mus be something that I have set wrong.

Thanks.

Frank.

OK, I can't figure out how to embed a graphic in this forum.  I have screenshots posted elsewhere. [Try this link.]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=131067")  It is in message #7.





> guest@media:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICE1724 [ICEnsemble ICE1724], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
guest@media:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface
        Flags: bus master, fast devsel, latency 0
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=80
        Memory behind bridge: d2000000-d5ffffff
        Prefetchable memory behind bridge: e0000000-f0ffffff
        Kernel modules: shpchp

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
        Flags: fast devsel
        Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM Device 0285
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM Device 0285
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM Device 0285                                                                                                                                                                                                                                                                                                                                                                                                                                                        
        Flags: bus master, medium devsel, latency 0, IRQ 18                                                                                                                                                                                                                                                                                                                                                                                                                               
        I/O ports at 1840 [size=32]                                                                                                                                                                                                                                                                                                                                                                                                                                                       
        Kernel driver in use: uhci_hcd                                                                                                                                                                                                                                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])                                                                                                                                                                                                                                                                                                                                                                     
        Subsystem: IBM Device 0285                                                                                                                                                                                                                                                                                                                                                                                                                                                        
        Flags: bus master, medium devsel, latency 0, IRQ 16                                                                                                                                                                                                                                                                                                                                                                                                                               
        I/O ports at 1860 [size=32]                                                                                                                                                                                                                                                                                                                                                                                                                                                       
        Kernel driver in use: uhci_hcd
                                                                                                                                                                              
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])                                                           
        Subsystem: IBM Device 0285                                                                                                                                            
        Flags: bus master, medium devsel, latency 0, IRQ 23                                                                                                                   
        Memory at d0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>                                                                                                                                         
        Kernel driver in use: ehci_hcd
                                                                                                                                                                              
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])                                                                                  
        Flags: bus master, fast devsel, latency 0                                                                                                                             
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=200                                                                                                        
        I/O behind bridge: 00002000-00002fff                                                                                                                                  
        Memory behind bridge: d6000000-d60fffff                                                                                                                               
        Kernel modules: shpchp                                                                                                                                                
                                                                                                                                                                              
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0                                                                                                                           
        Kernel modules: iTCO_wdt, intel-rng                                                                                                                                   
                                                                                                                                                                              
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])                                                      
        Subsystem: IBM Device 0285                                                                                                                                            
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]                                                                                                                                            
        I/O ports at 03f4 [size=1]                                                                                                                                            
        I/O ports at 0170 [size=8]                                                                                                                                            
        I/O ports at 0374 [size=1]                                                                                                                                            
        I/O ports at 1880 [size=16]                                                                                                                                           
        Memory at a0000000 (32-bit, non-prefetchable) [size=1K]
        Kernel driver in use: ata_piix                                                                                                                                        
                                                                                                                                                                              
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)                                                                                            
        Subsystem: IBM Device 0285                                                                                                                                            
        Flags: medium devsel, IRQ 9
        I/O ports at 18a0 [size=32]                                                                                                                                           
        Kernel modules: i2c-i801                                                                                                                                              

01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7300 GT] (rev a2) (prog-if 00 [VGA controller])                                                            
        Subsystem: eVga.com. Corp. Device a501
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at d4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at f0000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia_173, nouveau, nvidiafb

03:0a.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
        Subsystem: VIA Technologies Inc. Device 2403
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at 20c0 [size=32]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: ICE1724
        Kernel modules: snd-ice1724

03:0b.0 Ethernet controller: Intel Corporation 82541EI Gigabit Ethernet Controller
        Subsystem: IBM Device 0285
        Flags: bus master, 66MHz, medium devsel, latency 52, IRQ 16
        Memory at d6000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 2080 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: e1000
        Kernel modules: e1000

03:0c.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01) (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 48, IRQ 20
        Memory at d6020000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: firewire_ohci
        Kernel modules: firewire-ohci

guest@media:~$

---

### Post by chip616 on 2011-12-27
Update:

I gave up on the sound card.

The new NVIDIA video cards have HDMI out, which includes digital audio.  I went and bought an Asus GT520 Silent (no fan) and installed that, pulling the sound card out at the same time.  The flatscreen TV has s/pdif out.  I connected that to my DAC with an optical cable, and from the DAC to my stereo amplifier with regular audio cables.  I put in a new 1 TB drive into the old Dell Optiplex, an HDMI cable between the NVIDIA card and the flatscreen TV, and installed Kubuntu 11.10 with the option to update files as it goes, and also to install third party software.  Once the install was complete, I had beautiful 1920 x 1080 video, and crystal clear and smooth digital sound!!  No other tweaking necessary.  It just ran.

Sometimes its better to try another solution....

Frank.

---

