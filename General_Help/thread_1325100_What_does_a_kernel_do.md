---
title: "What does a kernel do?"
date: 2009-11-13
forum: General Help
---

### Post by mahela007 on 2009-11-13
What does the kernel do in an operating system?

---

### Post by t0p on 2009-11-13
[http://en.wikipedia.org/wiki/Kernel_%28computing%29](http://en.wikipedia.org/wiki/Kernel_%28computing%29)

---

### Post by Commander_Keen on 2009-11-13
Its the heart and soul of the OS.. with out.. the PC would just be a shell

---

### Post by ducttapeandzipties on 2009-11-13
The kernel _IS_ the operating system, it's what is doing all the work at the basic level.  X, pakcages, etc are just add ons basically.

---

### Post by RandomBrazilian on 2009-11-13
It provides an interface between the Operational Sistem and the hardware.

---

### Post by wojox on 2009-11-13
The kernel acts as a mediator for your programs and your hardware. First, it does (or arranges for) the memory management for all of the running programs (processes), and makes sure that they all get a fair (or unfair, if you please) share of the processor's cycles. In addition, it provides a nice, fairly portable interface for programs to talk to your hardware.

There is certainly more to the kernel's operation than this, but these basic functions are the most important to know.

---

### Post by mahela007 on 2009-11-13
Is it the kernel that takes user input or X?

---

### Post by Commander_Keen on 2009-11-13
X takes the user import and converts it, to data that can be read by the Kernal

---

### Post by amauk on 2009-11-13
An operating system is an extremely complex thing, and is typically built up in layers - each layer built off of the previous one

A Kernel is the lowest layer
it's primary function is manage the hardware, and present a standard API to the upper layers of the OS

a hard drive and a floppy drive are very different pieces of hardware. The actual method of operating those two devices are very different, however the end results are very similar
(ability to read / write data to the device)
The kernel abstracts away the physical differences of those two devices, and presents a standard interface for communication with storage devices.
The upshot is that higher layers of the OS need not worry about the type of device, instead these higher levels build off of the kernel's standard hardware interfaces

This is a simple example, and kernels typically do a myriad of different tasks, including memory management and process scheduling

but at the heart, a kernel will abstract out hardware differences so that programs higher up the chain do not have to be concerned with physical hardware

---

