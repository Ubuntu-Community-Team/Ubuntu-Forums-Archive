---
title: "Processor speed"
date: 2010-11-10
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-11-10
I set ubuntu 10.04.1 up on an older laptop the cpu scaling applet reads 800Mhz at all times even though it is set for 1.73GHz (userspace)
is the applet not registering the current speed? or is it only able to use 800Mhz for some reason
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175361&d=1289513972[/IMG] cpu governor is ondemand
model
dell latitude D510
lspci output:
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments Device 8037
02:03.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
``````
Processor Information
    Socket Designation: Microprocessor
    Type: Central Processor
    Family: Pentium M
    Manufacturer: Intel
    ID: D8 06 00 00 FF FB E9 AF
    Signature: Type 0, Family 6, Model 13, Stepping 8
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
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (Fast floating-point save and restore)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Not Specified
    Voltage: 3.3 V
    External Clock: 133 MHz
    Max Speed: 1800 MHz
    Current Speed: 800 MHz
    Status: Populated, Enabled
    Upgrade: None
    L1 Cache Handle: 0x0700
    L2 Cache Handle: 0x0701
    L3 Cache Handle: Not Provided
```

---

### Post by efflandt on 2010-11-10
It depends if your computer is doing any strenuous work.  In some cases it may seem like your computer is not running as fast as you might think it should, but if the speed bog is disk access, that does not really require that much cpu time.

Most of the time my computer is idling:
```
grep MHz /proc/cpuinfo
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
```If I run glxgears without vsync it works my gpu 100%, but not my cpu (i5 650):
```
grep MHz /proc/cpuinfo
cpu MHz        : 3201.000
cpu MHz        : 3201.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
```

---

### Post by pqwoerituytrueiwoq on 2010-11-10
it should be running faster
it will not go up for anything 
it is like the os sees the 1.73GHz but only allows 800Mhz for use
i thought is was cause of dirt in it but it is clean now (removed cat hair and dust)
it has 4 speeds if i set it for performance it stays at 800Mhz
even cpu intensive flash stuff does not send it up when on "ondemand" 
over clocking software may be the only way

---

### Post by Frogs Hair on 2010-11-10
Just out of curiosity what is your memory speed in mhz ?

---

### Post by pqwoerituytrueiwoq on 2010-11-10
> **Frogs Hair said:**
> Just out of curiosity what is your memory speed in mhz ?
that took a while to find (has 2 of these installed)
```
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM_A
    Bank Locator: Not Specified
    Type: DDR
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 7F7F7F0B00000000
    Serial Number: A5493400
    Asset Tag: Not Specified
    Part Number: Not Specified
```

---

### Post by neliudek on 2010-11-11
i've got the same problem, my laptop is Dell Vostro 1500 and it's on 800Mhz all the time, when earlier i could use up to 2GHz, yesterday made clean install, and the problem still hasnt gone

---

### Post by dcstar on 2010-11-11
> **neliudek said:**
> i've got the same problem, my laptop is Dell Vostro 1500 and it's on 800Mhz all the time, when earlier i could use up to 2GHz, yesterday made clean install, and the problem still hasnt gone

Install the CPU Frequency Scaling Applet and see if you actually have a "problem".

You can also install the **powernowd** package.

---

### Post by pqwoerituytrueiwoq on 2010-11-11
> **dcstar said:**
> Install the CPU Frequency Scaling Applet and see if you actually have a "problem".

You can also install the **powernowd** package.
that sounds good (powernowd) i will try that asap will be a few hours though

---

### Post by SlugSlug on 2010-11-11
My moneys on intel speedstep

it will lower your Mhz if CPU is not under load to save on power..

try running some CPU intensive apps (play a HD film)  see how it goes

---

### Post by mc4man on 2010-11-11
What you haven't mentioned is what does the applet show directly after boot when you first get to desktop.
Unless you've changed something, by default it will boot in performance mode and then switch to ondemand (60 sec after the ondemand script was initiated.
If your boot to desktop is less than 60 sec  does the applet show full cpu, then ondemand?

What you may want to ck. is the cpu temp right after you get to the desktop, if a throttle down is reached at any point, then cpu scaling will be locked at the lowest speed even if the temp returns to normal or pre throttle down level.
Here this will show the temp, may be different for you.
```
cat /proc/acpi/thermal_zone/THM/temperature
```

If you were throttling down during boot then your temp may seem ok, you could ck. the cpu state though I can't say how accurate or relevant it is
```
cat /proc/acpi/processor/CPU0/throttling
```

What i might do, if there was a possibility that the cpu was throttling down during boot and the boot to desktop time was around 60 sec or more, would be to extend the run at performance to a higher value and see if the cpu was able to run at full speed.
ondemand script is in /etc/init.d - raise the sleep value

---

### Post by neliudek on 2010-11-11
> **dcstar said:**
> Install the CPU Frequency Scaling Applet and see if you actually have a "problem".
???? you think i didn't ? I've tried applet from AWN,now , after clean install tried the one which already is in 10.10, no luck. How  do i start/use powernowd? Can't find it anywhere after install

---

### Post by pqwoerituytrueiwoq on 2010-11-11
> **SlugSlug said:**
> My moneys on intel speedstep

it will lower your Mhz if CPU is not under load to save on power..

try running some CPU intensive apps (play a HD film)  see how it goes
would you consider 90-100% cpu to be high load?
it stays at 800Mhz the text is purple but that could be a theme setting
i am hoping powernowd will fix it
i do not think it could handle an hd film at full speed
not even a flash game that uses 70% of my 2ghz dual core system will move it above 800Mhz
@neliudek
from what i read you just install it and it works ([http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7448580](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7448580))

---

### Post by Frogs Hair on 2010-11-11
Information: [http://en.wikipedia.org/wiki/Pentium_M](http://en.wikipedia.org/wiki/Pentium_M)

---

### Post by pqwoerituytrueiwoq on 2010-11-11
powernowd did not help T_T
added pic to 1st post

---

### Post by pqwoerituytrueiwoq on 2010-11-14
> **SlugSlug said:**
> My moneys on intel speedstep

it will lower your Mhz if CPU is not under load to save on power..

try running some CPU intensive apps (play a HD film)  see how it goes
you were right (speedstep) glad i did not put money on that bet lol

---

