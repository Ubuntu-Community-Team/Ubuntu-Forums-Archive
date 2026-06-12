---
title: "How to run CUDA enabled Nvidia card"
date: 2010-05-26
forum: General Help
---

### Post by chaotic_clone01 on 2010-05-26
I have two graphic cards in my system run on ubuntu. One is for the display and other is for the computations:

When I do the *lspci -v*

03:00.0 3D controller: nVidia Corporation Unknown device 05e7 (rev a1)
    Subsystem: nVidia Corporation Unknown device 066a
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d4000000 (64-bit, prefetchable) [size=64M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at d800 [size=128]
    [virtual] Expansion ROM at f9f80000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint IRQ 0

04:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Unknown device b039
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    Expansion ROM at fe000000 [disabled] [size=64K]
    Capabilities: [60] Power Management version 2


But The code  run on GT8800 was faster when compared to running on Tesla C1060 &GeForce2 MX/MX 400(This for video output). Whats the exact problem is the program not taking the Tesla on which I wanted to run the code on?but his is ruled out coz the MX 400 doesnt have the CUDA capability. Where am I going wrong 

please help

Thanks!

Uday

---

### Post by sjunior7 on 2010-09-30
have you installed the cuda toolkit from nvidia...? you also the nvcc compiler to move on, which i think is in this toolkit..

---

