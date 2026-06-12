---
title: "Not all of my RAM is used?"
date: 2011-03-02
forum: General Help
---

### Post by danne on 2011-03-02
Hi,
I've attached a screenshot of the graphic sysmonitor tool..It says I'm only having 2,5GB of ram but I've got 4GB.

Is it a common ubuntu thing or is it my laptop?
(acer aspire 64 bit system, running 32bit ubuntu)

and I'm sorry but It has been a long time since I've used ubuntu, but now that it has become really cool I'm trying it again..so yes another n00b in da house..

thanks in advance!

---

### Post by DanneStrat on 2011-03-02
> **danne said:**
> Hi,
I've attached a screenshot of the graphic sysmonitor tool..It says I'm only having 2,5GB of ram but I've got 4GB.

Is it a common ubuntu thing or is it my laptop?
(acer aspire 64 bit system, running 32bit ubuntu)

and I'm sorry but It has been a long time since I've used ubuntu, but now that it has become really cool I'm trying it again..so yes another n00b in da house..

thanks in advance!

Hi!

You're using a 32-bit operating system on a 64-bit capable system.

That means if you have more than 3 GB of ram then

the 32-bit OS will not make use of it.

One solution would be to use ubuntu 64-bit.

Or we can check if your computer supports PAE

"physical address extension".

Which ubuntu version do you use?

From wikipedia:

"Some operating systems and certain hardware configurations limit the physical memory space to 3 GB on [IA-32]("http://en.wikipedia.org/wiki/IA-32") systems, due to much of the 3&#8211;4 GB region being reserved for hardware addressing; see [3 GB barrier]("http://en.wikipedia.org/wiki/3_GB_barrier"). This is not present in 64-bit architectures, which can use 4 GB of memory and more. However, IA-32 processors from the [Pentium II]("http://en.wikipedia.org/wiki/Pentium_II") onwards allow for a 36-bit *physical* memory address space, using [Physical Address Extension]("http://en.wikipedia.org/wiki/Physical_Address_Extension")  (PAE), which gives a 64 GB physical address range, of which up to 62 GB  may be used by main memory; operating systems that support PAE may not  be limited to 4GB of physical memory, even on IA-32 processors."

[http://en.wikipedia.org/wiki/64-bit#32-bit_vs_64-bit](http://en.wikipedia.org/wiki/64-bit#32-bit_vs_64-bit)

---

### Post by matt_symes on 2011-03-02
Hi

Yes. Use a 64 bit operating system if you have a 64-bit chip. If you want to see if Ubuntu can see all your memory but cannot use it open a terminal and type

```
sudo lshw -C memory
```

Enter your password. It will not be echoed to the screen. That should tell you about cache, memory in banks and firmware.

Kind regards

---

### Post by danne on 2011-03-02
This is the result..4gb after all?

I've been told that 64-bit ubuntu is less stable and has less support or available software..but this isn't true?


 *-firmware              
       description: BIOS
       vendor: Acer
       physical id: 0
       version: V1.14 (09/13/2010)
       size: 1MiB
       capacity: 1472KiB
       capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
  *-memory
       description: System Memory
       physical id: 1a
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: SODIMM Synchronous 1067 MHz (0.9 ns)
          product: M471B5673FH0-CH9
          physical id: 0
          serial: 629D5A32
          slot: DIMM0
          size: 2GiB
          width: 64 bits
          clock: 1067MHz (0.9ns)
     *-bank:1
          description: SODIMM Synchronous 1067 MHz (0.9 ns)
          product: M471B5673FH0-CH9
          physical id: 1
          serial: 629D5A39
          slot: DIMM1
          size: 2GiB
          width: 64 bits
          clock: 1067MHz (0.9ns)
  *-cache:0
       description: L3 cache
       physical id: 2a
       slot: L3 Cache
       size: 3MiB
       capacity: 3MiB
       capabilities: synchronous internal write-through unified
  *-cache:1
       description: L2 cache
       physical id: 2c
       slot: L2 Cache
       size: 256KiB
       capacity: 256KiB
       capabilities: synchronous internal write-through unified
  *-cache:2
       description: L1 cache
       physical id: 2d
       slot: L1 Cache
       size: 32KiB
       capacity: 32KiB
       capabilities: synchronous internal write-through instruction
  *-cache
       description: L1 cache
       physical id: 2b
       slot: L1 Cache
       size: 32KiB
       capacity: 32KiB
       capabilities: synchronous internal write-through data

---

### Post by aeiah on 2011-03-02
ive never had a problem with 64bit, and ive been using it probably since version 8.10 i think.

incidentally, the reason you're seeing 2.5GB and not 3GB is most likely because you have on board graphics that use 512mb - so even when you use the pae kernel or install a 64bit OS you may only see 3.5gb

---

### Post by matt_symes on 2011-03-02
Hi

> I've been told that 64-bit ubuntu is less stable and has less support or available software..but this isn't true?

I think that used to be the case but not so much now. There used to be issues with the libraries if i remember correctly.

```
*-bank:0
description: SODIMM Synchronous 1067 MHz (0.9 ns)
product: M471B5673FH0-CH9
physical id: 0
serial: 629D5A32
slot: DIMM0
size: 2GiB
width: 64 bits
clock: 1067MHz (0.9ns)
*-bank:1
description: SODIMM Synchronous 1067 MHz (0.9 ns)
product: M471B5673FH0-CH9
physical id: 1
serial: 629D5A39
slot: DIMM1
size: 2GiB
width: 64 bits
clock: 1067MHz (0.9ns)
```

Ubuntu can see all your memory but just cant use it. It's a restriction of the kernel you are using.

Kind regards

---

### Post by AgentY on 2011-03-02
Yea, install the 64bit edition as suggested which will detect all of your RAM.

---

### Post by danne on 2011-03-02
> **aeiah said:**
> 
incidentally, the reason you're seeing 2.5GB and not 3GB is most likely because you have on board graphics that use 512mb - so even when you use the pae kernel or install a 64bit OS you may only see 3.5gb

ATI mobility HD 5400 (virtually shares up to 2GB but standalone 512mb, so it's not the case)
 --

I will try 64bit with the next release, but for now it's going more than smooth enough for me ;)

---

### Post by mastablasta on 2011-03-02
perhaps the OP was thinking of 64bit flash which caused problems. I believe they were solved lately.

---

### Post by DanneStrat on 2011-03-02
> This is the result..4gb after all?
 
That shows that you have 4 GB of ram inserted in your

ram slots.

Your 32-bit ubuntu (without pae)

can only use 3 GB of ram but you only see

 2,5 GB and as aeiah wrote, that may be because

512 MB is reserved by your graphics chip.

If you don't feel ready to make the switch to 64-bit

then you can tell me what ubuntu version you're using

and we can try to enable pae so you can make use of that last

GB of ram.

---

### Post by grahammechanical on 2011-03-02
I have used 32 bit Ubuntu and I am now using 64 bit Ubuntu both on the same machine. I have not had any problems in using 64 bit Ubuntu.

The good news is that we can use a 32 bit OS on a 64 bit CPU if we do experience problems with the 64 bit OS. Thanks Developer guys!

Regards.

---

