---
title: "New user - -super low RAM + computer has frozen a few times. Advice?"
date: 2012-06-03
forum: General Help
---

### Post by mimicatastrophe on 2012-06-03
This is the outcome of free -m
```

mimi@Isis:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           874        767        106          0         32        345
-/+ buffers/cache:        390        484
Swap:          893         12        881
mimi@Isis:~$ 

```Someone had mentioned that maybe it's that the actual RAM stick has failed or came loose but I am not sure how they came to that conclusion. 

I just want to see if there is another option since I have gone through a lot of computer issues recently and need to have something stable for work.

Related to the issue-I'd like to get rid of unity interface and switch to something that is lighter if anyone can tell me how to do that....
someone had given me Gnome classic no effects as an option but I had to reinstall.

---

### Post by 2F4U on 2012-06-03
I don't seem to understand the question. How much RAM do you think you have? If you say, for example, "I have 2 GB of RAM installed", I would probably say that most likely one of the RAM chips is defect. If you have 1 GB installed and there is also an integrated graphics card that takes its memory from the installed system RAM, the output you post looks reasonable.

On lighter desktop environments, you should look at Xubuntu or Lubuntu. Both desktops can be installed without re-install by installing the packages xubuntu-desktop or lubuntu-desktop on top of your current installation.

---

### Post by sanderj on 2012-06-03
I agree with 2F4U: how much RAM have you got? You can see it during boot. Or run the script [http://www.appelboor.com/dump/check-my-hardware.py](http://www.appelboor.com/dump/check-my-hardware.py) to see all memory details of your system.

Unity is too heavy for 1GB of RAM (which you seem to have), so choose Lubuntu or Xubuntu.

Computer frozen? How "frozen": for tens of seconds non-responsive and then it works again, or frozen-frozen and (edit:) NOT  coming back again. If the latter, run memtest86 from your GRUB menu to see if your RAM is OK.

---

### Post by mimicatastrophe on 2012-06-03
thank you that's really helpful I didnt even think to mention how much RAM I should have nor did the person helping me ever ask.  Under details however, it says I have 857MiB which he said was very very low and thought a card had failed. Your explanation has at least made me understand how to find out where the problem lies. 

I dont know anything about graphic cards but I did have a message awhile back (before this install) it was something about and error with gnome and my graphics card or lack there of. Not too sure. But my disk drive isnt working so I need to have the computer opened up anyway I will check on the graphic card. And thanks again for those suggestions, very much appreciated going to look them up now.

---

### Post by sanderj on 2012-06-03
> **mimicatastrophe said:**
> thank you that's really helpful I didnt even think to mention how much RAM I should have nor did the person helping me ever ask.  Under details however, it says I have 857MiB which he said was very very low and thought a card had failed. Your explanation has at least made me understand how to find out where the problem lies. 

I dont know anything about graphic cards but I did have a message awhile back (before this install) it was something about and error with gnome and my graphics card or lack there of. Not too sure. But my disk drive isnt working so I need to have the computer opened up anyway I will check on the graphic card. And thanks again for those suggestions, very much appreciated going to look them up now.

You don't need to have a look at your graphics card; its memory usage is just a detail.

The real interesting thing is how much RAM you have installed in your system. If it is 1GB, the information provided by "free -m" is correct.

So, run the script from [http://www.appelboor.com/dump/check-my-hardware.py](http://www.appelboor.com/dump/check-my-hardware.py) and you'll know.

Here's what the script reports about my 4GB laptop:

```

sander@R540:~$ sudo python check-my-hardware.py 
[sudo] password for sander: 
check-my-hardware.py - version: SJ 2012-03-05
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 3890 MB as usable
Memory seen by OS 3753 MB
BIOS version 06/21/2010
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 206 MB
Memory difference between BIOS offering and memory seen by OS 137 MB
Memory difference between DIMM hardware and memory seen by OS 343 MB

ADVICE:
Nothong unusual found, so no advice for your setup

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 4GiB
          description: SODIMM DDR3 Synchronous 667 MHz (1.5 ns)
          size: 2GiB
          description: SODIMM DDR3 Synchronous 667 MHz (1.5 ns)
          size: 2GiB
          description: SODIMM DDR3 Synchronous [empty]
          description: SODIMM DDR3 Synchronous [empty]

Finished
sander@R540:~$ 



```

HTH

---

### Post by mimicatastrophe on 2012-06-03
> **sanderj said:**
> run the script [http://www.appelboor.com/dump/check-my-hardware.py](http://www.appelboor.com/dump/check-my-hardware.py) to see all memory details of your system..

sorry is there a way to do that i see it looks like a terminal input but if i copy and paste into mine i imagine it would not work because of the user name? 

> 
Computer frozen? How "frozen": for tens of seconds non-responsive and then it works again, or frozen-frozen and coming back again. If the latter, run memtest86 from your GRUB menu to see if your RAM is OK

Nope it freezes for very long and I am unable to do anything. This has happened multiple times a day but has been spaced out where it hasn't been a huge problem but I do save a lot of important drafts I would hate for it to be an issue so if it is just RAM would it be the lack of RAM, and installing more (uninstalling faulty ones if any) fix this?

thanks so much!

---

### Post by mimicatastrophe on 2012-06-03
hahah sorry sanderj each time you replied I was replying! thanks for being so detailed! i will go through your last response and do anything there you have recommended.

---

### Post by sanderj on 2012-06-03
Open a terminal, then type:


```

wget http://www.appelboor.com/dump/check-my-hardware.py
sudo python check-my-hardware.py 

```

HTH

---

### Post by mimicatastrophe on 2012-06-03
nice! i have never ran wget. thanks for that and here is the outcome:

```

ANALYSIS:
Total of physical memory modules found 1024 MB in 2 memory module(s)
BIOS offers 894 MB as usable
Memory seen by OS 874 MB
BIOS version 08/11/2005
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is 32-bit with PAE

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 130 MB
Memory difference between BIOS offering and memory seen by OS 20 MB
Memory difference between DIMM hardware and memory seen by OS 150 MB

ADVICE:
Your physical memory is less than 3200 MB, and your system does not need special memory treatment

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 1GiB
       capacity: 2GiB
          description: DIMM DDR 266 MHz (3.8 ns)
          size: 512MiB
          description: DIMM DDR 266 MHz (3.8 ns)
          size: 512MiB

Finished

```

---

### Post by mimicatastrophe on 2012-06-03
wow is there a reason my BIOS is from 2005? I had a wiped clean hard drive before installing ubuntu 12.04 if that matters...

and not sure what that DIMM thing is or means but I noticed a large difference. 

your script is nice though, I like how easy the output was to read even for someone like me who doesnt know much about commands.

---

### Post by mcduck on 2012-06-03
Based on that output, and the one from "free" in your fist post, everything is workign just fine.

You have 2 512MB RAM modules installed, giving a total of 1GB of RAM. 128MB is assigned to the integrated graphics card, some is taken by the Linux kernel itself, leaving 874 MB available for use.

And form that 874 MB over half is still free, based on the "-/+ buffers/cache"-line from the free output. 390MB of RAM is used, and 484MB is still availbele should any program need it.

Sure, if you compare to new computers sold these days, especially all the ones running Windows 7, 1GB of RAM is not much. But on the other hand your system is doing quite fine with the amount of RAM you have. Upgrading that to 2GB might give you a small performance benefit, but chances are it would still be so small you wouldn't notice any actual difference.

---

### Post by sanderj on 2012-06-03
> **mimicatastrophe said:**
> wow is there a reason my BIOS is from 2005? I had a wiped clean hard drive before installing ubuntu 12.04 if that matters...


... because your hardware is from 2005? Installing an Operating System won't update your BIOS.
There is nothing wrong with a BIOS from 2005. Only update it (if possible) if it solves BIOS bugs with new hardware. Which you probably won't have.

> **mimicatastrophe said:**
> 

and not sure what that DIMM thing is or means but I noticed a large difference. 


DIMM is the name of the physical memory chips. You have two of those DIMM chips, each 512 MB, adding up to 1GB total.

> **mimicatastrophe said:**
> 

your script is nice though, I like how easy the output was to read even for someone like me who doesnt know much about commands.

Thank you! I've created it for users complaining their Ubuntu was only showing 3GB of RAM, whereas their system had more. That has to do with type (32-bit versus 64-bit) of processor and type of OS. Glad it helps you too.

Talking about which: you have a 64-bit processor. Interesting, as your hardware is already from 2005, at which time 64-bit processors were not yet common.

---

### Post by mimicatastrophe on 2012-06-03
> **mcduck said:**
> 
Sure, if you compare to new computers sold these days, especially all the ones running Windows 7, 1GB of RAM is not much. But on the other hand your system is doing quite fine with the amount of RAM you have. Upgrading that to 2GB might give you a small performance benefit, but chances are it would still be so small you wouldn't notice any actual difference.

do you think that difference would be so small even as a designer running high visual/graphic content and programs? most of the time? or would this be about the same performance as when I had windows.

the tech i mentioned never even asked if my computer was old. i am glad to hear its a factor like i thought. so thanks a bunch! looks like I am mostly all set here with my new linux and there documentation and forums have been very helpful. =D

---

### Post by Shadius on 2012-06-03
> **mimicatastrophe said:**
> wow is there a reason my BIOS is from 2005? I had a wiped clean hard drive before installing ubuntu 12.04 if that matters...

and not sure what that DIMM thing is or means but I noticed a large difference. 

your script is nice though, I like how easy the output was to read even for someone like me who doesnt know much about commands.

Everything seems to be working fine based on the output. DIMM (Dual In-line Memory Module) is basically the slots for the RAM (Random-Access Memory). Some more information below...

[DIMM]("http://en.wikipedia.org/wiki/DIMM") 
[RAM]("http://en.wikipedia.org/wiki/RAM")

I have less than 1GB of memory in my computer and I'm running Ubuntu with GNOME Classic (No Effects). You don't have to do a reinstall to get GNOME Classic. You can install GNOME Tweak Tool from the Ubuntu Software Center (correct me if I'm wrong guys), and then once it's installed just log out, and from the login screen choose the Ubuntu logo and select GNOME Classic or GNOME Classic (No Effects).

---

### Post by sanderj on 2012-06-03
> **mimicatastrophe said:**
> wow is there a reason my BIOS is from 2005? I had a wiped clean hard drive before installing ubuntu 12.04 if that matters...

and not sure what that DIMM thing is or means but I noticed a large difference. 

your script is nice though, I like how easy the output was to read even for someone like me who doesnt know much about commands.

> **mimicatastrophe said:**
> do you think that difference would be so small even as a designer running high visual/graphic content and programs? most of the time? or would this be about the same performance as when I had windows.

the tech i mentioned never even asked if my computer was old. i am glad to hear its a factor like i thought. so thanks a bunch! looks like I am mostly all set here with my new linux and there documentation and forums have been very helpful. =D

Graphic stuff (either from Unity or programs) requires high-end hardware. As your hardware is from 2005 (right?), so 7 years old, and your processor is probably moderate too, you should not expect big improvements from upgrading from 1GB to 2GB RAM.

I'm typing this on a 4GB Core i3 laptop, and Unity is OK with that.

HTH

---

### Post by mimicatastrophe on 2012-06-03
> **sanderj said:**
> ... because your hardware is from 2005? Installing an Operating System won't update your BIOS...

Talking about which: you have a 64-bit processor. Interesting, as your hardware is already from 2005, at which time 64-bit processors were not yet common.

haha okay that makes sense thanks i have only used newer computers before so it was strange to see a date that far back...about the processor I guess it could be coincidence but I do have a computer that has probably been rebuilt and customized from different parts quite a bit when I consider the person who gave it to me. 

but i was really surprised to see that too! does it effect the functionality of my computer? especially running 32 since thats what I have always done and my windows was even 32 and should i be installing an OS that is for 64-bit?

---

### Post by sanderj on 2012-06-03
> **mimicatastrophe said:**
> haha okay that makes sense thanks i have only used newer computers before so it was strange to see a date that far back...about the processor I guess it could be coincidence but I do have a computer that has probably been rebuilt and customized from different parts quite a bit when I consider the person who gave it to me. 

but i was really surprised to see that too! does it effect the functionality of my computer? especially running 32 since thats what I have always done and my windows was even 32 and should i be installing an OS that is for 64-bit?

64-bit Ubuntu won't make your system any faster. However, if you reinstall (for example Lubuntu or Xubuntu), you could choose the 64-bit OS.

---

### Post by mimicatastrophe on 2012-06-03
> **sanderj said:**
> 
I'm typing this on a 4GB Core i3 laptop, and Unity is OK with that.

HTH

sooooo if i were to install quite a bit more say 4gb or more of the RAM I would then notice the difference? I was told it was cheap plus I think I have access to some more as well. 

not sure why i didnt see a few of these replies i am seeing now but thanks for such detailed solutions and explanations its helped a lot =D

---

### Post by mimicatastrophe on 2012-06-03
> I have less than 1GB of memory in my computer and I'm running Ubuntu  with GNOME Classic (No Effects). You don't have to do a reinstall to get  GNOME Classic. You can install GNOME Tweak Tool from the Ubuntu  Software Center (correct me if I'm wrong guys), and then once it's  installed just log out, and from the login screen choose the Ubuntu logo  and select GNOME Classic or GNOME Classic (No Effects).

so I was unable to find that in the software center and before they used the terminal to install that option but i did not see how. they are super busy but i may ask again if i am experiencing any issues and i am glad to hear it is running well with a similar system or at least same RAM!

---

### Post by mcduck on 2012-06-03
> **sanderj said:**
> 64-bit Ubuntu won't make your system any faster. However, if you reinstall (for example Lubuntu or Xubuntu), you could choose the 64-bit OS.

Actually it does, depending on tasks you do and programs you use 64-bit computing can have significant performance benefits over 32-bit systems.

Especially all audio/video enconding and other media-related tasks can be done much faster on a 64-bit system, assuming of course that the programs that are used are made to take advantage of the 64-bit instructions available.

However when it comes to desktop perfomance, as opposed to raw processing performance, that's pretty much up to the graphics card and it's drivers.

---

### Post by mcduck on 2012-06-03
> **mimicatastrophe said:**
> sooooo if i were to install quite a bit more say 4gb or more of the RAM I would then notice the difference? I was told it was cheap plus I think I have access to some more as well. 

not sure why i didnt see a few of these replies i am seeing now but thanks for such detailed solutions and explanations its helped a lot =D

There's an easy wau to check that without spending any money at all. Just use the computer like you'd normally do, and check the amount of free RAM and used swap every now and then.

If you end runnign out of available RAM and the swap usage starts to grow, then installing more RAM would improve performance. On the other hand if you always have available RAM even with the current 1GB, then the performance improvement from having any more RAM would be pretty much neglible.

---

### Post by Shadius on 2012-06-03
> **mimicatastrophe said:**
> sooooo if i were to install quite a bit more say 4gb or more of the RAM I would then notice the difference? I was told it was cheap plus I think I have access to some more as well. 

not sure why i didnt see a few of these replies i am seeing now but thanks for such detailed solutions and explanations its helped a lot =D

Since you have a 64-bit processor, you'd benefit from having 4GB of RAM. Some pros and cons below...

[32-bit vs 64-bit]("http://en.wikipedia.org/wiki/64-bit#32-bit_vs_64-bit")

---

### Post by sanderj on 2012-06-03
> **mimicatastrophe said:**
> sooooo if i were to install quite a bit more say 4gb or more of the RAM I would then notice the difference? I was told it was cheap plus I think I have access to some more as well. 

not sure why i didnt see a few of these replies i am seeing now but thanks for such detailed solutions and explanations its helped a lot =D

There are a few things to check:
what is the amount of hardware memory your motherboard supports?
what type of DIMM does your motherboard support? In 2005 I think DDR2 was used (not the currently common DDR3)
how many DIMM-sockets are there on your motherboard?

So ... do you have the manual and/or the type number of your motherboard? If so, you can find the above information, and buy the correct memory.



HTH

---

### Post by sanderj on 2012-06-03
PS:

If you run the commands below, I hope you get the name of your motherboard:

```
sudo dmidecode -s system-product-name
sudo dmidecode -s baseboard-product-name
sudo dmidecode -s baseboard-manufacturer

```

If you post the full output of "sudo dmidecode" here, I can help you further.

HTH

---

### Post by mimicatastrophe on 2012-06-03
I am quite sure that the previous owner of the computer either has the manual or would know how to figure out anything with adding the RAM itself. I will ask him those questions but first I will keep an eye on things and check out this link about the 64-bits (thanks for that!) this has all been great to know thanks guys

---

### Post by Shadius on 2012-06-03
> **mimicatastrophe said:**
> I am quite sure that the previous owner of the computer either has the manual or would know how to figure out anything with adding the RAM itself. I will ask him those questions but first I will keep an eye on things and check out this link about the 64-bits (thanks for that!) this has all been great to know thanks guys

If you run those codes that sanderj suggested you should be able to get the information you're looking for. No need for the manual...yet. :)

---

### Post by mimicatastrophe on 2012-06-03
```
  Release Date: 08/11/2005
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Compaq Presario 061
    Product Name: PW520AA-ABA SR1463CL NA520
    Version: 0nB1411RE101SALMO00
    Serial Number: CNH5140PHH
    UUID: 0B000000-0000-0000-0000-000B000B0000
    Wake-up Type: Power Switch
    SKU Number:  
    Family:  

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: ASUSTek Computer INC.
    Product Name: Salmon 
    Version: 1.04
    Serial Number: MB-1234567890

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
    Manufacturer: Hewlett-Packard
    Type: Desktop
    Lock: Not Present
    Version: 1111
    Serial Number:  
    Asset Tag:  
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: Socket 754
    Type: Central Processor
    Family: Athlon 64
    Manufacturer: AMD
    ID: C0 0F 00 00 FF FB 8B 07
    Signature: Family 15, Model 12, Stepping 0
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
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
    Version: AMD Athlon(tm) 64 Processor 3300+
    Voltage: 1.5 V
    External Clock: 200 MHz
    Max Speed: 3700 MHz
    Current Speed: 2400 MHz
    Status: Populated, Enabled
    Upgrade: Socket 754
    L1 Cache Handle: 0x0008
    L2 Cache Handle: 0x0009
    L3 Cache Handle: Not Provided
    Serial Number:  
    Asset Tag:  
    Part Number:  

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 1024 MB
    Maximum Total Memory Size: 2048 MB
    Supported Speeds:
        70 ns
        60 ns
        50 ns
    Supported Memory Types:
        Standard
        SDRAM
    Memory Module Voltage: 2.9 V
    Associated Memory Slots: 2
        0x0006
        0x0007
    Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 0 1
    Current Speed: 70 ns
    Type: DIMM
    Installed Size: 512 MB (Double-bank Connection)
    Enabled Size: 512 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: 2
    Current Speed: 70 ns
    Type: DIMM
    Installed Size: 512 MB (Single-bank Connection)
    Enabled Size: 512 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0008, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 128 kB
    Maximum Size: 128 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 4-way Set-associative

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PRIMARY IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SECONDARY IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: FDD
    Internal Connector Type: On Board Floppy
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: 8251 FIFO Compatible

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM1
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator:  
    External Connector Type: DB-9 male
    Port Type: Serial Port 16450 Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM2
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator:  
    External Connector Type: DB-9 male
    Port Type: Serial Port 16450 Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LPT1
    Internal Connector Type: DB-25 female
    External Reference Designator:  
    External Connector Type: DB-25 female
    Port Type: Parallel Port ECP/EPP

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Keyboard
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Mouse
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Other
    Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Other
    Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Other
    Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB4
    External Connector Type: Other
    Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB5
    External Connector Type: Other
    Port Type: USB

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB6
    External Connector Type: Other
    Port Type: USB

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: VIDEO
    External Connector Type: DB-15 female
    Port Type: Video Port

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: Line In
    External Connector Type: None
    Port Type: Audio Port

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: ETHERNET
    External Connector Type: RJ-45
    Port Type: Network Port

Handle 0x001B, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 1
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x001C, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 2
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x001D, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI3
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 3
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x001E, DMI type 10, 12 bytes
On Board Device 1 Information
    Type: Other
    Status: Enabled
    Description:  
On Board Device 2 Information
    Type: Video
    Status: Enabled
    Description:  
On Board Device 3 Information
    Type: Ethernet
    Status: Enabled
    Description:  
On Board Device 4 Information
    Type: Sound
    Status: Enabled
    Description:  

Handle 0x001F, DMI type 9, 13 bytes
System Slot Information
    Designation: AGP
    Type: 32-bit AGP 8x
    Current Usage: Available
    Length: Short
    ID: 1
    Characteristics:
        PME signal is supported

Handle 0x0020, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Long
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1

Handle 0x0021, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0022, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0021
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: DDR
    Type Detail: None
    Speed: 266 MHz
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0023, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0021
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: DDR
    Type Detail: None
    Speed: 266 MHz
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0024, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Array Handle: 0x0021
    Partition Width: 1

Handle 0x0025, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0001FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x0022
    Memory Array Mapped Address Handle: 0x0024
    Partition Row Position: 1

Handle 0x0026, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00020000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x0023
    Memory Array Mapped Address Handle: 0x0024
    Partition Row Position: 1

Handle 0x0027, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

Handle 0x0029, DMI type 144, 12 bytes
OEM-specific Type
    Header and Data:
        90 0C 29 00 00 11 D8 D5 BB 49 C2 01
    Strings:
        SiS630E-MAC

Handle 0x0028, DMI type 11, 5 bytes
OEM Strings
    String 1: bid=52NAheRED3,52NAheRED3;ADPHOAL_STE;C_GOB;IS.N60d;MSDME_STD;MS
    String 2: MON_STD;PROD_MSWE;QUIF_NUE;RN_STD;RP_STD;SFCHK;SPY_BAS;WC_STD;WD
    String 3: _SE;##
    String 4:                                                                 
    String 5:                                                                 
    String 6:                                                                 
    String 7:                                                                 
    String 8:                                                                 
    String 9:                                                                 
    String 10:                                                                 
    String 11:                                                                 
    String 12:                                                                 
    String 13:                                                                 
    String 14:                                                                 
    String 15:                                                                 
    String 16:                                                                 

Handle 0x002A, DMI type 127, 4 bytes
End Of Table

```
:confused: hahaha

---

### Post by mimicatastrophe on 2012-06-03
```
mimi@Isis:~$ sudo dmidecode -s system-product-name
PW520AA-ABA SR1463CL NA520
mimi@Isis:~$ sudo dmidecode -s baseboard-product-name
Salmon 
mimi@Isis:~$ sudo dmidecode -s baseboard-manufacturer
ASUSTek Computer INC.

```

---

### Post by sanderj on 2012-06-03
> 
    Version: AMD Athlon(tm) 64 Processor 3300+
    Maximum Memory Module Size: 1024 MB
    Maximum Total Memory Size: 2048 MB

So:
- quite a nice processor
- you should be able to use two 1GB DDR2 SIMM modules. The cost about 11 Euro a piece.
- Don't expect miracles from the upgraded computer. And do not use Unity.

---

### Post by Shadius on 2012-06-03
> **mimicatastrophe said:**
> ```
  Release Date: 08/11/2005
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Compaq Presario 061
    Product Name: PW520AA-ABA SR1463CL NA520
    Version: 0nB1411RE101SALMO00
    Serial Number: CNH5140PHH
    UUID: 0B000000-0000-0000-0000-000B000B0000
    Wake-up Type: Power Switch
    SKU Number:  
    Family:  

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: ASUSTek Computer INC.
    Product Name: Salmon 
    Version: 1.04
    Serial Number: MB-1234567890

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
    Manufacturer: Hewlett-Packard
    Type: Desktop
    Lock: Not Present
    Version: 1111
    Serial Number:  
    Asset Tag:  
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: Socket 754
    Type: Central Processor
    Family: Athlon 64
    Manufacturer: AMD
    ID: C0 0F 00 00 FF FB 8B 07
    Signature: Family 15, Model 12, Stepping 0
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
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
    Version: AMD Athlon(tm) 64 Processor 3300+
    Voltage: 1.5 V
    External Clock: 200 MHz
    Max Speed: 3700 MHz
    Current Speed: 2400 MHz
    Status: Populated, Enabled
    Upgrade: Socket 754
    L1 Cache Handle: 0x0008
    L2 Cache Handle: 0x0009
    L3 Cache Handle: Not Provided
    Serial Number:  
    Asset Tag:  
    Part Number:  

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 1024 MB
    Maximum Total Memory Size: 2048 MB
    Supported Speeds:
        70 ns
        60 ns
        50 ns
    Supported Memory Types:
        Standard
        SDRAM
    Memory Module Voltage: 2.9 V
    Associated Memory Slots: 2
        0x0006
        0x0007
    Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 0 1
    Current Speed: 70 ns
    Type: DIMM
    Installed Size: 512 MB (Double-bank Connection)
    Enabled Size: 512 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: 2
    Current Speed: 70 ns
    Type: DIMM
    Installed Size: 512 MB (Single-bank Connection)
    Enabled Size: 512 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0008, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 128 kB
    Maximum Size: 128 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 4-way Set-associative

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PRIMARY IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SECONDARY IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: FDD
    Internal Connector Type: On Board Floppy
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: 8251 FIFO Compatible

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM1
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator:  
    External Connector Type: DB-9 male
    Port Type: Serial Port 16450 Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM2
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator:  
    External Connector Type: DB-9 male
    Port Type: Serial Port 16450 Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LPT1
    Internal Connector Type: DB-25 female
    External Reference Designator:  
    External Connector Type: DB-25 female
    Port Type: Parallel Port ECP/EPP

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Keyboard
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Mouse
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Other
    Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Other
    Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Other
    Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB4
    External Connector Type: Other
    Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB5
    External Connector Type: Other
    Port Type: USB

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB6
    External Connector Type: Other
    Port Type: USB

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: VIDEO
    External Connector Type: DB-15 female
    Port Type: Video Port

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: Line In
    External Connector Type: None
    Port Type: Audio Port

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: ETHERNET
    External Connector Type: RJ-45
    Port Type: Network Port

Handle 0x001B, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 1
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x001C, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 2
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x001D, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI3
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 3
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x001E, DMI type 10, 12 bytes
On Board Device 1 Information
    Type: Other
    Status: Enabled
    Description:  
On Board Device 2 Information
    Type: Video
    Status: Enabled
    Description:  
On Board Device 3 Information
    Type: Ethernet
    Status: Enabled
    Description:  
On Board Device 4 Information
    Type: Sound
    Status: Enabled
    Description:  

Handle 0x001F, DMI type 9, 13 bytes
System Slot Information
    Designation: AGP
    Type: 32-bit AGP 8x
    Current Usage: Available
    Length: Short
    ID: 1
    Characteristics:
        PME signal is supported

Handle 0x0020, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Long
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1

Handle 0x0021, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0022, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0021
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: DDR
    Type Detail: None
    Speed: 266 MHz
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0023, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0021
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: DDR
    Type Detail: None
    Speed: 266 MHz
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0024, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Array Handle: 0x0021
    Partition Width: 1

Handle 0x0025, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0001FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x0022
    Memory Array Mapped Address Handle: 0x0024
    Partition Row Position: 1

Handle 0x0026, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00020000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x0023
    Memory Array Mapped Address Handle: 0x0024
    Partition Row Position: 1

Handle 0x0027, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

Handle 0x0029, DMI type 144, 12 bytes
OEM-specific Type
    Header and Data:
        90 0C 29 00 00 11 D8 D5 BB 49 C2 01
    Strings:
        SiS630E-MAC

Handle 0x0028, DMI type 11, 5 bytes
OEM Strings
    String 1: bid=52NAheRED3,52NAheRED3;ADPHOAL_STE;C_GOB;IS.N60d;MSDME_STD;MS
    String 2: MON_STD;PROD_MSWE;QUIF_NUE;RN_STD;RP_STD;SFCHK;SPY_BAS;WC_STD;WD
    String 3: _SE;##
    String 4:                                                                 
    String 5:                                                                 
    String 6:                                                                 
    String 7:                                                                 
    String 8:                                                                 
    String 9:                                                                 
    String 10:                                                                 
    String 11:                                                                 
    String 12:                                                                 
    String 13:                                                                 
    String 14:                                                                 
    String 15:                                                                 
    String 16:                                                                 

Handle 0x002A, DMI type 127, 4 bytes
End Of Table

```
:confused: hahaha

:lolflag: I know running these codes can leave you feeling lost and confused. I know from experience. So I'm going to try to help you understand. 

> System Information
    Manufacturer: Compaq Presario 061
    Product Name: PW520AA-ABA SR1463CL NA520
    Version: 0nB1411RE101SALMO00
    Serial Number: CNH5140PHH

This part shows that your computer is a Compaq Presario 061, gives the product name and your serial number. We could probably look it up on HP.com now by using Compaq Presario 061.

> Base Board Information
    Manufacturer: ASUSTek Computer INC.
    Product Name: Salmon 
    Version: 1.04
    Serial Number: MB-1234567890

That part shows the manufacturer and the product name of the motherboard. Seems that ASUS made the board. The serial number is provided as well, which is nice! 

> Manufacturer: Hewlett-Packard
    Type: Desktop

Pretty self explanatory here, right? Confirms that we could possibly find your computer on HP.com. Good sign. :) 

Run through the output of the code yourself and you'll begin to understand what you're looking at. You'll learn a ton! :D

---

### Post by Shadius on 2012-06-03
I believe I have found your computer. Have a look and confirm. [Compaq Presario SR1463CL Desktop PC]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00257657&tmp_task=prodinfoCategory&cc=us&dlc=en&lang=en&lc=en&product=501558")

---

### Post by mimicatastrophe on 2012-06-03
speechless. you are awesome haha thanks so much i already feel my brain expanding and making its little "command prompt" file lol this is great. I am hoping i find someone or some way to install gnome classic and get rid of unity but maybe i will take a break and feel refreshed enough to reinstall lubuntu or x. i have been at this for exactly 1 week almost non stop guess i should have came here first! go figure! =)

---

### Post by mimicatastrophe on 2012-06-03
> **Shadius said:**
> I believe I have found your computer. Have a look and confirm. [Compaq Presario SR1463CL Desktop PC]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00257657&tmp_task=prodinfoCategory&cc=us&dlc=en&lang=en&lc=en&product=501558")

yep yep yep thats her! thanks! \\:D/hehe

---

### Post by Shadius on 2012-06-03
> **mimicatastrophe said:**
> speechless. you are awesome haha thanks so much i already feel my brain expanding and making its little "command prompt" file lol this is great. I am hoping i find someone or some way to install gnome classic and get rid of unity but maybe i will take a break and feel refreshed enough to reinstall lubuntu or x. i have been at this for exactly 1 week almost non stop guess i should have came here first! go figure! =)

I can help you with installing GNOME Classic as well. :) I will provide the method I used to install it. You can give Lubuntu a try. I've heard it's optimal for computers with low specifications.

Run this code in a terminal to install GNOME Tweak Tool:
```
sudo apt-get install gnome-tweak-tool
```

After installation, log out and select Ubuntu Logo drop-down icon and select GNOME Classic, then log in. Done! You can access the tool from **Advanced Settings** in the menu and tweak away!

Here's a video to help!
[GNOME Tweak Tool]("http://www.youtube.com/watch?v=uZAAjCbIFjg")

---

### Post by mimicatastrophe on 2012-06-03
> **Shadius said:**
> I can help you with installing GNOME Classic as well. :) I will provide the method I used to install it. You can give Lubuntu a try. I've heard it's optimal for computers with low specifications.

Run this code in a terminal to install GNOME Tweak Tool:
```
sudo apt-get install gnome-tweak-tool
```After installation, log out and select Ubuntu Logo drop-down icon and select GNOME Classic, then log in. Done! You can access the tool from **Advanced Settings** in the menu and tweak away!
  fabulous! thanks! going to do that now!!
):P

---

### Post by mimicatastrophe on 2012-06-03
so i completely forgot that it was not that the computer froze-- it just again upon logging in on classic did this-- it appeared to be frozen but music continues and the mouse is perfect but i am unable to click on anything. i dont know many keyboard short cuts on linux but i tried a few windows like ctrl alt del and nothing...had to restart. i would like to think it wont happen again but since its been more than once (not during this install but i have reinstalled a few times before)

---

### Post by Shadius on 2012-06-03
> **mimicatastrophe said:**
> so i completely forgot that it was not that the computer froze-- it just again upon logging in on classic did this-- it appeared to be frozen but music continues and the mouse is perfect but i am unable to click on anything. i dont know many keyboard short cuts on linux but i tried a few windows like ctrl alt del and nothing...had to restart. i would like to think it wont happen again but since its been more than once (not during this install but i have reinstalled a few times before)

You can do **Alt** + **PrintScreen** + **R** + **E** + **I** + **S** + **U** + **B**, better known as **R**eboot **E**ven **I**f **S**ystem **U**tterly **B**roken, when your Ubuntu freezes. Remember, Ubuntu Linux is **not** Windows so those Windows commands won't work. 

This will explain a bit more: [R E I S U B]("http://www.ubuntu-unleashed.com/2008/05/howto-restart-ubuntu-safely-when-it-is.html")

---

### Post by matt_symes on 2012-06-03
Hi

> **Shadius said:**
> You can do **Alt** + **PrintScreen** + **R** + **E** + **I** + **S** + **U** + **B**, better known as **R**eboot **E**ven **I**f **S**ystem **U**tterly **B**roken, when your Ubuntu freezes. Remember, Ubuntu Linux is **not** Windows so those Windows commands won't work. 

This will explain a bit more: [R E I S U B]("http://www.ubuntu-unleashed.com/2008/05/howto-restart-ubuntu-safely-when-it-is.html")

...or BUSIER spelt backwards :)

Kind regards

---

### Post by mimicatastrophe on 2012-06-03
great to know!! thanks!

---

### Post by Shadius on 2012-06-03
> **matt_symes said:**
> Hi



...or BUSIER spelt backwards :)

Kind regards

I like that one better! Thanks!

---

### Post by mimicatastrophe on 2012-06-04
that  alt prnt scn REISUB doesn't work for the issue at hand. Still computer remains 
"like frozen" with the ability sometimes to move the mouse sometimes not I can never click or select things with mouse or keys aft this point. still happening a couple times a day and I am not running much when it happens really. I am in gnome classic no effects. 

[CENTER]](*,) 
[/CENTER]

---

### Post by idoitprone on 2012-06-04
> **mimicatastrophe said:**
> that  alt prnt scn REISUB doesn't work for the issue at hand. Still computer remains 
"like frozen" with the ability sometimes to move the mouse sometimes not I can never click or select things with mouse or keys aft this point. still happening a couple times a day and I am not running much when it happens really. I am in gnome classic no effects. 

[CENTER]](*,) 
[/CENTER]


you should have 2GB of swap, since you have 1Gb of ram

that freezing is maybe because your system ran out of both ram and swap
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

