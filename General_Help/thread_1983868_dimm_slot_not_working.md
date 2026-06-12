---
title: "dimm slot not working"
date: 2012-05-20
forum: General Help
---

### Post by jakeshammer on 2012-05-20
Hi, I'm a relative neewbie and this is my first post on the forum, all problems I've had before have been resolved by going through general help and finding similar problems and the solutions. But I'm completely stuck at the moment after having added 2Gb of extra ram to my system which is completely unrecognized. Have tried lots of options replacing and switching modules around. Both modules work in Bank1 but nothing shows up in Bank2. It's a Compaq Presario CQ3505,64 bit, which is supposed to be capable of using 4Gb of ram. Any help or suggestions would be appreciated. Can provide more system info if needed. Thank You.

---

### Post by HiImTye on 2012-05-20
to start off, open a terminal (ctrl+alt+T) and type:
```
uname -m; free -m
```
and paste the output here

---

### Post by beboylips on 2012-05-20
Are you running a 64-bit version of Ubuntu?
How many RAM slots does your computer have? How many are taken? By what ram sticks? In which slots did you plug your ram sticks in?

What RAM do you have and what RAM did you use to upgrade? Size, company name, frequency?

-Beboy

---

### Post by jakeshammer on 2012-05-20
Thanks for the reply HilmTye 

output:     

      total        used       free     shared    buffers     cached
Mem:   1968        1721        246          0         17       1029
-/+ buffers/cache:   674       1294
Swap:        4020    82        3938

---

### Post by jakeshammer on 2012-05-20
> **HiImTye said:**
> to start off, open a terminal (ctrl+alt+T) and type:
```
uname -m; free -m
```
and paste the output here

x86_64
             total       used       free     shared    buffers     cached
Mem:          1968       1721        246          0         17       1029
-/+ buffers/cache:        674       1294
Swap:         4020         82       3938
mike@mike-WE144AA-ABU-CQ5305UK:~$

---

### Post by jakeshammer on 2012-05-20
> **beboylips said:**
> Are you running a 64-bit version of Ubuntu?
How many RAM slots does your computer have? How many are taken? By what ram sticks? In which slots did you plug your ram sticks in?

What RAM do you have and what RAM did you use to upgrade? Size, company name, frequency?

-Beboy

Yes running 64bit ubuntu, two slots, 2b, crucial, is the frequency 1333MT/s?, sorry not to technical.

---

### Post by jakeshammer on 2012-05-20
after typing dmidecode -t 17 output shows

Handle 0x0010, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x000E
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: DDR3
	Type Detail: Synchronous
	Speed: 800 MHz
	Manufacturer: Micron        
	Serial Number: E75DEA51
	Asset Tag: AssetTagNum0
	Part Number: 16JTF25664AZ-1G4G1
	Rank: Unknown

Handle 0x0011, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x000E
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: Unknown
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer01
	Serial Number: SerNum01
	Asset Tag: AssetTagNum1
	Part Number: ModulePartNumber01
	Rank: Unknown

---

### Post by beboylips on 2012-05-20
put the new ram into another slot if possible

---

### Post by jakeshammer on 2012-05-20
> **beboylips said:**
> put the new ram into another slot if possible

I have tried swapping both rams and they both work on their own in slot1 . I've taken them out and tried just one in slot2 which just got beeps from the computer and no boot screen. so as far as I can think there is a problem somehow with that slot. I have swapped them over together but still only the one slot is recognized.

---

### Post by beboylips on 2012-05-20
> **jakeshammer said:**
> I have tried swapping both rams and they both work on their own in slot1 . I've taken them out and tried just one in slot2 which just got beeps from the computer and no boot screen. so as far as I can think there is a problem somehow with that slot. I have swapped them over together but still only the one slot is recognized.

I am thinking its a channel problem. I'm guessing you have dual-channel RAM? If yes, you have to place the sticks on their own memory channels. 

So physically, it would look like this:

A1: 2 GB RAM stick
A2: EMPTY
B1: 2 GB RAM stick
B2: EMPTY

That's how the sticks should be placed.

Let me know if that works.

-Beboy

---

### Post by jakeshammer on 2012-05-20
I'm not sure there only seems to be two available slots? I am thinking although it is a relatively new computer that there is a problem with dimm2. How that could be rectified though I don't have the first clue. Many thanks anyway for the help beboy! Just one more thing would it be possible to put 4gb of ram just in the one slot?

---

### Post by beboylips on 2012-05-20
Both sticks from the same company? Crucial ?

---

### Post by jakeshammer on 2012-05-20
one was bought from crucial but the make is micron, the same as the other one.
The one from crucial is micron serial no 16JTF2566AZ-1G4G1 and the one already installed was a micron serial no 16JTF2566AZ-1G4F1

---

### Post by kurja on 2012-05-21
Just by that either memory works in first slot but nothing ever put in in the second slot works, I'd be inclined to guess that there's a hardware problem with your motherboard and if that's the case you can really fix it only by changing the motherboard... But first do find the motherboard's user manual and read carefully what it says about memory configuration.

Oh - by the way - after adding that memory in bank 2 you DID enter bios setup, save and exit? If both chips are identical your symptoms might be caused by not doing that, if your mobo requires that procedure to complete a RAM upgrade and afaik most motherboards do.

---

### Post by jakeshammer on 2012-05-21
Yes I think your right there's nothing more I can do, I think that there's an problem with the motherboard. Many thanks anyway for your help.

---

### Post by kurja on 2012-05-23
> **jakeshammer said:**
> Yes I think your right there's nothing more I can do, I think that there's an problem with the motherboard. Many thanks anyway for your help.

just to doublecheck - you did notice this?

> Oh - by the way - after adding that memory in bank 2 you DID enter bios  setup, save and exit? If both chips are identical your symptoms might be  caused by not doing that, if your mobo requires that procedure to  complete a RAM upgrade and afaik most motherboards do.

---

### Post by jakeshammer on 2012-05-25
Yes kurja have enter bios set up at boot after reinserting, still saying mem,ory bank two Not Installed,

---

