---
title: "Can My System Run Ubuntu 12.04 ?"
date: 2012-05-06
forum: General Help
---

### Post by tinker123 on 2012-05-06
I upgraded my system from Ubuntu 10.10 on a 9 year old computer to Ubuntu 12.04 last night.  During the installation process I saw an error message about a kernel module not being installed properly.   When I try to reboot I get a message telling me my video stuff isn't configured properly with an option for going in with low graphics mode.  I can't as Ubuntu doesn't pick up my mouse or keyboard.

I plan to go to the store tomorrow to get a USB hard drive to rescue my files with a livecd.

I'm wondering if I should attempt a clean install of Ubuntu 12.04 or use an older version that is newer than 10.10.

Will my hardware run Ubuntu 12.04 well?:

[B]
lspci output[/B]

```

ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
02:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:00.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:04.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
ubuntu@ubuntu:~$ 
[/quote]

**dmidecode ouput:**

[quote]
root@ubuntu:~# dmidecode
# dmidecode 2.9
SMBIOS 2.3 present.
68 structures occupying 2426 bytes.
Table at 0x000FBE40.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Intel Corp.
	Version: SV84510A.86A.0008.P04.0210201732
	Release Date: 10/20/2002
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
	Manufacturer:                                
	Product Name:                                
	Version:                        
	Serial Number:                                
	UUID: 6BD75CFC-201E-11D7-B0D6-00E01825AEC9
	Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Intel Corporation              
	Product Name: D845PESV                       
	Version: AAA97669-107           
	Serial Number: AZSV30207262                   

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer:                                
	Type: Unknown
	Lock: Not Present
	Version:                        
	Serial Number:                                
	Asset Tag:                                
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Other
	Security Status: Other
	OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: J2E1
	Type: Central Processor
	Family: Pentium 4
	Manufacturer: Intel            
	ID: 27 0F 00 00 FF FB EB BF
	Signature: Type 0, Family 15, Model 2, Stepping 7
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Pentium(R) 4 processor                     
	Voltage: 3.3 V 2.9 V
	External Clock: 133 MHz
	Max Speed: 3060 MHz
	Current Speed: 2533 MHz
	Status: Populated, Enabled
	Upgrade: Socket 478
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: None
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 8 KB
	Maximum Size: 8 KB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 4-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: None
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 512 KB
	Maximum Size: 512 KB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0007, DMI type 126, 35 bytes
Inactive

Handle 0x0008, DMI type 126, 19 bytes
Inactive

Handle 0x0009, DMI type 126, 19 bytes
Inactive

Handle 0x000A, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 512 MB
	Maximum Total Memory Size: 1024 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		Other
		Unknown
		Standard
		FPM
		EDO
		Parity
		ECC
		SIMM
		DIMM
		Burst EDO
		SDRAM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 2
		0x000B
		0x000C
	Enabled Error Correcting Capabilities:
		None

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 11 12
	Current Speed: 2 ns
	Type: DIMM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM2
	Bank Connections: 11 12
	Current Speed: 2 ns
	Type: DIMM
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: PS2Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A1
	Internal Connector Type: None
	External Reference Designator: COM 1
	External Connector Type: DB-9 female
	Port Type: Serial Port 16550A Compatible

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4A2
	Internal Connector Type: None
	External Reference Designator: LPT1
	External Connector Type: DB-25 male
	Port Type: Parallel Port ECP/EPP

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: JA5A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: JA5A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4A1
	Internal Connector Type: None
	External Reference Designator: VIDEO
	External Connector Type: DB-15 male
	Port Type: Video Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: JA5A1
	Internal Connector Type: None
	External Reference Designator: RJ-45 Type
	External Connector Type: RJ-45
	Port Type: Network Port

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Mic In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Line In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Line Out
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J5C1 - +12V
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4H1 - FDD
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6H2 - PRI IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6H1 - SEC IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8B1 - CDIN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6B1 - AUX IN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G1 - FRONT PANEL HDR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2F1 - CPU FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H3 - FNT PNL
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0023, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H3 - FRONT CHASSIS FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0024, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1B1 - REAR CHASSIS FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0025, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H2 - BIOS CONFIG
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0026, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8A1 - FP AUDIO
	Internal Connector Type: Proprietary
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0027, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9F1 - FRONT PANEL USB
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0028, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2H1 - PS
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0029, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8H3 - CH INTR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x002A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8H2 - SCSI
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x002B, DMI type 9, 13 bytes
System Slot Information
	Designation: J6C1
	Type: 32-bit AGP 4x
	Current Usage: In Use
	Length: Long
	ID: 0
	Characteristics:
		3.3 V is provided

Handle 0x002C, DMI type 9, 13 bytes
System Slot Information
	Designation: J7B1
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 1
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x002D, DMI type 9, 13 bytes
System Slot Information
	Designation: J8B2
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 2
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x002E, DMI type 9, 13 bytes
System Slot Information
	Designation: J9B2
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 3
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x002F, DMI type 9, 13 bytes
System Slot Information
	Designation: J9B1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 4
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0030, DMI type 9, 13 bytes
System Slot Information
	Designation: J9B5
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 5
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0031, DMI type 9, 13 bytes
System Slot Information
	Designation: J9B4
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 6
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0032, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Disabled
	Description: Intel GMCH AGP Graphics Controller

Handle 0x0033, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Disabled
	Description: Intel 82562 Ethernet Device

Handle 0x0034, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Disabled
	Description: Intel ICH4 Audio Device

Handle 0x0035, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		enUS
	Currently Installed Language: enUS

Handle 0x0036, DMI type 15, 35 bytes
System Event Log
	Area Length: 2048 bytes
	Header Start Offset: 0x0000
	Header Length: 16 bytes
	Data Start Offset: 0x0010
	Access Method: Memory-mapped physical 32-bit address
	Access Address: 0xFFFDF700
	Status: Valid, Not Full
	Change Token: 0x00000000
	Header Format: Type 1
	Supported Log Type Descriptors: 6
	Descriptor 1: POST error
	Data Format 1: POST results bitmap
	Descriptor 2: Parity memory error
	Data Format 2: Multiple-event
	Descriptor 3: I/O channel block
	Data Format 3: Multiple-event
	Descriptor 4: Single-bit ECC memory error
	Data Format 4: Multiple-event
	Descriptor 5: Multi-bit ECC memory error
	Data Format 5: Multiple-event
	Descriptor 6: System limit exceeded
	Data Format 6: System management

Handle 0x0037, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: Bad Read
	Granularity: Device Level
	Operation: Read
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0038, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 3 GB
	Error Information Handle: 0x0037
	Number Of Devices: 2

Handle 0x0039, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0005FFFFFFF
	Range Size: 1536 MB
	Physical Array Handle: 0x0038
	Partition Width: 0

Handle 0x003A, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0038
	Error Information Handle: 0x0037
	Total Width: 64 bits
	Data Width: 72 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: J6G1
	Bank Locator: DIMM0
	Type: DDR
	Type Detail: Synchronous
	Speed: 333 MHz (3.0 ns)
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

Handle 0x003B, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x003A
	Memory Array Mapped Address Handle: 0x0039
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x003C, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0038
	Error Information Handle: 0x0037
	Total Width: 64 bits
	Data Width: 72 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: J6G2
	Bank Locator: DIMM1
	Type: DDR
	Type Detail: Synchronous
	Speed: 333 MHz (3.0 ns)
	Manufacturer: Manufacturer2
	Serial Number: SerNum2
	Asset Tag: AssetTagNum2
	Part Number: PartNum2

Handle 0x003D, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00020000000
	Ending Address: 0x0005FFFFFFF
	Range Size: 1 GB
	Physical Device Handle: 0x003C
	Memory Array Mapped Address Handle: 0x0039
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x003E, DMI type 23, 13 bytes
System Reset
	Status: Disabled
	Watchdog Timer: Not Present

Handle 0x003F, DMI type 31, 28 bytes
Boot Integrity Services Entry Point

Handle 0x0040, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0041, DMI type 187, 9 bytes
OEM-specific Type
	Header and Data:
		BB 09 41 00 3A 00 03 0A 01

Handle 0x0042, DMI type 187, 9 bytes
OEM-specific Type
	Header and Data:
		BB 09 42 00 3C 00 03 0A 01

Handle 0x0043, DMI type 127, 4 bytes
End Of Table

root@ubuntu:~# 

```

---

### Post by Rodney9 on 2012-05-06
Try the Live Disc first, if it works, install.

For a older machine maybe Xubuntu or Lubuntu, which are lighter flavours of Ubuntu, they need less cpu, ram etc.

Rodney

---

### Post by kostkon on 2012-05-06
Try removing the nvidia driver (if it's installed) and reboot. The one in 12.04 doesn't support g4  mx cards anymore, obviously.

Hopefully, ubuntu will use the open source driver and boot in unity 2D. Hopefully...

---

### Post by grahammechanical on 2012-05-06
I see this

> Installed Size: 512 MB (Double-bank Connection)

and this

> Installed Size: 1024 MB (Double-bank Connection)

So you have more than enough RAM for the install to run.

But I also see this

> 01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

How much video memory does the card have? What is the CPU?

This machine may not be capable of running Ubuntu/Unity 3D but it should be capable of running Ubuntu/Unity 2D.

How did you upgrade 10.10 to 12.04? Why did the upgrade fail? That is the important question. 

Regards.

---

### Post by tinker123 on 2012-05-07
The chip is an Intel P-4 2.53 GHZ 533FSB 512K Cache

I got this info for the video card from lspci -v :

> 
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. V9180 Magic
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb



I updgraded first from 10.10 -> 11.04 -> 11.10 -> 12.04

During the 12.04 installation I got an error message saying that part of the kernel could not be installed correctly.  Things worked, but when I rebooted my computer I got told my video wasn't configured properly and that I could only run in low graphics mode.  When I pressed okay things just hung.  I couldn't get in.

I had an old livecd of Xubuntu 10.10 so I used that to get on my computer and copy my data off of my hard drive.  I then tried installing Xubuntu 10.10 with the intent of downloading something more advanced and trying again.

In the Xubuntu installer I checked the option to also download updates.  The installer stalled/ran for over 5 hours, periodically updating the time in the command shell window in the gui with a message that seemed to indicate it was stuck doing something with the kernel and "vga" ( the video card? ).

I let it run for the 5 hours because I thought it was sequentially taking me from 10.10 - 12.04 and the message updates made it look like it was still running.

However, 5 hours is too long even for that so I rebooted my computer and ran the XUbuntu 10.10 installer again, WITHOUT the option to dowload updates.  15 minutes later I had XUbuntu 10.10 on my box.

There is something about 12.04 or a version after 10.10 that does not like something about my system.

---

### Post by tinker123 on 2012-05-09
I read in a thread at ubuntuforums.org  that between actions from Canononical and NVIDA, support for my video card likely got inadvertently dropped in 12.04.  I'm guessing that led to a large part, if not all of my upgrade problems.

My system was running Ubuntu 10.10, which had updates turned off and support withdrawn this year.

I thought Unity was cool. However, I don't have a wide screen monitor and I'm doing more development at home these days. Learning new habits while programming would likely drive me bats right now since I am so busy.

So between the issue of Unity being very different and 12.04 not liking my hardware I decided not to upgrade to Ubuntu 12.04, but do a clean install of XUbuntu 11.10 instead.

I'm enjoying the simplicity of XUbuntu. Support for 11.10 only lasts until 2013 April. My computer will be 10 years old as of March that year.

At that point 1 of 3 things might happen:

[list]
[*] the Nvidia support issue with 12.04 will be resolved 
[*] I will buy a new PC with new hardware that will be supported
[*] I will go Mac
[/list]

Either way the problem will be solved and as for right now I am back in business at home with a minimum of hassle.

---

