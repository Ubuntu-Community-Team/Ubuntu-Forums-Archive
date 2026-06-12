---
title: "mysterious? POST code error beeps"
date: 2010-04-15
forum: General Help
---

### Post by rev9ers on 2010-04-15
After powering on but before booting the initial splash screen my computer emits a succession of three-beep sequences. The beeping continues until the boot process begins to load Ubuntu, after which my computer appears to run fine. 

After looking into possible explanations for the mysterious 3-beep sequence a little bit it seems that it may be a POST code error or something along those lines. That's when the information loses me.

Can anyone help me diagnose and remedy what could be going on with my computer? I am not totally ignorant of using linux but am still a novice so any help at all is most appreciated.

I've attached some screenshots of the sysinfo if it helps:

---

### Post by akakingess on 2010-04-15
What you really need to find out are the HW details of the motherboard, and a manual for it if you have it. If not look up the manual for that motherboard on the net and it will have near the back (usually an Appendix of some sort) an explanation of the different beep sequences. Every error has it's own sequence, i.e. 2 beeps, than 1 beep, than 2 beeps again could mean it's having RAM issues and you may want to do a RAM test from within the BIOS. That's just an example, so try to find the manual for your actual Motherboard even if it means opening up the computer and looking ;)  Good Luck and I will check back in the morning to see what you have found.

---

### Post by rev9ers on 2010-04-15
> **akakingess said:**
> What you really need to find out are the HW details of the motherboard, and a manual for it if you have it. If not look up the manual for that motherboard on the net and it will have near the back (usually an Appendix of some sort) an explanation of the different beep sequences. Every error has it's own sequence, i.e. 2 beeps, than 1 beep, than 2 beeps again could mean it's having RAM issues and you may want to do a RAM test from within the BIOS. That's just an example, so try to find the manual for your actual Motherboard even if it means opening up the computer and looking ;)  Good Luck and I will check back in the morning to see what you have found.

OK. I have an Intel DB43LD motherboard and the Technical Product Specifications manual associates the three beep sequence with a memory error. Does that mean my RAM is going bad? 

And is it possible to find out how much of the power supply's capacity is being utilized in order to determine whether peripherals may be added to the existing unit?
Thanks.

---

### Post by akakingess on 2010-04-15
To the 2nd question, that is going to have to be answered by either the manual or asking the manufacturer online, because there is a chance that you have to upgrade your power supply depending on what you plan on adding to the computer. To the 1st point, I would definitely boot into your BIOS (usually accomplished by pressing ESC, F10, or F12, etc. while booting) and do a full test on the RAM (memory is what the BIOS may call it, but if that is what the beep sequence is pointing to, than you definitely need to test it.

---

### Post by rev9ers on 2010-04-15
I can get into the BIOS settings by pressing F2 while the splash screen is up, but I do not see how to test the memory from there, although I did figure out how to have the computer turn itself on!

Thanks for your help, by the way.

---

### Post by akakingess on 2010-04-15
> **rev9ers said:**
> I can get into the BIOS settings by pressing F2 while the splash screen is up, but I do not see how to test the memory from there, although I did figure out how to have the computer turn itself on!

Thanks for your help, by the way.

No need for the thanks, thats what I love about this community, we are practically family, so just consider me helping a brother out. Now, there should be a way to test your memory within the BIOS, so I am going to go into mine and see if I might be able to shed some light on the subject. Hang in there, we will get you taken care of. On another note, have you just added some RAM? Also, would you feel comfortable enough to open the computer and through trial and error take out one piece of RAM and start up the computer to see if you get the beeps, if not, then put it back in and try taking out the other, and so on? Just another way of narrowing down the problem.

---

### Post by rev9ers on 2010-04-15
Only one stick o' RAM.

---

### Post by akakingess on 2010-04-15
Okay, now I am getting close to the end of my known options, I couldn't find the memtest in my own BIOS (I blame old age and grey hair even though I'm only 33), but the next thing that I could think of is creating a Live CD (you may already have one, if that's what you used to install Ubuntu) and when you boot from that CD there should be an option to do a 'MEMTEST' or something like that, which should test out the RAM on your motherboard. Other than trying that, I may need to continue this tomorrow and do some research online, by the way, would you mind posting what kind of motherboard it is and specifically what BIOS it is running if you can find that out easily, if not, don't worry, just try the LiveCD troubleshooting first and let's see how that goes and I will be online a little longer, but most will have to wait til tomorrow. Sorry I couldn't be of more assistance thus far, but hopefully we will get you taken care of.

---

### Post by rev9ers on 2010-04-15
Still working on doing the MEMTEST, but here is output regarding my BIOS. The Motherboard is an Intel Desktop Board DB43LD.

> anthony@anthony-desktop:~$ sudo dmidecode -t 0
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Intel Corp.
	Version: LDB4310H.86A.0030.2009.0410.1420
	Release Date: 04/10/2009
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

---

### Post by rev9ers on 2010-04-15
And here's output about the motherboard:

>  anthony@anthony-desktop:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: Intel Corporation
	Product Name: DB43LD
	Version: AAE60577-201
	Serial Number: BTLD9350018H
	Asset Tag: To be filled by O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To be filled by O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0024, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description:  Intelr 82567LM Gigabit Ethernet Device  

Handle 0x0025, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description:  Intelr High Definition Audio Device     

Handle 0x0026, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Disabled
	Description:  Device Disabled

---

### Post by rev9ers on 2010-04-15
And... here's info about the memory:

>  anthony@anthony-desktop:~$ sudo dmidecode -t memory
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x002A, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 8 GB
	Error Information Handle: 0x002B
	Number Of Devices: 2

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002A
	Error Information Handle: 0x002E
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: CHANNEL A
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0

Handle 0x0033, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002A
	Error Information Handle: 0x0034
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: CHANNEL B
	Bank Locator: BANK2
	Type: Unknown
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer2
	Serial Number: SerNum2
	Asset Tag: AssetTagNum2
	Part Number: PartNum2

---

### Post by akakingess on 2010-04-15
OK, just got this message, so before I start doing the research on it, it looks like you have 2 slots available for the RAM but are just using 1 of them, right?  Just for giggles, if you don't mind, try switching the RAM over to the other slot and see if the beeping persists. Of course, if there are even worse problems, it's just a matter of putting it back into the original slot and we will continue to research.

---

