---
title: "dmidecode and lshw problems"
date: 2009-12-27
forum: General Help
---

### Post by 5nak3 on 2009-12-27
Hi all, 

Got my hands on an older (2000 or there abouts) PC and it only has 512mb ram installed. Works well with Ubuntu but multitasking is a pain.

I want to upgrade the ram, but since Windows will not recognize the PCs network adapters I cannot use the Crucial tool to check what ram I can upgrade to.

After much searching I found Linux had two commands build in lshw and dmidecode. But I am a bit lost when it comes to reading the output and would love some help.

lshw:

>  *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 4224MiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 128MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 4GiB
             width: 256 bits
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3


dmidecode:
> Memory Controller Information
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
		DIMM
		SDRAM
	Memory Module Voltage: 5.0 V
	Associated Memory Slots: 4
		0x0006
		0x0007
		0x0008
		0x0009
	Enabled Error Correcting Capabilities:
		None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 0
	Current Speed: Unknown
	Type: Other
	Installed Size: 128 MB (Single-bank Connection)
	Enabled Size: 128 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2
	Current Speed: Unknown
	Type: Other Parity
	Installed Size: 4096 MB (Single-bank Connection)
	Enabled Size: 4096 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A2
	Bank Connections: None
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A3
	Bank Connections: None
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK



Am I correct in saying that the motherboard has 4 slots for ram, each with a maximum 1gb capacity and thus a 4gb capacity in total?

Also could someone actually point out where the output says what ram is installed. I know the installed ram is 2 x 256mb sticks making a total of 512mb (I opened the case), but the outputs do not show this...

Many thanks!

---

### Post by Parroose on 2010-01-22
It looks like both utilities are reporting incorrectly on the installed memory. They are saying you have a 128 MB module in the first slot and a single 4096 MB module in the second slot...

Both lshw and dmidecode can't really know what's in there if the manufacturers are reporting wrong information. I'm afraid you'll have to open the system and read the memory specs on the DIMMs themselves. If you're lucky, there'll be some information printed on a lable on the DIMMs.

If not, you should take the manufacturer and model of your motherboard and check at the manufacturer's website. Or just let me know it and I'll help you locating it.

---

