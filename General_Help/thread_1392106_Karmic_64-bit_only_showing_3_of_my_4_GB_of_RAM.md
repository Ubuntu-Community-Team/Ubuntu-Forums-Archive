---
title: "Karmic 64-bit only showing 3 of my 4 GB of RAM"
date: 2010-01-27
forum: General Help
---

### Post by steve_c on 2010-01-27
Have a nice Karmic x86-64 install.
```
$ uname -a
Linux onyx 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 **x86_64** GNU/Linux
```
Have 4 GB of RAM installed.
```
$ sudo dmidecode --type 17
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x1100, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	**Size: 1024 MB**
	Form Factor: DIMM
	Set: None
	Locator: DIMM_1
	Bank Locator: Not Specified
	Type: DDR
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: 7F98000000000000
	Serial Number: 682ED931
	Asset Tag: Not Specified
	Part Number:                   

Handle 0x1101, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	**Size: 1024 MB**
	Form Factor: DIMM
	Set: None
	Locator: DIMM_3
	Bank Locator: Not Specified
	Type: DDR
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: 7F98000000000000
	Serial Number: BE393054
	Asset Tag: Not Specified
	Part Number:                   

Handle 0x1102, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	**Size: 1024 MB**
	Form Factor: DIMM
	Set: None
	Locator: DIMM_2
	Bank Locator: Not Specified
	Type: DDR
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: 7F98000000000000
	Serial Number: 6534B36C
	Asset Tag: Not Specified
	Part Number:                   

Handle 0x1103, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	**Size: 1024 MB**
	Form Factor: DIMM
	Set: None
	Locator: DIMM_4
	Bank Locator: Not Specified
	Type: DDR
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: 7F98000000000000
	Serial Number: BE393154
	Asset Tag: Not Specified
	Part Number:
```

Yet for whatever reason, Karmic only sees 3 GB in everything -- top, /proc/meminfo, etc.
```
$ free -m
             **total**       used       free     shared    buffers     cached
Mem:          **3010**       2540        470          0         29        340
-/+ buffers/cache:       2169        840
Swap:         6236       1222       5013
```

Any thoughts/suggestions?

---

### Post by t4thfavor on 2010-01-27
Do you have an intel GMA chipset? If so your stuck, I have a GMA whatever chipset, and an x64 core 2 duo which will only ever use 3069MB due to limitations of the chipset, and other devices that use memory below 4gb.

It will also happen if you have a video card with shared memory.

---

