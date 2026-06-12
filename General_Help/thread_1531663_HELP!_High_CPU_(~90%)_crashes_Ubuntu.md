---
title: "HELP! High CPU (~90%) crashes Ubuntu"
date: 2010-07-15
forum: General Help
---

### Post by strangeusername on 2010-07-15
Hi all,
My amd64 laptop has had disturbing behaviour since I upgraded to Lucid. Basically, anything that will max out the CPU will simply crash the machine. Flash videos, buggy scripts in firefox or even rhythmbox.

The last one, the bit about rhythmbox, amazes me... and can be reproduced. I have a small NAS with all my music collection, a few thousand tracks. I cifs-mount (read-only) this NAS into my Music dir and rhythmbox happily uses it. Now if I'm not connected to the network and start rhythmbox, it figures out that some files previously in the collection are missing and diligently updates the list. I'd expect the process of "is file A there? NO, what about file B? NO" ... and so on thousands of times to max out the CPU. But COMPLETELY CRASH ubuntu?

Crash here means the screens (I got two attached) go blank - usually a grey scale colour (though i had the odd purple screen). No SSH or console possible. It's gone. Cold shutdown is only solution ... which I perform hoping that this doesn't damage the disk.

To make things even worse, there are no core dumps (/var/crash is empty), /var/log/messages has nothing at the time of the crash. Just shows at which point the machine booted. /var/log/kernel or /var/log/debug are as useless.

I have tried to keep calm about this but ... HELP!

This doesn't make sense. This machine is otherwise very healthy.

Here are my specs. Let me know if you need anything else that might help you help me ;)


pingu@him:/var/log$ uname -a
Linux him 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
pingu@him:/var/log$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm)X2 Ultra DualCore Mobile ZM-86
stepping	: 1
cpu MHz		: 600.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4799.94
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm)X2 Ultra DualCore Mobile ZM-86
stepping	: 1
cpu MHz		: 600.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4800.27
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

pingu@him:/var/log$ sudo dmidecode 
# dmidecode 2.9
SMBIOS 2.4 present.
19 structures occupying 1000 bytes.
Table at 0xAFDBC000.

Handle 0x0009, DMI type 0, 24 bytes
BIOS Information
	Vendor: Hewlett-Packard
	Version: 68GTT Ver. F.07
	Release Date: 09/19/2008
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 2048 kB
	Characteristics:
		PCI is supported
		PC Card (PCMCIA) is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		Smart battery is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 15.7
	Firmware Revision: 96.29

Handle 0x000A, DMI type 1, 27 bytes
System Information
	Manufacturer: Hewlett-Packard
	Product Name: HP Compaq 6735b
	Version: F.07
	Serial Number: XXX
	UUID: XXX
	Wake-up Type: Power Switch
	SKU Number: XXX
	Family: 103C_5336AN

Handle 0x000B, DMI type 2, 16 bytes
Base Board Information
	Manufacturer: Hewlett-Packard
	Product Name: 30E3
	Version: KBC Version 96.1C
	Serial Number: Base Board Serial Number
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x000C
	Type: Unknown
	Contained Object Handles: 0

Handle 0x000C, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: Hewlett-Packard
	Type: Notebook
	Lock: Not Present
	Version: Not Specified
	Serial Number: XXX
	Asset Tag: XXX
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Other
	Security Status: Other
	OEM Information: 0x00000000

Handle 0x0000, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Unknown
	Type: Central Processor
	Family: <OUT OF SPEC>
	Manufacturer: AMD Corporation
	ID: 31 0F 20 00 FF FB 8B 17
	Version: AMD Turion(tm)X2 Ultra DualCore Mobile ZM-86
	Voltage: 1.5 V
	External Clock: 200 MHz
	Max Speed: 2400 MHz
	Current Speed: 2400 MHz
	Status: Populated, Enabled
	Upgrade: <OUT OF SPEC>
	L1 Cache Handle: 0x0001
	L2 Cache Handle: 0x0002
	L3 Cache Handle: Not Provided
	Serial Number: NotSupport
	Asset Tag: FFFF
	Part Number: Not Specified

Handle 0x0001, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 256 KB
	Maximum Size: 256 KB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: Unknown
	Error Correction Type: Multi-bit ECC
	System Type: Unified
	Associativity: 2-way Set-associative

Handle 0x0002, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 2048 KB
	Maximum Size: 2048 KB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: Unknown
	Error Correction Type: Multi-bit ECC
	System Type: Unified
	Associativity: 16-way Set-associative

Handle 0x0010, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI SLOT1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 1
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x000E, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: 256

Handle 0x000F, DMI type 11, 5 bytes
OEM Strings
	String 1: ABS 70/71 79 7A 7B 7C
	String 2: CSM v02.1D

Handle 0x0003, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x0004, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0003
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: SODIMM 0
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: Elpida
	Serial Number: XXX
	Asset Tag: Unknown
	Part Number: XXX-8G-E 

Handle 0x0006, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0003
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: SODIMM 1
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: Unknown
	Serial Number: XXX
	Asset Tag: Unknown
	Part Number: XXX      

Handle 0x0008, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x0003
	Partition Width: 0

Handle 0x0005, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0004
	Memory Array Mapped Address Handle: 0x0008
	Partition Row Position: 1

Handle 0x0007, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0006
	Memory Array Mapped Address Handle: 0x0008
	Partition Row Position: 1

Handle 0x0011, DMI type 22, 26 bytes
Portable Battery
	Location: Primary
	Manufacturer: SDI - SDI
	Manufacture Date: 392B
	Serial Number: 0164
	Name: TD06055
	Design Capacity: 5100 mWh
	Design Voltage: 10800 mV
	SBDS Version: 1.1
	Maximum Error: Unknown
	SBDS Chemistry: LION
	OEM-specific Information: 0x00000000

Handle 0x000D, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0xFFFD, DMI type 127, 4 bytes
End Of Table

pingu@him:/var/log$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
09:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
0a:06.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

---

### Post by dino99 on 2010-07-15
system-monitor might show you which app have issue

---

### Post by strangeusername on 2010-07-16
Well, that's the thing. it doesn't really matter what app uses 100%, ubuntu will simply crash if CPU usage goes very high.

As I said, flash, rhythmbox and firefox are the ones I've seen  will cause a crash up to now.

---

### Post by strangeusername on 2010-07-16
@freaky88 please refrain from posting pornographic pictures to this forum. Needless to say I reported your post as an abuse.

---

### Post by mcduck on 2010-07-16
Do you dualboot the system? If so, do you have the same problem in your other OS? IF you don't dualboot, perhaps try stressing the system while running from a live-CD or something..

System crashing under high load really sounds more like a hardware-related problem than a software issue. You might want to check the system's temperatures (if possible) and make sure the CPU heatsink is properly in it's place, all the fans are clean and working etc..

Checking the voltages might also be a good idea, in case there's some problem with your PSU or motherboards power circuitry.

---

### Post by strangeusername on 2010-07-16
@mcduck, the last part of your post sounds promising! How do I go about checking these things like temperature etc?

I'm using a laptop which is permanently on a docking station, so lightly tilted which I assume if good for ventilation. I do hear the fans a bit too much though... maybe dust? I'll look into now.

I don't dualboot... Or at least I can't anymore (forgot the password)!

---

### Post by gradinaruvasile on 2010-07-16
CPU/GPU overheating issue... ?
Do you use the proprietary Ati driver? If not, install it because it will help with the temperature a bit.

---

### Post by strangeusername on 2010-07-16
@gradinaruvasile Yeah, I do use the proprietary ATI driver.

Thanks to everyone who posted up to now. I'm investigating every possibility. Keep the ideas coming!

---

### Post by strangeusername on 2010-07-16
Installed lm-sensors and acpitz-virtual-0 (which apparently is the motherboard itself) was showing 256 degrees. Considering that it also says that anything above 105 degrees is critical, I am inclined to believe I have found the culprit! Thanks @mcduck.

I've put a bunch of CD's under the edges of the laptop and the docking station and though the first thing I noticed was a less noisy system, sensors happily claimed that it's now running at 60 degrees.

I'll try to kill the system by doing some of them dangerous commands etc and see what happens... fork bombs? anyone?

---

### Post by mcduck on 2010-07-17
While cleaning the coolers properly would require actually opening the machine, that's probably a bit too complicated since it's a laptop. But you could try simply sucking as much dust as you can through the air vents in the laptop using a vacuum cleaner. It usually helps at least a bit.

..and here's the forkbomb for you: ;)
```
:(){ :|:& };:
```
**_DISCLAIMER: executing this code will freeze your system!_** While you can solve it with a simple reboot, make sure you aren't doing anything important on the machine at the time. (it's also possible to restrict the amount of processes a user is allowed to create, which would stop this kind of things from freezing your system.)

And by the way, there is also a package of CPU stressing tools called "cpuburn", available in the repositories. Although high chipset temperatures are more likely to be related to high overall system load instead of just high CPU load. You could also use the "superpi" program (not in the repositories, but you'll find it with google), and get a nice CPU benchmark at the same time. :)

---

### Post by strangeusername on 2010-07-17
@mcduck, thanks for help. I did have a few fork bombs around myself... Just had to look in my very early scripts from a few years back! ;)

I did used the vacuum cleaner on the air vents and temperature has dropped to around 50 when it was at 70 before. I did also use some of these butane keyboard cleaning sprays (or some other gas, you know what I mean).

As for loading the laptop, I do have some heavy scripts with a lot of I/O, calculations and so on.

Thanks to everyone who helped!

Cheers

---

