---
title: "Please help me in solving the TV setup in my UBUNTU machine"
date: 2009-10-06
forum: General Help
---

### Post by George Lukose on 2009-10-06
Please help me in solving the TV setup in my UBUNTU machine

I am from INDIA .I am using TATASKY( DTH India Satellite TV) as my digicomp .
I have dual OS. WIN XP and UBUNTU 9.04 EXT4 file system.
In WIN XP i am able to see TATASKY( DTH India Satellite TV) channals .But in UBUNTU i could not see it.


My machine details ate given below.


george@george-desktop:~$ grep -i dvb /var/log/messages
Oct  1 21:46:37 george-desktop kernel: [   12.782948] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
Oct  1 21:46:37 george-desktop kernel: [   12.782966] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
Oct  1 21:46:37 george-desktop kernel: [   12.782983] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
Oct  1 21:46:37 george-desktop kernel: [   12.782987] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
Oct  1 21:46:37 george-desktop kernel: [   12.783014] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
Oct  1 21:46:37 george-desktop kernel: [   12.783017] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
Oct  1 21:46:37 george-desktop kernel: [   12.783058] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
Oct  1 21:46:37 george-desktop kernel: [   12.783061] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
Oct  1 21:46:37 george-desktop kernel: [   12.783065] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
Oct  1 21:46:37 george-desktop kernel: [   12.783072] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
Oct  1 21:46:37 george-desktop kernel: [   12.783091] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
Oct  1 21:46:37 george-desktop kernel: [   12.783103] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
Oct  1 21:46:37 george-desktop kernel: [   12.783123] saa7134:   card=103 -> Compro Videomate DVB-T200A              
Oct  1 21:46:37 george-desktop kernel: [   12.783126] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
Oct  1 21:46:37 george-desktop kernel: [   12.783160] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
Oct  1 21:46:37 george-desktop kernel: [   12.783220] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
Oct  1 21:46:37 george-desktop kernel: [   12.783226] saa7134:   card=133 -> NXP Snake DVB-S reference design        
Oct  1 21:46:37 george-desktop kernel: [   12.783248] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
Oct  1 21:46:37 george-desktop kernel: [   12.783251] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
Oct  1 21:46:37 george-desktop kernel: [   12.783264] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636
Oct  1 22:57:13 george-desktop kernel: [    9.307629] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
Oct  1 22:57:13 george-desktop kernel: [    9.307646] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
Oct  1 22:57:13 george-desktop kernel: [    9.307663] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
Oct  1 22:57:13 george-desktop kernel: [    9.307667] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
Oct  1 22:57:13 george-desktop kernel: [    9.307692] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
Oct  1 22:57:13 george-desktop kernel: [    9.307695] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
Oct  1 22:57:13 george-desktop kernel: [    9.307735] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
Oct  1 22:57:13 george-desktop kernel: [    9.307738] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
Oct  1 22:57:13 george-desktop kernel: [    9.307742] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
Oct  1 22:57:13 george-desktop kernel: [    9.307748] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
Oct  1 22:57:13 george-desktop kernel: [    9.307767] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502george@george-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

=============================================

george@george-desktop:~$ lspci -k
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
    Kernel driver in use: agpgart-amd64
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
    Kernel modules: shpchp
00:0c.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)
    Kernel driver in use: serial
00:0d.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
    Kernel driver in use: saa7134
    Kernel modules: saa7134
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
    Kernel driver in use: sata_via
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
    Kernel driver in use: pata_via
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Kernel driver in use: uhci_hcd
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Kernel driver in use: uhci_hcd
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Kernel driver in use: uhci_hcd
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Kernel driver in use: uhci_hcd
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
    Kernel driver in use: ehci_hcd
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Kernel modules: i2c-viapro
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
    Kernel modules: snd-via82xx-modem
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Kernel driver in use: k8temp
    Kernel modules: k8temp
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
george@george-desktop:~$ 

Oct  1 22:57:13 george-desktop kernel: [    9.307779] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
Oct  1 22:57:13 george-desktop kernel: [    9.307798] saa7134:   card=103 -> Compro Videomate DVB-T200A              
Oct  1 22:57:13 george-desktop kernel: [    9.307800] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
Oct  1 22:57:13 george-desktop kernel: [    9.307834] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
Oct  1 22:57:13 george-desktop kernel: [    9.307892] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
Oct  1 22:57:13 george-desktop kernel: [    9.307898] saa7134:   card=133 -> NXP Snake DVB-S reference design        
Oct  1 22:57:13 george-desktop kernel: [    9.307919] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
Oct  1 22:57:13 george-desktop kernel: [    9.307922] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
Oct  1 22:57:13 george-desktop kernel: [    9.307934] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636
Oct  1 23:57:53 george-desktop kernel: [   20.552561] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
Oct  1 23:57:53 george-desktop kernel: [   20.552578] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
Oct  1 23:57:53 george-desktop kernel: [   20.552594] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
Oct  1 23:57:53 george-desktop kernel: [   20.552598] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
Oct  1 23:57:53 george-desktop kernel: [   20.552624] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
Oct  1 23:57:53 george-desktop kernel: [   20.552627] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
Oct  1 23:57:53 george-desktop kernel: [   20.552666] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
Oct  1 23:57:53 george-desktop kernel: [   20.552670] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
Oct  1 23:57:53 george-desktop kernel: [   20.552673] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
Oct  1 23:57:53 george-desktop kernel: [   20.552680] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
Oct  1 23:57:53 george-desktop kernel: [   20.552698] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
Oct  1 23:57:53 george-desktop kernel: [   20.552710] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
Oct  1 23:57:53 george-desktop kernel: [   20.552729] saa7134:   card=103 -> Compro Videomate DVB-T200A              
Oct  1 23:57:53 george-desktop kernel: [   20.552732] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
Oct  1 23:57:53 george-desktop kernel: [   20.552765] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
Oct  1 23:57:53 george-desktop kernel: [   20.552823] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
Oct  1 23:57:53 george-desktop kernel: [   20.552828] saa7134:   card=133 -> NXP Snake DVB-S reference design        
Oct  1 23:57:53 george-desktop kernel: [   20.552849] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
Oct  1 23:57:53 george-desktop kernel: [   20.552852] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
Oct  1 23:57:53 george-desktop kernel: [   20.552865] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636
Oct  2 08:19:08 george-desktop kernel: [   13.782573] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
Oct  2 08:19:08 george-desktop kernel: [   13.782590] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
Oct  2 08:19:08 george-desktop kernel: [   13.782606] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
Oct  2 08:19:08 george-desktop kernel: [   13.782610] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
Oct  2 08:19:08 george-desktop kernel: [   13.782635] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
Oct  2 08:19:08 george-desktop kernel: [   13.782638] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
Oct  2 08:19:08 george-desktop kernel: [   13.782677] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
Oct  2 08:19:08 george-desktop kernel: [   13.782680] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
Oct  2 08:19:08 george-desktop kernel: [   13.782684] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
Oct  2 08:19:08 george-desktop kernel: [   13.782691] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
Oct  2 08:19:08 george-desktop kernel: [   13.782710] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
Oct  2 08:19:08 george-desktop kernel: [   13.782721] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
Oct  2 08:19:08 george-desktop kernel: [   13.782740] saa7134:   card=103 -> Compro Videomate DVB-T200A              
Oct  2 08:19:08 george-desktop kernel: [   13.782742] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
Oct  2 08:19:08 george-desktop kernel: [   13.782776] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
Oct  2 08:19:08 george-desktop kernel: [   13.782833] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
Oct  2 08:19:08 george-desktop kernel: [   13.782839] saa7134:   card=133 -> NXP Snake DVB-S reference design        
Oct  2 08:19:08 george-desktop kernel: [   13.782860] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
Oct  2 08:19:08 george-desktop kernel: [   13.782863] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
Oct  2 08:19:08 george-desktop kernel: [   13.782875] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636
Oct  3 09:01:46 george-desktop kernel: [    9.410424] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
Oct  3 09:01:46 george-desktop kernel: [    9.410441] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
Oct  3 09:01:46 george-desktop kernel: [    9.410457] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
Oct  3 09:01:46 george-desktop kernel: [    9.410461] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
Oct  3 09:01:46 george-desktop kernel: [    9.410487] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
Oct  3 09:01:46 george-desktop kernel: [    9.410490] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
Oct  3 09:01:46 george-desktop kernel: [    9.410530] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
Oct  3 09:01:46 george-desktop kernel: [    9.410533] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
Oct  3 09:01:46 george-desktop kernel: [    9.410536] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
Oct  3 09:01:46 george-desktop kernel: [    9.410543] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
Oct  3 09:01:46 george-desktop kernel: [    9.410562] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
Oct  3 09:01:46 george-desktop kernel: [    9.410573] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
Oct  3 09:01:46 george-desktop kernel: [    9.410592] saa7134:   card=103 -> Compro Videomate DVB-T200A              
Oct  3 09:01:46 george-desktop kernel: [    9.410595] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
Oct  3 09:01:46 george-desktop kernel: [    9.410628] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
Oct  3 09:01:46 george-desktop kernel: [    9.410686] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
Oct  3 09:01:46 george-desktop kernel: [    9.410691] saa7134:   card=133 -> NXP Snake DVB-S reference design        
Oct  3 09:01:46 george-desktop kernel: [    9.410713] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
Oct  3 09:01:46 george-desktop kernel: [    9.410716] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
Oct  3 09:01:46 george-desktop kernel: [    9.410728] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636

//=====================================================================================================================================//

george@george-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
george@george-desktop:~$ sudo modprobe dvb-usb-dib0700
[sudo] password for george: 
george@george-desktop:~$ lspci -k
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
    Kernel driver in use: agpgart-amd64
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
    Kernel modules: shpchp
00:0c.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)
    Kernel driver in use: serial
00:0d.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
    Kernel driver in use: saa7134
    Kernel modules: saa7134
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
    Kernel driver in use: sata_via
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
    Kernel driver in use: pata_via
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Kernel driver in use: uhci_hcd
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Kernel driver in use: uhci_hcd
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Kernel driver in use: uhci_hcd
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Kernel driver in use: uhci_hcd
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
    Kernel driver in use: ehci_hcd
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Kernel modules: i2c-viapro
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
    Kernel modules: snd-via82xx-modem
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Kernel driver in use: k8temp
    Kernel modules: k8temp
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)



=============================================================================================================================

george@george-desktop:~$ dmesg

[   13.207115] Linux video capture interface: v2.00
[   13.282313] ACPI: I/O resource vt596_smbus [0x400-0x407] conflicts with ACPI region SMRG [0x400-0x40f]
[   13.282317] ACPI: Device needs an ACPI driver
[   13.288626] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   13.807626] saa7130/34: v4l2 driver version 0.2.14 loaded
[   13.809483] saa7134 0000:00:0d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.809491] saa7130[0]: found at 0000:00:0d.0, rev: 1, irq: 18, latency: 64, mmio: 0xfad00000
[   13.809498] saa7134: <rant>
[   13.809498] saa7134:  Congratulations!  Your TV card vendor saved a few
[   13.809499] saa7134:  cents for a eeprom, thus your pci board has no
[   13.809500] saa7134:  subsystem ID and I can't identify it automatically
[   13.809501] saa7134: </rant>
[   13.809502] saa7134: I feel better now.  Ok, here are the good news:
[   13.809503] saa7134: You can use the card=<nr> insmod option to specify
[   13.809504] saa7134: which board do you have.  The list:
[   13.809507] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   13.809510] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   13.809514] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   13.809518] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   13.809522] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   13.809525] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   13.809528] saa7134:   card=6 -> Tevion MD 9717                          
[   13.809530] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   13.809534] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   13.809537] saa7134:   card=9 -> Medion 5044                             
[   13.809540] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   13.809542] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   13.809545] saa7134:   card=12 -> Medion 7134                              16be:0003
[   13.809548] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   13.809551] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   13.809554] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   13.809557] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   13.809561] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   13.809564] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   13.809566] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   13.809570] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   13.809573] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   13.809576] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   13.809579] saa7134:   card=23 -> BMK MPEX Tuner                          
[   13.809581] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   13.809584] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   13.809587] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   13.809591] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   13.809593] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   13.809596] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   13.809599] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   13.809602] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   13.809605] saa7134:   card=32 -> AVACS SmartTV                           
[   13.809607] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   13.809611] saa7134:   card=34 -> Noval Prime TV 7133                     
[   13.809613] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   13.809616] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   13.809619] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   13.809622] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   13.809625] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   13.809629] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   13.809632] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   13.809635] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   13.809638] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   13.809640] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   13.809643] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   13.809646] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   13.809649] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   13.809652] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   13.809655] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   13.809658] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   13.809661] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   13.809664] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   13.809667] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   13.809670] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   13.809675] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   13.809678] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   13.809681] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   13.809684] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   13.809689] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   13.809692] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   13.809696] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   13.809699] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   13.809701] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   13.809704] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   13.809707] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   13.809709] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   13.809712] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   13.809715] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   13.809718] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   13.809721] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   13.809724] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   13.809727] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   13.809730] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   13.809733] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   13.809736] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   13.809739] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   13.809742] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   13.809745] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   13.809749] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   13.809751] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   13.809754] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   13.809757] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   13.809761] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   13.809764] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   13.809767] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   13.809771] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   13.809774] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   13.809777] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   13.809780] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   13.809783] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   13.809787] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   13.809790] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   13.809793] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   13.809796] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   13.809801] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   13.809804] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   13.809808] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   13.809811] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   13.809814] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   13.809817] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   13.809820] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   13.809823] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   13.809827] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   13.809829] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   13.809835] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   13.809838] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   13.809842] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   13.809845] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   13.809848] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   13.809850] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   13.809853] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   13.809857] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   13.809860] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   13.809863] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   13.809866] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   13.809869] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   13.809872] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   13.809875] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   13.809878] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   13.809881] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   13.809884] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   13.809887] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   13.809890] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   13.809893] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   13.809897] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   13.809900] saa7134:   card=126 -> Beholder BeholdTV 505 FM/RDS             0000:5051 0000:505b 5ace:5050
[   13.809904] saa7134:   card=127 -> Beholder BeholdTV 507 FM/RDS / BeholdTV  0000:5071 0000:507b 5ace:5070 5ace:5090
[   13.809908] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   13.809911] saa7134:   card=129 -> Beholder BeholdTV 607 / BeholdTV 609     5ace:6070 5ace:6071 5ace:6072 5ace:6073 5ace:6090 5ace:6091 5ace:6092 5ace:6093
[   13.809917] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   13.809920] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   13.809924] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   13.809926] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   13.809929] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   13.809932] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   13.809935] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   13.809938] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   13.809941] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   13.809944] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   13.809947] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   13.809950] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   13.809953] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   13.809956] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   13.809959] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   13.809963] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636
[   13.809966] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   13.809968] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   13.809971] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   13.809974] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   13.809977] saa7134:   card=150 -> Zogis Real Angel 220                    
[   13.809980] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   13.809983] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   13.809987] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   13.810081] saa7130[0]: board init: gpio is 38500
[   13.913214] saa7130[0]: Huh, no eeprom present (err=-5)?
[   13.913296] saa7130[0]: registered device video0 [v4l2]
[   13.913337] saa7130[0]: registered device vbi0
[   13.922510] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   13.922522] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   13.933924] ppdev: user-space parallel port driver
[   13.984232] saa7134 ALSA driver for DMA sound loaded
[   13.984268] saa7130[0]/alsa: saa7130[0] at 0xfad00000 irq 18 registered as card -2
[   14.676014] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   15.180243] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   15.180260] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   15.180881] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   15.181035] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   15.694739] codec_read: codec 0 is not valid [0xfe0000]
[   15.701260] codec_read: codec 0 is not valid [0xfe0000]
[   15.707799] codec_read: codec 0 is not valid [0xfe0000]
[   15.714303] codec_read: codec 0 is not valid [0xfe0000]
[   17.955764] lp0: using parport0 (interrupt-driven).
[   18.050257] Adding 3012176k swap on /dev/sda4.  Priority:-1 extents:1 across:3012176k
[   18.601191] EXT4 FS on sda3, internal journal on sda3:8
[   19.776739] type=1505 audit(1254838874.453:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1957
[   19.826816] type=1505 audit(1254838874.501:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1961
[   19.827007] type=1505 audit(1254838874.501:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1961
[   19.827065] type=1505 audit(1254838874.501:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1961
[   19.827117] type=1505 audit(1254838874.501:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1961
[   19.967379] type=1505 audit(1254838874.641:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1966
[   19.967620] type=1505 audit(1254838874.641:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1966
[   20.028141] type=1505 audit(1254838874.705:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=1970
[   20.060135] type=1505 audit(1254838874.737:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1974
[   34.405918] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.405921] Bluetooth: BNEP filters: protocol multicast
[   34.661706] Bridge firewalling registered
[   36.321552] [drm] Initialized drm 1.1.0 20060810
[   36.406758] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   36.407073] [drm] Initialized via 2.11.1 20070202 on minor 0
[   36.579660] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   36.579680] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   36.579761] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   39.323852] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   39.945228] NET: Registered protocol family 24
[   49.732011] eth0: no IPv6 routers present
[   98.870621] Marking TSC unstable due to cpufreq changes
[   99.012030] Clocksource tsc unstable (delta = -71436720 ns)
[ 2401.983044] dib0700: loaded with support for 8 different device-types
[ 2401.983089] usbcore: registered new interface driver dvb_usb_dib0700
george@george-desktop:~$ 

=====================================================================================================
george@george-desktop:~$ dmesg | grep dvb
[ 2401.983089] usbcore: registered new interface driver dvb_usb_dib0700

======================================================================================================

george@george-desktop:~$ lsmod |grep saa
saa7134_alsa           22176  0 
saa7134               176732  1 saa7134_alsa
snd_pcm                99464  5 snd_via82xx,saa7134_alsa,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
ir_common              56068  2 cx88xx,saa7134
snd                    78920  19 snd_via82xx,snd_mpu401_uart,saa7134_alsa,snd_seq_oss,snd_via82xx_modem,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
compat_ioctl32         18304  1 saa7134
videodev               45184  3 cx88xx,saa7134,compat_ioctl32
v4l2_common            23296  1 saa7134
videobuf_dma_sg        22660  4 cx8802,cx88xx,saa7134_alsa,saa7134
videobuf_core          29828  5 cx8802,cx88xx,videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               23428  2 cx88xx,saa7134

=======================================================================================================

george@george-desktop:~$ lsmod | grep dvb

videobuf_dvb           16516  2 cx8802,cx88xx
dvb_usb_dib0700        54536  0 
dib7000p               27400  1 dvb_usb_dib0700
dib7000m               24964  1 dvb_usb_dib0700
dvb_usb                27148  1 dvb_usb_dib0700
dvb_core              106924  2 videobuf_dvb,dvb_usb
dib3000mc              22280  1 dvb_usb_dib0700
dib0070                16772  1 dvb_usb_dib0700
videobuf_core          29828  5 cx8802,cx88xx,videobuf_dvb,saa7134,videobuf_dma_sg
george@george-desktop:~$ 



==================================================================================================

george@george-desktop:~$ locate saa7134

/home/george/GEORGE_FILES/SETUP(.deb files)/saa7134
/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/saa7134
/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/saa7134/saa6752hs.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/saa7134/saa7134-alsa.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/saa7134/saa7134-dvb.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/saa7134/saa7134-empress.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/saa7134/saa7134.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/saa7134
/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/saa7134/saa6752hs.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/saa7134/saa7134-alsa.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/saa7134/saa7134-dvb.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/saa7134/saa7134-empress.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/saa7134/saa7134.ko
/usr/src/linux-headers-2.6.28-15/drivers/media/video/saa7134
/usr/src/linux-headers-2.6.28-15/drivers/media/video/saa7134/Kconfig
/usr/src/linux-headers-2.6.28-15/drivers/media/video/saa7134/Makefile
/usr/src/linux-headers-2.6.28-15-generic/include/config/video/saa7134
/usr/src/linux-headers-2.6.28-15-generic/include/config/video/saa7134.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/video/saa7134/alsa.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/video/saa7134/dvb.h



PLEASE HELP ME......:(

---

### Post by bp0 on 2009-12-15
Which TV Capture Card do you have? 

As it says in dmesg, your TV capture card is cheap and doesn't report its subsystem ID, so you must specify which card it is to the driver.
First pick the number of your card out of the list, then create a file called /etc/modprobe.d/saa7134.conf with the following content:

```
options saa7134 card=?
```

Put your card's number in place of the '?'. Then restart the computer or remove/insert the module again.

---

### Post by George Lukose on 2009-12-20
**Details of  TV Capture Card**
-----------------------------------------

InterVideo WinDVR 
© 1998-2001 InterVideo, Incorporated. All rights reserved.  
 
The information contained herein is subject to change without notice. While every reasonable effort was made to ensure the completeness and correctness of this document, InterVideo Inc. makes no warranty of any kind with regard to this material, including but not limited to any implied warranties. InterVideo shall not be liable for errors or omissions contained herein or for any damages relating to the use of this material.  
 
WinDVR is a trademark of InterVideo, Incorporated.  
 
Microsoft, Windows, Windows 95, Windows 98, Windows 2000 and Windows NT are registered trademarks of the Microsoft Corporation. All other brand or product names are trademarks of their respective holders  
 
This document is protected by US copyright laws. No part of this document may be reproduced in any manner without written consent of InterVideo, Inc.  
 
InterVideo, Inc. 
47350 Fremont Blvd. 
Fremont, CA 94538, USA 
[www.intervideo.com](www.intervideo.com)  

--------------------------------------------------------

**From where i will get card number ?**

---

