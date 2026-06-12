---
title: "Wubi - Install help"
date: 2010-01-12
forum: General Help
---

### Post by richard.hughes on 2010-01-12
Hello

I am having trouble installing Ubuntu via wubi. Here is the error I get:

/scripts/casper-premount/20iso_scan: Line 45: Can't open /dev/sr0: No medium found

<a bit further down>

Could not find /ubuntu/install/ubuntu-9.10-desktop-amd64.iso

My system spec (from CPUID) is as follows:

[PHP]
CPU-Z TXT Report
-------------------------------------------------------------------------

Binaries
-------------------------------------------------------------------------

CPU-Z version			1.53.1

Processors
-------------------------------------------------------------------------

Number of processors		1
Number of threads		2

APICs
-------------------------------------------------------------------------

Processor 0	
	-- Core 0	
		-- Thread 0	0
	-- Core 1	
		-- Thread 0	1

Processors Information
-------------------------------------------------------------------------

Processor 1			ID = 0
	Number of cores		2 (max 2)
	Number of threads	2 (max 2)
	Name			AMD Athlon 64 X2 5600+
	Codename		Windsor
	Specification		AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
	Package 		Socket AM2 (940)
	CPUID			F.3.3
	Extended CPUID		F.43
	Brand ID		4
	Core Stepping		JH-F3
	Technology		90 nm
	Core Speed		2600.4 MHz
	Multiplier x FSB	13.0 x 200.0 MHz
	HT Link speed		1000.2 MHz
	Stock frequency		2800 MHz
	Instructions sets	MMX (+), 3DNow! (+), SSE, SSE2, SSE3, x86-64, AMD-V
	L1 Data cache		2 x 64 KBytes, 2-way set associative, 64-byte line size
	L1 Instruction cache	2 x 64 KBytes, 2-way set associative, 64-byte line size
	L2 cache		2 x 1024 KBytes, 16-way set associative, 64-byte line size
	FID/VID Control		yes
	Max FID			14.0x
	Max VID			1.350 V

	K8 Thermal sensor	yes
	K8 Revision ID		5.3
	Attached device		PCI device at bus 0, device 24, function 0
	Attached device		PCI device at bus 0, device 24, function 1
	Attached device		PCI device at bus 0, device 24, function 2
	Attached device		PCI device at bus 0, device 24, function 3


Thread dumps
-------------------------------------------------------------------------

CPU Thread 0	
	APIC ID			0
	Topology		Processor ID 0, Core ID 0, Thread ID 0
	Type			02002008h
	Max CPUID level		00000001h
	Max CPUID ext. level	80000018h
	Cache descriptor	Level 1, I, 64 KB, 1 thread(s)
	Cache descriptor	Level 1, D, 64 KB, 1 thread(s)
	Cache descriptor	Level 2, U, 1 MB, 1 thread(s)

	CPUID		 
	0x00000000		0x00000001	0x68747541	0x444D4163	0x69746E65
	0x00000001		0x00040F33	0x00020800	0x00002001	0x178BFBFF
	0x80000000		0x80000018	0x68747541	0x444D4163	0x69746E65
	0x80000001		0x00040F33	0x0000091F	0x0000001F	0xEBD3FBFF
	0x80000002		0x20444D41	0x6C687441	0x74286E6F	0x3620296D
	0x80000003		0x32582034	0x61754420	0x6F43206C	0x50206572
	0x80000004		0x65636F72	0x726F7373	0x30363520	0x00002B30
	0x80000005		0xFF08FF08	0xFF20FF20	0x40020140	0x40020140
	0x80000006		0x00000000	0x42004200	0x04008140	0x00000000
	0x80000007		0x00000000	0x00000000	0x00000000	0x0000003F
	0x80000008		0x00003028	0x00000000	0x00000001	0x00000000
	0x80000009		0x00000000	0x00000000	0x00000000	0x00000000
	0x8000000A		0x00000001	0x00000040	0x00000000	0x00000000
	0x8000000B		0x00000000	0x00000000	0x00000000	0x00000000
	0x8000000C		0x00000000	0x00000000	0x00000000	0x00000000
	0x8000000D		0x00000000	0x00000000	0x00000000	0x00000000
	0x8000000E		0x00000000	0x00000000	0x00000000	0x00000000
	0x8000000F		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000010		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000011		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000012		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000013		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000014		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000015		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000016		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000017		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000018		0x00000000	0x00000000	0x00000000	0x00000000

	MSR 0x0000001B		0x00000000	0xFEE00900
	MSR 0xC001001E		0x00000000	0x00000053
	MSR 0xC0010015		0x00000000	0x02000040
	MSR 0xC0010042		0x3108120A	0x08140214
	MSR 0xC0010041		0x00000001	0x00000A14

CPU Thread 1	
	APIC ID			1
	Topology		Processor ID 0, Core ID 1, Thread ID 0
	Type			02002008h
	Max CPUID level		00000001h
	Max CPUID ext. level	80000018h
	Cache descriptor	Level 1, I, 64 KB, 1 thread(s)
	Cache descriptor	Level 1, D, 64 KB, 1 thread(s)
	Cache descriptor	Level 2, U, 1 MB, 1 thread(s)

	CPUID		 
	0x00000000		0x00000001	0x68747541	0x444D4163	0x69746E65
	0x00000001		0x00040F33	0x01020800	0x00002001	0x178BFBFF
	0x80000000		0x80000018	0x68747541	0x444D4163	0x69746E65
	0x80000001		0x00040F33	0x0000091F	0x0000001F	0xEBD3FBFF
	0x80000002		0x20444D41	0x6C687441	0x74286E6F	0x3620296D
	0x80000003		0x32582034	0x61754420	0x6F43206C	0x50206572
	0x80000004		0x65636F72	0x726F7373	0x30363520	0x00002B30
	0x80000005		0xFF08FF08	0xFF20FF20	0x40020140	0x40020140
	0x80000006		0x00000000	0x42004200	0x04008140	0x00000000
	0x80000007		0x00000000	0x00000000	0x00000000	0x0000003F
	0x80000008		0x00003028	0x00000000	0x00000001	0x00000000
	0x80000009		0x00000000	0x00000000	0x00000000	0x00000000
	0x8000000A		0x00000001	0x00000040	0x00000000	0x00000000
	0x8000000B		0x00000000	0x00000000	0x00000000	0x00000000
	0x8000000C		0x00000000	0x00000000	0x00000000	0x00000000
	0x8000000D		0x00000000	0x00000000	0x00000000	0x00000000
	0x8000000E		0x00000000	0x00000000	0x00000000	0x00000000
	0x8000000F		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000010		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000011		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000012		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000013		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000014		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000015		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000016		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000017		0x00000000	0x00000000	0x00000000	0x00000000
	0x80000018		0x00000000	0x00000000	0x00000000	0x00000000

	MSR 0x0000001B		0x00000000	0xFEE00800
	MSR 0xC001001E		0x00000000	0x00000053
	MSR 0xC0010015		0x00000000	0x02000040
	MSR 0xC0010042		0x3108120A	0x08140214
	MSR 0xC0010041		0x00000001	0x00000A14



Chipset
-------------------------------------------------------------------------

Northbridge			NVIDIA GeForce 8300 rev. A2
Southbridge			NVIDIA ID075C rev. A2
Graphic Interface		PCI-Express
PCI-E Link Width		x16
PCI-E Max Link Width		x16
Memory Type			DDR2
Memory Size			8192 MBytes
Channels			Dual
Memory Frequency		371.5 MHz (CPU/7)
CAS# latency (CL)		5.0
RAS# to CAS# delay (tRCD)	5
RAS# Precharge (tRP)		5
Cycle Time (tRAS)		18
Bank Cycle Time (tRC)		23
Command Rate (CR)		2T

Memory SPD
-------------------------------------------------------------------------

DIMM #				1
	SMBus address		0x50
	Memory type		DDR2
	Module format		Regular UDIMM
	Manufacturer (ID)	Corsair (7F7F9E0000000000)
	Size			2048 MBytes
	Max bandwidth		PC2-6400 (400 MHz)
	Part number		CM2X2048-6400C5   
	Number of banks		2
	Data width		64 bits
	Correction		None
	Nominal Voltage		1.80 Volts
	EPP			no
	XMP			no
JEDEC timings table		CL-tRCD-tRP-tRAS-tRC @ frequency
	JEDEC #1		4.0-4-4-13-15 @ 270 MHz
	JEDEC #2		5.0-5-5-18-22 @ 400 MHz

DIMM #				2
	SMBus address		0x51
	Memory type		DDR2
	Module format		Regular UDIMM
	Manufacturer (ID)	Corsair (7F7F9E0000000000)
	Size			2048 MBytes
	Max bandwidth		PC2-6400 (400 MHz)
	Part number		CM2X2048-6400C5   
	Number of banks		2
	Data width		64 bits
	Correction		None
	Nominal Voltage		1.80 Volts
	EPP			no
	XMP			no
JEDEC timings table		CL-tRCD-tRP-tRAS-tRC @ frequency
	JEDEC #1		4.0-4-4-13-15 @ 270 MHz
	JEDEC #2		5.0-5-5-18-22 @ 400 MHz

DIMM #				3
	SMBus address		0x52
	Memory type		DDR2
	Module format		Regular UDIMM
	Manufacturer (ID)	Corsair (7F7F9E0000000000)
	Size			2048 MBytes
	Max bandwidth		PC2-6400 (400 MHz)
	Part number		CM2X2048-6400C5   
	Number of banks		2
	Data width		64 bits
	Correction		None
	Nominal Voltage		1.80 Volts
	EPP			no
	XMP			no
JEDEC timings table		CL-tRCD-tRP-tRAS-tRC @ frequency
	JEDEC #1		4.0-4-4-13-15 @ 270 MHz
	JEDEC #2		5.0-5-5-18-22 @ 400 MHz

DIMM #				4
	SMBus address		0x53
	Memory type		DDR2
	Module format		Regular UDIMM
	Manufacturer (ID)	Corsair (7F7F9E0000000000)
	Size			2048 MBytes
	Max bandwidth		PC2-6400 (400 MHz)
	Part number		CM2X2048-6400C5   
	Number of banks		2
	Data width		64 bits
	Correction		None
	Nominal Voltage		1.80 Volts
	EPP			no
	XMP			no
JEDEC timings table		CL-tRCD-tRP-tRAS-tRC @ frequency
	JEDEC #1		4.0-4-4-13-15 @ 270 MHz
	JEDEC #2		5.0-5-5-18-22 @ 400 MHz

DIMM #				1
SPD registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
	10	0C 08 30 03 02 00 03 37 50 00 00 32 1E 32 2D 01 
	20	18 25 05 13 3C 1E 1E 00 00 37 69 80 14 1E 00 00 
	30	00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 F1 
	40	7F 7F 9E 00 00 00 00 00 01 43 4D 32 58 32 30 34 
	50	38 2D 36 34 30 30 43 35 20 20 20 20 20 00 00 00 
	60	00 00 00 00 00 00 00 00 00 00 00 1F FF FF FF FF 
	70	FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
	80	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

DIMM #				2
SPD registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
	10	0C 08 30 03 02 00 03 37 50 00 00 32 1E 32 2D 01 
	20	18 25 05 13 3C 1E 1E 00 00 37 69 80 14 1E 00 00 
	30	00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 F1 
	40	7F 7F 9E 00 00 00 00 00 01 43 4D 32 58 32 30 34 
	50	38 2D 36 34 30 30 43 35 20 20 20 20 20 00 00 00 
	60	00 00 00 00 00 00 00 00 00 00 00 1F FF FF FF FF 
	70	FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
	80	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

DIMM #				3
SPD registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
	10	0C 08 30 03 02 00 03 37 50 00 00 32 1E 32 2D 01 
	20	18 25 05 13 3C 1E 1E 00 00 37 69 80 14 1E 00 00 
	30	00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 F1 
	40	7F 7F 9E 00 00 00 00 00 01 43 4D 32 58 32 30 34 
	50	38 2D 36 34 30 30 43 35 20 20 20 20 20 00 00 00 
	60	00 00 00 00 00 00 00 00 00 00 00 1F FF FF FF FF 
	70	FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
	80	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

DIMM #				4
SPD registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
	10	0C 08 30 03 02 00 03 37 50 00 00 32 1E 32 2D 01 
	20	18 25 05 13 3C 1E 1E 00 00 37 69 80 14 1E 00 00 
	30	00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 F1 
	40	7F 7F 9E 00 00 00 00 00 01 43 4D 32 58 32 30 34 
	50	38 2D 36 34 30 30 43 35 20 20 20 20 20 00 00 00 
	60	00 00 00 00 00 00 00 00 00 00 00 1F FF FF FF FF 
	70	FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
	80	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Monitoring
-------------------------------------------------------------------------

Mainboard Model		MI-A78U-8309 (0x000002C9 - 0x62D29720)

LPCIO
-------------------------------------------------------------------------

LPCIO Vendor		Winbond
LPCIO Model		W83627EHF
LPCIO Vendor ID		0x5CA3
LPCIO Chip ID		0x88
LPCIO Revision ID	0x63
Config Mode I/O address	0x2E
Config Mode LDN		0xB
Config Mode registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	FF FF FF FF FF FF FF 0B FF FF FF FF FF FF FF FF 
	10	FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
	20	88 63 FF 00 04 00 00 FF 70 81 00 00 02 01 00 FF 
	30	01 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
	40	FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
	50	FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
	60	0A 10 FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
	70	00 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
Register space		LPC, base address = 0x0A10


Hardware Monitors
-------------------------------------------------------------------------

Hardware monitor	Winbond W83627EHF
	Voltage 0	1.12 Volts [0x8C] (CPU VCORE)
	Voltage 1	1.90 Volts [0xED] (VIN0)
	Voltage 2	3.26 Volts [0xCC] (AVCC)
	Voltage 3	3.26 Volts [0xCC] (+3.3V)
	Voltage 4	0.95 Volts [0x77] (VIN1)
	Voltage 5	1.13 Volts [0x8D] (VIN2)
	Voltage 6	1.60 Volts [0xC8] (VIN3)
	Voltage 7	1.12 Volts [0x8C] (VIN4)
	Temperature 0	30°C (86°F) [0x1E] (SYSTIN)
	Temperature 1	33°C (91°F) [0x42] (CPUTIN)
	Temperature 2	45°C (112°F) [0x59] (AUXTIN)
	Fan 0		3835 RPM [0x2C] (SYSFANIN)
	Fan 1		2813 RPM [0x3C] (CPUFANIN0)
Hardware registers	
Register space		LPC, base address = 0x0A10
bank 0	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	04 FF 04 FA 01 00 00 00 01 01 01 01 3C 3C 0A 0A 
	10	04 FF 00 00 00 01 01 3C 43 17 00 00 57 00 00 C5 
	20	A5 EA CC CC 78 8D C8 1E 2B 3C FF DA 00 BF FF 7F 
	30	7F FD FF FF F9 E9 B7 7F 16 9B FF 7F FF BB EF FF 
	40	03 1E 1F DE FF FF 00 F4 2D FF 40 C4 10 95 00 A3 
	50	FF FF 80 FF FF FF 00 80 A1 7F FF FF 19 05 FF 05 
	60	04 FF 40 00 01 01 3C FF 01 FF 01 FF FF FF FF FF 
	70	FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
	80	04 FF 04 FA 01 00 00 00 01 01 01 01 3C 3C 0A 0A 
	90	04 FF 00 00 00 01 01 3C 43 17 00 00 57 00 00 C7 
	A0	A5 EA CC CC 78 8D C8 1E 2B 3C FF DA 00 BF FF 7F 
	B0	7F FD FF FF F9 E9 B7 7F 16 9B FF 7F FF BB EF FF 
	C0	03 00 10 DE FF FF 00 F4 2D FF 40 C4 10 95 00 A3 
	D0	FF FF 00 FF FF FF 00 80 A1 7F FF FF 19 05 FF 05 
	E0	04 FF 40 00 01 01 3C FF 01 FF 01 FF FF FF FF FF 
	F0	FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
bank 1	
	50	21 00 00 4B 00 50 00 FF FF FF FF FF FF FF FF FF 
bank 2	
	50	2C 80 00 4B 00 50 00 FF FF FF FF FF FF FF FF FF 
bank 3	
	50	00 00 00 01 03 02 01 03 01 00 FF FF FF FF FF FF 
bank 4	
	50	1B 13 FF 00 F8 02 00 FF 75 1E 1D 3B 89 FF FF FF 
bank 5	
	50	CC BC A4 FF FF EF FF FB CD FF FF FF FF 00 00 00 

Hardware monitor	AMD Athlon 64 X2 5600+
	Temperature 0	23°C (73°F) [0x48] (Core #0)
	Temperature 1	31°C (87°F) [0x50] (Core #1)

Hardware monitor	NVIDIA GeForce 8500 (GF 8400 + GF 8300)
	Temperature 0	53°C (127°F) (GPU Core)

Hardware monitor	NVIDIA GeForce 8500 (GF 8300 + GF 8400)
	Temperature 0	73°C (163°F) (GPU Core)


PCI Devices
-------------------------------------------------------------------------

Description			RAM Memory Controller
Location			bus 0 (0x00), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x0754
	Revision ID		0xA2
	PI			0x00
	SubClass		0x00
	BaseClass		0x05
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x00
	Int. Pin		0x00
PCI capability
	Caps class		HyperTransport
	Caps offset		0x94
	Interface type		Gen3
PCI capability
	Caps class		HyperTransport
	Caps offset		0x60
	Interface type		Retry Mode
PCI capability
	Caps class		HyperTransport
	Caps offset		0x44
	Caps revision		3.00
	Interface type		Slave/Primary
	Link 0 width (in/out)	16 bits/16 bits
	Link 0 frequency	1000 MHz
	Link 1 width (in/out)	8 bits/8 bits
	Link 1 frequency	200 MHz
PCI capability
	Caps class		HyperTransport
	Caps offset		0xD0
	Interface type		Power Management
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 54 07 06 00 B0 00 A2 00 00 05 00 00 00 00 
	10	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 94 00 00 00 00 00 00 00 00 00 00 00 
	40	DE 10 84 CB 08 D0 00 00 20 00 11 11 D0 00 00 00 
	50	60 16 F5 7F 63 00 00 00 00 00 00 00 00 00 00 00 
	60	08 44 00 C0 C0 02 00 00 57 E0 00 00 06 86 00 11 
	70	92 24 01 00 D0 09 00 00 21 00 00 00 00 00 40 08 
	80	0C 86 7D 1F 64 14 12 00 20 00 00 20 F5 7F 11 0E 
	90	70 00 00 80 08 60 07 D0 3A 00 00 00 00 00 00 00 
	A0	00 00 00 00 71 00 00 00 00 00 00 00 2B 32 00 3A 
	B0	00 00 00 00 00 00 00 00 10 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	08 00 00 E0 3F 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			PCI to ISA Bridge
Location			bus 0 (0x00), device 1 (0x01), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x075C
	Revision ID		0xA2
	PI			0x00
	SubClass		0x01
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 0 (port)	0x00002F00
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x00
	Int. Pin		0x00
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 5C 07 0F 00 A0 00 A2 00 01 06 00 00 80 00 
	10	01 2F 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	40	DE 10 84 CB 00 00 D0 FE FA 3E FF 00 FA 3E FF 00 
	50	FA 3E FF 00 00 5A 62 02 00 00 00 05 30 00 34 02 
	60	00 00 00 00 00 00 00 00 00 00 00 00 08 00 00 00 
	70	10 00 FF FF 45 80 17 00 00 00 44 99 00 00 00 00 
	80	00 00 00 00 00 00 00 00 00 00 40 03 FF 00 AA AA 
	90	FF 7F 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	01 00 10 81 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 0A 7F 0A 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 02 00 00 
	E0	41 20 E6 24 30 4A 93 56 0A 58 97 2C 00 00 00 00 
	F0	2C 00 00 FC FD 00 00 00 10 00 80 80 00 00 00 00 

Description			SMBus Controller
Location			bus 0 (0x00), device 1 (0x01), function 1 (0x01)
Common header
	Vendor ID		0x10DE
	Model ID		0x0752
	Revision ID		0xA1
	PI			0x00
	SubClass		0x05
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 0 (port)	0x00002900
	Address 4 (port)	0x00002D00
	Address 5 (port)	0x00002E00
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x0B
	Int. Pin		0x01
PCI capability
	Caps class		Power Management
	Caps offset		0x44
	Caps version		1.1
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 52 07 01 00 B0 00 A1 00 05 0C 00 00 80 00 
	10	01 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20	01 2D 00 00 01 2E 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 44 00 00 00 00 00 00 00 0B 01 00 00 
	40	DE 10 84 CB 01 00 02 C0 00 00 00 00 6A 96 00 00 
	50	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	01 20 00 00 01 24 00 00 01 28 00 00 00 10 D0 FE 
	70	00 00 00 00 00 00 E8 F8 00 00 00 00 01 00 00 00 
	80	00 40 D0 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	A0 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	D4 30 80 00 01 00 00 00 20 82 08 02 0D 0D 19 19 
	D0	C0 60 C0 00 10 00 01 00 05 00 00 00 00 00 00 00 
	E0	88 10 10 10 20 46 22 07 00 04 00 00 41 44 44 00 
	F0	02 00 00 20 A7 AF 9B F8 10 00 80 80 00 00 00 00 

Description			RAM Memory Controller
Location			bus 0 (0x00), device 1 (0x01), function 2 (0x02)
Common header
	Vendor ID		0x10DE
	Model ID		0x0751
	Revision ID		0xA1
	PI			0x00
	SubClass		0x00
	BaseClass		0x05
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x00
	Int. Pin		0x00
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 51 07 00 04 A0 00 A1 00 00 05 00 00 80 00 
	10	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	40	DE 10 84 CB 00 00 00 00 10 02 80 10 10 02 10 10 
	50	10 10 10 10 00 00 00 00 00 00 00 00 10 42 00 00 
	60	00 00 00 00 00 01 00 01 03 01 01 02 01 01 02 01 
	70	01 00 00 00 00 00 00 00 0B 0A 05 00 03 0D 00 00 
	80	01 00 06 00 00 04 0A 03 04 00 00 00 00 00 00 00 
	90	01 00 00 00 00 00 00 00 00 04 0B 1C 00 00 00 00 
	A0	05 00 00 00 00 11 0B 0C 00 01 00 00 0F 00 00 00 
	B0	00 00 00 00 12 12 12 12 12 12 01 01 0A 0C 05 06 
	C0	05 05 05 05 05 0E 0E 0C 0E 0E 0F 08 09 09 08 08 
	D0	08 0E 0D 0D 0D 0D 0F 00 12 12 12 12 12 12 12 12 
	E0	12 12 12 12 12 12 12 12 04 02 16 0B 0C 10 0E 0D 
	F0	10 11 17 0E 0E 08 08 00 01 01 01 00 02 01 10 01 

Description			Processor Device
Location			bus 0 (0x00), device 1 (0x01), function 3 (0x03)
Common header
	Vendor ID		0x10DE
	Model ID		0x0753
	Revision ID		0xA2
	PI			0x00
	SubClass		0x40
	BaseClass		0x0B
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 0 (memory)	0xF8E80000
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x0F
	Int. Pin		0x02
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 53 07 06 00 A0 00 A2 00 40 0B 00 00 80 00 
	10	00 00 E8 F8 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 00 00 00 00 00 00 00 00 0F 02 03 01 
	40	DE 10 84 CB 00 00 00 00 00 00 00 00 00 00 00 00 
	50	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 E8 F8 00 00 00 00 00 00 00 00 
	80	05 9C 80 01 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 08 00 02 A8 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			RAM Memory Controller
Location			bus 0 (0x00), device 1 (0x01), function 4 (0x04)
Common header
	Vendor ID		0x10DE
	Model ID		0x0568
	Revision ID		0xA1
	PI			0x00
	SubClass		0x00
	BaseClass		0x05
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x00
	Int. Pin		0x00
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 68 05 00 04 A0 00 A1 00 00 05 00 00 80 00 
	10	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	40	DE 10 84 CB 00 00 00 00 00 00 00 00 00 00 00 00 
	50	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	0D 00 00 00 00 00 00 00 08 01 02 0D 09 00 00 00 
	70	08 0D 00 00 00 00 00 00 00 00 00 00 06 00 00 00 
	80	00 00 00 00 0C 00 00 00 04 00 00 00 03 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 C0 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 FC 0D 00 00 00 00 00 00 

Description			USB Controller (OHCI)
Location			bus 0 (0x00), device 2 (0x02), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x077B
	Revision ID		0xA1
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 0 (memory)	0xF8E7F000
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x14
	Int. Pin		0x01
PCI capability
	Caps class		Power Management
	Caps offset		0x44
	Caps version		1.1
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 7B 07 06 00 B0 00 A1 10 03 0C 00 00 80 00 
	10	00 F0 E7 F8 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 44 00 00 00 00 00 00 00 14 01 03 01 
	40	DE 10 84 CB 01 00 02 FE 00 00 00 00 00 00 00 00 
	50	04 00 00 00 1D 47 40 00 10 00 00 00 10 00 1F 03 
	60	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 C0 80 00 00 00 00 

Description			USB 2.0 Controller (EHCI)
Location			bus 0 (0x00), device 2 (0x02), function 1 (0x01)
Common header
	Vendor ID		0x10DE
	Model ID		0x077C
	Revision ID		0xA1
	PI			0x20
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 0 (memory)	0xF8E7EC00
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x17
	Int. Pin		0x02
PCI capability
	Caps class		Debug Port
	Caps offset		0x44
PCI capability
	Caps class		Power Management
	Caps offset		0x80
	Caps version		1.1
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 7C 07 06 00 B0 00 A1 20 03 0C 00 00 80 00 
	10	00 EC E7 F8 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 44 00 00 00 00 00 00 00 17 02 03 01 
	40	DE 10 84 CB 0A 80 A0 20 00 00 00 00 00 00 00 00 
	50	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	20 20 01 00 00 60 18 85 03 3C 0A 01 00 00 00 00 
	70	00 01 08 00 00 10 20 80 89 3D B6 22 77 25 04 00 
	80	01 00 02 FE 00 80 00 00 00 00 00 00 15 16 00 00 
	90	00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	01 00 00 00 00 20 00 C0 00 00 00 00 00 00 00 00 
	B0	00 11 22 33 44 44 44 04 55 05 00 00 00 00 00 00 
	C0	10 10 2D 0D 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 10 00 C0 80 00 00 00 00 

Description			USB Controller (OHCI)
Location			bus 0 (0x00), device 4 (0x04), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x077D
	Revision ID		0xA1
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 0 (memory)	0xF8E7D000
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x16
	Int. Pin		0x01
PCI capability
	Caps class		Power Management
	Caps offset		0x44
	Caps version		1.1
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 7D 07 06 00 B0 00 A1 10 03 0C 00 00 80 00 
	10	00 D0 E7 F8 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 44 00 00 00 00 00 00 00 16 01 03 01 
	40	DE 10 84 CB 01 00 02 FE 00 00 00 00 00 00 00 00 
	50	08 00 00 00 1D 47 40 00 10 00 00 00 10 00 1F 03 
	60	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 C0 80 00 00 00 00 

Description			USB 2.0 Controller (EHCI)
Location			bus 0 (0x00), device 4 (0x04), function 1 (0x01)
Common header
	Vendor ID		0x10DE
	Model ID		0x077E
	Revision ID		0xA1
	PI			0x20
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 0 (memory)	0xF8E7E800
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x15
	Int. Pin		0x02
PCI capability
	Caps class		Debug Port
	Caps offset		0x44
PCI capability
	Caps class		Power Management
	Caps offset		0x80
	Caps version		1.1
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 7E 07 06 00 B0 00 A1 20 03 0C 00 00 80 00 
	10	00 E8 E7 F8 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 44 00 00 00 00 00 00 00 15 02 03 01 
	40	DE 10 84 CB 0A 80 A0 20 00 00 00 00 00 00 00 00 
	50	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	20 20 01 00 00 60 18 85 03 3C 0A 01 00 00 00 00 
	70	00 01 08 00 00 10 20 80 89 3D B6 22 77 25 C4 00 
	80	01 00 02 FE 00 80 00 00 00 00 00 00 15 16 00 00 
	90	00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	01 00 00 00 00 20 00 C0 00 00 00 00 00 00 00 00 
	B0	00 11 22 33 44 44 44 04 AA 0A 00 00 00 00 00 00 
	C0	10 10 2D 0D 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 10 00 C0 80 00 00 00 00 

Description			IDE Controller
Location			bus 0 (0x00), device 6 (0x06), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x0759
	Revision ID		0xA1
	PI			0x8A
	SubClass		0x01
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 4 (port)	0x0000FFA0
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x00
	Int. Pin		0x00
PCI capability
	Caps class		Power Management
	Caps offset		0x44
	Caps version		1.1
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 59 07 05 00 B0 00 A1 8A 01 01 00 00 00 00 
	10	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20	A1 FF 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 44 00 00 00 00 00 00 00 00 00 03 01 
	40	DE 10 84 CB 01 00 02 00 00 00 00 00 00 00 00 00 
	50	02 F0 00 00 00 00 00 00 A8 A8 20 20 5F 00 20 20 
	60	00 00 C0 C6 00 00 00 00 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	00 00 00 00 00 10 38 75 00 00 02 30 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 01 01 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 10 80 C0 00 00 00 00 00 

Description			Multimedia device
Location			bus 0 (0x00), device 7 (0x07), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x0774
	Revision ID		0xA1
	PI			0x00
	SubClass		0x03
	BaseClass		0x04
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (memory)	0xF8E78000
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x14
	Int. Pin		0x01
PCI capability
	Caps class		Power Management
	Caps offset		0x44
	Caps version		1.1
PCI capability
	Caps class		Message Signalled Interrupts
	Caps offset		0x50
PCI capability
	Caps class		HyperTransport
	Caps offset		0x6C
	Interface type		MSI Mapping
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 74 07 06 00 B0 00 A1 00 03 04 00 00 00 00 
	10	00 80 E7 F8 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 44 00 00 00 00 00 00 00 14 01 02 05 
	40	DE 10 84 CB 01 50 02 C0 00 00 00 00 00 00 00 00 
	50	05 6C 80 01 00 00 00 00 00 00 00 00 00 00 00 00 
	60	00 00 00 00 00 00 00 00 0F 00 00 00 08 00 03 A8 
	70	03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 47 80 29 C0 00 00 00 00 00 

Description			PCI to PCI Bridge
Location			bus 0 (0x00), device 8 (0x08), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x075A
	Revision ID		0xA1
	PI			0x01
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x01
	Int. Line		0x00
	Int. Pin		0x00
PCI capability
	Caps class		Subsystem Vendor
	Caps offset		0xB8
	SubVendor ID		0x10DE
	SubSystem ID		0xCB84
PCI capability
	Caps class		HyperTransport
	Caps offset		0x8C
	Interface type		MSI Mapping
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 5A 07 07 04 B0 00 A1 01 04 06 00 00 01 00 
	10	00 00 00 00 00 00 00 00 00 01 01 20 F0 00 80 22 
	20	F0 FF 00 00 F0 FF 00 00 00 00 00 00 00 00 00 00 
	30	00 00 00 00 B8 00 00 00 00 00 00 00 00 00 02 02 
	40	00 00 73 07 00 00 00 00 2F 07 00 00 00 00 44 00 
	50	00 00 00 00 00 00 00 00 FF 1F FF 1F 00 00 00 00 
	60	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	00 02 00 00 96 02 00 00 00 00 00 00 08 00 01 A8 
	90	00 00 E0 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 FF FF 00 00 0D 8C 00 00 DE 10 84 CB 
	C0	DE 10 84 CB 03 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			IDE Controller
Location			bus 0 (0x00), device 9 (0x09), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x0AD0
	Revision ID		0xA2
	PI			0x85
	SubClass		0x01
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (port)	0x0000B480
	Address 1 (port)	0x0000B400
	Address 2 (port)	0x0000B080
	Address 3 (port)	0x0000B000
	Address 4 (port)	0x0000AC00
	Address 5 (memory)	0xF8E76000
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x15
	Int. Pin		0x01
PCI capability
	Caps class		Power Management
	Caps offset		0x44
	Caps version		1.1
PCI capability
	Caps class		0x12
	Caps offset		0x8C
PCI capability
	Caps class		Message Signalled Interrupts
	Caps offset		0xB0
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 D0 0A 07 01 B0 00 A2 85 01 01 00 00 00 00 
	10	81 B4 00 00 01 B4 00 00 81 B0 00 00 01 B0 00 00 
	20	01 AC 00 00 00 60 E7 F8 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 44 00 00 00 00 00 00 00 15 01 03 01 
	40	DE 10 84 CB 01 8C 02 00 00 00 00 00 00 00 00 00 
	50	0F 68 78 60 00 00 00 00 00 00 00 00 00 00 00 00 
	60	00 00 00 00 40 0C 00 0F 01 0F 06 42 00 00 00 00 
	70	2C 78 C4 40 00 00 00 00 02 00 20 08 34 00 20 19 
	80	0F 00 40 00 00 00 00 00 00 00 00 00 12 B0 10 00 
	90	5F 02 00 00 00 00 00 00 05 9F 22 E3 01 01 00 00 
	A0	6E 5A 00 75 00 00 00 00 00 00 00 00 63 71 00 02 
	B0	05 00 86 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 08 00 40 00 00 00 00 00 
	E0	00 00 00 00 00 00 3F 00 00 00 00 00 08 00 02 A8 
	F0	00 00 00 00 00 00 00 00 00 C1 9E 00 00 00 00 00 

Description			PCI to PCI Bridge
Location			bus 0 (0x00), device 11 (0x0B), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x0569
	Revision ID		0xA1
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x10
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x02
	Int. Line		0x00
	Int. Pin		0x00
PCI capability
	Caps class		Subsystem Vendor
	Caps offset		0x40
	SubVendor ID		0x10DE
	SubSystem ID		0xCB84
PCI capability
	Caps class		Power Management
	Caps offset		0x48
	Caps version		1.1
PCI capability
	Caps class		HyperTransport
	Caps offset		0x60
	Interface type		MSI Mapping
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 69 05 07 04 10 00 A1 00 04 06 10 00 01 00 
	10	00 00 00 00 00 00 00 00 00 02 02 00 C1 C1 00 20 
	20	F0 F8 F0 F9 01 C6 F1 CF 00 00 00 00 00 00 00 00 
	30	00 00 00 00 40 00 00 00 00 00 00 00 00 00 02 00 
	40	0D 48 00 00 DE 10 84 CB 01 60 02 F8 00 00 00 00 
	50	05 60 82 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	08 00 01 A8 00 00 E0 FE 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	30 30 00 00 50 50 00 00 FF 00 FF 00 DE 10 84 CB 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			PCI to PCI Bridge
Location			bus 0 (0x00), device 16 (0x10), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x0778
	Revision ID		0xA1
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x10
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x03
	Int. Line		0x12
	Int. Pin		0x01
PCI capability
	Caps class		Subsystem Vendor
	Caps offset		0x40
	SubVendor ID		0x10DE
	SubSystem ID		0xCB84
PCI capability
	Caps class		Power Management
	Caps offset		0x48
	Caps version		1.2
PCI capability
	Caps class		Message Signalled Interrupts
	Caps offset		0x50
PCI capability
	Caps class		HyperTransport
	Caps offset		0x60
	Interface type		MSI Mapping
PCI capability
	Caps class		PCI Express
	Caps offset		0x80
	Device type		Root Port of PCI-E Root Complex
	Port			0
	Version			2.0
	Physical slot		#0
	Presence detect		yes
	Link width		16x (max 16x)
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 78 07 07 00 10 00 A1 00 04 06 10 00 01 00 
	10	00 00 00 00 00 00 00 00 00 03 03 00 D1 D1 00 00 
	20	00 FA A0 FE 01 D0 F1 DF 00 00 00 00 00 00 00 00 
	30	00 00 00 00 40 00 00 00 00 00 00 00 12 01 1A 00 
	40	0D 48 00 00 DE 10 84 CB 01 50 03 F8 00 00 00 00 
	50	05 60 82 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	08 80 01 A8 00 00 E0 FE 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	10 00 42 01 21 80 00 00 10 28 00 00 01 3D 31 00 
	90	00 00 01 31 80 25 08 00 C0 01 48 01 00 00 00 00 
	A0	00 00 00 00 13 00 00 00 06 00 00 00 00 00 00 00 
	B0	01 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			PCI to PCI Bridge
Location			bus 0 (0x00), device 18 (0x12), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x075B
	Revision ID		0xA1
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x10
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x04
	Int. Line		0x13
	Int. Pin		0x01
PCI capability
	Caps class		Subsystem Vendor
	Caps offset		0x40
	SubVendor ID		0x10DE
	SubSystem ID		0xCB84
PCI capability
	Caps class		Power Management
	Caps offset		0x48
	Caps version		1.2
PCI capability
	Caps class		Message Signalled Interrupts
	Caps offset		0x50
PCI capability
	Caps class		HyperTransport
	Caps offset		0x60
	Interface type		MSI Mapping
PCI capability
	Caps class		PCI Express
	Caps offset		0x80
	Device type		Root Port of PCI-E Root Complex
	Port			2
	Version			1.0
	Physical slot		#0
	Presence detect		no
	Link width		4x (max 1x)
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 5B 07 04 00 10 00 A1 00 04 06 10 00 01 00 
	10	00 00 00 00 00 00 00 00 00 04 04 00 F1 01 00 00 
	20	F0 FF 00 00 F1 FF 01 00 00 00 00 00 00 00 00 00 
	30	00 00 00 00 40 00 00 00 00 00 00 00 13 01 02 00 
	40	0D 48 00 00 DE 10 84 CB 01 50 03 F8 00 00 00 00 
	50	05 60 82 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	08 80 01 A8 00 00 E0 FE 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	10 00 41 01 21 80 00 00 10 28 00 00 11 3C 11 02 
	90	00 00 41 10 00 05 18 00 C0 01 08 00 00 00 00 00 
	A0	00 00 00 00 13 00 00 00 06 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			PCI to PCI Bridge
Location			bus 0 (0x00), device 19 (0x13), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x077A
	Revision ID		0xA1
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x10
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x05
	Int. Line		0x11
	Int. Pin		0x01
PCI capability
	Caps class		Subsystem Vendor
	Caps offset		0x40
	SubVendor ID		0x10DE
	SubSystem ID		0xCB84
PCI capability
	Caps class		Power Management
	Caps offset		0x48
	Caps version		1.2
PCI capability
	Caps class		Message Signalled Interrupts
	Caps offset		0x50
PCI capability
	Caps class		HyperTransport
	Caps offset		0x60
	Interface type		MSI Mapping
PCI capability
	Caps class		PCI Express
	Caps offset		0x80
	Device type		Root Port of PCI-E Root Complex
	Port			3
	Version			1.0
	Physical slot		#0
	Presence detect		yes
	Link width		1x (max 1x)
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 7A 07 07 00 10 00 A1 00 04 06 10 00 01 00 
	10	00 00 00 00 00 00 00 00 00 05 05 00 E1 E1 00 00 
	20	B0 FE B0 FE F1 FF 01 00 00 00 00 00 00 00 00 00 
	30	00 00 00 00 40 00 00 00 00 00 00 00 11 01 02 00 
	40	0D 48 00 00 DE 10 84 CB 01 50 03 F8 00 01 00 00 
	50	05 60 82 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	08 80 01 A8 00 00 E0 FE 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	10 00 41 01 21 80 00 00 10 28 00 00 11 3C 11 03 
	90	00 00 11 30 00 05 20 00 C0 01 48 01 00 00 00 00 
	A0	00 00 00 00 13 00 00 00 06 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			PCI to PCI Bridge
Location			bus 0 (0x00), device 20 (0x14), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x077A
	Revision ID		0xA1
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x10
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x06
	Int. Line		0x10
	Int. Pin		0x01
PCI capability
	Caps class		Subsystem Vendor
	Caps offset		0x40
	SubVendor ID		0x10DE
	SubSystem ID		0xCB84
PCI capability
	Caps class		Power Management
	Caps offset		0x48
	Caps version		1.2
PCI capability
	Caps class		Message Signalled Interrupts
	Caps offset		0x50
PCI capability
	Caps class		HyperTransport
	Caps offset		0x60
	Interface type		MSI Mapping
PCI capability
	Caps class		PCI Express
	Caps offset		0x80
	Device type		Root Port of PCI-E Root Complex
	Port			4
	Version			1.0
	Physical slot		#0
	Presence detect		no
	Link width		1x (max 1x)
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 7A 07 04 00 10 00 A1 00 04 06 10 00 01 00 
	10	00 00 00 00 00 00 00 00 00 06 06 00 F1 01 00 00 
	20	F0 FF 00 00 F1 FF 01 00 00 00 00 00 00 00 00 00 
	30	00 00 00 00 40 00 00 00 00 00 00 00 10 01 02 00 
	40	0D 48 00 00 DE 10 84 CB 01 50 03 F8 00 00 00 00 
	50	05 60 82 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	08 80 01 A8 00 00 E0 FE 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	10 00 41 01 21 80 00 00 10 28 00 00 11 3C 11 04 
	90	00 00 11 10 00 05 28 00 C0 01 00 00 00 00 00 00 
	A0	00 00 00 00 13 00 00 00 06 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			Host Bridge
Location			bus 0 (0x00), device 24 (0x18), function 0 (0x00)
Common header
	Vendor ID		0x1022
	Model ID		0x1100
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
PCI capability
	Caps class		HyperTransport
	Caps offset		0x80
	Caps revision		1.02
	Interface type		Host/Secondary
	Device number		0
	Link 0 width (in/out)	16 bits/16 bits
	Link 0 frequency	1000 MHz
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	22 10 00 11 00 00 10 00 00 00 00 06 00 00 80 00 
	10	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	30	00 00 00 00 80 00 00 00 00 00 00 00 00 00 00 00 
	40	01 01 01 00 01 01 01 00 01 01 01 00 01 01 01 00 
	50	01 01 01 00 01 01 01 00 01 01 01 00 01 01 01 00 
	60	00 00 01 00 E4 00 00 00 20 C8 2E 0F 2C 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	08 00 01 21 20 00 11 11 22 06 75 80 02 00 00 00 
	90	69 01 61 01 00 00 07 00 07 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			Host Bridge
Location			bus 0 (0x00), device 24 (0x18), function 1 (0x01)
Common header
	Vendor ID		0x1022
	Model ID		0x1101
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	22 10 01 11 00 00 00 00 00 00 00 06 00 00 80 00 
	10	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	30	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	40	03 00 00 00 00 00 39 02 00 00 00 00 00 00 00 00 
	50	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	03 00 E0 00 80 FF EF 00 00 00 00 00 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	03 0A 00 00 00 0B 00 00 03 00 C6 00 00 0B FE 00 
	C0	13 10 00 00 00 F0 FF 00 00 00 00 00 00 00 00 00 
	D0	03 20 00 00 00 20 00 00 00 00 00 00 00 00 00 00 
	E0	03 00 00 07 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	01 3A 00 C6 00 00 00 00 00 00 00 00 00 00 00 00 

Description			Host Bridge
Location			bus 0 (0x00), device 24 (0x18), function 2 (0x02)
Common header
	Vendor ID		0x1022
	Model ID		0x1102
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	22 10 02 11 00 00 00 00 00 00 00 06 00 00 80 00 
	10	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	30	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	40	01 00 00 00 01 02 00 00 01 04 00 00 01 06 00 00 
	50	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60	E0 39 F8 01 E0 39 F8 01 00 00 00 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 46 00 00 00 00 00 00 00 
	80	55 00 00 00 00 00 00 00 24 FA 7C 0C 20 13 22 01 
	90	30 0C 01 00 6B 00 10 77 39 00 00 80 00 00 00 00 
	A0	EF 02 00 0C 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	C1 FE D7 AA DC 00 00 00 18 1E 09 1E A2 77 9E 31 
	C0	00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	08 07 17 1F 0E 70 30 F2 38 3E 10 D1 6E 4E F8 09 
	E0	0C 83 13 9F C5 38 38 B1 38 1A 10 D9 26 45 F8 89 
	F0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			Host Bridge
Location			bus 0 (0x00), device 24 (0x18), function 3 (0x03)
Common header
	Vendor ID		0x1022
	Model ID		0x1103
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
PCI capability
	Caps class		Secure Device
	Caps offset		0xF0
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	22 10 03 11 00 00 10 00 00 00 00 06 00 00 80 00 
	10	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	30	00 00 00 00 F0 00 00 00 00 00 00 00 00 00 00 00 
	40	FF 3B 04 00 40 00 10 0A 00 00 00 00 00 00 00 00 
	50	00 00 00 00 00 00 00 00 00 00 00 00 00 3C 1F FF 
	60	1E 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70	11 01 32 51 21 40 70 50 00 2A 00 08 17 21 00 00 
	80	00 00 07 23 13 21 13 21 00 00 00 00 00 00 00 00 
	90	00 00 00 00 10 00 00 00 00 06 31 02 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 01 A7 0D 00 00 00 80 08 25 20 20 00 
	E0	00 00 00 00 24 19 51 00 19 17 00 00 00 00 00 00 
	F0	0F 00 10 00 00 00 00 00 00 00 00 00 33 0F 04 00 

Description			VGA Controller
Location			bus 2 (0x02), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x0848
	Revision ID		0xA2
	PI			0x00
	SubClass		0x00
	BaseClass		0x03
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (memory)	0xF9000000
	Address 1 (memory)	0xC8000000
	Address 3 (memory)	0xC6000000
	Address 5 (port)	0x0000CF80
	Subvendor ID		0x10DE
	Subsystem ID		0xCB84
	Int. Line		0x15
	Int. Pin		0x01
PCI capability
	Caps class		Power Management
	Caps offset		0x60
	Caps version		1.1
PCI capability
	Caps class		Message Signalled Interrupts
	Caps offset		0x68
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 48 08 07 01 10 00 A2 00 00 03 00 00 00 00 
	10	00 00 00 F9 0C 00 00 C8 00 00 00 00 0C 00 00 C6 
	20	00 00 00 00 81 CF 00 00 00 00 00 00 DE 10 84 CB 
	30	00 00 00 00 60 00 00 00 00 00 00 00 15 01 00 00 
	40	DE 10 84 CB 00 00 00 00 00 00 00 00 00 00 00 00 
	50	01 00 00 00 01 00 00 00 CE D6 23 00 00 00 00 00 
	60	01 68 02 00 00 00 00 00 05 00 80 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90	00 00 00 33 83 00 00 00 13 57 00 00 0F 00 00 80 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	00 00 00 00 00 60 0A 00 00 00 02 00 00 00 00 00 

Description			VGA Controller
Location			bus 3 (0x03), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x10DE
	Model ID		0x0422
	Revision ID		0xA1
	PI			0x00
	SubClass		0x00
	BaseClass		0x03
	Cache Line		0x10
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (memory)	0xFD000000
	Address 1 (memory)	0xD0000000
	Address 3 (memory)	0xFA000000
	Address 5 (port)	0x0000DC00
	Subvendor ID		0x1ACC
	Subsystem ID		0x0851
	Int. Line		0x12
	Int. Pin		0x01
PCI capability
	Caps class		Power Management
	Caps offset		0x60
	Caps version		1.1
PCI capability
	Caps class		Message Signalled Interrupts
	Caps offset		0x68
PCI capability
	Caps class		PCI Express
	Caps offset		0x78
	Device type		PCI-E Endpoint Device
	Port			0
	Version			1.0
	Link width		16x (max 16x)
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	DE 10 22 04 07 01 10 00 A1 00 00 03 10 00 00 00 
	10	00 00 00 FD 0C 00 00 D0 00 00 00 00 04 00 00 FA 
	20	00 00 00 00 01 DC 00 00 00 00 00 00 CC 1A 51 08 
	30	00 00 00 00 60 00 00 00 00 00 00 00 12 01 00 00 
	40	CC 1A 51 08 00 00 00 00 00 00 00 00 00 00 00 00 
	50	01 00 00 00 01 00 00 00 CE D6 23 00 00 00 00 00 
	60	01 68 02 00 00 00 00 00 05 78 80 00 00 00 00 00 
	70	00 00 00 00 00 00 00 00 10 00 01 00 E0 84 00 00 
	80	10 29 00 00 01 31 01 00 08 00 01 11 00 00 00 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0	02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

Description			Ethernet Controller
Location			bus 5 (0x05), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x11AB
	Model ID		0x4364
	Revision ID		0x14
	PI			0x00
	SubClass		0x00
	BaseClass		0x02
	Cache Line		0x10
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (memory)	0xFEBFC000
	Address 2 (port)	0x0000E800
	Subvendor ID		0x1AFA
	Subsystem ID		0x7150
	Int. Line		0x11
	Int. Pin		0x01
PCI capability
	Caps class		Power Management
	Caps offset		0x48
	Caps version		1.2
PCI capability
	Caps class		Virtual Product Data
	Caps offset		0x50
PCI capability
	Caps class		Message Signalled Interrupts
	Caps offset		0x5C
PCI capability
	Caps class		PCI Express
	Caps offset		0xE0
	Device type		Legacy PCI-E Endpoint Device
	Port			3
	Version			1.0
	Link width		1x (max 1x)
PCI registers	
		00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
	00	AB 11 64 43 07 01 10 00 14 00 00 02 10 00 00 00 
	10	04 C0 BF FE 00 00 00 00 01 E8 00 00 00 00 00 00 
	20	00 00 00 00 00 00 00 00 00 00 00 00 FA 1A 50 71 
	30	00 00 00 00 48 00 00 00 00 00 00 00 11 01 00 00 
	40	00 00 F0 01 00 80 A0 01 01 50 03 FE 00 21 00 13 
	50	03 5C 00 80 FF FF FF FF 00 00 34 01 05 E0 80 00 
	60	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70	00 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80	00 00 00 00 00 70 00 00 00 00 00 00 82 A8 E8 00 
	90	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0	10 00 11 00 C0 8F 00 00 00 40 19 00 11 AC 07 03 
	F0	08 00 11 10 00 00 00 00 00 00 00 00 00 00 00 00 


DMI
-------------------------------------------------------------------------

DMI BIOS		
	vendor			American Megatrends Inc.
	version			080015
	date			06/06/2008

DMI System Information		
	manufacturer		To Be Filled By O.E.M.
	product			To Be Filled By O.E.M.
	version			To Be Filled By O.E.M.
	serial			To Be Filled By O.E.M.
	UUID			00020003-00040005-00060007-00080009

DMI Baseboard		
	vendor			XFX
	model			MI-A78U-8309
	revision		Ver1.1
	serial			To be filled by O.E.M.

DMI System Enclosure		
	manufacturer		To Be Filled By O.E.M.
	chassis type		Desktop
	chassis serial		To Be Filled By O.E.M.

DMI Processor		
	manufacturer		AMD
	model			AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
	clock speed		2816.0 MHz
	FSB speed		200.0 MHz
	multiplier		14.0x

DMI Port Connector		
	designation		J1A1 (internal)
	designation		PS2Mouse (external)
	port type		Mouse Port
	connector		PS/2

DMI Port Connector		
	designation		J1A1 (internal)
	designation		Keyboard (external)
	port type		Keyboard Port
	connector		PS/2

DMI Port Connector		
	designation		J2A2 (internal)
	designation		USB1 (external)
	port type		USB
	connector		Access Bus (USB)

DMI Port Connector		
	designation		J2A2 (internal)
	designation		USB2 (external)
	port type		USB
	connector		Access Bus (USB)

DMI Port Connector		
	designation		J4A1 (internal)
	designation		LPT 1 (external)
	port type		Parallel Port ECP/EPP
	connector		DB-25 male

DMI Port Connector		
	designation		J2A1 (internal)
	designation		COM A (external)
	port type		Serial Port 16550A
	connector		DB-9 male

DMI Port Connector		
	designation		J6A1 (internal)
	designation		Audio Mic In (external)
	port type		Audio Port
	connector		Mini Jack (headphones)

DMI Port Connector		
	designation		J6A1 (internal)
	designation		Audio Line In (external)
	port type		Audio Port
	connector		Mini Jack (headphones)

DMI Port Connector		
	designation		J6B1 - AUX IN (internal)
	port type		Audio Port
	connector		On Board Sound Input From CD-ROM

DMI Port Connector		
	designation		J6B2 - CDIN (internal)
	port type		Audio Port
	connector		On Board Sound Input From CD-ROM

DMI Port Connector		
	designation		J6J2 - PRI IDE (internal)
	connector		On Board IDE

DMI Port Connector		
	designation		J6J1 - SEC IDE (internal)
	connector		On Board IDE

DMI Port Connector		
	designation		J4J1 - FLOPPY (internal)
	connector		On Board Floppy

DMI Port Connector		
	designation		J9H1 - FRONT PNL (internal)
	connector		9 Pin Dual Inline (pin 10 cut)

DMI Port Connector		
	designation		J1B1 - CHASSIS REAR FAN (internal)

DMI Port Connector		
	designation		J2F1 - CPU FAN (internal)

DMI Port Connector		
	designation		J8B4 - FRONT FAN (internal)

DMI Port Connector		
	designation		J9G2 - FNT USB (internal)

DMI Port Connector		
	designation		J6C3 - FP AUD (internal)

DMI Port Connector		
	designation		J9G1 - CONFIG (internal)

DMI Port Connector		
	designation		J8C1 - SCSI LED (internal)

DMI Port Connector		
	designation		J9J2 - INTRUDER (internal)

DMI Port Connector		
	designation		J9G4 - ITP (internal)

DMI Port Connector		
	designation		J2H1 - MAIN POWER (internal)

DMI Extension Slot		
	designation		AGP
	type			AGP 4x
	width			32 bits
	populated		yes

DMI Extension Slot		
	designation		PCI1
	type			PCI
	width			32 bits
	populated		no

DMI Physical Memory Array		
	location		Motherboard
	usage			System Memory
	correction		None
	max capacity		8192 MBytes
	max# of devices		4

DMI Memory Device		
	designation		DIMM0
	format			DIMM
	type			unknown
	total width		64 bits
	data width		72 bits
	size			2048 MBytes

DMI Memory Device		
	designation		DIMM1
	format			DIMM
	type			unknown
	total width		64 bits
	data width		72 bits
	size			2048 MBytes

DMI Memory Device		
	designation		DIMM2
	format			DIMM
	type			unknown
	total width		64 bits
	data width		72 bits
	size			2048 MBytes

DMI Memory Device		
	designation		DIMM3
	format			DIMM
	type			unknown
	total width		64 bits
	data width		72 bits
	size			2048 MBytes


Graphics
-------------------------------------------------------------------------

Number of adapters		2

Graphic APIs
-------------------------------------------------------------------------

API				NVIDIA NVAPI
API				NVIDIA I/O

Display Adapters
-------------------------------------------------------------------------

Display adapter 0	
	Manuf. API index	0
	Display name		\\.\DISPLAY1
	Name			NVIDIA GeForce 8500 (GF 8400 + GF 8300)
	Revision		A2
	Codename		G86
	Technology		80 nm
	Memory size		256 MB
	Memory type		DDR2
	Memory bus width	64 bits
	PCI device		bus 3 (0x3), device 0 (0x0), function 0 (0x0)
	Vendor ID		0x10DE (0x1ACC)
	Model ID		0x0422 (0x0851)
	Performance Level	3D Applications
		Core clock	459.0 MHz
		Shader clock	918.0 MHz
		Memory clock	300.0 MHz

Display adapter 1	
	Manuf. API index	1
	Display name		\\.\DISPLAY1
	Name			NVIDIA GeForce 8500 (GF 8300 + GF 8400)
	Revision		A2
	Memory size		256 MB
	PCI device		bus 2 (0x2), device 0 (0x0), function 0 (0x0)
	Vendor ID		0x10DE (0x10DE)
	Model ID		0x0848 (0xCB84)
	Performance Level	3D Applications
		Core clock	500.0 MHz
		Shader clock	1500.0 MHz
		Memory clock	800.0 MHz


Software
-------------------------------------------------------------------------

Windows Version			Microsoft Windows 7 (6.1) Ultimate Edition   (Build 7600) 
DirectX Version			11.0

ACPI
-------------------------------------------------------------------------

ACPI Tree		
_GPE
  _L0B
  _L10
  _L09
  _L0D
  _L05
  _L18
  _L17
  _L00
  _L15
  _L11
_PR_
  P001
    _PCT
    _PSS
    _PPC
    _PSD
  P002
    _PCT
    _PSS
    _PPC
    _PSD
  P003
  P004
  CPU1
  CPU2
  CPU3
  CPU4
_SB_
  PR00
  AR00
  PR02
  AR02
  PR10
  AR10
  PR11
  AR11
  PR12
  AR12
  PR13
  AR13
  PR14
  AR14
  PR15
  AR15
  PR16
  AR16
  PR17
  AR17
  PR01
  AR01
  PRSA
  PRSB
  PRSC
  PRSD
  RS0A
  RS0B
  RS0C
  RS0D
  RS1A
  RS1B
  RS1C
  RS1D
  RS2A
  RS2B
  RS2C
  RS2D
  RS3A
  RS3B
  RS3C
  RS3D
  RS4A
  RS4B
  RS4C
  RS4D
  RS5A
  RS5B
  RS5C
  RS5D
  RS6A
  RS6B
  RS6C
  RS6D
  RS7A
  RS7B
  RS7C
  RS7D
  RSA0
  RSAC
  RSB0
  RSB2
  RS11
  RS12
  RSMB
  RSMU
  RSZA
  RSRU
  RSTA
  RSIR
  RSII
  RSIG
  RSU1
  RSU2
  RSI1
  RSI2
  RSSA
  RSMA
  PCI0
    _HID
    _ADR
    _BBN
    _UID
    _PRT
    NPTS
    NWAK
    SBRG
      _ADR
      SPTS
      SWAK
      SMIE
      [ ]
      [ ]
      PS1S
      [ ]
      PS1E
      [ ]
      SXCT
      [ ]
      S1CT
      [ ]
      S3CT
      [ ]
      S4CT
      [ ]
      S5CT
      [ ]
      GPB0
      [ ]
      GP01
      GP02
      GP03
      GP04
      GP05
      GP06
      GP07
      GP08
      GP09
      GP10
      GP11
      GP12
      GP13
      GP14
      GP15
      GP16
      GP17
      GP18
      GP19
      GP20
      GP21
      GP22
      GP23
      GP24
      GP25
      GP26
      GP27
      GP28
      GP29
      GP30
      GP31
      GP32
      GP33
      GP34
      GP35
      GP36
      GP37
      GP38
      GP39
      GP40
      MM90
      [ ]
      [ ]
      [ ]
      CSLD
      [ ]
      CSLT
      [ ]
      SDLA
      RTCO
      [ ]
      CIND
      CDAT
      [ ]
      [ ]
      CMO1
      UCFG
      [ ]
      U1CF
      MUAR
        _UID
        _HID
        _STA
        _CRS
        UCRS
        UIRQ
        UIO1
        UIO2
      PIC_
        _HID
        _CRS
      DMAD
        _HID
        _CRS
      SPKR
        _HID
        _CRS
      COPR
        _HID
        _CRS
      UAR1
        _UID
        _HID
        _STA
        _DIS
        _CRS
        _SRS
        _PRS
        CMPR
      UAR2
        _UID
        _HID
        _STA
        _DIS
        _CRS
        _SRS
        _PRS
        CMPR
      FDC_
        _HID
        _FDE
        _STA
        _DIS
        _CRS
        _SRS
        _PRS
      LPTE
        _HID
        _STA
        _DIS
        _CRS
        _SRS
        _PRS
        LPPR
        EPPR
      RMSC
        _HID
        _UID
        CRS_
        _CRS
      HPET
        _HID
        _UID
        CRS0
        CRS1
        _STA
        _CRS
        CF29
        [ ]
        [ ]
        [ ]
        P2IR
        HPTE
        [ ]
        [ ]
        NVID
      LPDC
      [ ]
      S3F8
      S2F8
      [ ]
      S2E8
      [ ]
      S3E8
      [ ]
      M300
      [ ]
      M330
      [ ]
      FDC0
      [ ]
      P378
      P278
      P3BC
      [ ]
      G200
      G208
      RRIO
      RDMA
      TMR_
        _HID
        CRS0
        CRS1
        _CRS
      RTC0
        _HID
        CRS0
        CRS1
        _CRS
      OMSC
        _HID
        _UID
        CRS_
        CRS1
        _CRS
      PS2K
        _HID
        _CID
        _STA
        _CRS
        _PRW
        _PSW
      PS2M
        _HID
        _CID
        _STA
        M2R0
        M2R1
        _CRS
        _PRW
        _PSW
      SIOR
        _HID
        _UID
        CRS_
        _CRS
      DCAT
      ENFG
      EXFG
      LPTM
      UHID
      SIOK
      KBFG
      MSFG
      U1FG
      U2FG
      KBRW
      [ ]
      KP60
      [ ]
      KP64
      KB64
      [ ]
      [ ]
      KRDY
      [ ]
      SIOS
      SIOW
      SIOH
      IOID
      [ ]
      INDX
      DATA
      [ ]
      [ ]
      LDN_
      [ ]
      FDCP
      [ ]
      LPTP
      URAP
      URBP
      [ ]
      CR29
      [ ]
      ACTR
      [ ]
      IOAH
      IOAL
      IOH2
      IOL2
      [ ]
      INTR
      [ ]
      DMCH
      [ ]
      CRE0
      CRE1
      CRE2
      CRE3
      CRE4
      CRE5
      CRE6
      [ ]
      OPT0
      OPT1
      OPT2
      OPT3
      OPT4
      [ ]
      OPT6
      CGLD
      DSTA
      DCNT
      CRS1
      IRQM
      DMAM
      IO11
      IO12
      LEN1
      CRS2
      IRQE
      DMAE
      IO21
      IO22
      LEN2
      IO31
      IO32
      LEN3
      DCRS
      DSRS
    _S3D
    _S1D
    NATA
    NVRB
      _HID
      FNVR
      _DIS
      _SRS
      _STA
      _CRS
    PCIE
      _HID
      _UID
      CRS_
      _CRS
    SMB0
      _ADR
      SMCF
      [ ]
      SMPM
      SMT1
      SMT2
      SMAD
      [ ]
      SB1_
      SB2_
      SMBB
      SME4
      [ ]
      [ ]
      XPME
      GPMD
      _PRW
    IMAP
      _ADR
      PIMC
      [ ]
      PIID
      [ ]
      PILN
      [ ]
      PIU0
      PIU2
      UBR1
      UBR2
      [ ]
      [ ]
      PIRM
      PMUD
      PAZA
      GPUR
      PR0E
      [ ]
      PIRA
      PIRB
      PIRC
      PIRD
      [ ]
      P0EA
      P0EB
      P0EC
      P0ED
      P1EA
      P1EB
      P1EC
      P1ED
      P2EA
      P2EB
      P2EC
      P2ED
      P3EA
      P3EB
      P3EC
      P3ED
      P4EA
      P4EB
      P4EC
      P4ED
      P5EA
      P5EB
      P5EC
      P5ED
      P6EA
      P6EB
      P6EC
      P6ED
      P7EA
      P7EB
      P7EC
      P7ED
      [ ]
      XVE0
      XVE1
      XVE2
      XVE3
      XVE4
      XVE5
      XVE6
      XVE7
    USB0
      _ADR
      _S1D
      _S3D
      _PRW
    USB2
      _ADR
      _S1D
      _S3D
      _PRW
    US15
      _ADR
      _S1D
      _S3D
      _PRW
    US12
      _ADR
      _S1D
      _S3D
      _PRW
    NMAC
      _ADR
      _PRW
    IDE0
      _ADR
      PTS0
      SID0
      SID1
      SID2
      SID3
      SID4
      SID5
      IRQM
      [ ]
      IR0M
      REGF
      _REG
      A090
      [ ]
      ID20
      [ ]
      IDTS
      IDTP
      ID22
      UMSS
      UMSP
      TIM0
      TMD0
      PIO0
      DMA0
      PIO1
      DMA1
      CHNF
      CFG2
      [ ]
      SSPT
      SMPT
      PSPT
      PMPT
      SSAS
      SMAS
      PSAS
      PMAS
      [ ]
      SDDR
      SDDA
      PDDR
      PDDA
      SSUT
      [ ]
      SSUE
      SMUT
      [ ]
      SMUE
      PSUT
      [ ]
      PSUE
      PMUT
      [ ]
      PMUE
      GMPT
      GMUE
      GMUT
      GSPT
      GSUE
      GSUT
      CHN0
        _ADR
        _GTM
        _STM
        DRV0
          _ADR
          _GTF
        DRV1
          _ADR
          _GTF
      CHN1
        _ADR
        _GTM
        _STM
        DRV0
          _ADR
          _GTF
        DRV1
          _ADR
          _GTF
      DRMP
      GTM_
      STM_
      AT01
      AT02
      AT03
      AT04
      ATA0
      ATA1
      ATA2
      ATA3
      ATAB
      CMDC
      GTFB
      GTF_
      RATA
    ATA0
      _ADR
      PRI0
        _ADR
        SPTM
        _GTM
        _STM
        MAST
          _ADR
          _GTF
        SLAV
          _ADR
          _GTF
      SEC0
        _ADR
        SSTM
        _GTM
        _STM
        MAST
          _ADR
          _GTF
        SLAV
          _ADR
          _GTF
      DRMP
    P0P1
      _ADR
      _PRW
      _PRT
    HDAC
      _ADR
      SCID
      SACW
      _PS0
      _PS3
      PMCF
      [ ]
      PMDS
      [ ]
      PMEN
      [ ]
      PMST
      DCF2
      [ ]
      AOCW
      [ ]
      CDID
      _PRW
    IXVE
      _ADR
      _PRT
      IGPU
        _ADR
        ERR0
        ERR1
        VER1
        ERR2
        NVIF
        PBNK
        PCOL
        DBNK
        DBK2
        DCOL
        DCL2
        RNKP
        STAD
        GLDT
        PCS8
        CSE8
        BAL8
        GTBW
        GLBW
        GMCK
        ATB8
        IMPM
        HVER
        HCBF
        HCTG
        DDCA
        DDCB
        DGHC
        DGON
        DGOF
        HSTA
        _DSM
        GPUR
        SWIT
        DDDS
        D0ST
        D1ST
        D2ST
        D3ST
        D4ST
        D0ID
        D0EV
        D0EN
        D0CV
        D0CN
        D1ID
        D1EV
        D1EN
        D1CV
        D1CN
        D2ID
        D2EV
        D2EN
        D2CV
        D2CN
        D3ID
        D3EV
        D3EN
        D3CV
        D3CN
        D4ID
        D4EV
        D4EN
        D4CV
        D4CN
        DDEV
        DDCN
        DGSM
        GNAD
        _DOD
        LCD0
          _ADR
          MXMX
          _DGS
        CRT0
          _ADR
          MXMX
          _DGS
        SVD0
          _ADR
          MXMX
          _DGS
        HDV0
          _ADR
          MXMX
          _DGS
    HDCP
    [ ]
    SIGN
    CHKS
    RESR
    GLOB
    WMI0
      _HID
      _UID
      _WDG
      WMNV
      WQBA
    K800
      _ADR
      HTWF
      [ ]
      [ ]
      LDTF
    K802
      _ADR
      HMM2
      [ ]
      [ ]
      MEMW
      [ ]
      MCLK
      [ ]
      DDRM
      G040
      [ ]
      RR22
      [ ]
      RR23
      [ ]
      RR24
      [ ]
      RR25
      [ ]
      RR26
      [ ]
      RR27
      [ ]
      RR28
      [ ]
      RR29
      [ ]
      RB22
      [ ]
      RB23
      [ ]
      RB24
      [ ]
      RB25
      [ ]
      RB26
      [ ]
      RB27
      [ ]
      RB28
      [ ]
      RB29
      [ ]
      [ ]
      CSE0
      [ ]
      BAL0
      [ ]
      CSE1
      [ ]
      BAL1
      [ ]
      CSE2
      [ ]
      BAL2
      [ ]
      CSE3
      [ ]
      BAL3
      [ ]
      CSE4
      [ ]
      BAL4
      [ ]
      CSE5
      [ ]
      BAL5
      [ ]
      CSE6
      [ ]
      BAL6
      [ ]
      CSE7
      [ ]
      BAL7
      G080
      [ ]
      RR30
      RR31
      [ ]
      CS10
      CS32
      CS54
      CS76
    K803
      _ADR
      HMM3
      [ ]
      PMM0
      PM1A
      PM1C
    NVBF
    [ ]
    [ ]
    K10F
    [ ]
    TOM1
    TOM2
    [ ]
    LSMD
    [ ]
    RR10
    [ ]
    RR11
    [ ]
    RR12
    [ ]
    RR13
    [ ]
    RR14
    [ ]
    RR15
    [ ]
    RR16
    [ ]
    RR17
    [ ]
    RR18
    [ ]
    RR19
    [ ]
    RR20
    [ ]
    RR21
    [ ]
    RB14
    [ ]
    RB15
    [ ]
    RB16
    [ ]
    RB17
    [ ]
    RB18
    [ ]
    RB19
    [ ]
    RB20
    [ ]
    RB21
    [ ]
    [ ]
    RR32
    RR33
    [ ]
    [ ]
    YDDR
    GTOM
    WMI1
      _HID
      _UID
      _WDG
      WMMX
      WQXM
    MXR0
      _ADR
      _PRW
      _PRT
      PCV0
      [ ]
      PEV0
      [ ]
      [ ]
      XPE0
      [ ]
      RQD0
      PES0
      PEP0
    BR11
      _ADR
      _PRW
      _PRT
    BR12
      _ADR
      _PRW
      _PRT
    BR13
      _ADR
      _PRW
      _PRT
    BR14
      _ADR
      _PRW
      _PRT
    BR15
      _ADR
      _PRW
      _PRT
    BR16
      _ADR
      _PRW
      _PRT
    BR17
      _ADR
      _PRW
      _PRT
    SUPP
    CTRL
    _OSC
    CRS_
    MIN5
    MAX5
    LEN5
    MIN6
    MAX6
    LEN6
    MIN7
    MAX7
    LEN7
    _CRS
  BN00
  [ ]
  SMIP
  RMEM
    _HID
    _UID
    CRS_
    _CRS
  PWRB
    _HID
    _UID
    _STA
    _PRW
  BUFA
  ICRS
  LSTA
  LPRS
  LCRS
  LCRO
  LSRS
  LSRO
  LNKA
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LNKB
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LNKC
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LNKD
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN0A
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN0B
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN0C
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN0D
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN1A
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN1B
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN1C
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN1D
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN2A
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN2B
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN2C
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN2D
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN3A
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN3B
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN3C
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN3D
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN4A
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN4B
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN4C
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN4D
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN5A
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN5B
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN5C
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN5D
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN6A
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN6B
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN6C
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN6D
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN7A
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN7B
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN7C
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LN7D
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LUB0
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LUB2
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LMAC
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LAZA
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  SGRU
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LSMB
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LPMU
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LSA0
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  LATA
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  UB11
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  UB12
    _HID
    _UID
    _STA
    _PRS
    _DIS
    _CRS
    _SRS
  XCPD
  XNPT
  XCAP
  XDCP
  XDCT
  XDST
  XLCP
  XLCT
  XLST
  XSCP
  XSCT
  XSST
  XRCT
  MUTE
  RBPE
  RWPE
  RDPE
  WBPE
  WWPE
  WDPE
  RWDP
  RPME
_SI_
_TZ_
_REV
_OS_
_OSI
_GL_
NPTS
NWAK
FZTF
DP80
DP90
SPIO
IOSB
IOSL
IOHB
IOHL
SSMI
SSEP
SSEN
SHPB
SHPL
GPBS
PMBS
PMLN
SCBS
SCLN
ACBS
ACLN
MTAB
MTAL
ACA4
SCIO
SCTL
SNAS
SNAM
SNAL
SPAS
SPAM
SPAL
MUAE
APIC
PCIB
PCIL
WKTP
BIOS
[ ]
SS1_
SS2_
SS3_
SS4_
[ ]
IOST
TOPM
ROMS
MG1B
MG1L
MG2B
MG2L
[ ]
DMAX
HPTA
CPB0
CPB1
CPB2
CPB3
ASSB
AOTB
AAXB
SMIF
DTSE
DTS1
DTS2
MPEN
TPMF
MG3B
MG3L
MH1B
MH1L
OSTP
HYCM
RRIO
RDMA
PICM
_PIC
OSVR
OSFL
MCTH
PRWP
GPRW
WAKP
DEB0
[ ]
DBG8
DEB1
[ ]
DBG9
OSYS
SCPP
[ ]
IGUB
IGUL
SM00
[ ]
CTLR
HSTS
ADDR
CMDR
DAT0
DAT1
[ ]
ALAD
ALDL
ALDH
[ ]
[ ]
SB32
SWFS
SRBY
WBYT
CLAR
WWRD
RBYT
RWRD
SMRB
GPS0
[ ]
GS00
GS01
GS02
GS03
WOTB
WSSB
WAXB
_PTS
_WAK
_S0_
_S3_
_S4_
_S5_
PTS_
WAK_

[/PHP]

Thank you very much for your help and time,

Richard Hughes

---

