---
title: "how can i make my 64bit system use more memory"
date: 2012-07-26
forum: General Help
---

### Post by firsttimeuser on 2012-07-26
Hello, i have ubuntu 12.04 64bit LTS loaded on my w530 laptop, the system has Quard core CPUs(8 all together), and it has 16G memory, 240G ssd.

I have one thing really bothers me now, no matter what I run, the memory utiliztion never exceed 2G, the memory history graphic almost always shows less then 2G usage.

My laptop gets really busy when I run GNS3 with 10+ olive instances runnig, all 8 cores will reach 100% usage during peak time, but even in that case ,the memory utilization still would be under 2G.

What I am doing wrong here? How can I get the system to use more memory, thanks

---

### Post by papibe on 2012-07-26
Hi firsttimeuser.

Could you post the result of these commands?
```
uname -a

sudo dmidecode -t memory

cat /proc/meminfo

dmesg | grep -i bios

free -m
```
Regards.

---

### Post by firsttimeuser on 2012-07-26
```
$ uname -a
Linux noname 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

$ sudo dmidecode -t memory
# dmidecode 2.11
SMBIOS 2.7 present.

Handle 0x0007, DMI type 16, 23 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 32 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x0008, DMI type 17, 34 bytes
Memory Device
	Array Handle: 0x0007
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: ChannelA-DIMM0
	Bank Locator: BANK 0
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: None
	Part Number: Not Specified
	Rank: Unknown
	Configured Clock Speed: Unknown

Handle 0x0009, DMI type 17, 34 bytes
Memory Device
	Array Handle: 0x0007
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8192 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelA-DIMM1
	Bank Locator: BANK 1
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1600 MHz
	Manufacturer: 029E
	Serial Number: 00000000
	Asset Tag: None
	Part Number: CMSX8GX3M1A1600C1 
	Rank: Unknown
	Configured Clock Speed: 1600 MHz

Handle 0x000A, DMI type 17, 34 bytes
Memory Device
	Array Handle: 0x0007
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: ChannelB-DIMM0
	Bank Locator: BANK 2
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: None
	Part Number: Not Specified
	Rank: Unknown
	Configured Clock Speed: Unknown

Handle 0x000B, DMI type 17, 34 bytes
Memory Device
	Array Handle: 0x0007
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8192 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelB-DIMM1
	Bank Locator: BANK 3
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1600 MHz
	Manufacturer: 029E
	Serial Number: 00000000
	Asset Tag: None
	Part Number: CMSX8GX3M1A1600C1 
	Rank: Unknown
	Configured Clock Speed: 1600 MHz
```


```
$ cat /proc/meminfo
MemTotal:       16092976 kB
MemFree:         3924996 kB
Buffers:          130020 kB
Cached:         10268344 kB
SwapCached:          152 kB
Active:          4923100 kB
Inactive:        6571008 kB
Active(anon):     962108 kB
Inactive(anon):   136432 kB
Active(file):    3960992 kB
Inactive(file):  6434576 kB
Unevictable:        1376 kB
Mlocked:            1376 kB
SwapTotal:      16429052 kB
SwapFree:       16427756 kB
Dirty:                36 kB
Writeback:             0 kB
AnonPages:       1097080 kB
Mapped:           181132 kB
Shmem:              2796 kB
Slab:             380808 kB
SReclaimable:     338252 kB
SUnreclaim:        42556 kB
KernelStack:        4320 kB
PageTables:        34220 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    24475540 kB
Committed_AS:    3627504 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      153824 kB
VmallocChunk:   34359576572 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:     5740032 kB
DirectMap2M:    10690560 kB
```



```
$ dmesg | grep -i bios
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000ccd80000 (usable)
[    0.000000]  BIOS-e820: 00000000ccd80000 - 00000000df69f000 (reserved)
[    0.000000]  BIOS-e820: 00000000df69f000 - 00000000df79f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000df79f000 - 00000000df7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000df7ff000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed08000 - 00000000fed09000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000041e000000 (usable)
[    0.000000] DMI: LENOVO 2436CTO/2436CTO, BIOS G5ET29WW (1.07 ) 05/25/2012
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.947395] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.618489] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.565476] thinkpad_acpi: ThinkPad BIOS G5ET29WW (1.07 ), EC unknown
```



```
$ free -m
             total       used       free     shared    buffers     cached
Mem:         15715      11885       3830          0        127      10027
-/+ buffers/cache:       1730      13984
Swap:        16043          1      16042
```





> **papibe said:**
> Hi firsttimeuser.

Could you post the result of these commands?
```
uname -a

sudo dmidecode -t memory

cat /proc/meminfo

dmesg | grep -i bios

free -m
```
Regards.

---

### Post by QIII on 2012-07-26
Are you saying you want the OS to demand of the software that it use more memory than its developers designed it to?

---

### Post by papibe on 2012-07-26
Thanks.

This is what I can see:
[LIST]
[*]It looks like you are you using 2 out of 4 mem slots.
[*]Each with a 8Gb mem stick.
[*]Adding the usable range addresses reported by the BIOS, you have aprox 15.67Gb of RAM available.
[*]At the moment you executed those commands, your system was using 11885Mb (11.6Gb). That's around 75% of your RAM being used.
[/LIST]
At this point, I don't seem to confirm that your system is just using 2Gb.

How do you reach that conclusion?
Where did you get the data?

Kind Regards.

---

### Post by CharlesA on 2012-07-26
It's using memory for caching.

```
[B]             total       used       free     shared    buffers     cached
Mem:         15715      11885       3830          0        127      10027[/B]
-/+ buffers/cache:       1730      13984
Swap:        16043          1      16042
```

---

### Post by firsttimeuser on 2012-07-26
The system monitor graphic shows around 2G utlization. 

I noticed now free -m says used 11885, so why the monitor graphic says 2G



> **CharlesA said:**
> It's using memory for caching.

```
[B]             total       used       free     shared    buffers     cached
Mem:         15715      11885       3830          0        127      10027[/B]
-/+ buffers/cache:       1730      13984
Swap:        16043          1      16042
```

---

### Post by CharlesA on 2012-07-26
1730mb ~= 2gb

---

### Post by Cheesemill on 2012-07-26
System Monitor doesn't count the cached memory as being in use.

---

### Post by CharlesA on 2012-07-26
> **Cheesemill said:**
> System Monitor doesn't count the cached memory as being in use.
Yep. Also that is completely normal.

Linux will use any extra memory for disk caching.

---

### Post by firsttimeuser on 2012-07-26
Thanks all!

> **CharlesA said:**
> Yep. Also that is completely normal.

Linux will use any extra memory for disk caching.

---

