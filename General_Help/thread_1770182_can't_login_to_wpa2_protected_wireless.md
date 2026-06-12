---
title: "can't login to wpa2 protected wireless"
date: 2011-05-28
forum: General Help
---

### Post by n3140f on 2011-05-28
What does one do when you can't get help on the forums and your wireless won't work?

                                 I am having trouble connecting to the wireless network.
 

 I am using Linux Mint 11, kernel 2.6.38-8-genric-pae.  Not using ndiswrapper as I am sure I have the right driver.
 

 From reading the forums I saw that backports-wireless was solving some problems, but I was not able to find the correct one.  In terminal, I typed  sudo apt-get install linux-backports-modules-wireless-natty-generic ,  and got this:  E: Unable to locate package linux-backports-modules-wireless-natty-generic  
 

 .mpm-HP-Pavilion-dm3-Notebook-PC mpm # mintwifi  
 -------------------------  
 * I. scanning WIFI PCI devices...  
   -- Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)  
       ==> PCI ID = 168c:002a (rev 01)  
 -------------------------  
 * II. querying ndiswrapper...  
 -------------------------  
 * III. querying iwconfig...  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11abgn  ESSID:off/any   
           Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated    
           Tx-Power=18 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Encryption key:off  
           Power Management:off  
            
 -------------------------  
 * IV. querying ifconfig...  
 eth0      Link encap:Ethernet  HWaddr 00:21:cc:3f:73:9f   
           inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::221:ccff:fe3f:739f/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:2775 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:2982 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:2337844 (2.3 MB)  TX bytes:550774 (550.7 KB)  
           Interrupt:42 Base address:0xe000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:28 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:28 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:22:5f:ee:e7:16   
           inet6 addr: fe80::222:5fff:feee:e716/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:39 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:58 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:5265 (5.2 KB)  TX bytes:14726 (14.7 KB)  
 

 -------------------------  
 * V. querying DHCP...  
 -------------------------  
 * VI. querying nslookup google.com...  
 Server:        69.145.232.4  
 Address:    69.145.232.4#53  
 

 Non-authoritative answer:  
 Name:    google.com  
 Address: 74.125.227.48  
 Name:    google.com  
 Address: 74.125.227.49  
 Name:    google.com  
 Address: 74.125.227.50  
 Name:    google.com  
 Address: 74.125.227.51  
 Name:    google.com  
 Address: 74.125.227.52  
 

 mpm-HP-Pavilion-dm3-Notebook-PC mpm # sudo ifconfig wlan0 up  
 mpm-HP-Pavilion-dm3-Notebook-PC mpm # sudo apt-get install compat-wireless  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 E: Unable to locate package compat-wireless  
 mpm-HP-Pavilion-dm3-Notebook-PC mpm # sudo lshw |grep wireless  
                 capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless  
                 configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn 
 mpm-HP-Pavilion-dm3-Notebook-PC mpm # sudo modprobe wl  
 FATAL: Module wl not found.  
 mpm-HP-Pavilion-dm3-Notebook-PC mpm # auto wlan0  
 No command 'auto' found, did you mean:  
  Command 'uuto' from package 'uucp' (universe)  
 auto: command not found  
 mpm-HP-Pavilion-dm3-Notebook-PC mpm # wpa-ssid babywireless  
 wpa-ssid: command not found  
 mpm-HP-Pavilion-dm3-Notebook-PC mpm # ifup wlan0  
 Ignoring unknown interface wlan0=wlan0. 
 mpm-HP-Pavilion-dm3-Notebook-PC mpm #  auto eth0  
 No command 'auto' found, did you mean:  
  Command 'uuto' from package 'uucp' (universe)  
 auto: command not found  
 mpm-HP-Pavilion-dm3-Notebook-PC mpm # auto eth0  
 No command 'auto' found, did you mean:  
  Command 'uuto' from package 'uucp' (universe)  
 auto: command not found  
 mpm-HP-Pavilion-dm3-Notebook-PC mpm # iface eth0 inet dhcp  
 iface: command not found  
 mpm-HP-Pavilion-dm3-Notebook-PC mpm # lsusb  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 192f:0416 Avago Technologies, Pte.  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 004: ID 0603:8124 Novatek Microelectronics Corp.  
 Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 mpm-HP-Pavilion-dm3-Notebook-PC mpm # lspci -vvnn  
 00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-  
     Latency: 0  
     Capabilities: [c4] HyperTransport: Slave or Primary Interface  
         Command: BaseUnitID=1 UnitCnt=12 MastHost- DefDir- DUL-  
         Link Control 0: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b-  
         Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-  
         Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-  
         Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-  
         Revision ID: 3.00  
         Link Frequency 0: 800MHz  
         Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-  
         Link Frequency Capability 0: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-  
         Feature Capability: IsocFC- LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-  
         Link Frequency 1: 200MHz  
         Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-  
         Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-  
         Error Handling: PFlE- OFlE- PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE+ PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-  
         Prefetchable memory behind bridge Upper: 00-00  
         Bus Number: 00  
     Capabilities: [54] HyperTransport: UnitID Clumping  
     Capabilities: [40] HyperTransport: Retry Mode  
     Capabilities: [9c] HyperTransport: #1a 
     Capabilities: [f8] HyperTransport: #1c 
 

 00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602] (prog-if 00 [Normal decode])  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 64  
     Bus: primary=00, secondary=01, subordinate=01, sec-latency=0  
     I/O behind bridge: 00006000-00006fff  
     Memory behind bridge: f2100000-f22fffff  
     Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff  
     Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-  
     BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-  
         PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-  
     Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+  
     Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device [1022:1235]  
     Kernel modules: shpchp  
 

 00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604] (prog-if 00 [Normal decode])  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+  
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 0, Cache Line Size: 64 bytes  
     Bus: primary=00, secondary=02, subordinate=07, sec-latency=0  
     I/O behind bridge: 00002000-00005fff  
     Memory behind bridge: f1100000-f20fffff  
     Prefetchable memory behind bridge: 00000000f0000000-00000000f0ffffff  
     Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-  
     BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-  
         PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-  
     Capabilities: [50] Power Management version 3  
         Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)  
         Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-  
     Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00  
         DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us  
             ExtTag+ RBE+ FLReset-  
         DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-  
             RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+  
             MaxPayload 128 bytes, MaxReadReq 128 bytes  
         DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-  
         LnkCap:    Port #1, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <64ns, L1 <1us  
             ClockPM- Surprise- LLActRep+ BwNot+  
         LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+  
             ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-  
         LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-  
         SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+  
             Slot #4, PowerLimit 25.000W; Interlock- NoCompl+  
         SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-  
             Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-  
         SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-  
             Changed: MRL- PresDet+ LinkState+  
         RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-  
         RootCap: CRSVisible-  
         RootSta: PME ReqID 0000, PMEStatus- PMEPending-  
         DevCap2: Completion Timeout: Not Supported, TimeoutDis- ARIFwd-  
         DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-  
         LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB  
              Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-  
              Compliance De-emphasis: -6dB  
         LnkSta2: Current De-emphasis Level: -6dB  
     Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-  
         Address: fee0300c  Data: 4151  
     Capabilities: [b0] Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+  
     Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>  
     Capabilities: [110 v1] Virtual Channel 
         Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1  
         Arb:    Fixed- WRR32- WRR64- WRR128-  
         Ctrl:    ArbSelect=Fixed  
         Status:    InProgress-  
         VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-  
             Arb:    Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-  
             Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff  
             Status:    NegoPending- InProgress-  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp  
 

 00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605] (prog-if 00 [Normal decode])  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+  
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 0, Cache Line Size: 64 bytes  
     Bus: primary=00, secondary=08, subordinate=08, sec-latency=0  
     Memory behind bridge: f1000000-f10fffff  
     Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-  
     BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-  
         PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-  
     Capabilities: [50] Power Management version 3  
         Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)  
         Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-  
     Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00  
         DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us  
             ExtTag+ RBE+ FLReset-  
         DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-  
             RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+  
             MaxPayload 128 bytes, MaxReadReq 128 bytes  
         DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-  
         LnkCap:    Port #2, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <64ns, L1 <1us  
             ClockPM- Surprise- LLActRep+ BwNot+  
         LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+  
             ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-  
         LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-  
         SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-  
             Slot #5, PowerLimit 25.000W; Interlock- NoCompl+  
         SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-  
             Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-  
         SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-  
             Changed: MRL- PresDet+ LinkState+  
         RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-  
         RootCap: CRSVisible-  
         RootSta: PME ReqID 0000, PMEStatus- PMEPending-  
         DevCap2: Completion Timeout: Not Supported, TimeoutDis- ARIFwd-  
         DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-  
         LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB  
              Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-  
              Compliance De-emphasis: -6dB  
         LnkSta2: Current De-emphasis Level: -6dB  
     Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-  
         Address: fee0300c  Data: 4159  
     Capabilities: [b0] Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+  
     Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>  
     Capabilities: [110 v1] Virtual Channel 
         Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1  
         Arb:    Fixed- WRR32- WRR64- WRR128-  
         Ctrl:    ArbSelect=Fixed  
         Status:    InProgress-  
         VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-  
             Arb:    Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-  
             Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff  
             Status:    NegoPending- InProgress-  
     Kernel driver in use: pcieport  
     Kernel modules: shpchp  
 

 00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (prog-if 01 [AHCI 1.0])  
     Subsystem: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+  
     Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 64, Cache Line Size: 64 bytes 
     Interrupt: pin A routed to IRQ 43  
     Region 0: I/O ports at 7038 [size=8]  
     Region 1: I/O ports at 704c [size=4]  
     Region 2: I/O ports at 7030 [size=8]  
     Region 3: I/O ports at 7048 [size=4]  
     Region 4: I/O ports at 7010 [size=16]  
     Region 5: Memory at f2307000 (32-bit, non-prefetchable) [size=1K]  
     Capabilities: [50] MSI: Enable+ Count=1/8 Maskable- 64bit+  
         Address: 00000000fee0100c  Data: 4181 
     Capabilities: [70] SATA HBA v1.0 InCfgSpace  
     Kernel driver in use: ahci  
     Kernel modules: ahci  
 

 00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 64, Cache Line Size: 64 bytes 
     Interrupt: pin A routed to IRQ 16  
     Region 0: Memory at f2306000 (32-bit, non-prefetchable) [size=4K]  
     Kernel driver in use: ohci_hcd  
 

 00:12.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398] (prog-if 10 [OHCI])  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 64, Cache Line Size: 64 bytes 
     Interrupt: pin A routed to IRQ 16  
     Region 0: Memory at f2305000 (32-bit, non-prefetchable) [size=4K]  
     Kernel driver in use: ohci_hcd  
 

 00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 64, Cache Line Size: 64 bytes 
     Interrupt: pin B routed to IRQ 17  
     Region 0: Memory at f2307500 (32-bit, non-prefetchable) [size=256]  
     Capabilities: [c0] Power Management version 2  
         Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)  
         Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-  
         Bridge: PM- B3+  
     Capabilities: [e4] Debug port: BAR=1 offset=00e0  
     Kernel driver in use: ehci_hcd  
 

 00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 64, Cache Line Size: 64 bytes 
     Interrupt: pin A routed to IRQ 18  
     Region 0: Memory at f2304000 (32-bit, non-prefetchable) [size=4K]  
     Kernel driver in use: ohci_hcd  
 

 00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 64, Cache Line Size: 64 bytes 
     Interrupt: pin B routed to IRQ 19  
     Region 0: Memory at f2307400 (32-bit, non-prefetchable) [size=256]  
     Capabilities: [c0] Power Management version 2  
         Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)  
         Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-  
         Bridge: PM- B3+  
     Capabilities: [e4] Debug port: BAR=1 offset=00e0  
     Kernel driver in use: ehci_hcd  
 

 00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+  
     Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+  
     Kernel modules: sp5100_tco, i2c-piix4  
 

 00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 64, Cache Line Size: 64 bytes 
     Interrupt: pin ? routed to IRQ 16  
     Region 0: Memory at f2300000 (64-bit, non-prefetchable) [size=16K]  
     Capabilities: [50] Power Management version 2  
         Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)  
         Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-  
     Kernel driver in use: HDA Intel  
     Kernel modules: snd-hda-intel  
 

 00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 0  
 

 00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01 [Subtractive decode])  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 64  
     Bus: primary=00, secondary=09, subordinate=09, sec-latency=64  
     I/O behind bridge: 00001000-00001fff  
     Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-  
     BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-  
         PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-  
 

 00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]  
     Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Capabilities: [80] HyperTransport: Host or Secondary Interface  
         Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL-  
         Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=8 IsocEn- LSEn+ ExtCTL- 64b+  
         Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-  
         Revision ID: 1.02  
         Link Frequency: 800MHz  
         Link Error: <Prot- <Ovfl- <EOC- CTLTm-  
         Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-  
         Feature Capability: IsocFC- LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD- ExtRS- UCnfE-  
 

 00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]  
     Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
 

 00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102] 
     Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
 

 00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]  
     Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Capabilities: [f0] Secure device <?> 
     Kernel driver in use: k8temp  
     Kernel modules: k8temp  
 

 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612] (prog-if 00 [VGA controller])  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 0, Cache Line Size: 64 bytes  
     Interrupt: pin A routed to IRQ 18  
     Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]  
     Region 1: I/O ports at 6000 [size=256] 
     Region 2: Memory at f2200000 (32-bit, non-prefetchable) [size=64K]  
     Region 5: Memory at f2100000 (32-bit, non-prefetchable) [size=1M]  
     Expansion ROM at <unassigned> [disabled]  
     Capabilities: [50] Power Management version 3  
         Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)  
         Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-  
     Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+  
         Address: 0000000000000000  Data: 0000 
     Kernel driver in use: fglrx_pci  
     Kernel modules: fglrx, radeon  
 

 01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 0, Cache Line Size: 64 bytes  
     Interrupt: pin B routed to IRQ 19  
     Region 0: Memory at f2210000 (32-bit, non-prefetchable) [size=16K]  
     Capabilities: [50] Power Management version 3  
         Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)  
         Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-  
     Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+  
         Address: 0000000000000000  Data: 0000 
     Kernel driver in use: HDA Intel  
     Kernel modules: snd-hda-intel  
 

 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)  
     Subsystem: Hewlett-Packard Company Device [103c:3656]  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+  
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 0, Cache Line Size: 64 bytes  
     Interrupt: pin A routed to IRQ 42  
     Region 0: I/O ports at 2000 [size=256] 
     Region 2: Memory at f0010000 (64-bit, prefetchable) [size=4K]  
     Region 4: Memory at f0000000 (64-bit, prefetchable) [size=64K]  
     Expansion ROM at f0020000 [disabled] [size=128K]  
     Capabilities: [40] Power Management version 3  
         Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)  
         Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-  
     Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+  
         Address: 00000000fee0100c  Data: 4171 
     Capabilities: [70] Express (v2) Endpoint, MSI 01  
         DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <128ns, L1 <2us  
             ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-  
         DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-  
             RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-  
             MaxPayload 128 bytes, MaxReadReq 4096 bytes  
         DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-  
         LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us  
             ClockPM+ Surprise- LLActRep- BwNot-  
         LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+  
             ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-  
         LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-  
         DevCap2: Completion Timeout: Not Supported, TimeoutDis+  
         DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-  
         LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB  
              Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-  
              Compliance De-emphasis: -6dB  
         LnkSta2: Current De-emphasis Level: -6dB  
     Capabilities: [ac] MSI-X: Enable- Count=2 Masked-  
         Vector table: BAR=4 offset=00000000  
         PBA: BAR=4 offset=00000800  
     Capabilities: [cc] Vital Product Data  
         Unknown small resource type 00, will not decode more.  
     Capabilities: [100 v1] Advanced Error Reporting  
         UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-  
         UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-  
         UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-  
         CESta:    RxErr+ BadTLP+ BadDLLP- Rollover- Timeout- NonFatalErr+  
         CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+  
         AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-  
     Capabilities: [140 v1] Virtual Channel 
         Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1  
         Arb:    Fixed- WRR32- WRR64- WRR128-  
         Ctrl:    ArbSelect=Fixed  
         Status:    InProgress-  
         VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-  
             Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-  
             Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff  
             Status:    NegoPending- InProgress-  
     Capabilities: [160 v1] Device Serial Number 01-00-00-00-ff-ff-00-00  
     Kernel driver in use: r8169  
     Kernel modules: r8169  
 

 08:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)  
     Subsystem: Hewlett-Packard Company Device [103c:3041]  
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
     Latency: 0, Cache Line Size: 64 bytes  
     Interrupt: pin A routed to IRQ 17  
     Region 0: Memory at f1000000 (64-bit, non-prefetchable) [size=64K]  
     Capabilities: [40] Power Management version 2  
         Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold-)  
         Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-  
     Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-  
         Address: 00000000  Data: 0000  
     Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00  
         DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us  
             ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-  
         DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-  
             RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-  
             MaxPayload 128 bytes, MaxReadReq 512 bytes  
         DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-  
         LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM unknown, Latency L0 <512ns, L1 <64us  
             ClockPM- Surprise- LLActRep- BwNot-  
         LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+  
             ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-  
         LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-  
     Capabilities: [90] MSI-X: Enable- Count=1 Masked-  
         Vector table: BAR=0 offset=00000000  
         PBA: BAR=0 offset=00000000  
     Capabilities: [100 v1] Advanced Error Reporting  
         UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-  
         UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-  
         UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-  
         CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-  
         CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-  
         AERCap:    First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-  
     Capabilities: [140 v1] Virtual Channel 
         Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1  
         Arb:    Fixed- WRR32- WRR64- WRR128-  
         Ctrl:    ArbSelect=Fixed  
         Status:    InProgress-  
         VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-  
             Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-  
             Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff  
             Status:    NegoPending- InProgress-  
     Capabilities: [160 v1] Device Serial Number 00-00-00-00-00-00-00-00  
     Kernel driver in use: ath9k  
     Kernel modules: ath9k
 

   
 MADWIFI: Multimode Atheros Driver for WiFi on Linux (VAP branch)  
 ================================================================ 
 

 * Copyright (c) 2002-2005 Sam Leffler.  All rights reserved.  
 

 Read the file COPYRIGHT for the complete copyright.  
 

 

 Requirements  
 ------------  
 

 - Configured kernel sources of the target kernel.  Some Linux  
   distributions provide headers, makefiles and configuration data - it  
   should suffice.  
 

 - Wireless Extensions support (14 or later, 17 preferred) - option  
   CONFIG_NET_RADIO in kernel .config file.  
 

 - Sysctl support - option CONFIG_SYSCTL in kernel .config file.  
 

 - Crypto API support - option CONFIG_CRYPTO in kernel .config file (AES  
   support is used if present, otherwise the AES-CCMP cipher module falls  
   back to a private implementation).  
 

 - gcc of same version that was used to compile the kernel.  At least  
   make sure that the first two version numbers or the compiler are the  
   same (e.g. it's OK to use gcc 3.4.6 to compile MadWifi if the kernel  
   was compiled by gcc 3.4.2).  Ignoring this rule will cause "Invalid  
   module format" errors during module load.  
 

 Linux 2.4.x kernels starting with 2.4.22 and 2.6 kernels should work  
 without problems.  Due to quick pace of Linux development, there is no  
 way compatibility with the future 2.6 kernels can be ensured.  However,  
 the latest 2.6 kernel at the time of the release should be expected to  
 work.  
 

 Automatic module loading support (CONFIG_KMOD) is recommended; otherwise,  
 care will have to be taken to manually load needed modules.  
 

 Building the driver  
 -------------------  
 

 The driver is built using the Linux kernel build mechanism.  This means  
 you must have some part of the kernel source distribution installed on  
 the machine where you want to build the driver.  In particular, the  
 kernel include files, makefiles, build scripts and configuration must be  
 available.  
 

 This will be present if you built your kernel from source.  Otherwise  
 you may need to install an additional kernel development package from  
 your distribution that would match your kernel.  For example, the  
 development package for the default kernel is called linux-headers on  
 Debian and kernel-devel on Fedora Core.  Installing a package with full  
 kernel sources should not be generally necessary.  
 

 Note: in the following examples "$" stands for your system prompt;  
 you're not expected to type that as part of the actual command.  "#"  
 stands for the command prompt when the commands must be executed by  
 root.  
 

 Most people can just type:  
 

   $ make  
 

 in the top-level MadWifi source directory to build all the modules for  
 the currently running system.  
 

 You MUST do a "make clean" before compiling for a different version of  
 Linux, e.g. building for 2.6 after building for 2.4.  
 

 If you want to compile MadWifi for a different kernel, you need to  
 specify the location of the kernel build tree, e.g.:  
 

   $ make KERNELPATH=/usr/src/linux-2.6.3  
 

 Note that you can also specify this path by setting an environment  
 variable; e.g.  
 

   $ export KERNELPATH=/usr/src/linux-2.6.3  
   $ make  
   
 If the kernel was built outside the source directory, KERNELPATH should  
 point to the output directory where .config is located, not to the  
 sources.  
 

 MadWifi currently provides four different rate control algorithms,  
 ONOE, AMRR, SAMPLE and MINSTREL.  SAMPLE and MINSTREL are both very  
 advanced, but MINSTREL is quite new.  Consequently, SAMPLE is used by  
 default.  In order to make MadWifi use e.g. AMRR instead, you have to  
 specify that as the module parameter e.g.  
 

   # modprobe ath_pci ratectl=amrr  
 

 NOTE: Changing the rate control is only required (and recommended) for  
       users who want to setup an access point using MadWifi in difficult  
       (e.g. lossy) environments and who know what they are doing.  
 

 This distribution includes support for a variety of target platforms.  
 Because of the binary nature of the HAL not all platforms are supported  
 (the list grows as time permits).  The supported target platforms can be  
 found with:  
 

   $ ls hal/public/*.inc  
 

 A target specifies the CPU architecture, byte order (unless implied by  
 the CPU), and the ABI/file format.  For most popular platforms, the  
 build system will find the appropriate files.  When cross-compiling or  
 compiling for less common platforms, the target platform may need to be  
 specified using the TARGET variable, e.g:  
 

   $ make TARGET=armv4-le-elf  
 

 Consult the contents of the .inc file to find out what the target  
 platform is and what toolchain was used to build the HAL object module.  
 Beware of mixing toolchains; some target platforms require that the HAL  
 and driver be built with the same toolchain (i.e. compiler, assembler,  
 and linker) and the same compiler flags.  If you get warnings about  
 incompatible compiler flags, chances are that you are compiling for a  
 wrong target or using an incompatible compiler.  
 

 

 Cross-compiling  
 ---------------  
 

 The build system is designed to support cross-compiling without any  
 modification to the distribution files.  It should be sufficient to  
 specify any parameters on the make command line.  
 

 In most cases, only KERNELPATH and CROSS_COMPILE need to be defined.  
 CROSS_COMPILE is the prefix for cross-compiling tools.  For instance, if  
 the cross compiler is called arm-linux-gcc, set CROSS_COMPILE to  
 "arm-linux-":  
 

   $ make KERNELPATH=/usr/src/linux-arm CROSS_COMPILE=arm-linux-  
 

 The build system determines ARCH and TARGET based on the .config file in  
 the Linux build tree.  TARGET still may need to be provided on the  
 command line some uncommon systems.  If ARCH is determined incorrectly,  
 please report it.  
 

 

 Loading the modules  
 -------------------  
 

 Building the software will generate numerous loadable modules:  
 

   ath_pci        Atheros driver for PCI/Cardbus devices  
   ath_hal        Atheros HAL  
   wlan            802.11 support layer  
   wlan_wep        WEP cipher support  
   wlan_tkip        TKIP cipher support  
   wlan_ccmp        AES-CCMP cipher support  
   wlan_xauth        external authenticator  
   wlan_acl        MAC ACL support for AP operation  
   wlan_scan_ap        AP scanning support  
   wlan_scan_sta        station scanning support  
   ath_rate_onoe        ONOE rate control  
   ath_rate_amrr        AMRR rate control  
   ath_rate_sample    SAMPLE rate control  
 

 The ath_pci module must be loaded either manually or by the system, e.g.  
 through the hotplug or card manager support.  The remaining modules are  
 loaded automatically as needed, so after doing a "make install" you only  
 need to run following:  
 

   # modprobe ath_pci  
 

 For automatic module loading you may need to modify your system's  
 configuration files so the necessary modules are loaded when an Atheros  
 device is recognized.  The exact procedure varies from system to system.  
 

 There are module parameters available to fit your needs, e.g. you can  
 set the countrycode manually if your card's EEPROM does not contain the  
 correct one for your location.  See  
 [http://www.unicode.org/onlinedat/countries.html](http://www.unicode.org/onlinedat/countries.html) to find your code.  
 

 To activate German frequencies you would specify:  
 

   # modprobe ath_pci countrycode=276  
 

 To see all available module parameters type:  
 

   $ modinfo ath_pci  
 

 

 Integrating into the kernel sources  
 -----------------------------------  
 

 It is also possible to patch Linux kernel sources to integrate MadWifi  
 directly into the kernel tree.  This allows building MadWifi as part of  
 the kernel.  This could be useful for embedded systems that don't  
 support loadable modules.  Please refer to patches/README for details.  
 

 

 Further information  
 -------------------  
 

 Further information on how to work with the driver can be found in the  
 file README.  In addition, the project's wiki has a lot of valuable  
 information:  
 

 [http://madwifi.org/](http://madwifi.org/)
 

 

 

 how about this:  and thanks for playing:
 

 mpm@mpm-HP-Pavilion-dm3-Notebook-PC ~ $ iwconfig wlan0 essid babywireless  
 Error for wireless request "Set ESSID" (8B1A) :  
     SET failed on device wlan0 ; Operation not permitted.  
 

 

 Self-explanatory... I am using a Static IP instead of DHCP. "iface wlan0" must correspond to your network interface (see above).
 

 Self expanatory? – hey there is a gun with a bullet in it on the shelf right behind me – now THAT”S self explanotory!
 _**wpa-driver:**_
Use "wext" only. All other drivers are outdated no longer used.
[/QUOTE]
 

 then what?
 

 Isn't most of this stuff built into the new kernals?  Then why do I always get referred to a thread written in 2006 and then wreck my machine and have to re-install?
 

 And  as to re-installing – to quote B.B. King:  “The Thrill is Gone”.
 

 Archive:  /tmp/sp45635.exe  
 [/tmp/sp45635.exe]  
   End-of-central-directory signature not found.  Either this file is not  
   a zipfile, or it constitutes one disk of a multi-part archive.  In the  
   latter case the central directory and zipfile comment will be found on  
   the last disk(s) of this archive.  
 zipinfo:  cannot find zipfile directory in one of /tmp/sp45635.exe or  
           /tmp/sp45635.exe.zip, and cannot find /tmp/sp45635.exe.ZIP, period.  
 

 

 Isn't this getting fun after about 50 hours?  Remember always have fun with linux.  It's fun, right?
 

I know noone will talk to me.  Thanks for playing anyway.  It was fun.

---

