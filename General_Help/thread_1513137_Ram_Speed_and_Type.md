---
title: "Ram Speed and Type"
date: 2010-06-19
forum: General Help
---

### Post by COKEDUDE on 2010-06-19
I'm curious how else I can check my Ram Speed and Type besides using this command. I'm hoping the type is wrong because I paid for ddr2 and the label on the ram is even says ddr2. 
```
sudo dmidecode --type 17
```
[http://www.cyberciti.biz/faq/check-ram-speed-linux/](http://www.cyberciti.biz/faq/check-ram-speed-linux/)
```
~ $ sudo dmidecode --type 17
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x1100, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM_B
	Bank Locator: Not Specified
	Type: DDR
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: AD00000000000000
	Serial Number: 00001145
	Asset Tag: 410828
	Part Number: HYMP125S64CP8-Y5  

Handle 0x1101, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM_A
	Bank Locator: Not Specified
	Type: DDR
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: AD00000000000000
	Serial Number: 00001009
	Asset Tag: 410828
	Part Number: HYMP125S64CP8-Y5  

```

---

### Post by dino99 on 2010-06-19
DDR is a generic naming for all DDR type

---

### Post by buellman on 2010-06-19
Don't know if it helps but this is my output:

```
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x003D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x003B
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 72 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM_A1
	Bank Locator: BANK0
	Type: **DDR2**
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0

Handle 0x003F, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x003B
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 72 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM_B1
	Bank Locator: BANK1
	Type: **DDR2**
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

```
Greets. Buellman

---

### Post by dcstar on 2010-06-19
> **buellman said:**
> Don't know if it helps but this is my output:

```
# dmidecode 2.9
**SMBIOS 2.5** present.
........

```


The different SMBIOS versions will provide different info, along with what the MB and actual RAM modules also provide.

These things can only be indicative and really should not be taken as gospel.

My system has DDR2 modules but they are reported as "Type: Unknown".

---

### Post by cascade9 on 2010-06-19
My output from 

dmidecode --type 17 (run as su, not sudo, and edited to remove the output for bands 2+3 as they are empty) 


```
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x002C, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x002A
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 72 bits
        Size: 1024 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM0
        Bank Locator: BANK0
        Type: DDR2
        Type Detail: Synchronous
        Speed: 400 MHz (2.5 ns)
        Manufacturer: Manufacturer0
        Serial Number: SerNum0
        Asset Tag: AssetTagNum0
        Part Number: PartNum0

Handle 0x002E, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x002A
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 72 bits
        Size: 1024 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM1
        Bank Locator: BANK1
        Type: DDR2
        Type Detail: Synchronous
        Speed: 400 MHz (2.5 ns)
        Manufacturer: Manufacturer1
        Serial Number: SerNum1
        Asset Tag: AssetTagNum1
        Part Number: PartNum1

```

You might find that lshw will give you what you want, here is my output (run as su again, not sudo, and just the memory output pasted here, and edited again tro to remove output for empty RAM slots)- 

```
*-memory
          description: System Memory
          physical id: 2a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 400 MHz (2.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 400 MHz (2.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
```

BTW, AFAIK that will show you the speed the RAM is running at, not its rated speed. [FONT=monospace]
[/FONT]

---

### Post by 3rdalbum on 2010-06-19
The RAM is running at 667Mhz, which makes it DDR2. I don't believe you can fit a DDR1 module into a DDR2 slot anyway.

---

### Post by COKEDUDE on 2010-06-22
> **3rdalbum said:**
> The RAM is running at 667Mhz, which makes it DDR2. I don't believe you can fit a DDR1 module into a DDR2 slot anyway.

Even on a laptop? I thought the pin sizes were the same.

---

### Post by yetiman64 on 2010-06-22
2 attached pictures are of ddr1 and ddr2 laptop RAM. Even if the pin count is the same the "notch" position near the pins stop them from being interchangable. Hope this helps.

---

### Post by cascade9 on 2010-06-22
> **yetiman64 said:**
> 2 attached pictures are of ddr1 and ddr2 laptop RAM. Even if the pin count is the same the "notch" position near the pins stop them from being interchangable. Hope this helps.

True, and the notches are also how they made sure that desktop DDR2 wont get shoved into a DDR3 slot (and vice versa)

---

### Post by Zerocool Djx on 2010-06-22
The use of a tack hammer might come in handy here.. ;)

---

### Post by pricetech on 2010-06-22
Or a hacksaw.

Best way to determine what RAM you have is to either inspect it visually or check the BIOS.

---

### Post by COKEDUDE on 2010-06-24
> **yetiman64 said:**
> 2 attached pictures are of ddr1 and ddr2 laptop RAM. Even if the pin count is the same the "notch" position near the pins stop them from being interchangable. Hope this helps.

I use the one on the right. I remember the notch being close to the left side.

---

### Post by yetiman64 on 2010-06-25
> **COKEDUDE said:**
> I use the one on the right. I remember the notch being close to the left side.

If so, then you're using **DDR2** laptop RAM despite what the terminal output **indicates**.

I'll quote what dcstar said from post #4. 
> The different SMBIOS versions will provide different info, along with  what the MB and actual RAM modules also provide.

These things can only be indicative and really should not be taken as  gospel.

My system has DDR2 modules but they are reported as "Type: Unknown".I'm sure this explains what you originally noticed.
> I'm hoping the type is wrong because I paid for ddr2 and the label on  the ram is even says ddr2. I'm very sure the type is wrongly indicated and you are using DDR2 RAM.

---

