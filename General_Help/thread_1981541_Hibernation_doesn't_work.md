---
title: "Hibernation doesn't work"
date: 2012-05-16
forum: General Help
---

### Post by RogerDavis on 2012-05-16
When I select hibernation, it doesn't quite get it done, just stops and I have to turn off the main power to the system.  Just pushing the power button doesn't work.

Shut down does work.

How do I get this to work again?

Thanks!

---

### Post by idoitprone on 2012-05-17
> **RogerDavis said:**
> When I select hibernation, it doesn't quite get it done, just stops and I have to turn off the main power to the system.  Just pushing the power button doesn't work.

Shut down does work.

How do I get this to work again?

Thanks!

DO you have enough swap space?
```
swapon -a
free -m
```

---

### Post by RogerDavis on 2012-05-17
roger@roger-desktop:~$ swapon -a
roger@roger-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3023       1733       1290          0        306        570
-/+ buffers/cache:        856       2166
Swap:         2931          0       2931

roger@roger-desktop:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	3002360	0	-1

Is it odd that there appears to be no used space in the file?

---

### Post by idoitprone on 2012-05-17
> **RogerDavis said:**
> roger@roger-desktop:~$ swapon -a
roger@roger-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3023       1733       1290          0        306        570
-/+ buffers/cache:        856       2166
Swap:         2931          0       2931

roger@roger-desktop:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    3002360    0    -1

Is it odd that there appears to be no used space in the file?

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
it appears you have enough swap. 

maybe try this
```
sync; echo 3 > /proc/sys/vm/drop_caches
```
then hibernate

---

### Post by RogerDavis on 2012-05-17
How do I fix "permission denied"?  Is this just a goof on my part, or does it indicate a problem?

roger@roger-desktop:~$ sync; echo 3 > /proc/sys/vm/drop_caches
bash: /proc/sys/vm/drop_caches: Permission denied
roger@roger-desktop:~$ sudo sync; echo 3 > /proc/sys/vm/drop_caches
[sudo] password for roger: 
bash: /proc/sys/vm/drop_caches: Permission denied
roger@roger-desktop:~$ 

Thanks!

---

### Post by RogerDavis on 2012-05-17
I find that root is the owner of /proc/sys/vm/drop_caches.  I guess this is the problem.  How do I get by that in Ubuntu?

In poking about, I find roger/ubuntu one/ to have a red x superimposed.  Any clue, does it connect to this problem, or is it something completely different?

---

### Post by idoitprone on 2012-05-17
> **RogerDavis said:**
> I find that root is the owner of /proc/sys/vm/drop_caches.  I guess this is the problem.  How do I get by that in Ubuntu?

In poking about, I find roger/ubuntu one/ to have a red x superimposed.  Any clue, does it connect to this problem, or is it something completely different?

my fault for assumming that everyone can use sudo

sudo sync; sudo  'bash -c  echo 3 > /proc/sys/vm/drop_caches'

---

### Post by RogerDavis on 2012-05-17
roger@roger-desktop:~$ sudo sync
roger@roger-desktop:~$ sudo bash -c echo 3 > /proc/sys/vm/drop_caches
bash: /proc/sys/vm/drop_caches: Permission denied
roger@roger-desktop:~$ 

I guess maybe I made another error?  I've tried this with every variation I can think of.  At one time I got a roger@roger-desktop:~# instead of the $, but I can't duplicate it.

Thanks!

---

### Post by jadtech on 2012-05-17
try to copy and past it just like they typed it just like this 

```
 
sudo sync; sudo 'bash -c echo 3 > /proc/sys/vm/drop_caches


```

might not make a differance  but some times it does ..

if it still fails if this dont work there is ways to make changes as root or in root some can help you with if that is needed I dont know my self this could be something that need to be done  from live cd ..

---

### Post by RogerDavis on 2012-05-18
No error message, no text or results, cursor change to a ">" .

roger@roger-desktop:~$ sudo sync; sudo 'bash -c echo 3 > /proc/sys/vm/drop_caches
> 

Success?  Dismal failure?  ???

---

### Post by idoitprone on 2012-05-18
> **RogerDavis said:**
> No error message, no text or results, cursor change to a ">" .

roger@roger-desktop:~$ sudo sync; sudo 'bash -c echo 3 > /proc/sys/vm/drop_caches
> 

Success?  Dismal failure?  ???

```
sudo sync; sudo 'bash -c echo 3 > /proc/sys/vm/drop_caches**'**
```[B]

you forgot a ending quote

i am just testing if it there enough space in swap to hibernate
its a simple test
[/B]

---

### Post by RogerDavis on 2012-05-18
The penguin is out to get me...

roger@roger-desktop:~$ sudo sync; sudo 'bash -c echo 3 > /proc/sys/vm/drop_caches'
[sudo] password for roger: 
sudo: bash -c echo 3 > /proc/sys/vm/drop_caches: command not found
roger@roger-desktop:~$ 

Which command is not found?

---

### Post by idoitprone on 2012-05-18
> **RogerDavis said:**
> The penguin is out to get me...

roger@roger-desktop:~$ sudo sync; sudo 'bash -c echo 3 > /proc/sys/vm/drop_caches'
[sudo] password for roger: 
sudo: bash -c echo 3 > /proc/sys/vm/drop_caches: command not found
roger@roger-desktop:~$ 

Which command is not found?

opps i put the quote in the wrong place

```
sudo sync; sudo bash -c 'echo 3 > /proc/sys/vm/drop_caches'
```
then hibernate

this flushes your ram cache so you can ave less in ram to hibernate

---

### Post by nipunshakya on 2012-05-18
> **RogerDavis said:**
> When I select hibernation, it doesn't quite get it done, just stops and I have to turn off the main power to the system.  Just pushing the power button doesn't work.

Shut down does work.

How do I get this to work again?

Thanks!

How about running ubuntu in live session, using Gparted to re-format the swap area and use it as swap again? Haven't done personally, but might worth a try i guess...

Happy Linuxing

---

### Post by RogerDavis on 2012-05-18
I wonder if being pecked to death by a penguin is any more or less painful than being pecked to death by a duck...

No activity appears in Terminal

roger@roger-desktop:~$ sudo sync; sudo bash -c 'echo 3 > /proc/sys/vm/drop_caches'
[sudo] password for roger: 
roger@roger-desktop:~$ 

Also, exactly same hibernation result - looks like it gets mostly there, then everything just stops...

---

### Post by idoitprone on 2012-05-18
> **RogerDavis said:**
> I wonder if being pecked to death by a penguin is any more or less painful than being pecked to death by a duck...

No activity appears in Terminal

roger@roger-desktop:~$ sudo sync; sudo bash -c 'echo 3 > /proc/sys/vm/drop_caches'
[sudo] password for roger: 
roger@roger-desktop:~$ 

Also, exactly same hibernation result - looks like it gets mostly there, then everything just stops...

yikes you do have a real problem. I do not know how to diagonse it

Post you hardware specs

[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)
You can look at the wiki in the mean time

---

### Post by RogerDavis on 2012-05-18
Hardware Info
------------------------
Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4J1 - FDD
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J1 - PRI IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9C1 - CDIN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8B2 - SPDIF
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9J4 - FRONT PANEL HDR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1F2 - CPU FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8E1 - FNT PNL 1394 1
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8E2 - FNT PNL 1394 2
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0023, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8J2 - FRONT CHASSIS FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0024, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J5B2 - REAR CHASSIS FAN1
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0025, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J11A1 - REAR CHASSIS FAN2
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0026, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8J4 - BIOS CONFIG
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0027, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8A2 - FP AUDIO
	Internal Connector Type: Proprietary
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0028, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G2 - FRONT PANEL USB1
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0029, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H2 - FRONT PANEL USB2
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x002A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J3J1 - PS
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x002B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J7H1 - CH INTR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x002C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8H2 - SCSI
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x002D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H3 - SATA 0
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x002E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H4 - SATA 1
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x002F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9J1 - SATA 2
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0030, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9J2 - SATA 3
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0031, DMI type 9, 13 bytes
System Slot Information
	Designation: J6C1
	Type: x16 PCI Express
	Current Usage: In Use
	Length: Long
	ID: 11
	Characteristics:
		3.3 V is provided

Handle 0x0032, DMI type 9, 13 bytes
System Slot Information
	Designation: J7B1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 1
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0033, DMI type 9, 13 bytes
System Slot Information
	Designation: J8B1
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 2
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0034, DMI type 9, 13 bytes
System Slot Information
	Designation: J9C2
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 12
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0035, DMI type 9, 13 bytes
System Slot Information
	Designation: J8C1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 13
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0036, DMI type 9, 13 bytes
System Slot Information
	Designation: J10B1
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 3
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0037, DMI type 9, 13 bytes
System Slot Information
	Designation: J11B1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 4
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0038, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Disabled
	Description: Intel GMCH AGP Graphics Controller

Handle 0x0039, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Intel 82562 Ethernet Device

Handle 0x003A, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: Intel ICH6 Audio Device

Handle 0x003B, DMI type 10, 6 bytes
On Board Device Information
	Type: Other
	Status: Disabled
	Description: Agere 1394 Controller

Handle 0x003C, DMI type 12, 5 bytes
System Configuration Options
	Option 1: To Be Filled By O.E.M.
	Option 2: To Be Filled By O.E.M.
	Option 3: To Be Filled By O.E.M.

Handle 0x003D, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		enUS
	Currently Installed Language: enUS

Handle 0x003E, DMI type 15, 35 bytes
System Event Log
	Area Length: 1024 bytes
	Header Start Offset: 0x0000
	Header Length: 16 bytes
	Data Start Offset: 0x0010
	Access Method: Memory-mapped physical 32-bit address
	Access Address: 0xFFF83780
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

Handle 0x003F, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: Unknown
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0040, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: 0x003F
	Number Of Devices: 4

Handle 0x0041, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000BFFFFFFF
	Range Size: 3 GB
	Physical Array Handle: 0x0040
	Partition Width: 0

Handle 0x0042, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: 0x003F
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: 1
	Locator: J6G1
	Bank Locator: CHANNEL A DIMM0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

Handle 0x0043, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Device Handle: 0x0042
	Memory Array Mapped Address Handle: 0x0041
	Partition Row Position: 1
	Interleave Position: 1
	Interleaved Data Depth: 2

Handle 0x0044, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: 0x003F
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: 2
	Locator: J6G2
	Bank Locator: CHANNEL A DIMM1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: Manufacturer2
	Serial Number: SerNum2
	Asset Tag: AssetTagNum2
	Part Number: PartNum2

Handle 0x0045, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00040000000
	Ending Address: 0x0005FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x0044
	Memory Array Mapped Address Handle: 0x0041
	Partition Row Position: 1
	Interleave Position: 1
	Interleaved Data Depth: 2

Handle 0x0046, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: 0x003F
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: 1
	Locator: J6H1
	Bank Locator: CHANNEL B DIMM0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: Manufacturer3
	Serial Number: SerNum3
	Asset Tag: AssetTagNum3
	Part Number: PartNum3

Handle 0x0047, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00060000000
	Ending Address: 0x0009FFFFFFF
	Range Size: 1 GB
	Physical Device Handle: 0x0046
	Memory Array Mapped Address Handle: 0x0041
	Partition Row Position: 2
	Interleave Position: 2
	Interleaved Data Depth: 2

Handle 0x0048, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: 0x003F
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: 2
	Locator: J6H2
	Bank Locator: CHANNEL B DIMM1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: Manufacturer4
	Serial Number: SerNum4
	Asset Tag: AssetTagNum4
	Part Number: PartNum4

Handle 0x0049, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x000A0000000
	Ending Address: 0x000BFFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x0048
	Memory Array Mapped Address Handle: 0x0041
	Partition Row Position: 2
	Interleave Position: 2
	Interleaved Data Depth: 2

Handle 0x004A, DMI type 23, 13 bytes
System Reset
	Status: Disabled
	Watchdog Timer: Not Present

Handle 0x004B, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x004C, DMI type 187, 9 bytes
OEM-specific Type
	Header and Data:
		BB 09 4C 00 42 00 03 9B 02

Handle 0x004D, DMI type 187, 9 bytes
OEM-specific Type
	Header and Data:
		BB 09 4D 00 44 00 03 15 02

Handle 0x004E, DMI type 187, 9 bytes
OEM-specific Type
	Header and Data:
		BB 09 4E 00 46 00 03 9B 02

Handle 0x004F, DMI type 187, 9 bytes
OEM-specific Type
	Header and Data:
		BB 09 4F 00 48 00 03 15 02

Handle 0x0050, DMI type 131, 12 bytes
OEM-specific Type
	Header and Data:
		83 0C 50 00 01 01 02 01 09 06 40 01
	Strings:
		Intel_ASF_001
		Intel_ASF_001

Handle 0x0051, DMI type 136, 6 bytes
OEM-specific Type
	Header and Data:
		88 06 51 00 5A 5A

Handle 0x0052, DMI type 127, 4 bytes
End Of Table

roger@roger-desktop:~$

---

### Post by idoitprone on 2012-05-20
Are you running 12.04?

[https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394)

hibernate is disabled by default

---

### Post by RogerDavis on 2012-05-20
I'm using 10.04, trying to hang on until the recommended update time to go to 12.04.  However, I'm considering upgrading sooner.  I do have concerns that my present problems (hibernate doesn't work and network doesn't auto start) might carry through the update and contaminate the update, as I really want to NOT wipe the system.  So I'd rather:
1) Fix the hibernation
2) Fix the network doesn't auto start
3) Upgrade at the suggested time (June, was it?)
4) Not wipe the system
but
5) I might just make the jump soon and hope for the best.

------------
Found recommended update time:

Re: upgrade ubuntu 10.04 to 12.04
If you go into Software Sources, in the Updates tab, check the setting for upgrades (new version). Usually it would say Long Term releases.

That will make the Update Manager prompt you to upgrade to 12.04.1 once it's released in July.

When you are running the previous LTS (10.04), the update manager offers the upgrade to the next LTS only after the first .1 is released.

It's better to wait for some basic bugs to be solved in .1 anyway.

If you don't want to wait, you can start the update manager with the -d option and it should offer you upgrade to 12.04. You can do that in terminal with:
sudo update-manager -d
--------------------------

Thanks!

---

