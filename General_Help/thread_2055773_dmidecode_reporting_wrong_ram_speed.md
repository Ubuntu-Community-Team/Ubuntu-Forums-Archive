---
title: "dmidecode reporting wrong ram speed"
date: 2012-09-10
forum: General Help
---

### Post by Epodx64 on 2012-09-10
dmidecode and lshw are reporting that my ram is running at 400mhz but my bios and post show it running at 1153 
It's ddr3 Cosiar XMS3 2x2 1333mhz here's what dmidecode look like and lshw 
```
Handle 0x0019, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0018
        Error Information Handle: Not Provided
        Total Width: 256 bits
        Data Width: 204 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A0
        Bank Locator: Bank0/1
        Type: Unknown
        Type Detail: None
        Speed: 400 MHz
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0018
        Error Information Handle: Not Provided
        Total Width: Unknown
        Data Width: Unknown
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A1
        Bank Locator: Bank2/3
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0018
        Error Information Handle: Not Provided
        Total Width: 256 bits
        Data Width: 204 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A2
        Bank Locator: Bank4/5
        Type: Unknown
        Type Detail: None
        Speed: 400 MHz
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  

Handle 0x001C, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0018
        Error Information Handle: Not Provided
        Total Width: Unknown
        Data Width: Unknown
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A3
        Bank Locator: Bank6/7
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  


```
& lshw
```
*-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 204 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM 400 MHz (2.5 ns)
             physical id: 2
             slot: A2
             size: 2GiB
             width: 204 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3

```
Is this a problem with my bios not reporting the speeds? or is it accutally running at 400mhz? I think it's a problem reading the bios because I had it OC'd to 1300mhz w/ 8-8-8-24 timings 1.6v and my system was completely unstable.
and if this helps at all this is my hardware
Gigabyte GA-G41MT-S2PT F2 bios Intel Core 2 Duo E8400 slightly overclocked 357x9=  3213Ghz Ram is set to 1153mhz (is capable of 1333mhz) 8-8-8-24-1T Any ideas? I was thinking maybe it's because the Gigabyte boards use the dual-bios?

---

### Post by Epodx64 on 2012-09-10
bump! I really don't understand this I tried 2 different sticks of Ram Crucial 2Gb CL9 & Samsung Generic CL9 and it reported the Crucial as running 800mhz but the samsung at 400mhz now I have my corsairs back in and its reporting 400mhz my computers performance wouldn't suggest these are really running at 400mhz so I think it has to be a bios bug?

---

### Post by Epodx64 on 2012-09-10
Alright well turns out my Corsair XMS3 DDR3 Ram was bad I ran memtest86 on it after I started getting some strange errors random lock-ups dmesg reported really strange tables in e820 bios and the mtrr tables had several errors so I ran memtest86 and literally the second I started it it began to error 0% pass and 20,000 Errors at 4% I reset the bios to fail-safe same results manual adjusted the timings and voltage to reccomened settings and that still failed I tried losing the timings to a ridiculous 10-10-10-30 with 1.7v 1066mhz 1:1 cpu to clock ratio and still got the same results so I had to revert back to some ram I had lying a around a mixed match pair of 2Gb Crucial PC3-8500 CL7 and 2Gb HP/Samsung PC-10600 CL7 Ran memtest86 on it for a while no errors at all so atleast my dimm modules arent broken anyway here's the problem dmidecode is still reporting the wrong speeds now it has one dimm @ 800mhz and another dimm @ 400mhz and even stranger are the results from dmidecode --type memory at the top it says this
```
SMBIOS 2.4 present.

Handle 0x0005, DMI type 5, 24 bytes
Memory Controller Information
        Error Detecting Method: 8-bit Parity
        Error Correcting Capabilities:
                None
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 1024 MB
        Maximum Total Memory Size: 4096 MB
        Supported Speeds:
                Other
        Supported Memory Types:
                Other
        Memory Module Voltage: 5.0 V
        Associated Memory Slots: 4
                0x0006
                0x0007
                0x0008
                0x0009
        Enabled Error Correcting Capabilities:
                None

```
then the bottom reads like this
```
Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A0
        Bank Connections: 1
        Current Speed: Unknown
        Type: Other
        Installed Size: 2048 MB (Single-bank Connection)
        Enabled Size: 2048 MB (Single-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A1
        Bank Connections: 2
        Current Speed: Unknown
        Type: Unknown
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A2
        Bank Connections: 3
        Current Speed: Unknown
        Type: Other
        Installed Size: 2048 MB (Single-bank Connection)
        Enabled Size: 2048 MB (Single-bank Connection)
        Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A3
        Bank Connections: 4
        Current Speed: Unknown
        Type: Unknown
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x0018, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 32 GB
        Error Information Handle: Not Provided
        Number Of Devices: 4

Handle 0x0019, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0018
        Error Information Handle: Not Provided
        Total Width: 256 bits
        Data Width: 226 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A0
        Bank Locator: Bank0/1
        Type: Unknown
        Type Detail: None
        Speed: 800 MHz
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0018
        Error Information Handle: Not Provided
        Total Width: Unknown
        Data Width: Unknown
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A1
        Bank Locator: Bank2/3
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0018
        Error Information Handle: Not Provided
        Total Width: 2304 bits
        Data Width: 2178 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A2
        Bank Locator: Bank4/5
        Type: Unknown
        Type Detail: None
        Speed: 400 MHz
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  

Handle 0x001C, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0018
        Error Information Handle: Not Provided
        Total Width: Unknown
        Data Width: Unknown
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A3
        Bank Locator: Bank6/7
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer:  
        Serial Number:  
        Asset Tag:  
        Part Number:  

```
So it looks like it can't read the dimms and rates them as Unkown then for some reason rates the dimm modules at 800mhz & 400mhz but im not sure if those are even populated this is only a 2 dimm motherboard I think the Populated ones are unknown Anyone have any idea why dmidecode,smbios,lshw can't seem to read my ram? Do you think i'm at 1066mhz which my motherboard reports POST reports and Memtest86 Reports Both types speed 1066mhz,Dual-Channel,and CL7-7-7-20
obviously my ram is capable of running that speed I just want to confirm Kubuntu is running at that speed? any ideas?

---

### Post by Epodx64 on 2012-09-10
Seriously? nobody has any idea whats causing this? I'm starting wonder if it has something to do with it being 64bit I seem to recall some kind of memory bug early on before I was even using 64bit Iunno though Google has turned up nothing except a similar problem a slackware64 person had.

---

