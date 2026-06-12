---
title: "Ubuntu not recognizing ALL my new ram..."
date: 2009-09-11
forum: General Help
---

### Post by thegutterpoet on 2009-09-11
I have just upgraded my RAM from 1GB, to 2 X 2GB...When I booted my laptop back into life after the installation of the ram slices, Bios told me i now had 2.8gb RAM...I said FINE...Save...then the laptop restarted, I loaded in ubuntu...checked to see if it could use the full 4gb, but no...it only wants to play with 2.8gb.

 *-firmware              
       description: BIOS
       vendor: Hewlett-Packard
       physical id: 0
       version: 68TT2 Ver. F.06 (12/21/2006)
       size: 128KiB
       capacity: 960KiB
       capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: Internal L1 Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: burst internal write-back unified
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: Internal L2 Cache
       size: 256KiB
       capacity: 256KiB
       capabilities: burst external write-back unified
  *-memory
       description: System Memory
       physical id: a
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: SODIMM Synchronous 667 MHz (1.5 ns)
          product: VS2GSDS667D2
          vendor: 7F7F9E0000000000
          physical id: 0
          serial: 00000000
          slot: DIMM #1
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:1
          description: SODIMM Synchronous 667 MHz (1.5 ns)
          product: VS2GSDS667D2
          vendor: 7F7F9E0000000000
          physical id: 1
          serial: 00000000
          slot: DIMM #2
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)

Where am I going wrong??? 

One of the reasons I moved over to linux was because a friend told me that Windows would not recognize more than around 3gb of RAM...

Please help!

---

### Post by falconindy on 2009-09-11
If your BIOS only recognizes 2.8gb, then you need to start there (in the BIOS) if there's hope of getting this fixed. What's your motherboard/CPU? Have you downloaded the latest BIOS file for your motherboard?

I don't know exactly what your friend told you, but the amount of RAM you can use is typically more related to your hardware than your OS. Even 32-bit WindowsXP with PAE can see past the 2^32 mark as long as your BIOS sees it.

---

### Post by thegutterpoet on 2009-09-11
Are there any terminal commands which would give me the information you are referring to, mate???

An NO, I have not updated anything to do with my bios since I got the laptop last year.

I used this terminal command : sudo dmidecode, and got the following gibberish:>

# dmidecode 2.9
SMBIOS 2.4 present.
23 structures occupying 1029 bytes.
Table at 0x000FBBE2.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: 68TT2 Ver. F.06
    Release Date: 12/21/2006
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 1024 kB
    Characteristics:
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        3.5"/720 KB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        Smart battery is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 15.6
    Firmware Revision: 64.21

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Hewlett-Packard
    Product Name: HP Compaq nx6325 (RE950PA#ABG)
    Version: F.06
    Serial Number: CNU707065G
    UUID: 468259AB-9FD7-DD11-069C-6D990E02C129
    Wake-up Type: Power Switch
    SKU Number: RE950PA#ABG
    Family: 103C_5336AN

Handle 0x0040, DMI type 126, 33 bytes
Inactive

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Hewlett-Packard
    Product Name: 30B0
    Version: KBC Version 40.15
    Serial Number: Not Specified

Handle 0x0003, DMI type 3, 13 bytes
Chassis Information
    Manufacturer: Hewlett-Packard
    Type: Notebook
    Lock: Not Present
    Version: Not Specified
    Serial Number: CNU707065G
    Asset Tag: CNU707065G
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: External Interface Enabled

Handle 0x0041, DMI type 126, 32 bytes
Inactive

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: U10
    Type: Central Processor
    Family: Athlon 64
    Manufacturer: AMD(R)
    ID: 82 0F 04 00 FF FB 8B 17
    Signature: Family 15, Model 72, Stepping 2
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        MMX (MMX technology supported)
        FXSR (Fast floating-point save and restore)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        HTT (Hyper-threading technology)
    Version: AMD Turion(tm) 64 X2 Mobile TL-50              
    Voltage: 1.1 V
    External Clock: 200 MHz
    Max Speed: 1600 MHz
    Current Speed: 1600 MHz
    Status: Populated, Enabled
    Upgrade: None
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Internal L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 128 KB
    Maximum Size: 128 KB
    Supported SRAM Types:
        Burst
    Installed SRAM Type: Burst
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Internal L2 Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: External
    Installed Size: 256 KB
    Maximum Size: 256 KB
    Supported SRAM Types:
        Burst
    Installed SRAM Type: Burst
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x0007, DMI type 9, 13 bytes
System Slot Information
    Designation: PC CARD-Slot 0
    Type: 32-bit PC Card (PCMCIA)
    Current Usage: Available
    Length: Short
    ID: Adapter 0, Socket 0
    Characteristics:
        5.0 V is provided
        3.3 V is provided
        PC Card-16 is supported
        Cardbus is supported
        PME signal is supported

Handle 0x0008, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description: 128

Handle 0x0009, DMI type 11, 5 bytes
OEM Strings
    String 1: [www.hp.com](www.hp.com)
    String 2: ABS 70/71 79 7A 7B 7C

Handle 0x000A, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: No Error
    Number Of Devices: 2

Handle 0x000B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM #1
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 7F7F9E0000000000
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number: VS2GSDS667D2      

Handle 0x000C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM #2
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 7F7F9E0000000000
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number: VS2GSDS667D2      

Handle 0x000D, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 4 GB
    Physical Array Handle: 0x000A
    Partition Width: 0

Handle 0x000E, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x000B
    Memory Array Mapped Address Handle: 0x000D
    Partition Row Position: 1

Handle 0x000F, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00080000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x000C
    Memory Array Mapped Address Handle: 0x000D
    Partition Row Position: 2

Handle 0x0010, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

Handle 0x0085, DMI type 133, 34 bytes
OEM-specific Type
    Header and Data:
        85 22 85 00 01 A0 0F 50 0E 02 08 00 00 73 00 1B
        00 99 2B E9 F7 5C 2B 02 C0 00 00 00 7E 0E 70 0E
        93 0E
    Strings:
        32210 08/13/2005
        HP                

Handle 0x0086, DMI type 126, 34 bytes
Inactive

Handle 0x0011, DMI type 144, 26 bytes
OEM-specific Type
    Header and Data:
        90 1A 11 00 02 00 03 00 02 00 07 00 00 00 02 00
        00 00 00 00 02 00 06 00 00 00

Handle 0x0012, DMI type 127, 4 bytes
End Of Table

---

### Post by dcstar on 2009-09-11
> **weedguru said:**
> I have just upgraded my RAM from 1GB, to 2 X 2GB...When I booted my laptop back into life after the installation of the ram slices, Bios told me i now had 2.8gb RAM...I said FINE...Save...then the laptop restarted, I loaded in ubuntu...checked to see if it could use the full 4gb, but no...it only wants to play with 2.8gb.

 *-firmware              
       description: BIOS
       vendor: **Hewlett-Packard**
........

Where am I going wrong??? 

One of the reasons I moved over to linux was because a friend told me that Windows would not recognize more than around 3gb of RAM...

Please help!

Go to the HP website and find out the MAXIMUM RAM it says you laptop can use.

This is not what can be installed, it is what the system has been designed to **use**.

---

### Post by mrbiggbrain on 2009-09-11
If your running a 32-bit OS

2.8gb = 

4.0GB - ~750mb used to reference cache, and memory space of various parts of the board and computer, (drives, bios, sound cards, on board video, etc)

are you running a video card of some sort, maybe a 512 or something of the likes. you have to remember that 32-bit processors can address 4gb of total memory, not just ram, it has to set aside address space for your sound card, graphics card(s), physx cards, and any other device you have that takes memory (even ethernet cards, antyhing with any memory)

---

### Post by thegutterpoet on 2009-09-11
HP tells me the MAXIMUM RAM I can use is 4gb.

Do I need to update my bios?? Or go into BIOS to try to change the settings???

my current motherboard and bios information:>
hewlett packard
model 30b0     KBC version 40.15
cipset ATI Xpress 200 (RS480)   REV 10
southbridge ATI SB400
LPCIO   SMSC    SMSC

BIOS
Brand Hewlett Packard
Version 68tt2 ver.f.06
date 12/21/2006

I just check in BIOs and it assured me that it knew 4096bytes were installed as memory. I did  memory check also, in bios, and no problems found...so BIOS knows I have 4096...why does ubuntu only say, on system information, that I have 2.8gb RAM????

---

### Post by QIII on 2009-09-12
The 32  bit OS can see more than 4GB of memory if PAE (Physical Address Extension) is enabled.  The limit theoretically goes up to 64GB, but performance will be questionable.

PAE is not enabled in the kernel you installed.   You can install the 32 bit server kernel, in which PAE is enabled. But that might be a risky undertaking for someone new to Linux.

But you will still probably lose some of your available RAM to "memory holes" for some of your hardware that will grab what it thinks it needs.  Depending on your BIOS you may be able to set a limit, but you might also affect the performance of your hardware.

What are the processor specs?  (Sorry if you posted that and I missed it.)

If your processor architecture is 64 bit, you may be better off doing a fresh install of the 64 bit version and not worrying about installing a new kernel just for PAE.

---

### Post by thegutterpoet on 2009-09-12
I am unsure as to the clear thrust of your answer, mate...but you appear to know a lot more than me about my hardware, so please...explain more if possible.

My processor is a AMD turion 64 X2 1.6ghz (TL-50)

And I installed the latest version of ubuntu, i think the 64 bit  version if there was one available...

ubuntu...9.04 jaunty
kernel linux 2.6.28-15-generic
gnome 2.26.1

---

### Post by shae on 2009-09-12
You should install the Server kernel from synaptic because it supports 32 bit PAE and will see and use all your ram.

---

### Post by QIII on 2009-09-12
You have a 64 bit processor.  We'll skip what that means technically.
 
What it means practically for you is that you can use the 64 bit version of Ubuntu and not worry about PAE to access nearly all of you RAM, less whatever the rest of your hardware reserves.  Typically you will lose between 0.3 and 0.5GB to what is known as "memory holes" -- the memory reserved by those devices.  But your BIOS ***may  ***allow you to limit the amount reserved.

You can tell if you have the 32 bit or 64 bit version of Ubuntu installed by using the termial and typing

```
uname -m
```post the results back here.


(BTW ... Just for grins and giggles, a 64 bit operating system, not accounting for what you are limited to by your motherboard, can theoretically address 2^64bytes of RAM, which is 16 Exabytes.  That's about what you can fit on 16.8 million 1TB hard drives...)

---

### Post by QIII on 2009-09-12
> **shae said:**
> You should install the Server kernel from synaptic because it supports 32 bit PAE and will see and use all your ram.

Perhaps not the most understandable route for a new user.

---

### Post by Irvine_himself on 2009-09-12
> **shae said:**
> You should install the Server kernel from synaptic because it supports 32 bit PAE and will see and use all your ram.

Why would he want to install the 32 bit server kernel?

He has a 64 bit bus, which supports googles and googles of ram. The only thing he needs to do is check that he is using the 64 bit Jaunty.

---

### Post by QIII on 2009-09-12
+1

16 exabytes.

How much info is there on the entire web?  I've hear that all the information in THE WORLD is on the order of several thousand petabytes.  1 exabyte is roughly a thousand petabytes.

Is there even a total of 16 exabytes of information in the world?  (Man made, that is.)

PAE enabled on a 32 bit OS gives you an insignificantly puny 64GB...

---

### Post by thegutterpoet on 2009-09-12
the uname -m command gives me
**i686**

which means?

(and thankyou, for those trying to help me solve this cruel riddle)

i think it means that I am using the 64 bit version of ubuntu...but then, shouldn't it be recognizing my RAM.

I understand how some RAm resources may be annexed for hardware use. But I am 1.2gb under my installed total RAM, not .2 - .5

**"You should install the Server kernel from synaptic because it supports 32 bit PAE and will see and use all your ram."**

Please explain? And is this the answer to my woes?

---

### Post by QIII on 2009-09-12
Don't bother about the server kernel.

And the extra bit of RAM you are losing may be due to the fact that the 32 bit version often only sees a max of 3.27 GB to begin with.

Your answer to uname -m is interesting.  The man page for uname indicates that the -m flag should return the machine architecture, but I believe in many flavors of Linux it returns what architecture your kernel is built for.  So 64 bit machine architecture or not, you'd see the "capability" of the OS -- or 32 bit represented by i686.

A 32 bit OS will run on a 64 bit processor, but the reverse is not true.

Anyway.  You are running what is most certainly a 64 bit processor (Turion 64.  In this case, two cores).  If you were running the 64 bit version of Ubuntu, your return would have been x86_64.

I would say that you have the 32 bit version of Ubuntu installed.

Do you have your disk handy?  Can you tell me the name of the iso that you downloaded?

If you have the 32 bit version installed, you probably want to install the 64 bit version.  But if you do that, you will want to BACK UP all of your important files to removable media and do a new install using the entire disk.  Again:  BACK UP all of your important files.

But before you do anything, let me know the name of the iso file.

---

### Post by thegutterpoet on 2009-09-12
I will have a peek mate, but its on a CD ROM somewhere in the **** swamp of my room...I just assume I downloaded the 64 bit version, because I knew, when i downloaded linux, that my cores were 64-bit...

I will have a peek...

But your suspicion is that I have a 32 bit version installed? And that by installing instead, a 64 bit version, I will then be able to utilize the majority of my 4gb ram?

---

### Post by QIII on 2009-09-12
That is my suspicion (and the 32 bit version is the topmost selection on the download page, unfortunately).

And yes, if you use the 64 bit version you will be able to address a lot more of your RAM.

Where are you from?  My oldest brother, an ex-pat in Melbourne (dual citizen), and his family all use "mate" ... and they "talk funny", too.

---

### Post by thegutterpoet on 2009-09-12
I was born in Melbourne, many moons ago, but have been nurtured in England for the vast majority of my life leading up the NOW. My nature is very british, though the british mind has been tempered, well not tempered...more aggravated...challenged for supremacy...by the sicilian half of my blood. Well traveled, and currently marooned, to a degree, in Melbourne, with an 11 month old rat wolverine shitsu hound, a book to write, a website to develop, ongoing hald enjoyable work and the beauty of the VIctorian Spring greeting me every morning...So I will stay put for now...though, a Return to the MotherLand, will be likely. Just a matter of When. 

As for my use of 'mate', its far more british than native to the Whites here...

---

### Post by QIII on 2009-09-12
> **weedguru said:**
> I was born in Melbourne, many moons ago, but have been nurtured in England for the vast majority of my life leading up the NOW. My nature is very british, though the british mind has been tempered, well not tempered...more aggravated...challenged for supremacy...by the sicilian half of my blood. Well traveled, and currently marooned, to a degree, in Melbourne, with an 11 month old rat wolverine shitsu hound, a book to write, a website to develop, ongoing hald enjoyable work and the beauty of the VIctorian Spring greeting me every morning...So I will stay put for now...though, a Return to the MotherLand, will be likely. Just a matter of When. 

As for my use of 'mate', its far more british than native to the Whites here...

Ah.  But who, pray tell, would have made up the vast majority of those given the opportunity to take a lovely, multi-year vacation in places like "Van Diemen's Land"?

The vast majority of my world travels have resulted in a bit of unfortunate and mortal scuffling with the locals...

---

### Post by thegutterpoet on 2009-09-12
hohoho...I have never been to Tasmania. Though I will do, at some stage in the future...I am finding that being reluctantly installed as sole guardian and father figure of a hound greatly increase the weight of inertia, geographically speaking, of my existence.

As for my RAM problem...I am sure that I downloaded the 64 bit version. But I cannot find the disc or the file image. The download limit for the house here has been passed, and I will feel too guilty to make matters worse by downloading another 700mb, to put us even deeper into the mire.

So...is there any other way of checking my version of ubuntu, in order to at least ascertain, definitively, whether my RAM problems are due solely to my strange decision to avoid a 64-bit version of ubuntu, and choose the 32 bit routine...???

If we can get the Cause and Solution confirmed, I will be content to wait another 17 days for our internet limit to be increased back to the fluidity of water, rather than this oil sludge of the Now.

---

### Post by P4man on 2009-09-12
seems like no one suggested this yet: your onboard **videocard** is most likely using some of your RAM as framebuffer. YOu can probably configure in your BIOS how much, and I bet its set to 512Mb. That is RAM no operating system can use as system RAM, its used for your videocard exclusively. (and you may want to reduce that to 256Mb, its not likely useful to have that much video memory with an onboard videocard).

The remaining RAM that went missing is like others said, due to limits of using a 32 bit OS. Not sure if its worth reinstalling a 64 bit OS to recover a few 100Mb, unless you know you are using that much RAM. Most users rarely use more than 1 or 2GB on ubuntu (check in the system monitor and find out)

But to put your  mind at rest, those dmidecode outputs clearly show you have 2 2GB modules though, you didn't get robbed ;)

---

### Post by QIII on 2009-09-12
In truth, i686 is more than just a suspicion.  It is pretty definitive...

Sorry about the transfer limitations.  Just a way for your ISP to wring more money out of you.  Miserable, money-grubbing <insert vulgar, obscene pejorative of choice here> ...

I'd say to order the free CD from Canonical, but that can take up to 10 weeks to arrive.

Is there a Linux Users' Group or something like that in Melbourne?  You might be able to find a kindly stranger who can burn you a copy.

I'm off to bed now.  Taking my last natural child left at home and one of the fosters to go fishing in about 4 1/2 hours.

Will check in tomorrow.

---

### Post by thegutterpoet on 2009-09-18
My system monitor tells me I am using barely 400mb...I only wanted to try make use of the total 4gb if it was going to offer a definite increase in speed and performance. So the question now, is WOULD IT DO THAT??? If i downoad a copy of the 64 bit version...format this partition, then re install ubuntu???

Is it worth it??? Is what I need to know! Please...

---

### Post by dcstar on 2009-09-18
> **weedguru said:**
> My system monitor tells me I am using barely 400mb...I only wanted to try make use of the total 4gb if it was going to offer a definite increase in speed and performance. So the question now, is WOULD IT DO THAT??? If i downoad a copy of the 64 bit version...format this partition, then re install ubuntu???

Is it worth it??? Is what I need to know! Please...

Ubuntu will use any spare RAM for caching disk data, so if you work with large files then the data will already be in RAM and you will not have to wait for it to be fetched from the disk.

If you want to install 64-bit, set up a separate /home partition and then you can boot between 32 and 64 and use the same data.

---

### Post by thegutterpoet on 2009-09-18
after reading a little more about the i686 business, I am convinced that I have the 32 bit version...and am now downloading the amd 64 version...which will suit my amd 64 trurion X 2 dual thinking box set up more cozily...and maybe, it will see more of my RAM.

cheers for the advice people. I will head back here if Everything goes BAD.

---

### Post by thegutterpoet on 2009-09-19
So I have now installed the 64 bit version of ubuntu 9.04...but still, the same problem. It only recognizes 2.8gb of RAM...Why???

---

### Post by Ratscallion on 2009-09-19
That's odd... 64bit = 4GB and more, whereas 32bit = >4GB..
Have you got a Windows partition on there? If you have, see if Windows (grr) can recognise your RAM. If not, try downloading another Linux Distro (DamnSmallLinux if you want, it's very tiny) and LiveCD it. See if that can recognise it.

---

### Post by thegutterpoet on 2009-09-19
yes, I do have a windows partition...it also wants to use only 2.8gb...but that is more normal for windows, from what I have read. When I use a tool for checking my RAM, clearly it says I have 2 X 2gb RAM installed.

Are there any advantages to me running this 64 bit version of ubuntu on my 64 bit processors???

and are there any other suggestions for getting the beast to see ALL my ram? or a terminal command for checking what RAM total, I have INSTALLED???

---

### Post by 3rdalbum on 2009-09-19
If the 64-bit operating system still only sees 2.8 gigabytes, then it must either be a BIOS setting that limits the amount of seeable RAM, or it's a limitation of the laptop motherboard's chipset.

Usually the 32-bit addressable limit puts you at 3.3 gigabytes, not 2.8.

---

### Post by thegutterpoet on 2009-09-19
BIOS knows I have 4gb ram...it told me.

The chipset can handle a maximum of 4gb.

So those explanations don't seem Right...

any other ideas???

any commans to check where the missing 1.2gb are going???

---

### Post by Ratscallion on 2009-09-19
> **weedguru said:**
> BIOS knows I have 4gb ram...it told me.

The chipset can handle a maximum of 4gb.

So those explanations don't seem Right...

any other ideas???

any commans to check where the missing 1.2gb are going???
You mentioned in your first post that the BIOS said 2.8GB...

---

### Post by thegutterpoet on 2009-09-19
That wasn't BIOS...as I know BIOS...I think it was windows...and it was telling me something...I cant recall what, but I said YES, Go FOR IT...since then, i have checked in bios, and it says 4096...or something close to that...also checked with a couple of applications on windows, and all say that i have 4gb...I know that windows XP wont recognize the full 4gb, but I thought the 64 bit ubuntu WOULD.

Surely, 1.2gb are not going towards graphics and handling hardware, so where are they?

---

### Post by thegutterpoet on 2009-09-19
Running the follow command.. dmesg | grep Mem
gives me this:>
[    0.004000] Memory: 2916860k/3014464k available (4749k kernel code, 492k absent, 96420k reserved, 2523k data, 532k init)
[   12.106493] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd42fffff
[   12.106497] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xd8000000 - 0xdbffffff

---

### Post by thegutterpoet on 2009-09-19
Does anyone have any other suggestions as to how to make linux see and use all my physical RAM?

---

### Post by 3rdalbum on 2009-09-19
> **weedguru said:**
> BIOS knows I have 4gb ram...it told me.

The chipset can handle a maximum of 4gb.

So those explanations don't seem Right...

The other possible explanation that I can think of is memory-mapped I/O.

Some components of your system have little bits of RAM on-board (most notably, graphics card; but your SATA and IDE, floppy, USB, sound card etc have it). These bits of memory need to be accessed by the CPU, so they take up some of your address space.

This is quite serious in a 32-bit operating system these days, because we're now installing as much RAM as a 32-bit operating system can address, and some of this RAM becomes inaccessible because of those bits of memory on your components.

On 64-bit you shouldn't see memory-mapped I/O anymore, because it's now being mapped to the 16th terrabyte of address space, rather than the fourth gigabyte.

My hunch is that you've got some sort of BIOS setting enabled that pushes the memory maps down into the 3 gigabyte range; possibly for "compatibility" with badly-written Windows drivers? If Windows XP can't see more than 2.8GiB of RAM, and neither can 64-bit Linux, then it's not an operating system issue; it's either a chipset limitation, or a BIOS limitation, or a BIOS setting.

The only other thing I can think of is to run the Memtest86+ program from the GRUB menu, see how much RAM it sees. Start running it before you go to bed, and in the morning see whether it has encountered any problematic memory.

---

### Post by thegutterpoet on 2009-09-19
Thanks for the detailed explanations, mate. I will tun the GRUB utility, and report back...

---

### Post by klep9 on 2009-09-19
This reminded me of an article in the dutch linux-magazine.

It has to do with the 32bit environment. There is a trick to get more by using 4 extra bits as is mentioned in of the replies earlier (64GB). To do that, the mainboard/BIOS must be capable of adressing all the hardware after the 4GB limit. If the supplier of your hardware has not engineered that, a part of the RAM is dedicated to the memory-mapped IO. Hopefully you can for example change the memory the VGA uses from your main memory. The supplier is probably true, it does support 4GB memory, no it is not available to you. To support this, look at strange hardware configuration where suppliers sell 3GB of RAM. This is really weird. I did not understand till I had read this article.

Try to find BIOS upgrade!
Try changing settings that influence memory!

Even though you have 2.8GB left, thats far more then I have ever used in a linux-machine. I would like to remind you that your processor (I have also one my own) is perfectly capable of running 64bit linux and in my experience is a lot faster then its 32bit brother.

See you around!

---

### Post by P4man on 2009-09-20
While you're in the bios, check how much ram is allocated as shared memory for the onboard video. ive never seen 1GB, but i suppose its possible (though pointless).

---

### Post by xadder on 2009-09-29
I'm having a similar problem. I just installed 4x2 GB DIMMs on an Asus PC, my BIOS tells me that I have ca 7 G, but Ubuntu Jaunty (i686, 32 bit) tells me I have just 2.8 Gbyte.

I'd prefer not having to re-install, and am not sure if 64 bit is an option anyway. Any suggestions?

---

### Post by xadder on 2009-09-29
I found a thread with similar problems, and a solution (EnablingPAE) for 32 bit machines to access more memory:

[http://ubuntuforums.org/showthread.php?t=1007786]("http://ubuntuforums.org/showthread.php?t=1007786")

---

### Post by thegutterpoet on 2009-09-30
The PAE solution seems cool, but I am running a 64 bit ubuntu on a 64 bit machine...and it only sees 2.8gb.

---

### Post by bollix47 on 2009-09-30
> **weedguru said:**
> The PAE solution seems cool, but I am running a 64 bit ubuntu on a 64 bit machine...and it only sees 2.8gb.

Check the computer's bios settings and make sure Memory Remap is enabled.
On my setup it's under Advanced>Chipset>Northbridge

Had the same situation until I did the above.

gl :wink:

---

### Post by thegutterpoet on 2009-10-05
When I run set-up, before I get the option of choosing to boot linux or windows, the system information shows as this:

Memory 4096

which is how much I physically have. There was no option for remapping memory...

any other ideas?

---

### Post by thegutterpoet on 2009-10-06
A friend with a similar chipset has encountered the exact same problem...
[http://www.weedguru.com/forum/viewtopic.php?f=61&t=32566&p=515930#p515930](http://www.weedguru.com/forum/viewtopic.php?f=61&t=32566&p=515930#p515930)

does anyone have any other ideas as to how to get ubuntu to recognize the full 4gb???

My bios...or set-up...whatever the name of the program I can run by pressing a function key, before I am asked to choose an operating system to boot, KNOWS i have 4gb ram...why doesn't ubuntu???

---

### Post by dcstar on 2009-10-06
> **thegutterpoet said:**
> A friend with a similar chipset has encountered the exact same problem...
[http://www.weedguru.com/forum/viewtopic.php?f=61&t=32566&p=515930#p515930](http://www.weedguru.com/forum/viewtopic.php?f=61&t=32566&p=515930#p515930)

does anyone have any other ideas as to how to get ubuntu to recognize the full 4gb???

My bios...or set-up...whatever the name of the program I can run by pressing a function key, before I am asked to choose an operating system to boot, KNOWS i have 4gb ram...why doesn't ubuntu???

It doesn't matter what physical RAM you have installed if the design of the system does not allow you to use it all:

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00770952&jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00770952&jumpid=reg_R1002_USEN)

It is not Ubuntu, it is your hardware.

---

### Post by thegutterpoet on 2009-10-06
which gives me this:>
With the most relevant lines:
**Upgradeable to 4096-MB maximum **
and
**If you mix memory speeds, the system will perform at the lower memory speed. Above 3-GB, all memory may not be available due to system resource requirements.**

Surely if the bios and set up page can see the 4096 then it is using it???

Windows sees 3.1gb of it.

Ubuntu only 2.8gb.

Is this truly the end of the road???

That page says that the hardware can support up to 4096...which is what i have installed. Is it implying that only with official HP ram, will the system recognize 4096mb, or is that just sales propaganda??

---

