---
title: "Ubuntu instalation on another drive."
date: 2011-01-29
forum: General Help
---

### Post by XeroDay on 2011-01-29
Hey guys


well i am new to ubuntu but i installed it once before on my old computer which also had to harddrives. But after i booted into ubuntu i could not load windows and after i repaired it it has no internet connection.

This is not my issiue atm.

my current problem is i have a new computer and i wish to install ubuntu on my K drive not C... How can i go about installing ubuntu on K drive without it affecting my windows 7 install? and im kind of confused with the whole setup with partitions. if its a 1tb drive what do i do?

i want to install it on K drive as i reformat a lo0t and i dont want to lose ubuntu if i need to reformat

thanks guys for any help :)


btw i have windows 7 64 and trying to install ubuntu 10.10 64

any help is greatly appreciated thanks guys :)

---

### Post by Elfy on 2011-01-29
OK - first K drive and C drive mean little in linux - we know what you're talking about but that's as far as it goes.

I would suggest that the best thing you could do is boot windows and remove your k drive in there - then when you boot the livecd/usb you'll have free space to install to - you'll not be accidentally installing in the wrong place then.

Once you've done that boot with the live media - let it get to the desktop then open a terminal from the apps -accessories menu, run this command

```
sudo fdisk -l
```

and paste the output you get here, this will show us what partitions you already have and we can help you from there.

It will also help to know how much ram you have, whether you want to suspend.

---

### Post by XeroDay on 2011-01-29
hi thanks for the reply..

well i got 8gb of ram however i have a small problem, since this is a new computer im kinda stuck... i dont know how to boot from cd it only offers my my 2 hard drives 


here is my pc info if it helps

thanks

```

CPU Info
  Physical processors 1 
 Logical processors 8 
     CPU  Manufacturer Intel  Family Intel(R) Core(TM) i7 CPU K 875 @ 2.93GHz  Architecture 64-bit  Internal Clock 2.9 GHz   Internal Clock Maximum 2.9 GHz   External Clock 133.0 MHz   Socket Designation LGA1156  Type 
 Upgrade 
 MultiCore 4 Processor Cores  HyperThreadingTechnology Available - 2 HTT Processors per Core  Capabilities MMX, CMov, RDTSC, SSE, SSE2, SSE3, PAE, NX, SSSE3, SSE4.1,  SSE4.2  Version Intel(R) Core(TM) i7 CPU K 875 @ 2.93GHz  Caches      Cache  Level 1   Capacity 256 KB   Type Instruction, Write Through, Internal  Type Details -   Error Correction Type Parity  Associativity 4-way Set-Associative    Cache  Level 2   Capacity 1 MB   Type Instruction, Data, Write Through, Internal  Type Details -   Error Correction Type Single-bit ECC  Associativity 8-way Set-Associative    Cache  Level 3   Capacity 8 MB   Type Instruction, Data, Internal  Type Details -   Error Correction Type Single-bit ECC  Associativity 16-way  Set-Associative

 DirectX Info
  Version 11.0
 Long version 4.09.00.0904
     DirectDraw Info  Version 6.1.7600.16385  Primary Device NVIDIA GeForce GTX 580  Linked Display Adapters 2   Display Devices     Display device  Description NVIDIA GeForce GTX 580  Manufacturer NVIDIA  Total Local Video Memory 1.48 GB   Total Local Texture Memory 1.48 GB   AGP Aperture Size 2.50 GB   Driver File nvd3dum.dll  Driver Version 8.17.12.6309  Driver Details 
 Driver Date 11-9-2010  Driver WHQL Certified true  Max Texture Width 8192 px  Max Texture Height 8192 px  Max User Clipping Planes 8   Max Active Hardware Lights 8   Max Texture Blending Stages 8   Fixed Function Textures In Single Pass 8   Vertex Shader Version 5.0  Pixel Shader Version 5.0  Max Vertex Blend Matrices 0   Max Texture Coordinates 8   PCI NVIDIA GeForce GTX 5800x10de0x10800x158038420x00a1  Texture Formats 32-bit ARGB [8888], 32-bit RGB [888], 16-bit RGB [565],  16-bit RGB [555], 16-bit ARGB [1555], 16-bit ARGB [4444], 8-bit A [8], 8-bit YUV  [800], 16-bit AYUV [8800], FourCC [DXT1], FourCC [DXT2], FourCC [DXT3], FourCC  [DXT4], FourCC [DXT5],   Capabilities AGP Texturing, Hardware Transform and Lighting, Positional  Lights, Subpixel Accurate Rasterizing, Stencil Buffers, Range Fog, Table Fog,  Vertex Fog, W-Fog, Specular Gouraud Shading, Anisotropic Filtering, Bilinear  Filtering, Point Sampling, Trilinear Filtering, Additive Texture Blending, Dot3  Texture Blending, Multiplicative Texture Blending, Subtractive Texture Blending,  Environmental Bump Mapping, Environmental Bump Mapping With Luminance, Cube  Mapping, Factor Alpha Blending, Vertex Alpha Blending, Texture Alpha Blending,  Texture Clamping, Texture Mirroring, Texture Wrapping, Guard Band Support,  Mipmap LOD Bias Adjustment, Projected Textures, Volume Textures, Point Primitive  Support, Full-Screen Anti-Aliasing, DXT Compressed Textures, Two Sided Stencil  Test, Mipmapped Volume Textures, Mipmapped Cube Textures, Texture Border Color,  Spherical Mapping, Automatic Mipmap Generation, Hardware Rasterization, Shading,  Transform and Lighting, Scissor Test, Legacy Depth  Bias  Multi GPU Devices GeForce GTX 5800x10de0x10800x158038420x00a1GeForce GTX  5800x10de0x10800x158038420x00a1
     DirectShow Info  Version 6.6.7600.16385  Registered DirectShow Filters AC3 Parser Filter, ACM Wrapper, AVI Decompressor, AVI Draw,  AVI Splitter, AVI/WAV File Source, BDA MPEG2 Transport Information Filter, Color  Space Converter, Creative AC3 Source Filter, Creative CDDA Source Filter,  Creative File Reader Filter, Creative Flac Source Filter, Creative Internet  Source Filter, Creative LiveRecording Filter SxS, Creative MLP Source Filter,  Creative NVF Filter, Creative Ogg Source Filter, Creative Recording Wav_Asio  Filter, Creative WMA Source Filter, DV Muxer, DV Splitter, DV Video Decoder,  Decrypt/Tag, Default DirectSound Device, Default MidiOut Device, File Source  (Async.), File Source (URL), File stream renderer, Internal Script Command  Renderer, Line 21 Decoder, Line 21 Decoder 2, MIDI Parser, MJPEG Decompressor,  MP3 Decoder DMO, MPEG Audio Decoder, MPEG Video Decoder, MPEG-2 Demultiplexer,  MPEG-2 Sections and Tables, MPEG-2 Splitter, MPEG-I Stream Splitter, Microsoft  DTV-DVD Audio Decoder, Microsoft DTV-DVD Video Decoder, Mpeg4 Decoder DMO,  Mpeg43 Decoder DMO, Mpeg4s Decoder DMO, Multi-file Parser, PBDA DTFilter, RDP  DShow Redirection Filter, SAMI (CC) Parser, VBI Codec, VBI Surface Allocator,  VGA 16 Color Ditherer, Video Port Manager, Video Renderer, WM ASF Reader, WM ASF  Writer, WMAPro over S/PDIF DMO, WMAudio Decoder DMO, WMSpeech Decoder DMO, WMV  Screen decoder DMO, WMVideo Decoder DMO, Wave Parser, iTV Data Capture filter,  iTV Data Sink, 
     DirectSound Info  Version 6.1.7600.16385  Speaker Configuration Stereo  Speaker Geometry Wide  Primary Device Speakers (2- High Definition Audio Device)  Sound Devices 


 Memory Info
  Total Physical Memory 8.00 GB  
Free Physical Memory 5.89 GB 

 Total Pagefile Memory 15.99 GB  
Free Pagefile Memory 13.82 GB 

     Memory array  Max Module Capacity 4 MB   Location System Board  Use System  Supported Error DC 
 Supported Speeds -   Supported Types -   Supported Voltages -   Memory Slots      Memory slot  Installed Enabled Size 0 B   Form Factor DIMM  Frequency 0.0 Hz  Slot DIMM0 [BANK0]  Manufacturer Manufacturer0  Type DDR  Type Details Synchronous  Enabled Size 0 B   Total Bit Width 72 b  Data Bit Width 64 b
     Memory slot  Installed Enabled Size 0 B   Form Factor DIMM  Frequency 0.0 Hz  Slot DIMM1 [BANK1]  Manufacturer Manufacturer1  Type 
 Type Details -   Enabled Size 0 B   Total Bit Width 0 b  Data Bit Width 0 b
     Memory slot  Installed Enabled Size 0 B   Form Factor DIMM  Frequency 0.0 Hz  Slot DIMM2 [BANK2]  Manufacturer Manufacturer2  Type DDR  Type Details Synchronous  Enabled Size 0 B   Total Bit Width 72 b  Data Bit Width 64 b
     Memory slot  Installed Enabled Size 0 B   Form Factor DIMM  Frequency 0.0 Hz  Slot DIMM3 [BANK3]  Manufacturer Manufacturer3  Type 
 Type Details -   Enabled Size 0 B   Total Bit Width 0 b  Data Bit Width 0 b


 Storage Devices
     Hitachi HDS721010CLA332 ATA Device  Device Drive Type 
 Name Hitachi HDS721010CLA332 ATA Device  Manufacturer (Standard disk drives)  Model Hitachi HDS721010CLA332 ATA Device  Vendor ID String 
 Product ID String 
 Product Revision String 
 Serial Number 
 Interface Type IDE  Device Bus Type 
 Capacity 931.51 GB   Drive Letters 
 CD Max Read Speed 0   CD Read Capabilities -   CD Write Capabilities -   DVD Read Capabilities -   DVD Write Capabilities -   SMART 
 Acoustic Management 
 Physical sector size 0 B     ST31500341AS ATA Device  Device Drive Type 
 Name ST31500341AS ATA Device  Manufacturer (Standard disk drives)  Model ST31500341AS ATA Device  Vendor ID String 
 Product ID String 
 Product Revision String 
 Serial Number 
 Interface Type IDE  Device Bus Type 
 Capacity 1.364514262  Drive Letters C:  CD Max Read Speed 0   CD Read Capabilities -   CD Write Capabilities -   DVD Read Capabilities -   DVD Write Capabilities -   SMART 
 Acoustic Management 
 Physical sector size 0 B     unknown  Device Drive Type 
 Name unknown  Manufacturer unknown  Model unknown  Vendor ID String 
 Product ID String 
 Product Revision String 
 Serial Number 
 Interface Type unknown  Device Bus Type 
 Capacity 0 B   Drive Letters 
 CD Max Read Speed 0   CD Read Capabilities -   CD Write Capabilities -   DVD Read Capabilities -   DVD Write Capabilities -   SMART 
 Acoustic Management 
 Physical sector size 0 B     unknown  Device Drive Type 
 Name unknown  Manufacturer unknown  Model unknown  Vendor ID String 
 Product ID String 
 Product Revision String 
 Serial Number 
 Interface Type unknown  Device Bus Type 
 Capacity 0 B   Drive Letters 
 CD Max Read Speed 0   CD Read Capabilities -   CD Write Capabilities -   DVD Read Capabilities -   DVD Write Capabilities -   SMART 
 Acoustic Management 
 Physical sector size 0 B     unknown  Device Drive Type 
 Name unknown  Manufacturer unknown  Model unknown  Vendor ID String 
 Product ID String 
 Product Revision String 
 Serial Number 
 Interface Type unknown  Device Bus Type 
 Capacity 0 B   Drive Letters 
 CD Max Read Speed 0   CD Read Capabilities -   CD Write Capabilities -   DVD Read Capabilities -   DVD Write Capabilities -   SMART 
 Acoustic Management 
 Physical sector size 0 B     unknown  Device Drive Type 
 Name unknown  Manufacturer unknown  Model unknown  Vendor ID String 
 Product ID String 
 Product Revision String 
 Serial Number 
 Interface Type unknown  Device Bus Type 
 Capacity 0 B   Drive Letters 
 CD Max Read Speed 0   CD Read Capabilities -   CD Write Capabilities -   DVD Read Capabilities -   DVD Write Capabilities -   SMART 
 Acoustic Management 
 Physical sector size 0 B     unknown  Device Drive Type 
 Name unknown  Manufacturer unknown  Model unknown  Vendor ID String 
 Product ID String 
 Product Revision String 
 Serial Number 
 Interface Type unknown  Device Bus Type 
 Capacity 0 B   Drive Letters 
 CD Max Read Speed 0   CD Read Capabilities -   CD Write Capabilities -   DVD Read Capabilities -   DVD Write Capabilities -   SMART 
 Acoustic Management 
 Physical sector size 0 B     unknown  Device Drive Type 
 Name unknown  Manufacturer unknown  Model unknown  Vendor ID String 
 Product ID String 
 Product Revision String 
 Serial Number 
 Interface Type unknown  Device Bus Type 
 Capacity 644 MB   Drive Letters 
 CD Max Read Speed 0   CD Read Capabilities -   CD Write Capabilities -   DVD Read Capabilities -   DVD Write Capabilities -   SMART 
 Acoustic Management 
 Physical sector size 0 B     unknown  Device Drive Type 
 Name unknown  Manufacturer unknown  Model unknown  Vendor ID String 
 Product ID String 
 Product Revision String 
 Serial Number 
 Interface Type unknown  Device Bus Type 
 Capacity 644 MB   Drive Letters 
 CD Max Read Speed 0   CD Read Capabilities -   CD Write Capabilities -   DVD Read Capabilities -   DVD Write Capabilities -   SMART 
 Acoustic Management 
 Physical sector size 0 B 
 Operating system info
     Name Windows 7 Home Premium  Version 6.1.7600  PlatformId 2   Service Pack 
 Suite 768   Product Type 1   Product Version 3   Media Center true  Windows Environment 64-bit  ReadyBoost Devices 
 Locale US  Desktop Width 1920 px  Desktop Height 1080 px  Desktop BPP 32 b  Internet Explorer Version 87600  System Drive Letter C:  Windows Experience Index     Information  State 2   Description Windows Experience Index : Unrated  Rating 5.900000  Date 20110116010223  Sub Indices     Memory 8.00 GB Memory (RAM): 7.600000  Processor Intel(R) Core(TM) i7 CPU K 875 @ 2.93GHz Processor: 7.600000  HDD 1275GB Free (1397GB Total) Primary hard disk: 5.900000  Gaming Graphics 4095 MB Total available graphics memory Gaming graphics: 7.800000  Graphics NVIDIA GeForce GTX 580 Graphics: 7.800000  Applications  3DMarkVantage
Ubuntu Forums - Reply to Topic - Mozilla  Firefox
ZScreen 3.32.0.1 Beta
 Processes      Name PID Memory usage  System Idle Process 0  24 KB   System 4  808 KB   smss.exe 424  1 MB   csrss.exe 576  5 MB   wininit.exe 700  7 MB   csrss.exe 720  15 MB   services.exe 756  12 MB   lsass.exe 784  14 MB   lsm.exe 792  7 MB   svchost.exe 904  12 MB   CLPSLS.exe 964  5 MB   nvvsvc.exe 984  11 MB   winlogon.exe 144  9 MB   svchost.exe 436  10 MB   cmdagent.exe 564  49 MB   svchost.exe 844  19 MB   MsMpEng.exe 712  60 MB   svchost.exe 1148  21 MB   svchost.exe 1220  130 MB   svchost.exe 1264  38 MB   audiodg.exe 1336  17 MB   CTAudSvc.exe 1368  6 MB   svchost.exe 1408  15 MB   SbieSvc.exe 1468  7 MB   NvXDSync.exe 1576  23 MB   nvvsvc.exe 1588  24 MB   spoolsv.exe 2000  15 MB   taskhost.exe 2008  10 MB   svchost.exe 1132  16 MB   dwm.exe 1448  4 MB   AppleMobileDeviceService.exe 1720  15 MB   explorer.exe 1256  52 MB   AsSysCtrlService.exe 2068  5 MB   mDNSResponder.exe 2100  7 MB   spd.exe 2120  10 MB   sqlservr.exe 2200  3 MB   taskeng.exe 2212  9 MB   TurboVHelp.exe 2264  7 MB   EVGAPrecision.exe 2276  8 MB   sqlbrowser.exe 2340  5 MB   sqlwriter.exe 2456  9 MB   nvSCPAPISvr.exe 2492  7 MB   svchost.exe 2528  7 MB   WDDMService.exe 2568  17 MB   WDSmartWareBackgroundService.exe 2640  20 MB   rundll32.exe 2708  8 MB   cfp.exe 2724  23 MB   ZScreen.exe 2744  79 MB   SbieCtrl.exe 2772  15 MB   WLIDSVC.EXE 2828  20 MB   WDDMStatus.exe 3036  15 MB   WLIDSVCM.EXE 3052  6 MB   WDSmartWare.exe 2656  134 MB   TSVNCache.exe 3188  13 MB   svchost.exe 3928  8 MB   WUDFHost.exe 4000  8 MB   SearchIndexer.exe 3616  20 MB   firefox.exe 4064  92 MB   SearchProtocolHost.exe 4340  11 MB   SearchFilterHost.exe 4360  10 MB   svchost.exe 4808  9 MB   sppsvc.exe 4912  12 MB   3DMarkVantage.exe 5092  82 MB   dllhost.exe 552  13 MB   WmiPrvSE.exe 1964  9 MB   WmiPrvSE.exe 2880  8 MB   Logical Drives      Letter Label Type Capacity Available  C: 
Hard Disk 1.364514347 1.245136268  D: Ubuntu 10.10 amd CD-ROM 695 MB  0 B   E: WD SmartWare CD-ROM 644 MB  0 B   F: My Book Hard Disk 930.86 GB  41.53 GB   G: 
Floppy 0 B  0 B   H: 
Floppy 0 B  0 B   I: 
Floppy 0 B  0 B   J: 
Floppy 0 B  0 B   K: Local Disk Hard Disk 931.41 GB  900.86 GB  
 Monitor info
     Monitor  Name Generic PnP Monitor  Manufacturer (Standard monitor types)  Max Width 1600 px  Max Height 1200 px
 Mainboard info
     Supported Slot Types PCI, PCI Express  Manufacturer ASUSTeK Computer INC.  Model Maximus III Formula  Version Rev 1.xx  BIOS Vendor American Megatrends Inc.  BIOS Version 2001  BIOS Release Date 07/22/2010  BIOS Properties Plug and Play, Flash  Card Slots     Card Slot  Order 1   Designation PCIEX16_1  Type PCI Express  Characteristics 3.3V, Shared, PME Signal  Data Bus Width 32 b  Details In Use, Short    Card Slot  Order 2   Designation PCIEX1_1  Type PCI Express  Characteristics 3.3V, Shared, PME Signal  Data Bus Width 32 b  Details Available, Short    Card Slot  Order 3   Designation PCIEX1_2  Type PCI Express  Characteristics 3.3V, Shared, PME Signal  Data Bus Width 32 b  Details Available, Short    Card Slot  Order 4   Designation PCIEX16_2  Type PCI Express  Characteristics 3.3V, Shared, PME Signal  Data Bus Width 32 b  Details In Use, Short    Card Slot  Order 5   Designation PCI1  Type PCI  Characteristics 3.3V, Shared, PME Signal  Data Bus Width 32 b  Details Available, Short    Card Slot  Order 6   Designation PCIEX16_3  Type PCI Express  Characteristics 3.3V, Shared, PME Signal  Data Bus Width 32 b  Details Available, Short    Card Slot  Order 7   Designation PCI2  Type PCI  Characteristics 3.3V, Shared, PME Signal  Data Bus Width 32 b  Details Available, Short  PCI Devices     PCI Device  Manufacturer Microsoft  Location PCI bus 1, device 0, function 1  Type 
 PCI High Definition Audio Controller    PCI Device  Manufacturer Microsoft  Location PCI bus 2, device 0, function 1  Type 
 PCI High Definition Audio Controller    PCI Device  Manufacturer NVIDIA  Location PCI bus 1, device 0, function 0  Type 
 PCI NVIDIA GeForce GTX 580    PCI Device  Manufacturer NVIDIA  Location PCI bus 2, device 0, function 0  Type 
 PCI NVIDIA GeForce GTX 580    PCI Device  Manufacturer Realtek  Location PCI bus 8, device 4, function 0  Type 
 PCI Realtek PCI GBE Family Controller    PCI Device  Manufacturer VIA  Location PCI bus 8, device 3, function 0  Type 
 PCI VIA 1394 OHCI Compliant Host  Controller    PCI Device  Manufacturer Ralink Technology Corp.  Location PCI bus 8, device 1, function 0  Type 
 PCI 802.11g PCI Turbo Wireless Adapter    PCI Device  Manufacturer JMicron Technology Corp.  Location PCI bus 3, device 0, function 0  Type 
 PCI JMicron JMB36X Controller    PCI Device  Manufacturer JMicron Technology Corp.  Location PCI bus 4, device 0, function 0  Type 
 PCI JMicron JMB36X Controller    PCI Device  Manufacturer Intel  Location PCI bus 0, device 30, function 0  Type 
 PCI Intel(R) 82801 PCI Bridge - 244E    PCI Device  Manufacturer Intel  Location PCI bus 0, device 31, function 0  Type 
 PCI Intel(R) P55 Express Chipset LPC Interface Controller -  3B02    PCI Device  Manufacturer Intel  Location PCI bus 0, device 31, function 2  Type 
 PCI Intel(R) 5 Series/3400 Series Chipset Family 4 port Serial ATA  Storage Controller - 3B20    PCI Device  Manufacturer Intel  Location PCI bus 0, device 31, function 5  Type 
 PCI Intel(R) 5 Series/3400 Series Chipset Family 2 port Serial ATA  Storage Controller - 3B26    PCI Device  Manufacturer Intel  Location PCI bus 0, device 31, function 3  Type 
 PCI Intel(R) 5 Series/3400 Series Chipset Family SMBus Controller -  3B30    PCI Device  Manufacturer Intel  Location PCI bus 0, device 29, function 0  Type 
 PCI Intel(R) 5 Series/3400 Series Chipset Family USB Enhanced Host  Controller - 3B34    PCI Device  Manufacturer Intel  Location PCI bus 0, device 26, function 0  Type 
 PCI Intel(R) 5 Series/3400 Series Chipset Family USB Enhanced Host  Controller - 3B3C    PCI Device  Manufacturer Intel  Location PCI bus 0, device 28, function 0  Type 
 PCI Intel(R) 5 Series/3400 Series Chipset Family PCI Express Root  Port 1 - 3B42    PCI Device  Manufacturer Intel  Location PCI bus 0, device 28, function 4  Type 
 PCI Intel(R) 5 Series/3400 Series Chipset Family PCI Express Root  Port 5 - 3B4A    PCI Device  Manufacturer Intel  Location PCI bus 0, device 28, function 5  Type 
 PCI Intel(R) 5 Series/3400 Series Chipset Family PCI Express Root  Port 6 - 3B4C    PCI Device  Manufacturer Intel  Location PCI bus 0, device 28, function 6  Type 
 PCI Intel(R) 5 Series/3400 Series Chipset Family PCI Express Root  Port 7 - 3B4E    PCI Device  Manufacturer Intel  Location PCI bus 0, device 28, function 7  Type 
 PCI Intel(R) 5 Series/3400 Series Chipset Family PCI Express Root  Port 8 - 3B50    PCI Device  Manufacturer Microsoft  Location PCI bus 0, device 27, function 0  Type 
 PCI High Definition Audio Controller    PCI Device  Manufacturer Intel  Location PCI bus 0, device 0, function 0  Type 
 PCI Intel(R) processor DMI - D131    PCI Device  Manufacturer Intel  Location PCI bus 0, device 3, function 0  Type 
 PCI Intel(R) processor PCI Express Root Port 1 -  D138    PCI Device  Manufacturer Intel  Location PCI bus 0, device 5, function 0  Type 
 PCI Intel(R) processor PCI Express Root Port 3 -  D13A    PCI Device  Manufacturer Intel  Location PCI bus 0, device 16, function 0  Type 
 PCI Intel(R) QuickPath Interconnect - D150    PCI Device  Manufacturer Intel  Location PCI bus 0, device 16, function 1  Type 
 PCI Intel(R) QuickPath Interconnect - D151    PCI Device  Manufacturer Intel  Location PCI bus 0, device 8, function 0  Type 
 PCI Intel(R) processor System Management Registers -  D155    PCI Device  Manufacturer Intel  Location PCI bus 0, device 8, function 1  Type 
 PCI Intel(R) processor Semaphore and Scratchpad Registers -  D156    PCI Device  Manufacturer Intel  Location PCI bus 0, device 8, function 2  Type 
 PCI Intel(R) processor System Control and Status Registers -  D157    PCI Device  Manufacturer Intel  Location PCI bus 0, device 8, function 3  Type 
 PCI Intel(R) processor Miscellaneous Registers -  D158  System Devices     System Device  Manufacturer Intel  PCI Intel(R) 82801 PCI Bridge - 244E    System Device  Manufacturer Intel  PCI Intel(R) P55 Express Chipset LPC Interface Controller -  3B02    System Device  Manufacturer Intel  PCI Intel(R) 5 Series/3400 Series Chipset Family SMBus Controller -  3B30    System Device  Manufacturer Intel  PCI Intel(R) 5 Series/3400 Series Chipset Family PCI Express Root  Port 1 - 3B42    System Device  Manufacturer Intel  PCI Intel(R) 5 Series/3400 Series Chipset Family PCI Express Root  Port 5 - 3B4A    System Device  Manufacturer Intel  PCI Intel(R) 5 Series/3400 Series Chipset Family PCI Express Root  Port 6 - 3B4C    System Device  Manufacturer Intel  PCI Intel(R) 5 Series/3400 Series Chipset Family PCI Express Root  Port 7 - 3B4E    System Device  Manufacturer Intel  PCI Intel(R) 5 Series/3400 Series Chipset Family PCI Express Root  Port 8 - 3B50    System Device  Manufacturer Microsoft  PCI High Definition Audio Controller    System Device  Manufacturer Intel  PCI Intel(R) processor DMI - D131    System Device  Manufacturer Intel  PCI Intel(R) processor PCI Express Root Port 1 -  D138    System Device  Manufacturer Intel  PCI Intel(R) processor PCI Express Root Port 3 -  D13A    System Device  Manufacturer Intel  PCI Intel(R) QuickPath Interconnect - D150    System Device  Manufacturer Intel  PCI Intel(R) QuickPath Interconnect - D151    System Device  Manufacturer Intel  PCI Intel(R) processor System Management Registers -  D155    System Device  Manufacturer Intel  PCI Intel(R) processor Semaphore and Scratchpad Registers -  D156    System Device  Manufacturer Intel  PCI Intel(R) processor System Control and Status Registers -  D157    System Device  Manufacturer Intel  PCI Intel(R) processor Miscellaneous Registers -  D158  USB Devices     USB Device  Description USB Root Hub  Driver Date 6-21-2006  Driver Version 6.1.7600.16385  Device Class Universal Serial Bus Controller  Vendor ID 0x8086  Product ID 0x3b3c  Revision 0x0006    USB Device  Description USB Root Hub  Driver Date 6-21-2006  Driver Version 6.1.7600.16385  Device Class Universal Serial Bus Controller  Vendor ID 0x8086  Product ID 0x3b34  Revision 0x0006    USB Device  Description Logitech USB Camera (QuickCam S5500)  Driver Date 10-7-2009  Driver Version 12.10.1110.0  Device Class Universal Serial Bus Controller  Vendor ID 0x046d  Product ID 0x09a1  Revision 0x0008    USB Device  Description Logitech QuickCam S5500  Driver Date 10-7-2009  Driver Version 12.10.1110.0  Device Class Imaging Device  Vendor ID 0x046d  Product ID 0x09a1  Revision 0x0008    USB Device  Description Logitech Mic (QuickCam S5500)  Driver Date 10-7-2009  Driver Version 12.10.1110.0  Device Class Sound, Video or Game Controller  Vendor ID 0x046d  Product ID 0x09a1  Revision 0x0008    USB Device  Description USB Input Device  Driver Date 6-21-2006  Driver Version 6.1.7600.16385  Device Class Human Interface Device  Vendor ID 0x046d  Product ID 0xc315  Revision 0x2800    USB Device  Description USB Mass Storage Device  Driver Date 6-21-2006  Driver Version 6.1.7600.16385  Device Class Universal Serial Bus Controller  Vendor ID 0x058f  Product ID 0x6362  Revision 0x0129    USB Device  Description Apple Mobile Device USB Driver  Driver Date 9-16-2010  Driver Version 6.0.9999.52  Device Class Universal Serial Bus Controller  Vendor ID 0x05ac  Product ID 0x1292  Revision 0x0001    USB Device  Description USB Mass Storage Device  Driver Date 6-21-2006  Driver Version 6.1.7600.16385  Device Class Universal Serial Bus Controller  Vendor ID 0x1058  Product ID 0x1111  Revision 0x2003    USB Device  Description Razer Diamondback 3G  Driver Date 3-7-2007  Driver Version 1.0.0.2  Device Class Human Interface Device  Vendor ID 0x1532  Product ID 0x000d  Revision 0x2300    USB Device  Description Generic USB Hub  Driver Date 6-21-2006  Driver Version 6.1.7600.16385  Device Class Universal Serial Bus Controller  Vendor ID 0x8087  Product ID 0x0020  Revision 0x0000    USB Device  Description Generic USB Hub  Driver Date 6-21-2006  Driver Version 6.1.7600.16385  Device Class Universal Serial Bus Controller  Vendor ID 0x8087  Product ID 0x0020  Revision 0x0000  FireWire Devices 
 Bluetooth Devices
```

---

### Post by kad78 on 2011-01-29
To boot from CD, you need to enter your bios setup as your computer boots.

To do this, you press a certain button (normally DELETE) while your computer is booting. This certain button can be found by looking at the bios splash screen (picture that comes up as computer boots). [http://www.computerhope.com/issues/ch000192.htm](http://www.computerhope.com/issues/ch000192.htm)

Somewhere in the setting there will be an option to boot from CD. 

Once you have booted from the ubuntu cd, it should be quite easy to install on your 'K:' drive. You should be given a clear option.

---

### Post by XeroDay on 2011-01-30
thanks ill give it a try and will post back here :)

---

### Post by Elfy on 2011-01-30
> it should be quite easy to install on your 'K:' drive. You should be given a clear option.It won't be clear to someone who's never seen drives and partitions lablelled sdxy ;)

---

