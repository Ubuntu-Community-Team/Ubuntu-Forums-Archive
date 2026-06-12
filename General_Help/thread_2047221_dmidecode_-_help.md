---
title: "dmidecode - help"
date: 2012-08-24
forum: General Help
---

### Post by cannon_dt on 2012-08-24
Hello!
I was going to upgrad my RAM from 4 to 8 GB and for this I wanted to know the RAM type I got. So I got down to using dmidecode but the output says it is Type:Other instead of DDR3 or DDR2. Can anyone help out here?

Ouput was :

```
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0039, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0037
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: Other
	Type Detail: Synchronous
	Speed: 1333 MHz (0.8 ns)
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0

Handle 0x003B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0037
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: Other
	Type Detail: Synchronous
	Speed: 1333 MHz (0.8 ns)
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

Handle 0x003D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0037
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK2
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Manufacturer2
	Serial Number: SerNum2
	Asset Tag: AssetTagNum2
	Part Number: PartNum2

Handle 0x003F, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0037
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM3
	Bank Locator: BANK3
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Manufacturer3
	Serial Number: SerNum3
	Asset Tag: AssetTagNum3
	Part Number: PartNum3


```

lshw -short -C memory also gives no DDR info

```
H/W path         Device      Class       Description
====================================================
/0/0                         memory      64KiB BIOS
/0/4/5                       memory      256KiB L1 cache
/0/4/6                       memory      1MiB L2 cache
/0/4/7                       memory      6MiB L3 cache
/0/37                        memory      4GiB System Memory
/0/37/0                      memory      2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/37/1                      memory      2GiB DIMM Synchronous 1333 MHz (0.8 ns)
/0/37/2                      memory      DIMM [empty]
/0/37/3                      memory      DIMM [empty]

```

Any clarification would be greatly appreciated.

Thanks,
Ananth

---

### Post by dcstar on 2012-08-25
> **cannon_dt said:**
> Hello!
I was going to upgrad my RAM from 4 to 8 GB and for this I wanted to know the RAM type I got.


Open the machine and look for yourself.

---

### Post by codemaniac on 2012-08-25
dmidecode is sometimes inaccurate in reporting memory information .

[http://www.linuxtoday.com/infrastructure/2004113000626OSHWHL](http://www.linuxtoday.com/infrastructure/2004113000626OSHWHL)
It gives you the DMI information as reported by the BIOS.

---

### Post by coldcritter64 on 2012-08-25
OP this is a visual reference for you if you do open the machine and look. Note the position of the notch between the pins to tell which yours is.

ddr2
[ [IMG]http://dl.dropbox.com/u/30874719/UF/ddr2-ram_thm.jpg[/IMG]]("http://dl.dropbox.com/u/30874719/UF/ddr2-ram.jpg")
ddr3
[ [IMG]http://dl.dropbox.com/u/30874719/UF/ddr3-ram_thm.jpg[/IMG] ]("http://dl.dropbox.com/u/30874719/UF/ddr3-ram.jpg")

---

### Post by cannon_dt on 2012-08-25
@dcstar
I was hoping to avoid that and use just the command line.

@codemaniac
Thanks for the link. I guess I got no choice other than to confirm it visually.

@coldcritter64
Thanks for the visuals, will come in handy when I am going to have to take dcstar's advice

---

