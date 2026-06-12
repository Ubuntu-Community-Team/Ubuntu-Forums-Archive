---
title: "install problem - green flashing at startup"
date: 2009-09-14
forum: General Help
---

### Post by hachikid on 2009-09-14
hello everyone. I'm new to Ubuntu, and I'm definitely interested in switching. my plan is to have a part of the HD partitioned for XP Pro SP3, and another part for Ubuntu. I burned 9.04 to a disc, booted from the disc, and I clicked the option to try Ubuntu without any changed to my hard drive, and the loading screen came up. all was good, but after it was done, the screen just started flashing green and black vertical lines. I have a video on my phone, I'll just have to transfer it from my phone. I'm not sure what I need to list (still learning about computer stuff), so just tell me what information you need to know (if you do), and I'll put it up.



Joseph.

---

### Post by Jive Turkey on 2009-09-14
go back and boot into the flashing green screen and try pressing ctrl+alt+f1 keys.  That may get you to a command prompt.  If asked for a username and password, try blank ones or the word ubuntu.  Once you are at a command prompt try the command "lspci"  This should list all the items on the pci bus of your laptop.  Of interest is the video chipset.  You could also just check it out in device manager on Windows XP which might be easier for you.

Once you figure out the name / model of your video chipset, google for <name/model of vga chipset> + "ubuntu" and see if you can find some hints.  Come back to this thread with any more questions to help you understand anything you need.

You might consider the wubi option, though I've never tried it myself, to install inside windows.

---

### Post by hachikid on 2009-09-14
I've got CPU-Z. I saved the report as a .txt file and here is what it said:

CPU-Z TXT Report
-------------------------------------------------------------------------

Binaries
-------------------------------------------------------------------------

CPU-Z version            1.52.2

Processors
-------------------------------------------------------------------------

Number of processors        1
Number of threads        2

APICs
-------------------------------------------------------------------------

Processor 0    
    -- Core 0    
        -- Thread 0    0
    -- Core 1    
        -- Thread 0    1

Processors Information
-------------------------------------------------------------------------

Processor 1            ID = 0
    Number of cores        2 (max 2)
    Number of threads    2 (max 2)
    Name            Intel Core 2 Duo E6420
    Codename        Conroe
    Specification        Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz
    Package (platform ID)    Socket 775 LGA (0x0)
    CPUID            6.F.6
    Extended CPUID        6.F
    Core Stepping        B2
    Technology        65 nm
    Core Speed        1600.1 MHz
    Multiplier x FSB    6.0 x 266.7 MHz
    Rated Bus speed        1066.7 MHz
    Stock frequency        2133 MHz
    Instructions sets    MMX, SSE, SSE2, SSE3, SSSE3, EM64T
    L1 Data cache        2 x 32 KBytes, 8-way set associative, 64-byte line size
    L1 Instruction cache    2 x 32 KBytes, 8-way set associative, 64-byte line size
    L2 cache        4096 KBytes, 16-way set associative, 64-byte line size
    FID/VID Control        yes
    FID range        6.0x - 8.0x
    Max VID            1.338 V



Thread dumps
-------------------------------------------------------------------------

CPU Thread 0    
    APIC ID            0
    Topology        Processor ID 0, Core ID 0, Thread ID 0
    Type            01008001h
    Max CPUID level        0000000Ah
    Max CPUID ext. level    80000008h
    Cache descriptor    Level 1, D, 32 KB, 1 thread(s)
    Cache descriptor    Level 1, I, 32 KB, 1 thread(s)
    Cache descriptor    Level 2, U, 4 MB, 2 thread(s)

    CPUID         
    0x00000000        0x0000000A    0x756E6547    0x6C65746E    0x49656E69
    0x00000001        0x000006F6    0x00020800    0x0000E3BD    0xBFEBFBFF
    0x00000002        0x05B0B101    0x005657F0    0x00000000    0x2CB43049
    0x00000003        0x00000000    0x00000000    0x00000000    0x00000000
    0x00000004        0x04000121    0x01C0003F    0x0000003F    0x00000001
    0x00000004        0x04000122    0x01C0003F    0x0000003F    0x00000001
    0x00000004        0x04004143    0x03C0003F    0x00000FFF    0x00000001
    0x00000005        0x00000040    0x00000040    0x00000003    0x00000020
    0x00000006        0x00000001    0x00000002    0x00000001    0x00000000
    0x00000007        0x00000000    0x00000000    0x00000000    0x00000000
    0x00000008        0x00000400    0x00000000    0x00000000    0x00000000
    0x00000009        0x00000000    0x00000000    0x00000000    0x00000000
    0x0000000A        0x07280202    0x00000000    0x00000000    0x00000000
    0x80000000        0x80000008    0x00000000    0x00000000    0x00000000
    0x80000001        0x00000000    0x00000000    0x00000001    0x20100000
    0x80000002        0x65746E49    0x2952286C    0x726F4320    0x4D542865
    0x80000003        0x43203229    0x20205550    0x20202020    0x20202020
    0x80000004        0x30323436    0x20402020    0x33312E32    0x007A4847
    0x80000005        0x00000000    0x00000000    0x00000000    0x00000000
    0x80000006        0x00000000    0x00000000    0x10008040    0x00000000
    0x80000007        0x00000000    0x00000000    0x00000000    0x00000000
    0x80000008        0x00003024    0x00000000    0x00000000    0x00000000

    MSR 0x0000001B        0x00000000    0xFEE00900
    MSR 0x00000017        0x00000000    0x88048829
    MSR 0x000000CD        0x00000000    0x00000800
    MSR 0x0000003F        0x00000000    0x000000EA
    MSR 0x000000CE        0x001B0829    0x7F7F0718
    MSR 0x000001A0        0x00000040    0x62972489
    MSR 0x000000EE        0xA8000000    0xC17D4300
    MSR 0x0000011E        0x00000000    0xBE702109
    MSR 0x0000019C        0x00000000    0x88200000
    MSR 0x00000198        0x08290829    0x06000829
    MSR 0x00000199        0x00000000    0x00000829

CPU Thread 1    
    APIC ID            1
    Topology        Processor ID 0, Core ID 1, Thread ID 0
    Type            01008001h
    Max CPUID level        0000000Ah
    Max CPUID ext. level    80000008h
    Cache descriptor    Level 1, D, 32 KB, 1 thread(s)
    Cache descriptor    Level 1, I, 32 KB, 1 thread(s)
    Cache descriptor    Level 2, U, 4 MB, 2 thread(s)

    CPUID         
    0x00000000        0x0000000A    0x756E6547    0x6C65746E    0x49656E69
    0x00000001        0x000006F6    0x01020800    0x0000E3BD    0xBFEBFBFF
    0x00000002        0x05B0B101    0x005657F0    0x00000000    0x2CB43049
    0x00000003        0x00000000    0x00000000    0x00000000    0x00000000
    0x00000004        0x04000121    0x01C0003F    0x0000003F    0x00000001
    0x00000004        0x04000122    0x01C0003F    0x0000003F    0x00000001
    0x00000004        0x04004143    0x03C0003F    0x00000FFF    0x00000001
    0x00000005        0x00000040    0x00000040    0x00000003    0x00000020
    0x00000006        0x00000001    0x00000002    0x00000001    0x00000000
    0x00000007        0x00000000    0x00000000    0x00000000    0x00000000
    0x00000008        0x00000400    0x00000000    0x00000000    0x00000000
    0x00000009        0x00000000    0x00000000    0x00000000    0x00000000
    0x0000000A        0x07280202    0x00000000    0x00000000    0x00000000
    0x80000000        0x80000008    0x00000000    0x00000000    0x00000000
    0x80000001        0x00000000    0x00000000    0x00000001    0x20100000
    0x80000002        0x65746E49    0x2952286C    0x726F4320    0x4D542865
    0x80000003        0x43203229    0x20205550    0x20202020    0x20202020
    0x80000004        0x30323436    0x20402020    0x33312E32    0x007A4847
    0x80000005        0x00000000    0x00000000    0x00000000    0x00000000
    0x80000006        0x00000000    0x00000000    0x10008040    0x00000000
    0x80000007        0x00000000    0x00000000    0x00000000    0x00000000
    0x80000008        0x00003024    0x00000000    0x00000000    0x00000000

    MSR 0x0000001B        0x00000000    0xFEE00800
    MSR 0x00000017        0x00000000    0x88048829
    MSR 0x000000CD        0x00000000    0x00000800
    MSR 0x0000003F        0x00000000    0x000000EA
    MSR 0x000000CE        0x001B0829    0x7F7F0718
    MSR 0x000001A0        0x00000040    0x62972489
    MSR 0x000000EE        0xA8000000    0xC17D4300
    MSR 0x0000011E        0x00000000    0xBE702109
    MSR 0x0000019C        0x00000000    0x88230000
    MSR 0x00000198        0x08290829    0x06000829
    MSR 0x00000199        0x00000000    0x00000829



Chipset
-------------------------------------------------------------------------

Northbridge            NVIDIA nForce4 SLI Intel Edition rev. A3
Southbridge            NVIDIA nForce 410/430 MCP rev. A2
Graphic Interface        PCI-Express
PCI-E Link Width        x8
PCI-E Max Link Width        x16
Memory Type            DDR2
Memory Size            3072 MBytes
Channels            Dual
Memory Frequency        266.7 MHz (1:1)
CAS# latency (CL)        4.0
RAS# to CAS# delay (tRCD)    4
RAS# Precharge (tRP)        4
Cycle Time (tRAS)        12
Bank Cycle Time (tRC)        16

Memory SPD
-------------------------------------------------------------------------

DIMM #                1
    SMBus address        0x50
    Memory type        DDR2
    Module format        Regular UDIMM
    Manufacturer (ID)    Infineon (C100000000000000)
    Size            1024 MBytes
    Max bandwidth        PC2-4300 (266 MHz)
    Part number        AET760UD00-370A08X
    Serial number        955C0915
    Manufacturing date    Week 32/Year 05
    Number of banks        1
    Data width        64 bits
    Correction        None
    Nominal Voltage        1.80 Volts
    EPP            no
    XMP            no
JEDEC timings table        CL-tRCD-tRP-tRAS-tRC @ frequency
    JEDEC #1        3.0-3-3-9-12 @ 200 MHz
    JEDEC #2        4.0-4-4-12-16 @ 266 MHz
    JEDEC #3        5.0-4-4-12-16 @ 266 MHz
SPD registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    80 08 08 0E 0A 60 40 00 05 3D 50 00 82 08 00 00 
    10    0C 08 38 00 02 00 01 3D 50 50 50 3C 1E 3C 2D 01 
    20    25 37 10 22 3C 1E 1E 00 00 3C 80 80 1E 28 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 00 00 11 3D 
    40    C1 00 00 00 00 00 00 00 4B 41 45 54 37 36 30 55 
    50    44 30 30 2D 33 37 30 41 30 38 58 20 01 05 32 95 
    60    5C 09 15 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    90    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    A0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    B0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    C0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    D0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    E0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    F0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 

DIMM #                2
    SMBus address        0x51
    Memory type        DDR2
    Module format        Regular UDIMM
    Manufacturer (ID)    Kingston (7F98000000000000)
    Size            2048 MBytes
    Max bandwidth        PC2-5300 (333 MHz)
    Part number        2G-UDIMM
    Serial number        B2146FE2
    Manufacturing date    Week 11/Year 08
    Number of banks        2
    Data width        64 bits
    Correction        None
    Nominal Voltage        1.80 Volts
    EPP            no
    XMP            no
JEDEC timings table        CL-tRCD-tRP-tRAS-tRC @ frequency
    JEDEC #1        3.0-3-3-9-12 @ 200 MHz
    JEDEC #2        4.0-4-4-12-16 @ 266 MHz
    JEDEC #3        5.0-5-5-15-20 @ 333 MHz
SPD registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    80 08 08 0E 0A 61 40 00 05 30 45 00 82 08 00 00 
    10    0C 08 38 01 02 00 03 3D 50 50 60 3C 1E 3C 2D 01 
    20    20 27 10 17 3C 1E 1E 00 06 3C 7F 80 18 22 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 13 
    40    7F 98 00 00 00 00 00 00 04 32 47 2D 55 44 49 4D 
    50    4D 00 00 00 00 00 00 00 00 00 00 00 00 08 0B B2 
    60    14 6F E2 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    39 39 30 35 33 31 36 2D 31 34 37 2E 41 30 30 4C 


Monitoring
-------------------------------------------------------------------------

Mainboard Model        C19/MCP51 (0x00000222 - 0x025E97EC)

LPCIO
-------------------------------------------------------------------------

LPCIO Vendor        NS
LPCIO Vendor ID        0xFF02
LPCIO Chip ID        0x5
LPCIO Revision ID    0x30
Config Mode I/O address    0x4E
Config Mode LDN        0x9
Config Mode registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    FF FF 00 FF FF FF FF 09 FF FF FF FF FF FF FF FF 
    10    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    20    05 41 20 19 34 00 80 30 40 00 00 00 00 0F 00 00 
    30    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    40    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    50    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    60    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    70    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 

Hardware Monitors
-------------------------------------------------------------------------

Hardware monitor    Hardware monitor ID=0x5CA300A0
Register space        SMBus, base address = 0x05100
SMBus request        channel 0x0, address 0x2F

        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    FF 04 00 03 FF FF FF FF FF FF FF FF FF FF FF FF 
    10    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    20    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    30    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    40    FF FF FF FF FF FF FF FF FF FF FF FF A3 5C A0 00 
    50    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    60    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    70    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    80    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    90    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    A0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    B0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    C0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    D0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    E0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
    F0    FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 

Hardware monitor    Intel Core 2 Duo E6420
    Temperature 0    53°C (127°F) [0x20] (Core #0)
    Temperature 1    50°C (121°F) [0x23] (Core #1)

Hardware monitor    NVIDIA GeForce 7900 GS
    Temperature 0    51°C (123°F) (GPU Core)


PCI Device
-------------------------------------------------------------------------

Description            Host Bridge
Location            bus 0 (0x00), device 0 (0x00), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x0071
    Revision ID        0xA3
    PI            0x00
    SubClass        0x00
    BaseClass        0x06
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0x00
    Int. Pin        0x00
PCI capability
    Caps class        tHyperTransport
    Caps offset        0x40
    Caps revision        0.16
    Interface type        Host/Secondary
    Device number    0
    Link 0 width (in/out)    8 bits/8 bits
    Link 0 frequency    800 MHz
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 71 00 06 00 B0 00 A3 00 00 06 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 40 00 00 00 00 00 00 00 00 00 00 00 
    40    08 00 01 20 22 10 00 00 10 35 3F 00 03 01 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    60    21 49 44 44 13 01 00 00 00 00 00 00 10 00 00 00 
    70    07 05 2E 00 00 00 00 00 81 01 05 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 0E 10 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    CB 10 00 02 F4 FF 00 00 00 00 00 00 E2 3B D0 BB 
    C0    11 31 03 00 31 10 01 00 03 00 00 00 00 50 07 00 
    D0    00 00 00 00 00 00 00 00 FF 3F 70 07 00 00 00 00 
    E0    08 00 01 A8 00 00 E0 FE 00 00 00 00 00 00 00 00 
    F0    01 00 FF FF 00 00 00 00 00 00 00 00 00 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 0 (0x00), function 1 (0x01)
Common header
    Vendor ID        0x10DE
    Model ID        0x007F
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0x00
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 7F 00 00 00 20 00 A1 00 00 05 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    40    00 00 00 00 00 00 60 51 32 04 00 00 00 00 00 00 
    50    00 00 10 00 22 22 16 00 11 11 00 00 08 00 00 00 
    60    21 24 15 04 DE 8F E1 1F 18 06 61 20 02 3F 00 20 
    70    10 32 54 0A 10 00 00 00 20 00 00 00 18 00 01 01 
    80    00 35 0C 00 00 00 00 00 00 00 50 3F 90 7F 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 01 00 00 00 80 F9 FD 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 C7 12 28 00 00 00 00 00 00 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 0 (0x00), function 2 (0x02)
Common header
    Vendor ID        0x10DE
    Model ID        0x0075
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0x00
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 75 00 00 00 20 00 A1 00 00 05 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    40    00 00 00 00 0B 80 C0 81 00 00 00 00 0B 80 C0 01 
    50    00 00 00 00 00 00 00 00 00 00 00 00 F2 01 1F C2 
    60    44 60 C3 58 FF FF 00 00 FF FF 00 00 FF FF 00 00 
    70    FF FF 00 00 44 60 C3 00 03 2C 1C 80 03 2C 1C 00 
    80    00 00 00 80 01 00 00 00 07 00 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 81 00 00 00 00 00 00 00 21 54 76 08 
    C0    FF FF FF FF FF FF FF FF 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 04 84 00 13 0A 00 00 00 04 08 A1 64 02 13 00 
    F0    1B 1B 1B 1B 00 FF 01 00 76 07 02 04 01 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 0 (0x00), function 3 (0x03)
Common header
    Vendor ID        0x10DE
    Model ID        0x006F
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x00
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0xFF
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 6F 00 00 00 A0 00 A1 00 00 05 00 00 00 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 
    40    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 02 10 1C A0 
    60    02 0C 1C 90 02 10 1C 90 02 0A 1C 80 02 0C 1C 80 
    70    02 10 1C 80 02 14 1C 80 02 0E 1C 80 02 1C 1C 80 
    80    01 10 1C 80 0C 40 C0 C1 00 00 00 00 00 00 00 00 
    90    00 00 00 00 1A C2 3F FF C4 80 02 00 01 0C 1C 80 
    A0    11 00 00 00 00 00 00 00 00 00 00 00 00 04 00 00 
    B0    02 10 1C 80 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    1C 00 E0 45 30 00 00 00 92 24 49 12 92 24 49 12 
    D0    01 08 FF FF 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    01 F9 00 09 00 00 00 00 12 00 00 00 36 07 00 00 
    F0    78 70 40 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 0 (0x00), function 4 (0x04)
Common header
    Vendor ID        0x10DE
    Model ID        0x00B4
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x00
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0xFF
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 B4 00 06 00 A0 00 A1 00 00 05 00 00 00 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 
    40    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    50    00 00 00 00 00 B8 D5 A4 D8 43 43 43 54 60 66 05 
    60    64 74 30 33 93 69 66 76 87 58 05 10 27 1A 27 0B 
    70    00 00 00 00 44 20 12 00 00 00 00 00 28 00 00 00 
    80    06 40 33 23 45 00 00 00 00 00 00 00 07 22 22 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 1 (0x01), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x0076
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0xFF
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 76 00 00 00 20 00 A1 00 00 05 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 
    40    10 00 00 00 4F 04 00 00 00 00 00 00 00 00 00 00 
    50    08 F8 F0 20 31 00 20 00 0C 0C 0C 7E 02 2B 7F 00 
    60    01 20 00 42 00 00 00 00 00 00 00 00 00 00 00 00 
    70    36 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    F3 13 33 E3 00 00 00 00 00 00 00 00 10 23 0C 44 
    90    26 97 23 20 50 83 72 34 0D 25 22 65 03 04 33 0A 
    A0    40 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 80 00 80 00 80 00 80 00 80 00 80 00 80 00 80 
    C0    00 00 27 00 31 26 24 00 00 00 00 00 33 0A 00 00 
    D0    00 00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 
    E0    03 00 00 00 11 01 07 00 00 00 00 00 F1 00 98 F8 
    F0    10 18 DE 08 20 10 04 00 00 00 00 00 21 03 0B 07 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 1 (0x01), function 1 (0x01)
Common header
    Vendor ID        0x10DE
    Model ID        0x0078
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0xFF
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 78 00 00 00 20 00 A1 00 00 05 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 
    40    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 5B 40 00 80 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    01 08 A0 3E 00 00 00 00 01 10 A0 BE 00 00 00 00 
    80    0A 08 00 00 13 20 1F 00 18 00 18 00 18 18 07 00 
    90    13 00 10 00 02 10 08 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 08 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 12 04 82 81 00 20 00 00 01 01 00 00 
    D0    4A 06 00 01 40 00 10 00 00 00 20 00 00 00 30 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 FF 20 FF 20 
    F0    FF 20 FF 7F 00 00 00 00 00 00 00 00 00 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 1 (0x01), function 2 (0x02)
Common header
    Vendor ID        0x10DE
    Model ID        0x0079
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0xFF
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 79 00 00 00 20 00 A1 00 00 05 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 
    40    F3 08 D0 32 00 00 00 00 68 1A 68 84 96 02 00 04 
    50    74 77 80 00 00 00 48 08 00 00 00 00 00 00 00 00 
    60    01 01 01 01 06 00 B1 3C 0A 22 77 57 50 50 F2 F2 
    70    95 13 00 00 25 F2 CE FB E1 00 01 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 1 (0x01), function 3 (0x03)
Common header
    Vendor ID        0x10DE
    Model ID        0x007A
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0xFF
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 7A 00 00 00 20 00 A1 00 00 05 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 
    40    38 4B 4B 4E 47 4D 4A 4F 00 00 00 00 00 00 00 00 
    50    00 00 00 00 A5 94 52 0A A5 94 52 0A A5 94 02 00 
    60    91 91 FF 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 11 00 01 00 00 00 00 00 
    90    00 00 00 01 00 00 00 00 00 00 00 00 99 99 99 99 
    A0    FF FF FF FF AF 0A F0 08 BA BA 89 8A AB A9 98 09 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 07 00 00 
    C0    00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00 
    D0    00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00 
    E0    00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00 
    F0    00 07 00 00 00 07 00 00 00 07 00 00 00 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 1 (0x01), function 4 (0x04)
Common header
    Vendor ID        0x10DE
    Model ID        0x007B
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0xFF
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 7B 00 00 00 20 00 A1 00 00 05 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 
    40    FC 1F 00 00 FF FF 00 00 98 3A 30 88 80 01 00 02 
    50    00 00 00 00 1F 1F 1F 00 0F 0F 0F 0F 0F 0F 0F 0F 
    60    0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 
    70    0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 
    80    0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 
    90    0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 
    A0    0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 0F 
    B0    11 0C 14 00 45 54 44 00 45 44 45 44 44 04 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 1 (0x01), function 5 (0x05)
Common header
    Vendor ID        0x10DE
    Model ID        0x007C
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0xFF
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 7C 00 00 00 20 00 A1 00 00 05 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 
    40    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 FF DF FF EF 00 00 00 00 FF DF FF EF 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    F9 05 F9 05 00 00 00 00 00 00 00 00 01 00 01 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 1 (0x01), function 6 (0x06)
Common header
    Vendor ID        0x10DE
    Model ID        0x007D
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x0000
    Subsystem ID        0x0000
    Int. Line        0xFF
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 7D 00 00 00 20 00 A1 00 00 05 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 
    40    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            PCI to PCI Bridge
Location            bus 0 (0x00), device 2 (0x02), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x007E
    Revision ID        0xA2
    PI            0x00
    SubClass        0x04
    BaseClass        0x06
    Cache Line        0x08
    Latency            0x00
    Header            0x01
PCI header
    Primary bus        0x00
    Secondary bus        0x01
    Int. Line        0xFF
    Int. Pin        0x00
PCI capability
    Caps class        Power Management
    Caps offset        0x40
    Caps version        1.1
PCI capability
    Caps class        Message Signalled Interrupts
    Caps offset        0x48
PCI capability
    Caps class        PCI Express
    Caps offset        0x80
    Device type        Root Port of PCI-E Root Complex
    Port            0
    Version            1.0
    Physical slot        #0
    Presence detect        no
    Link width        8x (max 8x)
Extended capabilities
    Caps class        Virtual Channel
    Caps offset        0x100
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 7E 00 07 00 10 00 A2 00 04 06 08 00 01 00 
    10    00 00 00 00 00 00 00 00 00 01 01 00 D1 D1 00 00 
    20    00 FA F0 FC 01 D0 F1 DF 00 00 00 00 00 00 00 00 
    30    00 00 00 00 40 00 00 00 00 00 00 00 FF 00 08 00 
    40    01 48 02 F8 00 00 00 00 05 80 82 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    10 00 41 01 C0 04 00 00 10 28 00 00 81 44 01 00 
    90    00 00 81 10 00 00 08 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    100    02 00 01 00 11 00 00 00 01 00 00 00 02 00 00 00 
    110    00 00 00 00 FF 00 00 80 00 00 00 00 00 00 00 00 
    120    00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 
    130    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            PCI to PCI Bridge
Location            bus 0 (0x00), device 4 (0x04), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x007E
    Revision ID        0xA2
    PI            0x00
    SubClass        0x04
    BaseClass        0x06
    Cache Line        0x08
    Latency            0x00
    Header            0x01
PCI header
    Primary bus        0x00
    Secondary bus        0x02
    Int. Line        0xFF
    Int. Pin        0x00
PCI capability
    Caps class        Power Management
    Caps offset        0x40
    Caps version        1.1
PCI capability
    Caps class        Message Signalled Interrupts
    Caps offset        0x48
PCI capability
    Caps class        PCI Express
    Caps offset        0x80
    Device type        Root Port of PCI-E Root Complex
    Port            1
    Version            1.0
    Physical slot        #0
    Presence detect        no
    Link width        8x (max 8x)
Extended capabilities
    Caps class        Virtual Channel
    Caps offset        0x100
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 7E 00 07 00 10 00 A2 00 04 06 08 00 01 00 
    10    00 00 00 00 00 00 00 00 00 02 02 00 C1 C1 00 00 
    20    D0 FD D0 FD C1 FD C1 FD 00 00 00 00 00 00 00 00 
    30    00 00 00 00 40 00 00 00 00 00 00 00 FF 00 04 00 
    40    01 48 02 F8 00 00 00 00 05 80 82 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    10 00 41 01 C0 04 00 00 10 28 00 00 81 44 01 01 
    90    00 00 81 10 00 00 10 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    100    02 00 01 00 11 00 00 00 01 00 00 00 02 00 00 00 
    110    00 00 00 00 FF 00 00 80 00 00 00 00 00 00 00 00 
    120    00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 
    130    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            PCI to PCI Bridge
Location            bus 0 (0x00), device 5 (0x05), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x007E
    Revision ID        0xA2
    PI            0x00
    SubClass        0x04
    BaseClass        0x06
    Cache Line        0x08
    Latency            0x00
    Header            0x01
PCI header
    Primary bus        0x00
    Secondary bus        0x03
    Int. Line        0xFF
    Int. Pin        0x00
PCI capability
    Caps class        Power Management
    Caps offset        0x40
    Caps version        1.1
PCI capability
    Caps class        Message Signalled Interrupts
    Caps offset        0x48
PCI capability
    Caps class        PCI Express
    Caps offset        0x80
    Device type        Root Port of PCI-E Root Complex
    Port            2
    Version            1.0
    Physical slot        #0
    Presence detect        no
    Link width        4x (max 1x)
Extended capabilities
    Caps class        Virtual Channel
    Caps offset        0x100
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 7E 00 07 00 10 00 A2 00 04 06 08 00 01 00 
    10    00 00 00 00 00 00 00 00 00 03 03 00 B1 B1 00 00 
    20    B0 FD B0 FD A1 FD A1 FD 00 00 00 00 00 00 00 00 
    30    00 00 00 00 40 00 00 00 00 00 00 00 FF 00 04 00 
    40    01 48 02 F8 00 00 00 00 05 80 82 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    10 00 41 01 C0 04 00 00 10 28 00 00 11 44 01 02 
    90    00 00 41 10 00 00 20 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    100    02 00 01 00 11 00 00 00 01 00 00 00 02 00 00 00 
    110    00 00 00 00 FF 00 00 80 00 00 00 00 00 00 00 00 
    120    00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 
    130    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            PCI to PCI Bridge
Location            bus 0 (0x00), device 6 (0x06), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x007E
    Revision ID        0xA2
    PI            0x00
    SubClass        0x04
    BaseClass        0x06
    Cache Line        0x08
    Latency            0x00
    Header            0x01
PCI header
    Primary bus        0x00
    Secondary bus        0x04
    Int. Line        0xFF
    Int. Pin        0x00
PCI capability
    Caps class        Power Management
    Caps offset        0x40
    Caps version        1.1
PCI capability
    Caps class        Message Signalled Interrupts
    Caps offset        0x48
PCI capability
    Caps class        PCI Express
    Caps offset        0x80
    Device type        Root Port of PCI-E Root Complex
    Port            3
    Version            1.0
    Physical slot        #1
    Presence detect        yes
    Link width        4x (max 1x)
Extended capabilities
    Caps class        Virtual Channel
    Caps offset        0x100
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 7E 00 07 00 10 00 A2 00 04 06 08 00 01 00 
    10    00 00 00 00 00 00 00 00 00 04 04 00 91 91 00 00 
    20    90 FD 90 FD 61 FD 61 FD 00 00 00 00 00 00 00 00 
    30    00 00 00 00 40 00 00 00 00 00 00 00 FF 00 04 00 
    40    01 48 02 F8 00 00 00 00 05 80 82 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    10 00 41 01 C0 04 00 00 10 28 00 00 11 44 01 03 
    90    00 00 41 10 00 00 40 00 00 00 48 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    100    02 00 01 00 11 00 00 00 01 00 00 00 02 00 00 00 
    110    00 00 00 00 FF 00 00 80 00 00 00 00 00 00 00 00 
    120    00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 
    130    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            PCI to PCI Bridge
Location            bus 0 (0x00), device 7 (0x07), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x007E
    Revision ID        0xA2
    PI            0x00
    SubClass        0x04
    BaseClass        0x06
    Cache Line        0x08
    Latency            0x00
    Header            0x01
PCI header
    Primary bus        0x00
    Secondary bus        0x05
    Int. Line        0xFF
    Int. Pin        0x00
PCI capability
    Caps class        Power Management
    Caps offset        0x40
    Caps version        1.1
PCI capability
    Caps class        Message Signalled Interrupts
    Caps offset        0x48
PCI capability
    Caps class        PCI Express
    Caps offset        0x80
    Device type        Root Port of PCI-E Root Complex
    Port            4
    Version            1.0
    Physical slot        #2
    Presence detect        yes
    Link width        1x (max 1x)
Extended capabilities
    Caps class        Virtual Channel
    Caps offset        0x100
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 7E 00 07 00 10 00 A2 00 04 06 08 00 01 00 
    10    00 00 00 00 00 00 00 00 00 05 05 00 E1 E1 00 00 
    20    50 FD 50 FD E1 FD E1 FD 00 00 00 00 00 00 00 00 
    30    00 00 00 00 40 00 00 00 00 00 00 00 FF 00 04 00 
    40    01 48 02 F8 00 00 00 00 05 80 82 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    10 00 41 01 C0 04 00 00 10 28 00 00 11 44 01 04 
    90    00 00 11 10 00 00 80 00 00 00 48 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    100    02 00 01 00 11 00 00 00 01 00 00 00 02 00 00 00 
    110    00 00 00 00 FF 00 00 80 00 00 00 00 00 00 00 00 
    120    00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 
    130    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 9 (0x09), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x0270
    Revision ID        0xA2
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x00
PCI header
    Subvendor ID        0x10DE
    Subsystem ID        0xCB84
    Int. Line        0xFF
    Int. Pin        0x00
PCI capability
    Caps class        tHyperTransport
    Caps offset        0x44
    Caps revision        1.03
    Interface type        Slave/Primary
    Link 0 width (in/out)    8 bits/8 bits
    Link 0 frequency    800 MHz
    Link 1 width (in/out)    8 bits/8 bits
    Link 1 frequency    200 MHz
PCI capability
    Caps class        tHyperTransport
    Caps offset        0xE0
    Interface type        MSI Mapping
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 70 02 06 00 B0 00 A2 00 00 05 00 00 00 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
    30    00 00 00 00 44 00 00 00 00 00 00 00 FF 00 00 00 
    40    DE 10 84 CB 08 E0 E9 01 22 30 00 00 D0 00 00 00 
    50    23 05 7F 80 03 00 00 00 00 00 03 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 06 06 05 00 
    70    44 44 44 00 50 01 00 00 11 00 00 00 11 11 55 00 
    80    23 55 55 00 FA 00 64 0C 03 00 00 00 7F 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 01 01 01 01 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 80 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    08 00 00 A8 00 00 E0 FE 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            PCI to ISA Bridge
Location            bus 0 (0x00), device 10 (0x0A), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x0260
    Revision ID        0xA2
    PI            0x00
    SubClass        0x01
    BaseClass        0x06
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x10DE
    Subsystem ID        0xCB84
    Int. Line        0xFF
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 60 02 0F 00 A0 00 A2 00 01 06 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
    30    00 00 00 00 00 00 00 00 00 00 00 00 FF 00 00 00 
    40    DE 10 84 CB 00 00 00 00 FA 3E FF 00 FA 3E FF 00 
    50    FA 3E FF 00 00 5A 62 02 00 00 00 01 00 00 FF FF 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 F9 FF 
    70    10 00 FF FF CD 00 00 00 00 00 44 19 03 00 03 00 
    80    09 20 00 21 0D 18 00 00 C0 00 00 01 00 00 00 00 
    90    00 00 00 00 00 00 00 00 21 47 65 B7 EF CD 00 00 
    A0    00 00 10 51 00 00 00 00 00 04 0F 04 00 00 00 00 
    B0    90 02 9F 02 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 10 00 00 00 00 00 00 00 

Description            SMBus Controller
Location            bus 0 (0x00), device 10 (0x0A), function 1 (0x01)
Common header
    Vendor ID        0x10DE
    Model ID        0x0264
    Revision ID        0xA2
    PI            0x00
    SubClass        0x05
    BaseClass        0x0C
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Address 4 (port)    0x00005000
    Address 5 (port)    0x00005100
    Subvendor ID        0x10DE
    Subsystem ID        0xCB84
    Int. Line        0x0B
    Int. Pin        0x01
PCI capability
    Caps class        Power Management
    Caps offset        0x44
    Caps version        1.1
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 64 02 01 00 B0 00 A2 00 05 0C 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    01 50 00 00 01 51 00 00 00 00 00 00 DE 10 84 CB 
    30    00 00 00 00 44 00 00 00 00 00 00 00 0B 01 00 00 
    40    DE 10 84 CB 01 00 02 C0 00 00 00 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    60    01 40 00 00 01 44 00 00 01 48 00 00 00 00 00 00 
    70    01 00 00 00 00 00 FC FD 00 00 00 00 01 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    D4 30 80 01 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    10 10 04 00 00 A0 80 00 80 30 00 00 41 44 44 11 
    F0    5A FF 5F BF 00 00 00 C0 10 00 00 00 00 00 00 00 

Description            RAM Memory Controller
Location            bus 0 (0x00), device 10 (0x0A), function 2 (0x02)
Common header
    Vendor ID        0x10DE
    Model ID        0x0272
    Revision ID        0xA2
    PI            0x00
    SubClass        0x00
    BaseClass        0x05
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Subvendor ID        0x10DE
    Subsystem ID        0xCB84
    Int. Line        0x00
    Int. Pin        0x00
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 72 02 00 04 A0 00 A2 00 00 05 00 00 80 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
    30    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    40    00 00 00 00 00 00 00 00 10 00 00 10 00 00 10 10 
    50    10 10 10 10 00 00 00 00 00 00 00 00 00 00 00 00 
    60    02 03 00 00 12 00 00 00 02 00 00 00 10 01 12 00 
    70    32 33 00 00 03 00 00 00 00 00 00 00 12 01 00 00 
    80    10 00 00 00 00 00 00 00 00 00 00 00 30 02 00 00 
    90    00 00 00 00 01 20 00 00 01 00 00 00 00 09 00 00 
    A0    01 02 00 00 00 10 00 00 05 00 00 00 01 00 00 00 
    B0    00 10 00 80 01 00 00 80 00 00 00 00 02 00 00 00 
    C0    07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            USB Controller (OHCI)
Location            bus 0 (0x00), device 11 (0x0B), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x026D
    Revision ID        0xA2
    PI            0x10
    SubClass        0x03
    BaseClass        0x0C
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Address 0 (memory)    0xFE02F000
    Subvendor ID        0x10DE
    Subsystem ID        0xCB84
    Int. Line        0x15
    Int. Pin        0x01
PCI capability
    Caps class        Power Management
    Caps offset        0x44
    Caps version        1.1
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 6D 02 07 00 B0 00 A2 10 03 0C 00 00 80 00 
    10    00 F0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
    30    00 00 00 00 44 00 00 00 00 00 00 00 15 01 03 01 
    40    DE 10 84 CB 01 00 02 FE 00 00 00 00 00 00 00 00 
    50    4C 00 00 00 1D 47 40 00 10 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            USB 2.0 Controller (EHCI)
Location            bus 0 (0x00), device 11 (0x0B), function 1 (0x01)
Common header
    Vendor ID        0x10DE
    Model ID        0x026E
    Revision ID        0xA2
    PI            0x20
    SubClass        0x03
    BaseClass        0x0C
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Address 0 (memory)    0xFE02E000
    Subvendor ID        0x10DE
    Subsystem ID        0xCB84
    Int. Line        0x16
    Int. Pin        0x02
PCI capability
    Caps class        Debug Port
    Caps offset        0x44
PCI capability
    Caps class        Power Management
    Caps offset        0x80
    Caps version        1.1
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 6E 02 06 00 B0 00 A2 20 03 0C 00 00 80 00 
    10    00 E0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
    30    00 00 00 00 44 00 00 00 00 00 00 00 16 02 03 01 
    40    DE 10 84 CB 0A 80 98 20 00 00 00 00 00 00 00 00 
    50    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    60    20 20 01 00 00 60 18 85 03 3C 0A 01 00 00 00 00 
    70    00 00 08 05 00 10 20 80 89 3D B6 22 77 25 F4 00 
    80    01 00 02 FE 00 00 00 00 00 00 00 00 15 16 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    01 00 01 01 00 00 00 E0 00 00 00 00 00 00 00 00 
    B0    00 11 22 33 00 00 00 00 FF 00 00 00 00 00 00 00 
    C0    10 10 2D 0D 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 10 00 00 00 00 00 00 00 

Description            IDE Controller
Location            bus 0 (0x00), device 13 (0x0D), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x0265
    Revision ID        0xA1
    PI            0x8A
    SubClass        0x01
    BaseClass        0x01
    Cache Line        0x00
    Latency            0x00
    Header            0x00
PCI header
    Address 4 (port)    0x0000FD00
    Subvendor ID        0x10DE
    Subsystem ID        0xCB84
    Int. Line        0x00
    Int. Pin        0x00
PCI capability
    Caps class        Power Management
    Caps offset        0x44
    Caps version        1.1
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 65 02 05 00 B0 00 A1 8A 01 01 00 00 00 00 
    10    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    20    01 FD 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
    30    00 00 00 00 44 00 00 00 00 00 00 00 00 00 03 01 
    40    DE 10 84 CB 01 00 02 00 00 00 00 00 00 00 00 00 
    50    03 F0 01 00 00 00 00 00 20 20 A8 A8 A6 00 20 99 
    60    00 C0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 E8 BA 3A 0A 
    90    00 00 74 02 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 10 00 00 00 00 00 00 00 

Description            IDE Controller
Location            bus 0 (0x00), device 14 (0x0E), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x0266
    Revision ID        0xA1
    PI            0x85
    SubClass        0x01
    BaseClass        0x01
    Cache Line        0x00
    Latency            0x00
    Header            0x00
PCI header
    Address 0 (port)    0x000009F0
    Address 1 (port)    0x00000BF0
    Address 2 (port)    0x00000970
    Address 3 (port)    0x00000B70
    Address 4 (port)    0x0000F800
    Address 5 (memory)    0xFE02D000
    Subvendor ID        0x10DE
    Subsystem ID        0xCB84
    Int. Line        0x16
    Int. Pin        0x01
PCI capability
    Caps class        Power Management
    Caps offset        0x44
    Caps version        1.1
PCI capability
    Caps class        Message Signalled Interrupts
    Caps offset        0xB0
PCI capability
    Caps class        tHyperTransport
    Caps offset        0xCC
    Interface type        MSI Mapping
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 66 02 07 00 B0 00 A1 85 01 01 00 00 00 00 
    10    F1 09 00 00 F1 0B 00 00 71 09 00 00 71 0B 00 00 
    20    01 F8 00 00 00 D0 02 FE 00 00 00 00 DE 10 84 CB 
    30    00 00 00 00 44 00 00 00 00 00 00 00 16 01 03 01 
    40    DE 10 84 CB 01 B0 02 00 00 00 00 00 00 00 00 00 
    50    03 00 00 00 00 00 00 00 A8 20 A8 20 66 00 20 20 
    60    00 C7 00 C7 51 0C 00 00 00 0F 06 42 00 00 00 00 
    70    2C 78 C4 40 01 10 00 00 01 10 00 00 20 00 20 00 
    80    00 00 00 C0 00 50 93 AE 00 00 B8 AE 00 90 8F 20 
    90    00 00 20 8F 00 00 00 00 06 00 06 10 00 00 01 01 
    A0    14 10 00 2C 00 00 00 00 00 00 00 00 33 33 00 02 
    B0    05 CC 84 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 0A 00 0A 00 08 00 02 A8 
    D0    0A 00 02 06 42 00 00 00 00 00 00 00 0F 00 30 E0 
    E0    0A 00 02 06 42 00 00 00 00 00 00 00 00 40 01 E1 
    F0    00 00 00 00 00 00 00 00 00 00 0C 00 00 00 00 00 

Description            IDE Controller
Location            bus 0 (0x00), device 15 (0x0F), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x0267
    Revision ID        0xA1
    PI            0x85
    SubClass        0x01
    BaseClass        0x01
    Cache Line        0x00
    Latency            0x00
    Header            0x00
PCI header
    Address 0 (port)    0x000009E0
    Address 1 (port)    0x00000BE0
    Address 2 (port)    0x00000960
    Address 3 (port)    0x00000B60
    Address 4 (port)    0x0000F300
    Address 5 (memory)    0xFE02C000
    Subvendor ID        0x10DE
    Subsystem ID        0xCB84
    Int. Line        0x17
    Int. Pin        0x01
PCI capability
    Caps class        Power Management
    Caps offset        0x44
    Caps version        1.1
PCI capability
    Caps class        Message Signalled Interrupts
    Caps offset        0xB0
PCI capability
    Caps class        tHyperTransport
    Caps offset        0xCC
    Interface type        MSI Mapping
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 67 02 07 00 B0 00 A1 85 01 01 00 00 00 00 
    10    E1 09 00 00 E1 0B 00 00 61 09 00 00 61 0B 00 00 
    20    01 F3 00 00 00 C0 02 FE 00 00 00 00 DE 10 84 CB 
    30    00 00 00 00 44 00 00 00 00 00 00 00 17 01 03 01 
    40    DE 10 84 CB 01 B0 02 00 00 00 00 00 00 00 00 00 
    50    03 00 00 00 00 00 00 00 A8 A8 A8 A8 AA 00 99 99 
    60    00 00 00 00 51 0C 00 00 00 0F 06 42 00 00 00 00 
    70    2C 78 C4 40 01 10 00 00 01 10 00 00 20 00 20 00 
    80    00 00 00 00 0D AC 89 C9 00 00 81 0A AD A6 00 51 
    90    00 00 FC 33 00 00 00 00 06 00 06 10 00 00 01 01 
    A0    14 10 00 00 00 00 00 00 00 00 00 00 33 33 00 02 
    B0    05 CC 84 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 0A 00 0A 00 08 00 02 A8 
    D0    0A 00 02 06 42 00 00 00 00 00 00 00 00 00 F0 07 
    E0    0A 00 02 06 42 00 00 00 00 00 00 00 00 00 F0 07 
    F0    00 00 00 00 00 00 00 00 00 00 0C 00 00 00 00 00 

Description            PCI to PCI Bridge
Location            bus 0 (0x00), device 16 (0x10), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x026F
    Revision ID        0xA2
    PI            0x01
    SubClass        0x04
    BaseClass        0x06
    Cache Line        0x00
    Latency            0x00
    Header            0x81
PCI header
    Primary bus        0x00
    Secondary bus        0x06
    Int. Line        0xFF
    Int. Pin        0x00
PCI capability
    Caps class        Subsystem Vendor
    Caps offset        0xB8
    SubVendor ID        0x10DE
    SubSystem ID        0xCB84
PCI capability
    Caps class        tHyperTransport
    Caps offset        0x8C
    Interface type        MSI Mapping
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 6F 02 07 00 B0 00 A2 01 04 06 00 00 81 00 
    10    00 00 00 00 00 00 00 00 00 06 06 20 F0 00 80 02 
    20    F0 FF 00 00 F0 FF 00 00 00 00 00 00 00 00 00 00 
    30    00 00 00 00 B8 00 00 00 00 00 00 00 FF 00 00 02 
    40    00 00 03 00 01 00 02 00 05 00 00 00 00 00 44 00 
    50    00 00 FE BF 00 00 00 00 FF 1F FF 1F 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 FE 3F 00 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 08 00 00 A8 
    90    00 00 E0 FE 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    06 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 FF FF 00 00 0D 8C 00 00 DE 10 84 CB 
    C0    DE 10 84 CB 03 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description            Multimedia device
Location            bus 0 (0x00), device 16 (0x10), function 1 (0x01)
Common header
    Vendor ID        0x10DE
    Model ID        0x026C
    Revision ID        0xA2
    PI            0x00
    SubClass        0x03
    BaseClass        0x04
    Cache Line        0x00
    Latency            0x00
    Header            0x80
PCI header
    Address 0 (memory)    0xFE024000
    Subvendor ID        0x16F3
    Subsystem ID        0x6601
    Int. Line        0x17
    Int. Pin        0x02
PCI capability
    Caps class        Power Management
    Caps offset        0x44
    Caps version        1.1
PCI capability
    Caps class        Message Signalled Interrupts
    Caps offset        0x50
PCI capability
    Caps class        tHyperTransport
    Caps offset        0x6C
    Interface type        MSI Mapping
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 6C 02 06 00 B0 00 A2 00 03 04 00 00 80 00 
    10    00 40 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 F3 16 01 66 
    30    00 00 00 00 44 00 00 00 00 00 00 00 17 02 02 05 
    40    F3 16 01 66 01 50 02 C0 00 00 00 00 01 01 0F 00 
    50    05 6C 80 01 00 00 00 00 00 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 0F 00 00 00 08 00 02 A8 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 46 00 29 00 00 00 00 00 00 

Description            Bridge device
Location            bus 0 (0x00), device 20 (0x14), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x0269
    Revision ID        0xA1
    PI            0x00
    SubClass        0x80
    BaseClass        0x06
    Cache Line        0x00
    Latency            0x00
    Header            0x00
PCI header
    Address 0 (memory)    0xFE02B000
    Address 1 (port)    0x0000F200
    Subvendor ID        0x10DE
    Subsystem ID        0xCB84
    Int. Line        0x14
    Int. Pin        0x01
PCI capability
    Caps class        Power Management
    Caps offset        0x44
    Caps version        1.1
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 69 02 07 00 B0 00 A1 00 80 06 00 00 00 00 
    10    00 B0 02 FE 01 F2 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
    30    00 00 00 00 44 00 00 00 00 00 00 00 14 01 01 14 
    40    DE 10 84 CB 01 00 02 FE 00 00 00 00 0B 00 00 10 
    50    05 6C 84 01 00 00 00 00 00 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 0F 00 00 00 08 00 02 A8 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 11 00 00 00 42 01 00 00 00 00 00 00 

Description            VGA Controller
Location            bus 1 (0x01), device 0 (0x00), function 0 (0x00)
Common header
    Vendor ID        0x10DE
    Model ID        0x0292
    Revision ID        0xA1
    PI            0x00
    SubClass        0x00
    BaseClass        0x03
    Cache Line        0x08
    Latency            0x00
    Header            0x00
PCI header
    Address 0 (memory)    0xFA000000
    Address 1 (memory)    0xD0000000
    Address 3 (memory)    0xFB000000
    Address 5 (port)    0x0000DF00
    Subvendor ID        0x196E
    Subsystem ID        0x0429
    Int. Line        0x10
    Int. Pin        0x01
PCI capability
    Caps class        Power Management
    Caps offset        0x60
    Caps version        1.1
PCI capability
    Caps class        Message Signalled Interrupts
    Caps offset        0x68
PCI capability
    Caps class        PCI Express
    Caps offset        0x78
    Device type        PCI-E Endpoint Device
    Port            0
    Version            1.0
    Link width        8x (max 16x)
Extended capabilities
    Caps class        Virtual Channel
    Caps offset        0x100
    Caps class        Power Budgeting
    Caps offset        0x128
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    DE 10 92 02 07 00 10 00 A1 00 00 03 08 00 00 00 
    10    00 00 00 FA 0C 00 00 D0 00 00 00 00 04 00 00 FB 
    20    00 00 00 00 01 DF 00 00 00 00 00 00 6E 19 29 04 
    30    00 00 00 00 60 00 00 00 00 00 00 00 10 01 00 00 
    40    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    50    01 00 00 00 01 00 00 00 CE D6 23 00 00 00 00 00 
    60    01 68 02 00 00 00 00 00 05 78 80 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 10 00 01 00 00 05 00 00 
    80    10 28 00 00 01 4D 01 00 08 00 81 10 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    100    02 00 81 12 00 00 00 00 00 00 00 00 00 00 00 00 
    110    00 00 00 00 FF 00 00 80 00 00 00 00 00 00 00 00 
    120    00 00 00 00 00 00 00 00 04 00 01 00 00 00 00 00 
    130    21 81 07 00 00 00 00 00 00 01 00 00 00 00 00 07 

Description            OHCI FireWire Controller
Location            bus 6 (0x06), device 3 (0x03), function 0 (0x00)
Common header
    Vendor ID        0x1106
    Model ID        0x3044
    Revision ID        0x80
    PI            0x10
    SubClass        0x00
    BaseClass        0x0C
    Cache Line        0x08
    Latency            0x20
    Header            0x00
PCI header
    Address 0 (memory)    0xFD8FF000
    Address 1 (port)    0x0000AF00
    Subvendor ID        0x1106
    Subsystem ID        0x3044
    Int. Line        0x10
    Int. Pin        0x01
PCI capability
    Caps class        Power Management
    Caps offset        0x50
    Caps version        1.1
PCI registers    
        00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    00    06 11 44 30 87 00 10 02 80 10 00 0C 08 20 00 00 
    10    00 F0 8F FD 01 AF 00 00 00 00 00 00 00 00 00 00 
    20    00 00 00 00 00 00 00 00 00 00 00 00 06 11 44 30 
    30    00 00 00 00 50 00 00 00 00 00 00 00 10 01 00 20 
    40    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    50    01 00 02 E4 00 00 00 00 00 00 00 00 00 00 00 00 
    60    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    70    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    80    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    90    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    A0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    B0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    C0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    D0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    E0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    F0    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


DMI
-------------------------------------------------------------------------

DMI BIOS        
    vendor            Phoenix Technologies, LTD
    version            6.00 PG
    date            10/11/2006

DMI System Information        
    manufacturer        unknown
    product            unknown
    version            unknown
    serial            unknown
    UUID            FFFFFFFF-FFFFFFFF-FFFFFFFF-FFFFFFFF

DMI Baseboard        
    vendor            unknown
    model            C19/MCP51
    revision        unknown
    serial            unknown

DMI System Enclosure        
    manufacturer        unknown
    chassis type        Desktop
    chassis serial        unknown

DMI Processor        
    manufacturer        Intel
    model            Intel(R) Core(TM)2
    clock speed        2128.0 MHz
    FSB speed        266.0 MHz
    multiplier        8.0x

DMI Processor        
    manufacturer        Intel
    model            Intel(R) Core(TM)2
    clock speed        2128.0 MHz
    FSB speed        266.0 MHz
    multiplier        8.0x

DMI Memory Controller        
    correction        8-bit parity
    Max module size        32 MBytes

DMI Memory Module        
    designation        A0
    size            1024 MBytes (single bank)

DMI Memory Module        
    designation        A1

DMI Memory Module        
    designation        A2
    size            2048 MBytes (double bank)

DMI Memory Module        
    designation        A3

DMI Port Connector        
    designation        PRIMARY IDE (internal)
    connector        On Board IDE

DMI Port Connector        
    designation        SECONDARY IDE (internal)
    connector        On Board IDE

DMI Port Connector        
    designation        FDD (internal)
    port type        8251 FIFO Compatible
    connector        On Board Floppy

DMI Port Connector        
    designation        COM1 (internal)
    port type        Serial Port 16450
    connector        9 Pin Dual Inline (pin 10 cut)
    connector        DB-9 male

DMI Port Connector        
    designation        COM2 (internal)
    port type        Serial Port 16450
    connector        9 Pin Dual Inline (pin 10 cut)
    connector        DB-9 male

DMI Port Connector        
    designation        LPT1 (internal)
    port type        Parallel Port ECP/EPP
    connector        DB-25 female
    connector        DB-25 female

DMI Port Connector        
    designation        Keyboard (internal)
    port type        Keyboard Port
    connector        PS/2
    connector        PS/2

DMI Port Connector        
    designation        PS/2 Mouse (internal)
    port type        Mouse Port
    connector        PS/2
    connector        PS/2

DMI Port Connector        
    designation        USB0 (external)
    port type        USB

DMI Extension Slot        
    designation        PCI0
    type            PCI
    width            32 bits
    populated        no

DMI Extension Slot        
    designation        PCI1
    type            PCI
    width            32 bits
    populated        no

DMI Extension Slot        
    designation        PCI2
    type            PCI
    width            32 bits
    populated        yes

DMI Extension Slot        
    designation        PCI3
    type            A5
    width            32 bits
    populated        yes

DMI Physical Memory Array        
    location        Motherboard
    usage            System Memory
    correction        None
    max capacity        2048 MBytes
    max# of devices        4

DMI Memory Device        
    designation        A0
    format            DIMM
    type            unknown
    size            1024 MBytes

DMI Memory Device        
    designation        A1
    format            DIMM
    type            unknown

DMI Memory Device        
    designation        A2
    format            DIMM
    type            unknown
    size            2048 MBytes

DMI Memory Device        
    designation        A3
    format            DIMM
    type            unknown


Graphics
-------------------------------------------------------------------------

Number of adapters        1

Graphic APIs
-------------------------------------------------------------------------

API                NVIDIA NVAPI
API                NVIDIA I/O

Display Adapters
-------------------------------------------------------------------------

Display adapter 0    
    Manuf. API index    0
    Display name        \\.\DISPLAY1
    Name            NVIDIA GeForce 7900 GS
    Revision        A2
    Codename        G71
    Technology        90 nm
    Memory size        256 MB
    Memory type        DDR3
    Memory bus width    256 bits
    PCI device        bus 1 (0x1), device 0 (0x0), function 0 (0x0)
    Vendor ID        0x10DE (0x196E)
    Model ID        0x292 (0x429)
    Performance Level    Default
        Core clock    450.0 MHz
        Memory clock    660.0 MHz
    Performance Level    3D Applications
        Core clock    450.0 MHz
        Memory clock    660.0 MHz


Software
-------------------------------------------------------------------------

Windows Version            Microsoft Windows XP Professional  Service Pack 3 (Build 2600) 
DirectX Version            9.0c


I have the parts list from when I ordered it all from Newegg about two years ago. would you like me to post up any of the parts from there? or does this report cover it all?




Joseph.

---

### Post by hachikid on 2009-09-14
hey. here is the video. I got it off my phone:

[http://www.youtube.com/watch?v=yQaYVHqbcdY](http://www.youtube.com/watch?v=yQaYVHqbcdY)


anybody have any idea what's going on?





Joseph.

---

### Post by hachikid on 2009-09-15
bump.

---

