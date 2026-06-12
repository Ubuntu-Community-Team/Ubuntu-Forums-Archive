---
title: "CPU frequency scaling unsupported"
date: 2010-10-09
forum: General Help
---

### Post by P4man on 2010-10-09
I recently bought a replacement motherboard for my venerable core 2 duo. Now when I over or underclock my cpu, I can no longer scale the frequency in ubuntu. 

Its rather odd, once I set the FSB speed to manual in the bios, even at stock speed or below, I no longer have any working CPU governors in ubuntu. Its stuck at maximum speed. CPU Frequency Scaling Monitor gives me the above error and shows nothing.  It still clocks up and down dynamically in windows. When I set the BIOS to auto, it works as expected.

The motherboard is a gigabyte GA-965P-DS4 running the latest bios now. Running 10.10, but the same issue is observed in 10.04 and 9.10

Its clearly related to the BIOS and this is not a very big issue (though I dont like giving up a 50% stable overclock), but if anyone has any ideas how to make it work, it would be appreciated.

---

### Post by dcstar on 2010-10-09
> **P4man said:**
> I recently bought a **replacement motherboard** for my venerable core 2 duo. Now when I over or underclock my cpu, I can no longer scale the frequency in ubuntu. 
........

Did you you a **full** reinstall of all your Ubuntu systems of just plug them into the new hardware?

---

### Post by psusi on 2010-10-10
What cpu is this?  And what does cat /proc/acpi/processor/CPU0/info say, both with and without the overclock?

---

### Post by P4man on 2010-10-10
Its a fresh install. The CPU is a core2duo E6400.

This is overclocked:

```
~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   no
power management:        no
throttling control:      yes
limit interface:         yes
```

Ill add stock speed in a minute. Looks you are on to something.
edit. or maybe not. This is at stock speed with cpu scaling working:

```
$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   no
power management:        no
throttling control:      yes
limit interface:         yes
```

---

### Post by P4man on 2010-10-10
Another pointer perhaps.
At stock speed, I see this:

```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
conservative ondemand userspace powersave performance 

$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
2133000 1600000 
```

Just like youd expect.

When I set FSB control to manual in the bios, I dont even have a /sys/devices/system/cpu/cpu0/cpufreq folder:

```
~$ ls  /sys/devices/system/cpu/cpu0
cache  crash_notes  node0  thermal_throttle  topology

```

---

### Post by sendblink23 on 2010-10-10
I would ask 1 thing

Do you see a performance difference(I mean is it better when its overclocked on *linux - compared to the stock settings)?


If on overclocked the performance is vastly horrible.. then i would understand your pain, but if the performance is better.. simply ignore the issue your are currently hassling about.

---

### Post by P4man on 2010-10-10
In linux, no I dont run many things that benefit from 3+ GHz cpu speeds. But I dual boot in to windows for some games, and there the difference is day and night (for my fav game from 2.1 to 3.2 GHz is the difference between unplayable and rather fluid). 

So its a bit cumbersome to go in to the bios each time to change the FSB and ram speeds.. or have my cpu run unnecessarily hot in linux.

Like I said in my first post, its not a major issue, but if it can be solved somehow it would be great.

---

### Post by sendblink23 on 2010-10-10
> **P4man said:**
> In linux, no I dont run many things that benefit from 3+ GHz cpu speeds. But I dual boot in to windows for some games, and there the difference is day and night (for my fav game from 2.1 to 3.2 GHz is the difference between unplayable and rather fluid). 

So its a bit cumbersome to go in to the bios each time to change the FSB and ram speeds.. or have my cpu run unnecessarily hot in linux.

Like I said in my first post, its not a major issue, but if it can be solved somehow it would be great.

Do you have in your bios a feature like: cool n quiet    <-- that's on AMD....  but is there a feature like that on Intel ? that way when you are just using the computer regularly it will run at a lower the CPU frequency & voltage - but when using an intensive app it will push to your overclock speed

In other words on linux it will be running very cold unless you use an app that uses your resources

This is just an idea so that you don't have to keep switching between overclocks on your Bios - worrying about running hot when not in full use

---

### Post by P4man on 2010-10-10
> **sendblink23 said:**
> Do you have in your bios a feature like: cool n quiet    <-- that's on AMD....  but is there a feature like that on Intel ? that way when you are just using the computer regularly it will run at a lower the CPU frequency & voltage - but when using an intensive app it will push to your overclock speed

In other words on linux it will be running very cold unless you use an app that uses your resources

Its called EIST on intel, and that dynamic clock scaling is precisely whats not working when overclocked and precisely what I want to fix.

---

### Post by sendblink23 on 2010-10-10
> **P4man said:**
> Its called EIST on intel, and that dynamic clock scaling is precisely whats not working when overclocked and precisely what I want to fix.

And how do you know its not working on Linux?

Do you monitor your temps, to see if it goes low when on idle.. then on using software if it goes much higher? *Compare them on Windows & Linux

---

### Post by P4man on 2010-10-10
It is working at its full speed and not clocking down when idle

```
~$ cat /proc/cpuinfo | grep -i Mhz
cpu MHz		: 2999.915
cpu MHz		: 2999.915

```

( I have it set at 375 MHz FSB in the bios now, which results in 3 GHz. it can go up to ~410 but I like some safety margin)

Idle temps are what youd expect at this overclocked speed, considerably higher than in windows where the clock and vcore are scaled down on idle, even with a manual FSB setting:

Doing nothing:
```
sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +54.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +56.0°C  (high = +84.0°C, crit = +100.0°C)  
```

In windows its around 40-42 at this 3 GHz clock. Loaded temps ought to be very similar, since in both cases the cpu will run at full clock and vcore.

---

### Post by psusi on 2010-10-10
What does /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver say when not overclocked?

It looks like your bios does not export ACPI P-state control like it should.  AMD has the powernow-k8 driver take over and do frequency scaling when ACPI doesn't, so I imagine there must be a similar driver for Intel that doesn't like it when you're overclocked.  It also is odd that even when it is working you only get one frequency other than full speed.  That is pretty weak.  I get a total of 6.

At the end of the day, the bios is supposed to provide ACPI P-states to do this, so you should complain to your motherboard manufacturer.

---

### Post by P4man on 2010-10-10
> **psusi said:**
> What does /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver say when not overclocked?

```

~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver 
acpi-cpufreq

```

> It looks like your bios does not export ACPI P-state control like it should.  AMD has the powernow-k8 driver take over and do frequency scaling when ACPI doesn't, so I imagine there must be a similar driver for Intel that doesn't like it when you're overclocked.  It also is odd that even when it is working you only get one frequency other than full speed.  That is pretty weak.  I get a total of 6.

Well, its an old CPU. It only supports 2 states, but thats better than one :)

> At the end of the day, the bios is supposed to provide ACPI P-states to do this, so you should complain to your motherboard manufacturer.

Yeah Im not blaming linux, its clearly a bios issue (and not the only one, it does other weird things when you enable manual FSB control, like not always posting, regardless of frequencies, when something is connected to the internal USB header). Its just, forgive me for saying, it works in windows, so I was hoping there was a way to force this in linux.

For all its flaws, this motherboard is a stellar overclocker.

---

### Post by psusi on 2010-10-10
Hrm... it looks like you ARE using acpi P-state control.  What other files do you have and what do they contain in /proc/acpi/processor/CPU0 when not overclocked?

My guess is that your bios disables the P-state when you overclock.

---

### Post by P4man on 2010-10-10
> **psusi said:**
> Hrm... it looks like you ARE using acpi P-state control. 

Without manual FSB setting (ie, no "overclock") in the bios, yeah. Everything works fine then. I have access to the usual acpi CPU governors and clock scaling works out of the box.

>  What other files do you have and what do they contain in /proc/acpi/processor/CPU0 when not overclocked?

These (at default speed settings):

```
bob@bob-desktop:~$ ls /proc/acpi/processor/CPU0 
info  limit  power  throttling
bob@bob-desktop:~$ cat /proc/acpi/processor/CPU0/info 
processor id:            0
acpi id:                 0
bus mastering control:   no
power management:        no
throttling control:      yes
limit interface:         yes
bob@bob-desktop:~$ cat /proc/acpi/processor/CPU0/limit
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0
bob@bob-desktop:~$ cat /proc/acpi/processor/CPU0/power
active state:            C0
max_cstate:              C8
maximum allowed latency: 2000000000 usec
states:
    C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000] duration[00000000000000000000]
bob@bob-desktop:~$ cat /proc/acpi/processor/CPU0/throttling 
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%
```



> My guess is that your bios disables the P-state when you overclock.

Looks like it. Question is, how then does windows get around it, and can I do something similar in linux?

---

### Post by psusi on 2010-10-10
Often times the ACPI tables provided by the bios are buggy or explicitly disable certain things when they detect the host OS is not a certain version of windows.  It also could be that they have a windows driver that does the frequency scaling without using acpi.  There was a thread somewhere on the forums about how to disassemble your DSDT and try to fix it, or pass a kernel parameter to have it lie to the bios and claim to be windows.

---

### Post by P4man on 2010-10-11
Ill give disassembling the DSDT a shot, but having no clue about that I doubt Ill be able to find and fix a bug in there. Im also unsure what I would do with a fixed DSDT, should I flash my bios with it?

Anyway, Ill google on it and see where it goes. Probably not very far :)

---

### Post by mc4man on 2010-10-11
this was the post on
[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

read the update at the bottom about karmic and later kernels

---

### Post by P4man on 2010-10-11
> **mc4man said:**
> this was the post on
[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

read the update at the bottom about karmic and later kernels

Thanks for the link. I disassembled my dsdt, but as expected, I cant make much sense of it:

```
/*
 * Intel ACPI Component Architecture
 * AML Disassembler version 20090521
 *
 * Disassembly of dsdt.dat, Mon Oct 11 09:05:34 2010
 *
 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x00004B35 (19253)
 *     Revision         0x01 **** ACPI 1.0, no 64-bit math support
 *     Checksum         0x9E
 *     OEM ID           "GBT   "
 *     OEM Table ID     "GBTUACPI"
 *     OEM Revision     0x00001000 (4096)
 *     Compiler ID      "MSFT"
 *     Compiler Version 0x0100000C (16777228)
 */
DefinitionBlock ("dsdt.aml", "DSDT", 1, "GBT   ", "GBTUACPI", 0x00001000)
{
    Scope (\_PR)
    {
        Processor (\_PR.CPU0, 0x00, 0x00000410, 0x06) {}
        Processor (\_PR.CPU1, 0x01, 0x00000410, 0x06) {}
        Processor (\_PR.CPU2, 0x02, 0x00000410, 0x06) {}
        Processor (\_PR.CPU3, 0x03, 0x00000410, 0x06) {}
    }

    Name (\_S0, Package (0x04)
    {
        0x00, 
        0x00, 
        0x00, 
        0x00
    })
    Name (\SS1, Package (0x04)
    {
        0x01, 
        0x00, 
        0x00, 
        0x00
    })
    Name (\_S3, Package (0x04)
    {
        0x05, 
        0x00, 
        0x00, 
        0x00
    })
    Name (\_S4, Package (0x04)
    {
        0x06, 
        0x00, 
        0x00, 
        0x00
    })
    Name (\_S5, Package (0x04)
    {
        0x07, 
        0x00, 
        0x00, 
        0x00
    })
    Name (FLAG, 0x00)
    Name (STAT, 0x00)
    OperationRegion (SMOD, SystemMemory, 0x000FF840, 0x01)
    Field (SMOD, ByteAcc, NoLock, Preserve)
    {
            ,   7, 
        SUSF,   1
    }

    OperationRegion (\DEBG, SystemIO, 0x80, 0x01)
    Field (\DEBG, ByteAcc, NoLock, Preserve)
    {
        DBG1,   8
    }

    OperationRegion (RCRB, SystemMemory, 0xFED1C000, 0x4000)
    Field (RCRB, DWordAcc, Lock, Preserve)
    {
                Offset (0x3404), 
            ,   7, 
        HPTF,   1
    }

    OperationRegion (ELKM, SystemMemory, 0x000FFFEA, 0x01)
    Field (ELKM, ByteAcc, NoLock, Preserve)
    {
            ,   1, 
            ,   1, 
        ELSO,   1, 
            ,   1, 
            ,   1, 
            ,   1, 
            ,   1
    }

    OperationRegion (EXTM, SystemMemory, 0x000FF830, 0x10)
    Field (EXTM, WordAcc, NoLock, Preserve)
    {
        ROM1,   16, 
        RMS1,   16, 
        ROM2,   16, 
        RMS2,   16, 
        ROM3,   16, 
        RMS3,   16, 
        AMEM,   32
    }

    OperationRegion (\SMIC, SystemIO, 0xB2, 0x01)
    Field (\SMIC, ByteAcc, NoLock, Preserve)
    {
        SCP,    8
    }

    OperationRegion (\GP2C, SystemIO, 0x042C, 0x02)
    Field (\GP2C, ByteAcc, NoLock, Preserve)
    {
        G2C1,   8, 
        G2C2,   8
    }

    OperationRegion (\GBLE, SystemIO, 0x0421, 0x01)
    Field (\GBLE, ByteAcc, NoLock, Preserve)
    {
        ESMI,   8
    }

    OperationRegion (APMP, SystemIO, 0xB2, 0x02)
    Field (APMP, ByteAcc, NoLock, Preserve)
    {
        APMC,   8, 
        APMD,   8
    }

    OperationRegion (\AGPS, SystemIO, 0x0438, 0x04)
    Field (\AGPS, ByteAcc, NoLock, Preserve)
    {
        GPSE,   16, 
        GPSS,   16
    }

    OperationRegion (\GPCN, SystemIO, 0x0442, 0x01)
    Field (\GPCN, ByteAcc, NoLock, Preserve)
    {
        THRP,   1, 
                Offset (0x01)
    }

    Name (OSFX, 0x01)
    Name (OSFL, 0x01)
    Method (STRC, 2, NotSerialized)
    {
        If (LNotEqual (SizeOf (Arg0), SizeOf (Arg1)))
        {
            Return (0x00)
        }

        Add (SizeOf (Arg0), 0x01, Local0)
        Name (BUF0, Buffer (Local0) {})
        Name (BUF1, Buffer (Local0) {})
        Store (Arg0, BUF0)
        Store (Arg1, BUF1)
        While (Local0)
        {
            Decrement (Local0)
            If (LNotEqual (DerefOf (Index (BUF0, Local0)), DerefOf (Index (
                BUF1, Local0))))
            {
                Return (Zero)
            }
        }

        Return (One)
    }

    OperationRegion (INFO, SystemMemory, 0x000FF840, 0x02)
    Field (INFO, ByteAcc, NoLock, Preserve)
    {
        KBDI,   1, 
        RTCW,   1, 
        PS2F,   1, 
        IRFL,   2, 
        DISE,   1, 
        SSHU,   1
    }

    Scope (\)
    {
        Name (PICF, 0x00)
        Method (_PIC, 1, NotSerialized)
        {
            Store (Arg0, PICF)
        }
    }

    Method (\_PTS, 1, NotSerialized)
    {
        Or (Arg0, 0xF0, Local0)
        Store (Local0, DBG1)
        OSTP ()
        If (LEqual (Arg0, 0x01)) {}
        If (LEqual (Arg0, 0x03)) {}
        If (LEqual (Arg0, 0x05))
        {
            Store (ESMI, Local0)
            And (Local0, 0xFB, Local0)
            Store (Local0, ESMI)
        }

        If (LEqual (Arg0, 0x04))
        {
            If (LNot (PICF))
            {
                Sleep (0x64)
            }
        }
    }

    Method (\_WAK, 1, NotSerialized)
    {
        Store (0xFF, DBG1)
        If (LEqual (Arg0, 0x03))
        {
            Store (0x8F, SCP)
        }

        If (LEqual (Arg0, 0x04))
        {
            If (LEqual (OSFL, 0x00))
            {
                If (LEqual (OSFX, 0x03))
                {
                    Store (0x59, SMIP)
                }
                Else
                {
                    Store (0x58, SMIP)
                }
            }

            If (LEqual (OSFL, 0x01))
            {
                Store (0x56, SMIP)
            }

            If (LEqual (OSFL, 0x02))
            {
                Store (0x57, SMIP)
            }

            If (LEqual (OSFX, 0x03))
            {
                Store (0x59, SMIP)
            }
        }

        If (LEqual (Arg0, 0x01)) {}
        If (OSFL)
        {
            Notify (\_SB.PWRB, 0x02)
        }
        Else
        {
            If (LEqual (RTCW, 0x00))
            {
                Notify (\_SB.PWRB, 0x02)
            }
        }

        Notify (\_SB.PCI0.USB0, 0x00)
        Notify (\_SB.PCI0.USB1, 0x00)
        Notify (\_SB.PCI0.USB2, 0x00)
        Notify (\_SB.PCI0.USB3, 0x00)
        Notify (\_SB.PCI0.USB4, 0x00)
    }

    Scope (\_SI)
    {
        Method (_MSG, 1, NotSerialized)
        {
            Store (Local0, Local0)
        }

        Method (_SST, 1, NotSerialized)
        {
            Store (Local0, Local0)
        }
    }

    Scope (\_GPE)
    {
        Method (_L08, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.PX40.UAR1, 0x02)
        }

        Method (_L03, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB0, 0x02)
            Notify (\_SB.PWRB, 0x02)
        }

        Method (_L04, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB1, 0x02)
            Notify (\_SB.PWRB, 0x02)
        }

        Method (_L0C, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB2, 0x02)
            Notify (\_SB.PWRB, 0x02)
        }

        Method (_L0E, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB3, 0x02)
            Notify (\_SB.PWRB, 0x02)
            Notify (\_SB.PCI0.US31, 0x02)
            Notify (\_SB.PWRB, 0x02)
        }

        Method (_L05, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB4, 0x02)
            Notify (\_SB.PWRB, 0x02)
        }

        Method (_L0D, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USBE, 0x02)
            Notify (\_SB.PCI0.USE2, 0x02)
            Notify (\_SB.PWRB, 0x02)
            Notify (\_SB.PCI0.AZAL, 0x02)
            Notify (\_SB.PCI0.IGBE, 0x02)
        }

        Method (_L0B, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.HUB0, 0x02)
        }

        Method (_L09, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.PEX0, 0x02)
            Notify (\_SB.PCI0.PEX1, 0x02)
            Notify (\_SB.PCI0.PEX2, 0x02)
            Notify (\_SB.PCI0.PEX3, 0x02)
            Notify (\_SB.PCI0.PEX4, 0x02)
            Notify (\_SB.PCI0.PEX5, 0x02)
        }
    }

    Scope (\_SB)
    {
        Device (PWRB)
        {
            Name (_HID, EisaId ("PNP0C0C"))
            Method (_STA, 0, NotSerialized)
            {
                Return (0x0B)
            }
        }

        Device (PCI0)
        {
            Name (_HID, EisaId ("PNP0A03"))
            Name (_ADR, 0x00)
            Name (_UID, 0x01)
            Name (_BBN, 0x00)
            Method (_S3D, 0, NotSerialized)
            {
                If (LEqual (OSFL, 0x02))
                {
                    Return (0x02)
                }
                Else
                {
                    Return (0x03)
                }
            }

            Method (_STA, 0, NotSerialized)
            {
                Return (0x0F)
            }

            Method (_CRS, 0, NotSerialized)
            {
                Name (BUF0, ResourceTemplate ()
                {
                    WordBusNumber (ResourceConsumer, MinNotFixed, MaxNotFixed, PosDecode,
                        0x0000,             // Granularity
                        0x0000,             // Range Minimum
                        0x003F,             // Range Maximum
                        0x0000,             // Translation Offset
                        0x0040,             // Length
                        ,, )
                    IO (Decode16,
                        0x0CF8,             // Range Minimum
                        0x0CF8,             // Range Maximum
                        0x01,               // Alignment
                        0x08,               // Length
                        )
                    WordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                        0x0000,             // Granularity
                        0x0000,             // Range Minimum
                        0x0CF7,             // Range Maximum
                        0x0000,             // Translation Offset
                        0x0CF8,             // Length
                        ,, , TypeStatic)
                    WordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                        0x0000,             // Granularity
                        0x0D00,             // Range Minimum
                        0xFFFF,             // Range Maximum
                        0x0000,             // Translation Offset
                        0xF300,             // Length
                        ,, , TypeStatic)
                    DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                        0x00000000,         // Granularity
                        0x000A0000,         // Range Minimum
                        0x000BFFFF,         // Range Maximum
                        0x00000000,         // Translation Offset
                        0x00020000,         // Length
                        ,, , AddressRangeMemory, TypeStatic)
                    DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                        0x00000000,         // Granularity
                        0x000C0000,         // Range Minimum
                        0x000DFFFF,         // Range Maximum
                        0x00000000,         // Translation Offset
                        0x00020000,         // Length
                        ,, , AddressRangeMemory, TypeStatic)
                    DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                        0x00000000,         // Granularity
                        0x00100000,         // Range Minimum
                        0xFEBFFFFF,         // Range Maximum
                        0x00000000,         // Translation Offset
                        0xFFF00000,         // Length
                        ,, _Y00, AddressRangeMemory, TypeStatic)
                })
                CreateDWordField (BUF0, \_SB.PCI0._CRS._Y00._MIN, TCMM)
                CreateDWordField (BUF0, \_SB.PCI0._CRS._Y00._LEN, TOMM)
                Add (AMEM, 0x00010000, TCMM)
                Add (TCMM, 0x00010000, TCMM)
                Subtract (0xFEC00000, TCMM, TOMM)
                Return (BUF0)
            }

            Name (PICM, Package (0x1A)
            {
                Package (0x04)
                {
                    0x0003FFFF, 
                    0x00, 
                    \_SB.PCI0.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0003FFFF, 
                    0x01, 
                    \_SB.PCI0.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0003FFFF, 
                    0x02, 
                    \_SB.PCI0.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0003FFFF, 
                    0x03, 
                    \_SB.PCI0.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001BFFFF, 
                    0x00, 
                    \_SB.PCI0.LNK0, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x00, 
                    \_SB.PCI0.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x01, 
                    \_SB.PCI0.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x02, 
                    \_SB.PCI0.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x03, 
                    \_SB.PCI0.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x00, 
                    \_SB.PCI0.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x01, 
                    \_SB.PCI0.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x02, 
                    \_SB.PCI0.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x03, 
                    \_SB.PCI0.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x00, 
                    \_SB.PCI0.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x01, 
                    \_SB.PCI0.LNKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001DFFFF, 
                    0x00, 
                    \_SB.PCI0.LNK1, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001DFFFF, 
                    0x01, 
                    \_SB.PCI0.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001DFFFF, 
                    0x02, 
                    \_SB.PCI0.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001DFFFF, 
                    0x03, 
                    \_SB.PCI0.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001FFFFF, 
                    0x01, 
                    \_SB.PCI0.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001FFFFF, 
                    0x01, 
                    \_SB.PCI0.LNKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001FFFFF, 
                    0x02, 
                    \_SB.PCI0.LNKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0019FFFF, 
                    0x00, 
                    \_SB.PCI0.LNKE, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001AFFFF, 
                    0x00, 
                    \_SB.PCI0.LNKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001AFFFF, 
                    0x01, 
                    \_SB.PCI0.LNKF, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x001AFFFF, 
                    0x02, 
                    \_SB.PCI0.LNKC, 
                    0x00
                }
            })
            Name (APIC, Package (0x1A)
            {
                Package (0x04)
                {
                    0x0003FFFF, 
                    0x00, 
                    0x00, 
                    0x10
                }, 

                Package (0x04)
                {
                    0x0003FFFF, 
                    0x01, 
                    0x00, 
                    0x11
                }, 

                Package (0x04)
                {
                    0x0003FFFF, 
                    0x02, 
                    0x00, 
                    0x12
                }, 

                Package (0x04)
                {
                    0x0003FFFF, 
                    0x03, 
                    0x00, 
                    0x13
                }, 

                Package (0x04)
                {
                    0x001BFFFF, 
                    0x00, 
                    0x00, 
                    0x16
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x00, 
                    0x00, 
                    0x10
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x01, 
                    0x00, 
                    0x11
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x02, 
                    0x00, 
                    0x12
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x03, 
                    0x00, 
                    0x13
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x00, 
                    0x00, 
                    0x10
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x01, 
                    0x00, 
                    0x11
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x02, 
                    0x00, 
                    0x12
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x03, 
                    0x00, 
                    0x13
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x00, 
                    0x00, 
                    0x10
                }, 

                Package (0x04)
                {
                    0x001CFFFF, 
                    0x01, 
                    0x00, 
                    0x11
                }, 

                Package (0x04)
                {
                    0x001DFFFF, 
                    0x00, 
                    0x00, 
                    0x17
                }, 

                Package (0x04)
                {
                    0x001DFFFF, 
                    0x01, 
                    0x00, 
                    0x13
                }, 

                Package (0x04)
                {
                    0x001DFFFF, 
                    0x02, 
                    0x00, 
                    0x12
                }, 

                Package (0x04)
                {
                    0x001DFFFF, 
                    0x03, 
                    0x00, 
                    0x10
                }, 

                Package (0x04)
                {
                    0x001FFFFF, 
                    0x01, 
                    0x00, 
                    0x13
                }, 

                Package (0x04)
                {
                    0x001FFFFF, 
                    0x01, 
                    0x00, 
                    0x13
                }, 

                Package (0x04)
                {
                    0x001FFFFF, 
                    0x02, 
                    0x00, 
                    0x12
                }, 

                Package (0x04)
                {
                    0x0019FFFF, 
                    0x00, 
                    0x00, 
                    0x14
                }, 

                Package (0x04)
                {
                    0x001AFFFF, 
                    0x00, 
                    0x00, 
                    0x10
                }, 

                Package (0x04)
                {
                    0x001AFFFF, 
                    0x01, 
                    0x00, 
                    0x15
                }, 

                Package (0x04)
                {
                    0x001AFFFF, 
                    0x02, 
                    0x00, 
                    0x12
                }
            })
            Method (_PRT, 0, NotSerialized)
            {
                If (LNot (PICF))
                {
                    Return (PICM)
                }
                Else
                {
                    Return (APIC)
                }
            }

            Device (PEX0)
            {
                Name (_ADR, 0x001C0000)
                Method (_STA, 0, NotSerialized)
                {
                    Return (0x0F)
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (Package (0x02)
                    {
                        0x09, 
                        0x05
                    })
                }

                Name (PIC0, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        \_SB.PCI0.LNKA, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        \_SB.PCI0.LNKB, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        \_SB.PCI0.LNKD, 
                        0x00
                    }
                })
                Name (API0, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        0x00, 
                        0x10
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        0x00, 
                        0x11
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        0x00, 
                        0x12
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        0x00, 
                        0x13
                    }
                })
                Method (_PRT, 0, NotSerialized)
                {
                    If (LNot (PICF))
                    {
                        Return (PIC0)
                    }
                    Else
                    {
                        Return (API0)
                    }
                }
            }

            Device (PEX1)
            {
                Name (_ADR, 0x001C0001)
                Method (_STA, 0, NotSerialized)
                {
                    Return (0x0F)
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (Package (0x02)
                    {
                        0x09, 
                        0x05
                    })
                }

                Name (PIC1, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        \_SB.PCI0.LNKB, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        \_SB.PCI0.LNKD, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        \_SB.PCI0.LNKA, 
                        0x00
                    }
                })
                Name (API1, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        0x00, 
                        0x11
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        0x00, 
                        0x12
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        0x00, 
                        0x13
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        0x00, 
                        0x10
                    }
                })
                Method (_PRT, 0, NotSerialized)
                {
                    If (LNot (PICF))
                    {
                        Return (PIC1)
                    }
                    Else
                    {
                        Return (API1)
                    }
                }
            }

            Device (PEX2)
            {
                Name (_ADR, 0x001C0002)
                Method (_STA, 0, NotSerialized)
                {
                    Return (0x0F)
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (Package (0x02)
                    {
                        0x09, 
                        0x05
                    })
                }

                Name (PIC2, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        \_SB.PCI0.LNKD, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        \_SB.PCI0.LNKA, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        \_SB.PCI0.LNKB, 
                        0x00
                    }
                })
                Name (API2, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        0x00, 
                        0x12
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        0x00, 
                        0x13
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        0x00, 
                        0x10
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        0x00, 
                        0x11
                    }
                })
                Method (_PRT, 0, NotSerialized)
                {
                    If (LNot (PICF))
                    {
                        Return (PIC2)
                    }
                    Else
                    {
                        Return (API2)
                    }
                }
            }

            Device (PEX3)
            {
                Name (_ADR, 0x001C0003)
                Method (_STA, 0, NotSerialized)
                {
                    Return (0x0F)
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (Package (0x02)
                    {
                        0x09, 
                        0x05
                    })
                }

                Name (PIC3, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        \_SB.PCI0.LNKD, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        \_SB.PCI0.LNKA, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        \_SB.PCI0.LNKB, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }
                })
                Name (API3, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        0x00, 
                        0x13
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        0x00, 
                        0x10
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        0x00, 
                        0x11
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        0x00, 
                        0x12
                    }
                })
                Method (_PRT, 0, NotSerialized)
                {
                    If (LNot (PICF))
                    {
                        Return (PIC3)
                    }
                    Else
                    {
                        Return (API3)
                    }
                }
            }

            Device (PEX4)
            {
                Name (_ADR, 0x001C0004)
                Method (_STA, 0, NotSerialized)
                {
                    Return (0x0F)
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (Package (0x02)
                    {
                        0x09, 
                        0x05
                    })
                }

                Name (PIC4, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        \_SB.PCI0.LNKA, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        \_SB.PCI0.LNKB, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        \_SB.PCI0.LNKD, 
                        0x00
                    }
                })
                Name (API4, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        0x00, 
                        0x10
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        0x00, 
                        0x11
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        0x00, 
                        0x12
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        0x00, 
                        0x13
                    }
                })
                Method (_PRT, 0, NotSerialized)
                {
                    If (LNot (PICF))
                    {
                        Return (PIC4)
                    }
                    Else
                    {
                        Return (API4)
                    }
                }
            }

            Device (PEX5)
            {
                Name (_ADR, 0x001C0005)
                Method (_STA, 0, NotSerialized)
                {
                    Return (0x0F)
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (Package (0x02)
                    {
                        0x09, 
                        0x05
                    })
                }

                Name (PIC5, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        \_SB.PCI0.LNKB, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        \_SB.PCI0.LNKD, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        \_SB.PCI0.LNKA, 
                        0x00
                    }
                })
                Name (API5, Package (0x04)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        0x00, 
                        0x11
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        0x00, 
                        0x12
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        0x00, 
                        0x13
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        0x00, 
                        0x10
                    }
                })
                Method (_PRT, 0, NotSerialized)
                {
                    If (LNot (PICF))
                    {
                        Return (PIC5)
                    }
                    Else
                    {
                        Return (API5)
                    }
                }
            }

            Device (\_SB.PCI0.PEX5.JMB0)
            {
                Name (_ADR, 0x00)
                Name (PIOT, Package (0x05)
                {
                    0x0258, 
                    0x0186, 
                    0x014A, 
                    0xB4, 
                    0x78
                })
                Name (MDMA, Package (0x03)
                {
                    0x01E0, 
                    0x96, 
                    0x78
                })
                Name (UDMA, Package (0x07)
                {
                    0x78, 
                    0x50, 
                    0x3C, 
                    0x28, 
                    0x1E, 
                    0x14, 
                    0x0F
                })
                OperationRegion (CF40, PCI_Config, 0x40, 0x04)
                Field (CF40, ByteAcc, NoLock, Preserve)
                {
                        ,   3, 
                    CAB0,   1, 
                        ,   18, 
                    SWAP,   1, 
                    CHN0,   1, 
                            Offset (0x04)
                }

                OperationRegion (CF80, PCI_Config, 0x80, 0x04)
                Field (CF80, ByteAcc, NoLock, Preserve)
                {
                        ,   19, 
                    CAB1,   1, 
                            Offset (0x03), 
                    CHN1,   1, 
                            Offset (0x04)
                }

                Name (IDEB, Buffer (0x14) {})
                CreateDWordField (IDEB, 0x00, GTM0)
                CreateDWordField (IDEB, 0x04, GTM1)
                CreateDWordField (IDEB, 0x08, GTM2)
                CreateDWordField (IDEB, 0x0C, GTM3)
                CreateDWordField (IDEB, 0x10, GTM4)
                Name (PMIO, 0x04)
                Name (PMDM, 0x06)
                Name (PSIO, 0x04)
                Name (PSDM, 0x06)
                Name (SMIO, 0x04)
                Name (SMDM, 0x06)
                Name (SSIO, 0x04)
                Name (SSDM, 0x06)
                Name (MODP, 0x05)
                Name (MODS, 0x05)
                Device (SDE0)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Store (DerefOf (Index (PIOT, PMIO)), Local0)
                        Store (DerefOf (Index (PIOT, PSIO)), Local2)
                        Store (0x1A, Local4)
                        If (LAnd (MODP, 0x01))
                        {
                            Store (DerefOf (Index (UDMA, PMDM)), Local1)
                            If (LGreater (PMDM, 0x02))
                            {
                                If (LAnd (LNotEqual (SWAP, 0x01), LEqual (CHN1, 0x01)))
                                {
                                    If (CAB1)
                                    {
                                        Store (0x02, PMDM)
                                        Store (DerefOf (Index (UDMA, PMDM)), Local1)
                                    }
                                }

                                If (LAnd (LEqual (SWAP, 0x01), LEqual (CHN0, 0x01)))
                                {
                                    If (CAB0)
                                    {
                                        Store (0x02, PMDM)
                                        Store (DerefOf (Index (UDMA, PMDM)), Local1)
                                    }
                                }
                            }

                            Or (Local4, 0x01, Local4)
                        }
                        Else
                        {
                            Store (DerefOf (Index (MDMA, PMDM)), Local1)
                        }

                        If (LAnd (MODP, 0x04))
                        {
                            Store (DerefOf (Index (UDMA, PSDM)), Local3)
                            If (LGreater (PSDM, 0x02))
                            {
                                If (LAnd (LNotEqual (SWAP, 0x01), LEqual (CHN1, 0x01)))
                                {
                                    If (CAB1)
                                    {
                                        Store (0x02, PSDM)
                                        Store (DerefOf (Index (UDMA, PSDM)), Local3)
                                    }
                                }

                                If (LAnd (LEqual (SWAP, 0x01), LEqual (CHN0, 0x01)))
                                {
                                    If (CAB0)
                                    {
                                        Store (0x02, PSDM)
                                        Store (DerefOf (Index (UDMA, PSDM)), Local3)
                                    }
                                }
                            }

                            Or (Local4, 0x04, Local4)
                        }
                        Else
                        {
                            Store (DerefOf (Index (MDMA, PSDM)), Local3)
                        }

                        Store (Local0, GTM0)
                        Store (Local1, GTM1)
                        Store (Local2, GTM2)
                        Store (Local3, GTM3)
                        Store (Local4, GTM4)
                        Return (IDEB)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (Arg0, IDEB)
                        Store (GTM0, Local0)
                        Store (GTM1, Local1)
                        Store (GTM2, Local2)
                        Store (GTM3, Local3)
                        Store (GTM4, Local4)
                        If (LAnd (LNotEqual (Local0, 0xFFFFFFFF), LNotEqual (Local0, 0x00)))
                        {
                            Store (Match (PIOT, MEQ, Local0, MTR, 0x00, 0x00), PMIO)
                        }

                        If (LAnd (LNotEqual (Local1, 0xFFFFFFFF), LNotEqual (Local1, 0x00)))
                        {
                            If (LAnd (Local4, 0x01))
                            {
                                Store (Match (UDMA, MEQ, Local1, MTR, 0x00, 0x00), PMDM)
                            }
                            Else
                            {
                                Store (Match (MDMA, MEQ, Local1, MTR, 0x00, 0x00), PMDM)
                            }
                        }

                        If (LAnd (LNotEqual (Local2, 0xFFFFFFFF), LNotEqual (Local2, 0x00)))
                        {
                            Store (Match (PIOT, MEQ, Local2, MTR, 0x00, 0x00), PSIO)
                        }

                        If (LAnd (LNotEqual (Local3, 0xFFFFFFFF), LNotEqual (Local3, 0x00)))
                        {
                            If (LAnd (Local4, 0x04))
                            {
                                Store (Match (UDMA, MEQ, Local3, MTR, 0x00, 0x00), PSDM)
                            }
                            Else
                            {
                                Store (Match (MDMA, MEQ, Local3, MTR, 0x00, 0x00), PSDM)
                            }
                        }

                        Store (Local4, MODP)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                                }, Local0)
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                                }, Local1)
                            CreateByteField (Local0, 0x01, PIOM)
                            CreateByteField (Local1, 0x01, DMAM)
                            Store (PMIO, PIOM)
                            Or (PIOM, 0x08, PIOM)
                            Store (PMDM, DMAM)
                            If (LAnd (MODP, 0x01))
                            {
                                Or (DMAM, 0x40, DMAM)
                            }
                            Else
                            {
                                Or (DMAM, 0x20, DMAM)
                            }

                            Concatenate (Local0, Local1, Local2)
                            Return (Local2)
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                                }, Local0)
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                                }, Local1)
                            CreateByteField (Local0, 0x01, PIOM)
                            CreateByteField (Local1, 0x01, DMAM)
                            Store (PSIO, PIOM)
                            Or (PIOM, 0x08, PIOM)
                            Store (PSDM, DMAM)
                            If (LAnd (MODP, 0x04))
                            {
                                Or (DMAM, 0x40, DMAM)
                            }
                            Else
                            {
                                Or (DMAM, 0x20, DMAM)
                            }

                            Concatenate (Local0, Local1, Local2)
                            Return (Local2)
                        }
                    }
                }

                Device (SDE1)
                {
                    Name (_ADR, 0x01)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Store (DerefOf (Index (PIOT, SMIO)), Local0)
                        Store (DerefOf (Index (PIOT, SSIO)), Local2)
                        Store (0x1A, Local4)
                        If (LAnd (MODS, 0x01))
                        {
                            Store (DerefOf (Index (UDMA, SMDM)), Local1)
                            If (LGreater (SMDM, 0x02))
                            {
                                If (LAnd (LNotEqual (SWAP, 0x01), LEqual (CHN0, 0x01)))
                                {
                                    If (CAB0)
                                    {
                                        Store (0x02, SMDM)
                                        Store (DerefOf (Index (UDMA, SMDM)), Local1)
                                    }
                                }

                                If (LAnd (LEqual (SWAP, 0x01), LEqual (CHN1, 0x01)))
                                {
                                    If (CAB1)
                                    {
                                        Store (0x02, SMDM)
                                        Store (DerefOf (Index (UDMA, SMDM)), Local1)
                                    }
                                }
                            }

                            Or (Local4, 0x01, Local4)
                        }
                        Else
                        {
                            Store (DerefOf (Index (MDMA, SMDM)), Local1)
                        }

                        If (LAnd (MODS, 0x04))
                        {
                            Store (DerefOf (Index (UDMA, SSDM)), Local3)
                            If (LGreater (SSDM, 0x02))
                            {
                                If (LAnd (LNotEqual (SWAP, 0x01), LEqual (CHN0, 0x01)))
                                {
                                    If (CAB0)
                                    {
                                        Store (0x02, SSDM)
                                        Store (DerefOf (Index (UDMA, SSDM)), Local3)
                                    }
                                }

                                If (LAnd (LEqual (SWAP, 0x01), LEqual (CHN1, 0x01)))
                                {
                                    If (CAB1)
                                    {
                                        Store (0x02, SSDM)
                                        Store (DerefOf (Index (UDMA, SSDM)), Local3)
                                    }
                                }
                            }

                            Or (Local4, 0x04, Local4)
                        }
                        Else
                        {
                            Store (DerefOf (Index (MDMA, SSDM)), Local3)
                        }

                        Store (Local0, GTM0)
                        Store (Local1, GTM1)
                        Store (Local2, GTM2)
                        Store (Local3, GTM3)
                        Store (Local4, GTM4)
                        Return (IDEB)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (Arg0, IDEB)
                        Store (GTM0, Local0)
                        Store (GTM1, Local1)
                        Store (GTM2, Local2)
                        Store (GTM3, Local3)
                        Store (GTM4, Local4)
                        If (LAnd (LNotEqual (Local0, 0xFFFFFFFF), LNotEqual (Local0, 0x00)))
                        {
                            Store (Match (PIOT, MEQ, Local0, MTR, 0x00, 0x00), SMIO)
                        }

                        If (LAnd (LNotEqual (Local1, 0xFFFFFFFF), LNotEqual (Local1, 0x00)))
                        {
                            If (LAnd (Local4, 0x01))
                            {
                                Store (Match (UDMA, MEQ, Local1, MTR, 0x00, 0x00), SMDM)
                            }
                            Else
                            {
                                Store (Match (MDMA, MEQ, Local1, MTR, 0x00, 0x00), SMDM)
                            }
                        }

                        If (LAnd (LNotEqual (Local2, 0xFFFFFFFF), LNotEqual (Local2, 0x00)))
                        {
                            Store (Match (PIOT, MEQ, Local2, MTR, 0x00, 0x00), SSIO)
                        }

                        If (LAnd (LNotEqual (Local3, 0xFFFFFFFF), LNotEqual (Local3, 0x00)))
                        {
                            If (LAnd (Local4, 0x04))
                            {
                                Store (Match (UDMA, MEQ, Local3, MTR, 0x00, 0x00), SSDM)
                            }
                            Else
                            {
                                Store (Match (MDMA, MEQ, Local3, MTR, 0x00, 0x00), SSDM)
                            }
                        }

                        Store (Local4, MODS)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                                }, Local0)
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                                }, Local1)
                            CreateByteField (Local0, 0x01, PIOM)
                            CreateByteField (Local1, 0x01, DMAM)
                            Store (SMIO, PIOM)
                            Or (PIOM, 0x08, PIOM)
                            Store (SMDM, DMAM)
                            If (LAnd (MODS, 0x01))
                            {
                                Or (DMAM, 0x40, DMAM)
                            }
                            Else
                            {
                                Or (DMAM, 0x20, DMAM)
                            }

                            Concatenate (Local0, Local1, Local2)
                            Return (Local2)
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                                }, Local0)
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                                }, Local1)
                            CreateByteField (Local0, 0x01, PIOM)
                            CreateByteField (Local1, 0x01, DMAM)
                            Store (SSIO, PIOM)
                            Or (PIOM, 0x08, PIOM)
                            Store (SSDM, DMAM)
                            If (LAnd (MODS, 0x04))
                            {
                                Or (DMAM, 0x40, DMAM)
                            }
                            Else
                            {
                                Or (DMAM, 0x20, DMAM)
                            }

                            Concatenate (Local0, Local1, Local2)
                            Return (Local2)
                        }
                    }
                }
            }

            Device (\_SB.PCI0.PEX5.JMB1)
            {
                Name (_ADR, 0x01)
                Name (PIOT, Package (0x05)
                {
                    0x0258, 
                    0x0186, 
                    0x014A, 
                    0xB4, 
                    0x78
                })
                Name (MDMA, Package (0x03)
                {
                    0x01E0, 
                    0x96, 
                    0x78
                })
                Name (UDMA, Package (0x07)
                {
                    0x78, 
                    0x50, 
                    0x3C, 
                    0x28, 
                    0x1E, 
                    0x14, 
                    0x0F
                })
                OperationRegion (CF40, PCI_Config, 0x40, 0x04)
                Field (CF40, ByteAcc, NoLock, Preserve)
                {
                        ,   3, 
                    CAB0,   1, 
                        ,   18, 
                    SWAP,   1, 
                    CHN0,   1, 
                            Offset (0x04)
                }

                OperationRegion (CF80, PCI_Config, 0x80, 0x04)
                Field (CF80, ByteAcc, NoLock, Preserve)
                {
                        ,   19, 
                    CAB1,   1, 
                            Offset (0x03), 
                    CHN1,   1, 
                            Offset (0x04)
                }

                Name (IDEB, Buffer (0x14) {})
                CreateDWordField (IDEB, 0x00, GTM0)
                CreateDWordField (IDEB, 0x04, GTM1)
                CreateDWordField (IDEB, 0x08, GTM2)
                CreateDWordField (IDEB, 0x0C, GTM3)
                CreateDWordField (IDEB, 0x10, GTM4)
                Name (PMIO, 0x04)
                Name (PMDM, 0x06)
                Name (PSIO, 0x04)
                Name (PSDM, 0x06)
                Name (SMIO, 0x04)
                Name (SMDM, 0x06)
                Name (SSIO, 0x04)
                Name (SSDM, 0x06)
                Name (MODP, 0x05)
                Name (MODS, 0x05)
                Device (SDE0)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Store (DerefOf (Index (PIOT, PMIO)), Local0)
                        Store (DerefOf (Index (PIOT, PSIO)), Local2)
                        Store (0x1A, Local4)
                        If (LAnd (MODP, 0x01))
                        {
                            Store (DerefOf (Index (UDMA, PMDM)), Local1)
                            If (LGreater (PMDM, 0x02))
                            {
                                If (LAnd (LNotEqual (SWAP, 0x01), LEqual (CHN1, 0x01)))
                                {
                                    If (CAB1)
                                    {
                                        Store (0x02, PMDM)
                                        Store (DerefOf (Index (UDMA, PMDM)), Local1)
                                    }
                                }

                                If (LAnd (LEqual (SWAP, 0x01), LEqual (CHN0, 0x01)))
                                {
                                    If (CAB0)
                                    {
                                        Store (0x02, PMDM)
                                        Store (DerefOf (Index (UDMA, PMDM)), Local1)
                                    }
                                }
                            }

                            Or (Local4, 0x01, Local4)
                        }
                        Else
                        {
                            Store (DerefOf (Index (MDMA, PMDM)), Local1)
                        }

                        If (LAnd (MODP, 0x04))
                        {
                            Store (DerefOf (Index (UDMA, PSDM)), Local3)
                            If (LGreater (PSDM, 0x02))
                            {
                                If (LAnd (LNotEqual (SWAP, 0x01), LEqual (CHN1, 0x01)))
                                {
                                    If (CAB1)
                                    {
                                        Store (0x02, PSDM)
                                        Store (DerefOf (Index (UDMA, PSDM)), Local3)
                                    }
                                }

                                If (LAnd (LEqual (SWAP, 0x01), LEqual (CHN0, 0x01)))
                                {
                                    If (CAB0)
                                    {
                                        Store (0x02, PSDM)
                                        Store (DerefOf (Index (UDMA, PSDM)), Local3)
                                    }
                                }
                            }

                            Or (Local4, 0x04, Local4)
                        }
                        Else
                        {
                            Store (DerefOf (Index (MDMA, PSDM)), Local3)
                        }

                        Store (Local0, GTM0)
                        Store (Local1, GTM1)
                        Store (Local2, GTM2)
                        Store (Local3, GTM3)
                        Store (Local4, GTM4)
                        Return (IDEB)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (Arg0, IDEB)
                        Store (GTM0, Local0)
                        Store (GTM1, Local1)
                        Store (GTM2, Local2)
                        Store (GTM3, Local3)
                        Store (GTM4, Local4)
                        If (LAnd (LNotEqual (Local0, 0xFFFFFFFF), LNotEqual (Local0, 0x00)))
                        {
                            Store (Match (PIOT, MEQ, Local0, MTR, 0x00, 0x00), PMIO)
                        }

                        If (LAnd (LNotEqual (Local1, 0xFFFFFFFF), LNotEqual (Local1, 0x00)))
                        {
                            If (LAnd (Local4, 0x01))
                            {
                                Store (Match (UDMA, MEQ, Local1, MTR, 0x00, 0x00), PMDM)
                            }
                            Else
                            {
                                Store (Match (MDMA, MEQ, Local1, MTR, 0x00, 0x00), PMDM)
                            }
                        }

                        If (LAnd (LNotEqual (Local2, 0xFFFFFFFF), LNotEqual (Local2, 0x00)))
                        {
                            Store (Match (PIOT, MEQ, Local2, MTR, 0x00, 0x00), PSIO)
                        }

                        If (LAnd (LNotEqual (Local3, 0xFFFFFFFF), LNotEqual (Local3, 0x00)))
                        {
                            If (LAnd (Local4, 0x04))
                            {
                                Store (Match (UDMA, MEQ, Local3, MTR, 0x00, 0x00), PSDM)
                            }
                            Else
                            {
                                Store (Match (MDMA, MEQ, Local3, MTR, 0x00, 0x00), PSDM)
                            }
                        }

                        Store (Local4, MODP)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                                }, Local0)
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                                }, Local1)
                            CreateByteField (Local0, 0x01, PIOM)
                            CreateByteField (Local1, 0x01, DMAM)
                            Store (PMIO, PIOM)
                            Or (PIOM, 0x08, PIOM)
                            Store (PMDM, DMAM)
                            If (LAnd (MODP, 0x01))
                            {
                                Or (DMAM, 0x40, DMAM)
                            }
                            Else
                            {
                                Or (DMAM, 0x20, DMAM)
                            }

                            Concatenate (Local0, Local1, Local2)
                            Return (Local2)
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                                }, Local0)
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                                }, Local1)
                            CreateByteField (Local0, 0x01, PIOM)
                            CreateByteField (Local1, 0x01, DMAM)
                            Store (PSIO, PIOM)
                            Or (PIOM, 0x08, PIOM)
                            Store (PSDM, DMAM)
                            If (LAnd (MODP, 0x04))
                            {
                                Or (DMAM, 0x40, DMAM)
                            }
                            Else
                            {
                                Or (DMAM, 0x20, DMAM)
                            }

                            Concatenate (Local0, Local1, Local2)
                            Return (Local2)
                        }
                    }
                }

                Device (SDE1)
                {
                    Name (_ADR, 0x01)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Store (DerefOf (Index (PIOT, SMIO)), Local0)
                        Store (DerefOf (Index (PIOT, SSIO)), Local2)
                        Store (0x1A, Local4)
                        If (LAnd (MODS, 0x01))
                        {
                            Store (DerefOf (Index (UDMA, SMDM)), Local1)
                            If (LGreater (SMDM, 0x02))
                            {
                                If (LAnd (LNotEqual (SWAP, 0x01), LEqual (CHN0, 0x01)))
                                {
                                    If (CAB0)
                                    {
                                        Store (0x02, SMDM)
                                        Store (DerefOf (Index (UDMA, SMDM)), Local1)
                                    }
                                }

                                If (LAnd (LEqual (SWAP, 0x01), LEqual (CHN1, 0x01)))
                                {
                                    If (CAB1)
                                    {
                                        Store (0x02, SMDM)
                                        Store (DerefOf (Index (UDMA, SMDM)), Local1)
                                    }
                                }
                            }

                            Or (Local4, 0x01, Local4)
                        }
                        Else
                        {
                            Store (DerefOf (Index (MDMA, SMDM)), Local1)
                        }

                        If (LAnd (MODS, 0x04))
                        {
                            Store (DerefOf (Index (UDMA, SSDM)), Local3)
                            If (LGreater (SSDM, 0x02))
                            {
                                If (LAnd (LNotEqual (SWAP, 0x01), LEqual (CHN0, 0x01)))
                                {
                                    If (CAB0)
                                    {
                                        Store (0x02, SSDM)
                                        Store (DerefOf (Index (UDMA, SSDM)), Local3)
                                    }
                                }

                                If (LAnd (LEqual (SWAP, 0x01), LEqual (CHN1, 0x01)))
                                {
                                    If (CAB1)
                                    {
                                        Store (0x02, SSDM)
                                        Store (DerefOf (Index (UDMA, SSDM)), Local3)
                                    }
                                }
                            }

                            Or (Local4, 0x04, Local4)
                        }
                        Else
                        {
                            Store (DerefOf (Index (MDMA, SSDM)), Local3)
                        }

                        Store (Local0, GTM0)
                        Store (Local1, GTM1)
                        Store (Local2, GTM2)
                        Store (Local3, GTM3)
                        Store (Local4, GTM4)
                        Return (IDEB)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (Arg0, IDEB)
                        Store (GTM0, Local0)
                        Store (GTM1, Local1)
                        Store (GTM2, Local2)
                        Store (GTM3, Local3)
                        Store (GTM4, Local4)
                        If (LAnd (LNotEqual (Local0, 0xFFFFFFFF), LNotEqual (Local0, 0x00)))
                        {
                            Store (Match (PIOT, MEQ, Local0, MTR, 0x00, 0x00), SMIO)
                        }

                        If (LAnd (LNotEqual (Local1, 0xFFFFFFFF), LNotEqual (Local1, 0x00)))
                        {
                            If (LAnd (Local4, 0x01))
                            {
                                Store (Match (UDMA, MEQ, Local1, MTR, 0x00, 0x00), SMDM)
                            }
                            Else
                            {
                                Store (Match (MDMA, MEQ, Local1, MTR, 0x00, 0x00), SMDM)
                            }
                        }

                        If (LAnd (LNotEqual (Local2, 0xFFFFFFFF), LNotEqual (Local2, 0x00)))
                        {
                            Store (Match (PIOT, MEQ, Local2, MTR, 0x00, 0x00), SSIO)
                        }

                        If (LAnd (LNotEqual (Local3, 0xFFFFFFFF), LNotEqual (Local3, 0x00)))
                        {
                            If (LAnd (Local4, 0x04))
                            {
                                Store (Match (UDMA, MEQ, Local3, MTR, 0x00, 0x00), SSDM)
                            }
                            Else
                            {
                                Store (Match (MDMA, MEQ, Local3, MTR, 0x00, 0x00), SSDM)
                            }
                        }

                        Store (Local4, MODS)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                                }, Local0)
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                                }, Local1)
                            CreateByteField (Local0, 0x01, PIOM)
                            CreateByteField (Local1, 0x01, DMAM)
                            Store (SMIO, PIOM)
                            Or (PIOM, 0x08, PIOM)
                            Store (SMDM, DMAM)
                            If (LAnd (MODS, 0x01))
                            {
                                Or (DMAM, 0x40, DMAM)
                            }
                            Else
                            {
                                Or (DMAM, 0x20, DMAM)
                            }

                            Concatenate (Local0, Local1, Local2)
                            Return (Local2)
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                                }, Local0)
                            Store (Buffer (0x07)
                                {
                                    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                                }, Local1)
                            CreateByteField (Local0, 0x01, PIOM)
                            CreateByteField (Local1, 0x01, DMAM)
                            Store (SSIO, PIOM)
                            Or (PIOM, 0x08, PIOM)
                            Store (SSDM, DMAM)
                            If (LAnd (MODS, 0x04))
                            {
                                Or (DMAM, 0x40, DMAM)
                            }
                            Else
                            {
                                Or (DMAM, 0x20, DMAM)
                            }

                            Concatenate (Local0, Local1, Local2)
                            Return (Local2)
                        }
                    }
                }
            }

            Device (HUB0)
            {
                Name (_ADR, 0x001E0000)
                Method (_STA, 0, NotSerialized)
                {
                    Return (0x0F)
                }

                Name (PICM, Package (0x0C)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        \_SB.PCI0.LNKE, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        \_SB.PCI0.LNKD, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        \_SB.PCI0.LNKA, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x0001FFFF, 
                        0x00, 
                        \_SB.PCI0.LNKD, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x0001FFFF, 
                        0x01, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x0001FFFF, 
                        0x02, 
                        \_SB.PCI0.LNKA, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x0001FFFF, 
                        0x03, 
                        \_SB.PCI0.LNKE, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x0006FFFF, 
                        0x00, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x0006FFFF, 
                        0x01, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x0006FFFF, 
                        0x02, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x0006FFFF, 
                        0x03, 
                        \_SB.PCI0.LNKC, 
                        0x00
                    }
                })
                Name (APIC, Package (0x0C)
                {
                    Package (0x04)
                    {
                        0xFFFF, 
                        0x00, 
                        0x00, 
                        0x14
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x01, 
                        0x00, 
                        0x13
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x02, 
                        0x00, 
                        0x12
                    }, 

                    Package (0x04)
                    {
                        0xFFFF, 
                        0x03, 
                        0x00, 
                        0x10
                    }, 

                    Package (0x04)
                    {
                        0x0001FFFF, 
                        0x00, 
                        0x00, 
                        0x13
                    }, 

                    Package (0x04)
                    {
                        0x0001FFFF, 
                        0x01, 
                        0x00, 
                        0x12
                    }, 

                    Package (0x04)
                    {
                        0x0001FFFF, 
                        0x02, 
                        0x00, 
                        0x10
                    }, 

                    Package (0x04)
                    {
                        0x0001FFFF, 
                        0x03, 
                        0x00, 
                        0x14
                    }, 

                    Package (0x04)
                    {
                        0x0006FFFF, 
                        0x00, 
                        0x00, 
                        0x12
                    }, 

                    Package (0x04)
                    {
                        0x0006FFFF, 
                        0x01, 
                        0x00, 
                        0x12
                    }, 

                    Package (0x04)
                    {
                        0x0006FFFF, 
                        0x02, 
                        0x00, 
                        0x12
                    }, 

                    Package (0x04)
                    {
                        0x0006FFFF, 
                        0x03, 
                        0x00, 
                        0x12
                    }
                })
                Method (_PRT, 0, NotSerialized)
                {
                    If (LNot (PICF))
                    {
                        Return (PICM)
                    }
                    Else
                    {
                        Return (APIC)
                    }
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (Package (0x02)
                    {
                        0x0B, 
                        0x05
                    })
                }
            }

            Device (PX40)
            {
                Name (_ADR, 0x001F0000)
                OperationRegion (PREV, PCI_Config, 0x08, 0x01)
                Scope (\)
                {
                    Field (\_SB.PCI0.PX40.PREV, ByteAcc, NoLock, Preserve)
                    {
                        REV0,   8
                    }
                }

                OperationRegion (PIRQ, PCI_Config, 0x60, 0x04)
                Scope (\)
                {
                    Field (\_SB.PCI0.PX40.PIRQ, ByteAcc, NoLock, Preserve)
                    {
                        PIRA,   8, 
                        PIRB,   8, 
                        PIRC,   8, 
                        PIRD,   8
                    }
                }

                OperationRegion (PIR2, PCI_Config, 0x68, 0x04)
                Scope (\)
                {
                    Field (\_SB.PCI0.PX40.PIR2, ByteAcc, NoLock, Preserve)
                    {
                        PIRE,   8, 
                        PIRF,   8, 
                        PIRG,   8, 
                        PIRH,   8
                    }
                }

                OperationRegion (LPIO, PCI_Config, 0x80, 0x0E)
                Scope (\)
                {
                    Field (\_SB.PCI0.PX40.LPIO, ByteAcc, NoLock, Preserve)
                    {
                        UAIO,   8, 
                        PRIO,   8, 
                        LPE1,   8, 
                        LPE2,   8, 
                        GN1L,   8, 
                        GN1H,   8, 
                        GN2L,   8, 
                        GN2H,   8
                    }

                    Method (DISD, 1, NotSerialized)
                    {
                        If (LEqual (Arg0, 0x00))
                        {
                            And (LPE1, 0xFE, LPE1)
                        }

                        If (LEqual (Arg0, 0x01))
                        {
                            And (LPE1, 0xFD, LPE1)
                        }

                        If (LEqual (Arg0, 0x02))
                        {
                            And (LPE1, 0xFB, LPE1)
                        }

                        If (LEqual (Arg0, 0x03))
                        {
                            And (LPE1, 0xF7, LPE1)
                        }

                        If (LEqual (Arg0, 0x04))
                        {
                            And (LPE2, 0xFC, LPE2)
                        }

                        If (LEqual (Arg0, 0x05))
                        {
                            And (LPE1, 0xDF, LPE1)
                        }

                        If (LEqual (Arg0, 0x06))
                        {
                            And (GN2L, 0xFE, GN2L)
                        }
                    }

                    Method (CKIO, 2, NotSerialized)
                    {
                        If (LEqual (Arg1, 0x00))
                        {
                            Or (LPE1, 0x01, LPE1)
                            And (UAIO, 0xF0, Local0)
                            If (LEqual (Arg0, 0x03F8))
                            {
                                Or (Local0, 0x00, UAIO)
                            }

                            If (LEqual (Arg0, 0x02F8))
                            {
                                Or (Local0, 0x01, UAIO)
                            }

                            If (LEqual (Arg0, 0x02E8))
                            {
                                Or (Local0, 0x05, UAIO)
                            }

                            If (LEqual (Arg0, 0x03E8))
                            {
                                Or (Local0, 0x07, UAIO)
                            }
                        }

                        If (LEqual (Arg1, 0x01))
                        {
                            Or (LPE1, 0x02, LPE1)
                            And (UAIO, 0x0F, Local0)
                            If (LEqual (Arg0, 0x03F8))
                            {
                                Or (Local0, 0x00, UAIO)
                            }

                            If (LEqual (Arg0, 0x02F8))
                            {
                                Or (Local0, 0x10, UAIO)
                            }

                            If (LEqual (Arg0, 0x02E8))
                            {
                                Or (Local0, 0x50, UAIO)
                            }

                            If (LEqual (Arg0, 0x03E8))
                            {
                                Or (Local0, 0x70, UAIO)
                            }
                        }

                        If (LEqual (Arg1, 0x02))
                        {
                            Or (LPE1, 0x04, LPE1)
                            And (PRIO, 0xFC, Local0)
                            If (LEqual (Arg0, 0x0378))
                            {
                                Or (Local0, 0x00, PRIO)
                            }

                            If (LEqual (Arg0, 0x0278))
                            {
                                Or (Local0, 0x01, PRIO)
                            }

                            If (LEqual (Arg0, 0x03BC))
                            {
                                Or (Local0, 0x02, PRIO)
                            }
                        }

                        If (LEqual (Arg1, 0x03))
                        {
                            Or (LPE1, 0x08, LPE1)
                        }

                        If (LEqual (Arg1, 0x04))
                        {
                            If (LEqual (Arg0, 0x0201))
                            {
                                Or (LPE2, 0x01, LPE2)
                            }

                            If (LEqual (Arg0, 0x0209))
                            {
                                Or (LPE2, 0x02, LPE2)
                            }
                        }

                        If (LEqual (Arg1, 0x06))
                        {
                            If (LNotEqual (Arg0, 0xFFFF))
                            {
                                And (Arg0, 0xFF, Local0)
                                Or (Local0, 0x01, GN2L)
                                ShiftRight (Arg0, 0x08, GN2H)
                            }
                            Else
                            {
                                Store (Zero, GN2H)
                                Store (Zero, GN2L)
                            }
                        }
                    }
                }

                Scope (\)
                {
                    Method (SLDM, 2, NotSerialized)
                    {
                    }
                }

                Scope (\)
                {
                    OperationRegion (\SCPP, SystemIO, 0xB2, 0x01)
                    Field (\SCPP, ByteAcc, NoLock, Preserve)
                    {
                        SMIP,   8
                    }
                }

                Method (\_SB.PCI0._INI, 0, NotSerialized)
                {
                    If (STRC (\_OS, "Microsoft Windows"))
                    {
                        Store (0x56, SMIP)
                    }
                    Else
                    {
                        If (STRC (\_OS, "Microsoft Windows NT"))
                        {
                            If (CondRefOf (\_OSI, Local0))
                            {
                                If (\_OSI ("Windows 2001"))
                                {
                                    Store (0x59, SMIP)
                                    Store (0x00, OSFL)
                                    Store (0x03, OSFX)
                                }
                            }
                            Else
                            {
                                Store (0x58, SMIP)
                                Store (0x00, OSFL)
                            }
                        }
                        Else
                        {
                            Store (0x57, SMIP)
                            Store (0x02, OSFL)
                        }
                    }
                }

                Scope (\)
                {
                    Method (OSTP, 0, NotSerialized)
                    {
                        If (LEqual (OSFL, 0x01))
                        {
                            Store (0x56, SMIP)
                        }

                        If (LEqual (OSFL, 0x02))
                        {
                            Store (0x57, SMIP)
                        }

                        If (LEqual (OSFL, 0x00))
                        {
                            If (LEqual (OSFX, 0x03))
                            {
                                Store (0x59, SMIP)
                            }
                            Else
                            {
                                Store (0x58, SMIP)
                            }
                        }

                        If (LEqual (OSFX, 0x03))
                        {
                            Store (0x59, SMIP)
                        }
                    }
                }

                Device (SYSR)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x01)
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0010,             // Range Minimum
                            0x0010,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x0022,             // Range Minimum
                            0x0022,             // Range Maximum
                            0x01,               // Alignment
                            0x1E,               // Length
                            )
                        IO (Decode16,
                            0x0044,             // Range Minimum
                            0x0044,             // Range Maximum
                            0x01,               // Alignment
                            0x1C,               // Length
                            )
                        IO (Decode16,
                            0x0062,             // Range Minimum
                            0x0062,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0065,             // Range Minimum
                            0x0065,             // Range Maximum
                            0x01,               // Alignment
                            0x0B,               // Length
                            )
                        IO (Decode16,
                            0x0074,             // Range Minimum
                            0x0074,             // Range Maximum
                            0x01,               // Alignment
                            0x0C,               // Length
                            )
                        IO (Decode16,
                            0x0091,             // Range Minimum
                            0x0091,             // Range Maximum
                            0x01,               // Alignment
                            0x03,               // Length
                            )
                        IO (Decode16,
                            0x00A2,             // Range Minimum
                            0x00A2,             // Range Maximum
                            0x01,               // Alignment
                            0x1E,               // Length
                            )
                        IO (Decode16,
                            0x00E0,             // Range Minimum
                            0x00E0,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x04D0,             // Range Minimum
                            0x04D0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0290,             // Range Minimum
                            0x0290,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x0800,             // Range Minimum
                            0x0800,             // Range Maximum
                            0x01,               // Alignment
                            0x80,               // Length
                            )
                        IO (Decode16,
                            0x0290,             // Range Minimum
                            0x0290,             // Range Maximum
                            0x01,               // Alignment
                            0x05,               // Length
                            )
                        IO (Decode16,
                            0x0880,             // Range Minimum
                            0x0880,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                    })
                }

                Device (PIC)
                {
                    Name (_HID, EisaId ("PNP0000"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0020,             // Range Minimum
                            0x0020,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A0,             // Range Minimum
                            0x00A0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IRQNoFlags ()
                            {2}
                    })
                }

                Device (DMA1)
                {
                    Name (_HID, EisaId ("PNP0200"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        DMA (Compatibility, BusMaster, Transfer8, )
                            {4}
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x0080,             // Range Minimum
                            0x0080,             // Range Maximum
                            0x01,               // Alignment
                            0x11,               // Length
                            )
                        IO (Decode16,
                            0x0094,             // Range Minimum
                            0x0094,             // Range Maximum
                            0x01,               // Alignment
                            0x0C,               // Length
                            )
                        IO (Decode16,
                            0x00C0,             // Range Minimum
                            0x00C0,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                    })
                }

                Device (TMR)
                {
                    Name (_HID, EisaId ("PNP0100"))
                    Name (ATT5, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0040,             // Range Minimum
                            0x0040,             // Range Maximum
                            0x00,               // Alignment
                            0x04,               // Length
                            )
                        IRQNoFlags ()
                            {0}
                    })
                    Name (ATT6, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0040,             // Range Minimum
                            0x0040,             // Range Maximum
                            0x00,               // Alignment
                            0x04,               // Length
                            )
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        If (LGreaterEqual (OSFX, 0x03))
                        {
                            If (HPTF)
                            {
                                Return (ATT6)
                            }
                            Else
                            {
                                Return (ATT5)
                            }
                        }
                        Else
                        {
                            Return (ATT5)
                        }
                    }
                }

                Device (HPET)
                {
                    Name (_HID, EisaId ("PNP0103"))
                    Name (ATT3, ResourceTemplate ()
                    {
                        IRQNoFlags ()
                            {0}
                        IRQNoFlags ()
                            {8}
                        Memory32Fixed (ReadWrite,
                            0xFED00000,         // Address Base
                            0x00000400,         // Address Length
                            )
                    })
                    Name (ATT4, ResourceTemplate ()
                    {
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        If (LGreaterEqual (OSFX, 0x03))
                        {
                            If (HPTF)
                            {
                                Return (0x0F)
                            }
                            Else
                            {
                                Return (0x00)
                            }
                        }
                        Else
                        {
                            Return (0x00)
                        }
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        If (LGreaterEqual (OSFX, 0x03))
                        {
                            If (HPTF)
                            {
                                Return (ATT3)
                            }
                            Else
                            {
                                Return (ATT4)
                            }
                        }
                        Else
                        {
                            Return (ATT4)
                        }
                    }
                }

                Device (RTC)
                {
                    Name (_HID, EisaId ("PNP0B00"))
                    Name (ATT0, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x00,               // Alignment
                            0x04,               // Length
                            )
                        IRQNoFlags ()
                            {8}
                    })
                    Name (ATT1, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x00,               // Alignment
                            0x04,               // Length
                            )
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        If (LGreaterEqual (OSFX, 0x03))
                        {
                            If (HPTF)
                            {
                                Return (ATT1)
                            }
                            Else
                            {
                                Return (ATT0)
                            }
                        }
                        Else
                        {
                            Return (ATT0)
                        }
                    }
                }

                Device (SPKR)
                {
                    Name (_HID, EisaId ("PNP0800"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0061,             // Range Minimum
                            0x0061,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                    })
                }

                Device (COPR)
                {
                    Name (_HID, EisaId ("PNP0C04"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x00F0,             // Range Minimum
                            0x00F0,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IRQNoFlags ()
                            {13}
                    })
                }

                Scope (\)
                {
                    OperationRegion (WIN1, SystemIO, 0x2E, 0x02)
                    Field (WIN1, ByteAcc, NoLock, Preserve)
                    {
                        INDP,   8, 
                        DATP,   8
                    }

                    OperationRegion (GPIO, SystemIO, 0x0800, 0x05)
                    Field (GPIO, ByteAcc, NoLock, Preserve)
                    {
                        GO01,   8, 
                        GO02,   8, 
                        GO03,   8, 
                        GO04,   8, 
                        GO05,   8
                    }

                    IndexField (INDP, DATP, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x02), 
                        CFG,    8, 
                                Offset (0x07), 
                        LDN,    8, 
                                Offset (0x20), 
                        IDHI,   8, 
                        IDLO,   8, 
                        POWC,   8, 
                                Offset (0x30), 
                        ACTR,   8, 
                                Offset (0x60), 
                        IOAH,   8, 
                        IOAL,   8, 
                        IO2H,   8, 
                        IO2L,   8, 
                                Offset (0x70), 
                        INTR,   8, 
                                Offset (0x72), 
                        INT1,   8, 
                                Offset (0x74), 
                        DMCH,   8, 
                                Offset (0xC0), 
                        GP40,   8, 
                                Offset (0xF0), 
                        OPT1,   8, 
                        OPT2,   8, 
                        OPT3,   8, 
                        OPT4,   8
                    }

                    Method (ENFG, 0, NotSerialized)
                    {
                        Store (0x87, INDP)
                        Store (0x01, INDP)
                        Store (0x55, INDP)
                        Store (0x55, INDP)
                    }

                    Method (EXFG, 0, NotSerialized)
                    {
                        Store (0x02, CFG)
                    }

                    Method (GSRG, 1, NotSerialized)
                    {
                        Store (Arg0, INDP)
                        Return (DATP)
                    }

                    Method (SSRG, 2, NotSerialized)
                    {
                        Store (Arg0, INDP)
                        Store (Arg1, DATP)
                    }
                }

                Device (FDC0)
                {
                    Name (_HID, EisaId ("PNP0700"))
                    Method (_STA, 0, NotSerialized)
                    {
                        ENFG ()
                        Store (Zero, LDN)
                        If (ACTR)
                        {
                            EXFG ()
                            Return (0x0F)
                        }
                        Else
                        {
                            If (LOr (IOAH, IOAL))
                            {
                                EXFG ()
                                Return (0x0D)
                            }
                            Else
                            {
                                EXFG ()
                                Return (0x00)
                            }
                        }
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        ENFG ()
                        Store (0x00, LDN)
                        Store (Zero, ACTR)
                        SLDM (DMCH, 0x04)
                        EXFG ()
                        DISD (0x03)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUF0, ResourceTemplate ()
                        {
                            IO (Decode16,
                                0x03F0,             // Range Minimum
                                0x03F0,             // Range Maximum
                                0x01,               // Alignment
                                0x06,               // Length
                                _Y01)
                            IO (Decode16,
                                0x03F7,             // Range Minimum
                                0x03F7,             // Range Maximum
                                0x01,               // Alignment
                                0x01,               // Length
                                )
                            IRQNoFlags ()
                                {6}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {2}
                        })
                        CreateByteField (BUF0, \_SB.PCI0.PX40.FDC0._CRS._Y01._MIN, IOLO)
                        CreateByteField (BUF0, 0x03, IOHI)
                        CreateByteField (BUF0, \_SB.PCI0.PX40.FDC0._CRS._Y01._MAX, IORL)
                        CreateByteField (BUF0, 0x05, IORH)
                        ENFG ()
                        EXFG ()
                        Return (BUF0)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03F0,             // Range Minimum
                                0x03F0,             // Range Maximum
                                0x01,               // Alignment
                                0x06,               // Length
                                )
                            IO (Decode16,
                                0x03F7,             // Range Minimum
                                0x03F7,             // Range Maximum
                                0x01,               // Alignment
                                0x01,               // Length
                                )
                            IRQNoFlags ()
                                {6}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {2}
                        }
                        EndDependentFn ()
                    })
                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x02, IOLO)
                        CreateByteField (Arg0, 0x03, IOHI)
                        CreateWordField (Arg0, 0x02, IOAD)
                        CreateWordField (Arg0, 0x19, IRQW)
                        CreateByteField (Arg0, 0x1C, DMAV)
                        ENFG ()
                        Store (Zero, LDN)
                        Store (One, ACTR)
                        SLDM (DMCH, DMCH)
                        CKIO (IOAD, 0x03)
                        EXFG ()
                    }
                }

                Device (UAR1)
                {
                    Name (_HID, EisaId ("PNP0501"))
                    Name (_UID, 0x01)
                    Method (_STA, 0, NotSerialized)
                    {
                        ENFG ()
                        Store (0x01, LDN)
                        If (ACTR)
                        {
                            EXFG ()
                            Return (0x0F)
                        }
                        Else
                        {
                            If (LOr (IOAH, IOAL))
                            {
                                EXFG ()
                                Return (0x0D)
                            }
                            Else
                            {
                                EXFG ()
                                Return (0x00)
                            }
                        }

                        EXFG ()
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        ENFG ()
                        Store (0x01, LDN)
                        Store (Zero, ACTR)
                        EXFG ()
                        DISD (0x00)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUF1, ResourceTemplate ()
                        {
                            IO (Decode16,
                                0x0000,             // Range Minimum
                                0x0000,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                _Y02)
                            IRQNoFlags (_Y03)
                                {}
                        })
                        CreateByteField (BUF1, \_SB.PCI0.PX40.UAR1._CRS._Y02._MIN, IOLO)
                        CreateByteField (BUF1, 0x03, IOHI)
                        CreateByteField (BUF1, \_SB.PCI0.PX40.UAR1._CRS._Y02._MAX, IORL)
                        CreateByteField (BUF1, 0x05, IORH)
                        CreateWordField (BUF1, \_SB.PCI0.PX40.UAR1._CRS._Y03._INT, IRQW)
                        ENFG ()
                        Store (0x01, LDN)
                        Store (IOAL, IOLO)
                        Store (IOAL, IORL)
                        Store (IOAH, IOHI)
                        Store (IOAH, IORH)
                        Store (One, Local0)
                        ShiftLeft (Local0, INTR, IRQW)
                        EXFG ()
                        Return (BUF1)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03F8,             // Range Minimum
                                0x03F8,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,7,9,10,11,12}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x02F8,             // Range Minimum
                                0x02F8,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,7,9,10,11,12}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03E8,             // Range Minimum
                                0x03E8,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,7,9,10,11,12}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x02E8,             // Range Minimum
                                0x02E8,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,7,9,10,11,12}
                        }
                        EndDependentFn ()
                    })
                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x02, IOLO)
                        CreateByteField (Arg0, 0x03, IOHI)
                        CreateWordField (Arg0, 0x02, IOAD)
                        CreateWordField (Arg0, 0x09, IRQW)
                        ENFG ()
                        Store (0x01, LDN)
                        Store (One, ACTR)
                        Store (IOLO, IOAL)
                        Store (IOHI, IOAH)
                        FindSetRightBit (IRQW, Local0)
                        Subtract (Local0, 0x01, INTR)
                        EXFG ()
                        CKIO (IOAD, 0x00)
                    }

                    Method (_PRW, 0, NotSerialized)
                    {
                        If (SUSF)
                        {
                            Return (Package (0x02)
                            {
                                0x08, 
                                0x03
                            })
                        }
                        Else
                        {
                            Return (Package (0x02)
                            {
                                0x08, 
                                0x01
                            })
                        }
                    }

                    Method (_PSW, 1, NotSerialized)
                    {
                        If (Arg0)
                        {
                            Or (G2C2, 0x01, G2C2)
                        }
                        Else
                        {
                            And (G2C2, 0xFE, G2C2)
                        }
                    }
                }

                Device (LPT1)
                {
                    Name (_HID, EisaId ("PNP0400"))
                    Method (_STA, 0, NotSerialized)
                    {
                        ENFG ()
                        Store (0x03, LDN)
                        And (OPT1, 0x02, Local0)
                        If (LNotEqual (Local0, 0x02))
                        {
                            If (ACTR)
                            {
                                EXFG ()
                                Return (0x0F)
                            }
                            Else
                            {
                                If (LOr (IOAH, IOAL))
                                {
                                    EXFG ()
                                    Return (0x0D)
                                }
                                Else
                                {
                                    EXFG ()
                                    Return (0x00)
                                }
                            }
                        }
                        Else
                        {
                            EXFG ()
                            Return (0x00)
                        }
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        ENFG ()
                        Store (0x03, LDN)
                        Store (Zero, ACTR)
                        EXFG ()
                        DISD (0x02)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUF5, ResourceTemplate ()
                        {
                            IO (Decode16,
                                0x0000,             // Range Minimum
                                0x0000,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                _Y04)
                            IRQNoFlags (_Y05)
                                {}
                        })
                        CreateByteField (BUF5, \_SB.PCI0.PX40.LPT1._CRS._Y04._MIN, IOLO)
                        CreateByteField (BUF5, 0x03, IOHI)
                        CreateByteField (BUF5, \_SB.PCI0.PX40.LPT1._CRS._Y04._MAX, IORL)
                        CreateByteField (BUF5, 0x05, IORH)
                        CreateByteField (BUF5, \_SB.PCI0.PX40.LPT1._CRS._Y04._LEN, IOLE)
                        CreateWordField (BUF5, \_SB.PCI0.PX40.LPT1._CRS._Y05._INT, IRQW)
                        ENFG ()
                        Store (0x03, LDN)
                        Store (IOAL, IOLO)
                        Store (IOLO, IORL)
                        Store (IOAH, IOHI)
                        Store (IOHI, IORH)
                        If (LEqual (IOLO, 0xBC))
                        {
                            Store (0x04, IOLE)
                        }
                        Else
                        {
                            Store (0x08, IOLE)
                        }

                        Store (One, Local0)
                        Store (INTR, Local5)
                        ShiftLeft (Local0, Local5, IRQW)
                        EXFG ()
                        Return (BUF5)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0378,             // Range Minimum
                                0x0378,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,7,9,10,11,12}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0278,             // Range Minimum
                                0x0278,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,7,9,10,11,12}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03BC,             // Range Minimum
                                0x03BC,             // Range Maximum
                                0x01,               // Alignment
                                0x04,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,7,9,10,11,12}
                        }
                        EndDependentFn ()
                    })
                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x02, IOLO)
                        CreateByteField (Arg0, 0x03, IOHI)
                        CreateWordField (Arg0, 0x02, IOAD)
                        CreateByteField (Arg0, 0x04, IORL)
                        CreateByteField (Arg0, 0x05, IORH)
                        CreateWordField (Arg0, 0x09, IRQW)
                        ENFG ()
                        Store (0x03, LDN)
                        Store (One, ACTR)
                        Store (IOLO, IOAL)
                        Store (IOHI, IOAH)
                        FindSetLeftBit (IRQW, Local0)
                        Subtract (Local0, 0x01, Local0)
                        Store (Local0, INTR)
                        EXFG ()
                        CKIO (IOAD, 0x02)
                    }
                }

                Device (ECP1)
                {
                    Name (_HID, EisaId ("PNP0401"))
                    Method (_STA, 0, NotSerialized)
                    {
                        ENFG ()
                        Store (0x03, LDN)
                        And (OPT1, 0x02, Local0)
                        If (LEqual (Local0, 0x02))
                        {
                            If (ACTR)
                            {
                                EXFG ()
                                Return (0x0F)
                            }
                            Else
                            {
                                If (LOr (IOAH, IOAL))
                                {
                                    EXFG ()
                                    Return (0x0D)
                                }
                                Else
                                {
                                    EXFG ()
                                    Return (0x00)
                                }
                            }
                        }
                        Else
                        {
                            EXFG ()
                            Return (0x00)
                        }
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        ENFG ()
                        Store (0x03, LDN)
                        Store (Zero, ACTR)
                        SLDM (DMCH, 0x04)
                        EXFG ()
                        DISD (0x02)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUF6, ResourceTemplate ()
                        {
                            IO (Decode16,
                                0x0000,             // Range Minimum
                                0x0000,             // Range Maximum
                                0x01,               // Alignment
                                0x04,               // Length
                                _Y06)
                            IO (Decode16,
                                0x0000,             // Range Minimum
                                0x0000,             // Range Maximum
                                0x01,               // Alignment
                                0x04,               // Length
                                _Y07)
                            IRQNoFlags (_Y08)
                                {}
                            DMA (Compatibility, NotBusMaster, Transfer8, _Y09)
                                {}
                        })
                        CreateByteField (BUF6, \_SB.PCI0.PX40.ECP1._CRS._Y06._MIN, IOLO)
                        CreateByteField (BUF6, 0x03, IOHI)
                        CreateByteField (BUF6, \_SB.PCI0.PX40.ECP1._CRS._Y06._MAX, IORL)
                        CreateByteField (BUF6, 0x05, IORH)
                        CreateByteField (BUF6, \_SB.PCI0.PX40.ECP1._CRS._Y06._LEN, IOLE)
                        CreateByteField (BUF6, \_SB.PCI0.PX40.ECP1._CRS._Y07._MIN, IOEL)
                        CreateByteField (BUF6, 0x0B, IOEH)
                        CreateByteField (BUF6, \_SB.PCI0.PX40.ECP1._CRS._Y07._MAX, IOML)
                        CreateByteField (BUF6, 0x0D, IOMH)
                        CreateWordField (BUF6, \_SB.PCI0.PX40.ECP1._CRS._Y08._INT, IRQW)
                        CreateByteField (BUF6, \_SB.PCI0.PX40.ECP1._CRS._Y09._DMA, DMAC)
                        ENFG ()
                        Store (0x03, LDN)
                        Store (IOAL, Local2)
                        Store (Local2, IOLO)
                        Store (IOAH, Local3)
                        Store (Local3, IOHI)
                        Or (Local3, 0x04, Local3)
                        Store (Local3, IOEH)
                        Store (Local3, IOMH)
                        Store (IOLO, IORL)
                        Store (IOLO, IOEL)
                        Store (IOLO, IOML)
                        Store (IOHI, IORH)
                        If (LEqual (IOLO, 0xBC))
                        {
                            Store (0x04, IOLE)
                        }
                        Else
                        {
                            Store (0x08, IOLE)
                        }

                        Store (One, Local0)
                        Store (INTR, Local5)
                        ShiftLeft (Local0, Local5, IRQW)
                        Store (One, Local0)
                        Store (DMCH, Local5)
                        ShiftLeft (Local0, Local5, DMAC)
                        EXFG ()
                        Return (BUF6)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0378,             // Range Minimum
                                0x0378,             // Range Maximum
                                0x00,               // Alignment
                                0x08,               // Length
                                )
                            IO (Decode16,
                                0x0778,             // Range Minimum
                                0x0778,             // Range Maximum
                                0x00,               // Alignment
                                0x04,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,7,9,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,3}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0278,             // Range Minimum
                                0x0278,             // Range Maximum
                                0x00,               // Alignment
                                0x08,               // Length
                                )
                            IO (Decode16,
                                0x0678,             // Range Minimum
                                0x0678,             // Range Maximum
                                0x00,               // Alignment
                                0x04,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,7,9,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,3}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03BC,             // Range Minimum
                                0x03BC,             // Range Maximum
                                0x00,               // Alignment
                                0x04,               // Length
                                )
                            IO (Decode16,
                                0x07BC,             // Range Minimum
                                0x07BC,             // Range Maximum
                                0x00,               // Alignment
                                0x04,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,7,9,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,3}
                        }
                        EndDependentFn ()
                    })
                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x02, IOLO)
                        CreateByteField (Arg0, 0x03, IOHI)
                        CreateWordField (Arg0, 0x02, IOAD)
                        CreateWordField (Arg0, 0x11, IRQW)
                        CreateByteField (Arg0, 0x14, DMAC)
                        ENFG ()
                        Store (0x03, LDN)
                        Store (One, ACTR)
                        Store (IOLO, IOAL)
                        Store (IOHI, IOAH)
                        FindSetLeftBit (IRQW, Local0)
                        Subtract (Local0, 0x01, Local0)
                        Store (Local0, INTR)
                        FindSetLeftBit (DMAC, Local1)
                        Store (DMCH, Local0)
                        Subtract (Local1, 0x01, DMCH)
                        SLDM (Local0, DMCH)
                        EXFG ()
                        CKIO (IOAD, 0x02)
                    }
                }

                OperationRegion (KBCT, SystemIO, 0x60, 0x05)
                Field (KBCT, ByteAcc, NoLock, Preserve)
                {
                    P060,   8, 
                            Offset (0x04), 
                    P064,   8
                }

                Device (PS2M)
                {
                    Name (_HID, EisaId ("PNP0F13"))
                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (PS2F, 0x00))
                        {
                            Return (0x0F)
                        }
                        Else
                        {
                            Return (0x00)
                        }
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUF1, ResourceTemplate ()
                        {
                            IRQNoFlags ()
                                {12}
                        })
                        Name (BUF2, ResourceTemplate ()
                        {
                            IO (Decode16,
                                0x0060,             // Range Minimum
                                0x0060,             // Range Maximum
                                0x01,               // Alignment
                                0x01,               // Length
                                )
                            IO (Decode16,
                                0x0064,             // Range Minimum
                                0x0064,             // Range Maximum
                                0x01,               // Alignment
                                0x01,               // Length
                                )
                            IRQNoFlags ()
                                {12}
                        })
                        If (LEqual (KBDI, 0x01))
                        {
                            If (LEqual (OSFL, 0x02))
                            {
                                Return (BUF1)
                            }

                            If (LEqual (OSFL, 0x01))
                            {
                                Return (BUF1)
                            }
                            Else
                            {
                                Return (BUF2)
                            }
                        }
                        Else
                        {
                            Return (BUF1)
                        }
                    }
                }

                Device (PS2K)
                {
                    Name (_HID, EisaId ("PNP0303"))
                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (KBDI, 0x01))
                        {
                            Return (0x00)
                        }
                        Else
                        {
                            Return (0x0F)
                        }
                    }

                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0060,             // Range Minimum
                            0x0060,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0064,             // Range Minimum
                            0x0064,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IRQNoFlags ()
                            {1}
                    })
                }

                Device (PSMR)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x03)
                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (KBDI, 0x00))
                        {
                            Return (0x00)
                        }

                        If (LEqual (PS2F, 0x00))
                        {
                            If (LEqual (OSFL, 0x02))
                            {
                                Return (0x0F)
                            }

                            If (LEqual (OSFL, 0x01))
                            {
                                Return (0x0F)
                            }

                            Return (0x00)
                        }

                        Return (0x00)
                    }

                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0060,             // Range Minimum
                            0x0060,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0064,             // Range Minimum
                            0x0064,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                    })
                }

                Device (PMIO)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x02)
                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUF0, ResourceTemplate ()
                        {
                            IO (Decode16,
                                0x0400,             // Range Minimum
                                0x0400,             // Range Maximum
                                0x01,               // Alignment
                                0xC0,               // Length
                                )
                        })
                        Return (BUF0)
                    }
                }
            }

            Device (IGBE)
            {
                Name (_ADR, 0x00190000)
                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x04
                })
            }

            Device (USB0)
            {
                Name (_ADR, 0x001D0000)
                Method (_S3D, 0, NotSerialized)
                {
                    If (LEqual (OSFL, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x03)
                }

                Name (_PRW, Package (0x02)
                {
                    0x03, 
                    0x03
                })
            }

            Device (USB1)
            {
                Name (_ADR, 0x001D0001)
                Method (_S3D, 0, NotSerialized)
                {
                    If (LEqual (OSFL, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x03)
                }

                Name (_PRW, Package (0x02)
                {
                    0x04, 
                    0x03
                })
            }

            Device (USB2)
            {
                Name (_ADR, 0x001D0002)
                Method (_S3D, 0, NotSerialized)
                {
                    If (LEqual (OSFL, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x03)
                }

                Name (_PRW, Package (0x02)
                {
                    0x0C, 
                    0x03
                })
            }

            Device (USB3)
            {
                Name (_ADR, 0x001D0003)
                Method (_S3D, 0, NotSerialized)
                {
                    If (LEqual (OSFL, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x03)
                }

                Name (_PRW, Package (0x02)
                {
                    0x0E, 
                    0x03
                })
            }

            Device (US31)
            {
                Name (_ADR, 0x001A0000)
                Method (_S3D, 0, NotSerialized)
                {
                    If (LEqual (OSFL, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x03)
                }

                Name (_PRW, Package (0x02)
                {
                    0x0E, 
                    0x03
                })
            }

            Device (USB4)
            {
                Name (_ADR, 0x001A0001)
                Method (_S3D, 0, NotSerialized)
                {
                    If (LEqual (OSFL, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x03)
                }

                Name (_PRW, Package (0x02)
                {
                    0x05, 
                    0x03
                })
            }

            Device (USBE)
            {
                Name (_ADR, 0x001D0007)
                Method (_S3D, 0, NotSerialized)
                {
                    If (LEqual (OSFL, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x03)
                }

                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x03
                })
            }

            Device (USE2)
            {
                Name (_ADR, 0x001A0007)
                Method (_S3D, 0, NotSerialized)
                {
                    If (LEqual (OSFL, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x03)
                }

                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x03
                })
            }

            Device (IDE1)
            {
                Name (_ADR, 0x001F0002)
                OperationRegion (PCI, PCI_Config, 0x40, 0x20)
                Field (PCI, DWordAcc, NoLock, Preserve)
                {
                    ITM0,   16, 
                    ITM1,   16, 
                    SIT0,   4, 
                    SIT1,   4, 
                            Offset (0x08), 
                    UDC0,   2, 
                    UDC1,   2, 
                            Offset (0x0A), 
                    UDT0,   8, 
                    UDT1,   8, 
                            Offset (0x14), 
                    ICF0,   2, 
                    ICF1,   2, 
                        ,   6, 
                    WPPE,   1, 
                        ,   1, 
                    FAS0,   2, 
                    FAS1,   2
                }

                Device (PRIM)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Store (GTM (ITM0, SIT0, UDC0, UDT0, ICF0, FAS0), Local0)
                        Return (Local0)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (STM (Arg0, Arg1, Arg2), Local0)
                        CreateDWordField (Local0, 0x00, ITM)
                        CreateDWordField (Local0, 0x04, SIT)
                        CreateDWordField (Local0, 0x08, UDC)
                        CreateDWordField (Local0, 0x0C, UDT)
                        CreateDWordField (Local0, 0x10, ICF)
                        CreateDWordField (Local0, 0x14, FAS)
                        Store (UDC, UDC0)
                        Store (UDT, UDT0)
                        Store (ICF, ICF0)
                        Store (FAS, FAS0)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Name (H15F, Zero)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (GTF0 (ITM0, SIT0, UDC0, UDT0, ICF0, H15F, FAS0), Local0)
                            Return (Local0)
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Name (H15F, Zero)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (GTF1 (ITM0, SIT0, UDC0, UDT0, ICF0, H15F, FAS0), Local0)
                            Return (Local0)
                        }
                    }
                }

                Device (SECD)
                {
                    Name (_ADR, 0x01)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Store (GTM (ITM1, SIT1, UDC1, UDT1, ICF1, FAS1), Local0)
                        Return (Local0)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (STM (Arg0, Arg1, Arg2), Local0)
                        CreateDWordField (Local0, 0x00, ITM)
                        CreateDWordField (Local0, 0x04, SIT)
                        CreateDWordField (Local0, 0x08, UDC)
                        CreateDWordField (Local0, 0x0C, UDT)
                        CreateDWordField (Local0, 0x10, ICF)
                        CreateDWordField (Local0, 0x14, FAS)
                        Store (UDC, UDC1)
                        Store (UDT, UDT1)
                        Store (ICF, ICF1)
                        Store (FAS, FAS1)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Name (H15F, Zero)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (GTF0 (ITM1, SIT1, UDC1, UDT1, ICF1, H15F, FAS1), Local0)
                            Return (Local0)
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Name (H15F, Zero)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (GTF1 (ITM1, SIT1, UDC1, UDT1, ICF1, H15F, FAS1), Local0)
                            Return (Local0)
                        }
                    }
                }
            }

            Device (IDE2)
            {
                Name (_ADR, 0x001F0005)
                OperationRegion (PCI, PCI_Config, 0x40, 0x20)
                Field (PCI, DWordAcc, NoLock, Preserve)
                {
                    ITM0,   16, 
                    ITM1,   16, 
                    SIT0,   4, 
                    SIT1,   4, 
                            Offset (0x08), 
                    UDC0,   1, 
                        ,   1, 
                    UDC1,   1, 
                            Offset (0x0A), 
                    UDT0,   8, 
                    UDT1,   8, 
                            Offset (0x14), 
                    ICF0,   2, 
                    ICF1,   2, 
                        ,   6, 
                    WPPE,   1, 
                        ,   1, 
                    FAS0,   2, 
                    FAS1,   2
                }

                Device (PRIM)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Store (GTM (ITM0, SIT0, UDC0, UDT0, ICF0, FAS0), Local0)
                        Return (Local0)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (STM (Arg0, Arg1, Arg2), Local0)
                        CreateDWordField (Local0, 0x00, ITM)
                        CreateDWordField (Local0, 0x04, SIT)
                        CreateDWordField (Local0, 0x08, UDC)
                        CreateDWordField (Local0, 0x0C, UDT)
                        CreateDWordField (Local0, 0x10, ICF)
                        CreateDWordField (Local0, 0x14, FAS)
                        Store (UDC, UDC0)
                        Store (UDT, UDT0)
                        Store (ICF, ICF0)
                        Store (FAS, FAS0)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Name (H15F, Zero)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (GTF0 (ITM0, SIT0, UDC0, UDT0, ICF0, H15F, FAS0), Local0)
                            Return (Local0)
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Name (H15F, Zero)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (GTF1 (ITM0, SIT0, UDC0, UDT0, ICF0, H15F, FAS0), Local0)
                            Return (Local0)
                        }
                    }
                }

                Device (SECD)
                {
                    Name (_ADR, 0x01)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Store (GTM (ITM1, SIT1, UDC1, UDT1, ICF1, FAS1), Local0)
                        Return (Local0)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (STM (Arg0, Arg1, Arg2), Local0)
                        CreateDWordField (Local0, 0x00, ITM)
                        CreateDWordField (Local0, 0x04, SIT)
                        CreateDWordField (Local0, 0x08, UDC)
                        CreateDWordField (Local0, 0x0C, UDT)
                        CreateDWordField (Local0, 0x10, ICF)
                        CreateDWordField (Local0, 0x14, FAS)
                        Store (UDC, UDC1)
                        Store (UDT, UDT1)
                        Store (ICF, ICF1)
                        Store (FAS, FAS1)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Name (H15F, Zero)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (GTF0 (ITM1, SIT1, UDC1, UDT1, ICF1, H15F, FAS1), Local0)
                            Return (Local0)
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Name (H15F, Zero)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store (GTF1 (ITM1, SIT1, UDC1, UDT1, ICF1, H15F, FAS1), Local0)
                            Return (Local0)
                        }
                    }
                }
            }

            Method (GTM, 6, NotSerialized)
            {
                Store (Buffer (0x14) {}, Local0)
                CreateDWordField (Local0, 0x00, PIO0)
                CreateDWordField (Local0, 0x04, DMA0)
                CreateDWordField (Local0, 0x08, PIO1)
                CreateDWordField (Local0, 0x0C, DMA1)
                CreateDWordField (Local0, 0x10, FLAG)
                Store (0x10, FLAG)
                If (LOr (And (Arg0, 0x08), LNot (And (Arg0, 0x01
                    ))))
                {
                    Store (0x0384, PIO0)
                }
                Else
                {
                    Add (ShiftRight (And (Arg0, 0x0300), 0x08), ShiftRight (And (
                        Arg0, 0x3000), 0x0C), Local1)
                    Multiply (Subtract (0x09, Local1), 0x1E, PIO0)
                }

                If (LOr (LAnd (Arg0, 0x4000), LAnd (Arg2, 0x01)))
                {
                    If (LOr (And (Arg0, 0x80), LNot (And (Arg0, 0x10
                        ))))
                    {
                        Store (0x0384, PIO1)
                    }
                    Else
                    {
                        Add (And (Arg1, 0x03), ShiftRight (And (Arg1, 0x0C), 
                            0x02), Local1)
                        Multiply (Subtract (0x09, Local1), 0x1E, PIO1)
                    }
                }
                Else
                {
                    Store (PIO0, PIO1)
                }

                If (And (Arg2, 0x01))
                {
                    Subtract (0x04, And (Arg3, 0x03), Local1)
                    If (And (Arg5, 0x01))
                    {
                        Store (0x14, DMA0)
                    }
                    Else
                    {
                        If (And (Arg4, 0x01))
                        {
                            Multiply (Local1, 0x0F, DMA0)
                        }
                        Else
                        {
                            Multiply (Local1, 0x1E, DMA0)
                        }
                    }
                }
                Else
                {
                    Store (PIO0, DMA0)
                }

                If (LOr (LAnd (Arg0, 0x4000), LAnd (Arg2, 0x01)))
                {
                    If (And (Arg2, 0x02))
                    {
                        Subtract (0x04, ShiftRight (And (Arg3, 0x30), 0x04), Local1)
                        If (And (Arg5, 0x02))
                        {
                            Store (0x14, DMA1)
                        }
                        Else
                        {
                            If (And (Arg4, 0x02))
                            {
                                Multiply (Local1, 0x0F, DMA1)
                            }
                            Else
                            {
                                Multiply (Local1, 0x1E, DMA1)
                            }
                        }
                    }
                    Else
                    {
                        Store (PIO1, DMA1)
                    }
                }
                Else
                {
                    Store (DMA0, DMA1)
                }

                Store (Zero, FLAG)
                If (And (Arg0, 0x01))
                {
                    Or (FLAG, 0x10, FLAG)
                }

                If (And (Arg2, 0x01))
                {
                    Or (FLAG, 0x01, FLAG)
                }

                If (And (Arg0, 0x02))
                {
                    Or (FLAG, 0x02, FLAG)
                }

                If (And (Arg2, 0x02))
                {
                    Or (FLAG, 0x04, FLAG)
                }

                If (And (Arg0, 0x20))
                {
                    Or (FLAG, 0x08, FLAG)
                }

                Return (Local0)
            }

            Method (STM, 3, NotSerialized)
            {
                Store (Buffer (0x18) {}, Local7)
                CreateDWordField (Local7, 0x00, ITM)
                CreateDWordField (Local7, 0x04, SIT)
                CreateDWordField (Local7, 0x08, UDC)
                CreateDWordField (Local7, 0x0C, UDT)
                CreateDWordField (Local7, 0x10, ICF)
                CreateDWordField (Local7, 0x14, FAS)
                CreateDWordField (Arg0, 0x00, PIO0)
                CreateDWordField (Arg0, 0x04, DMA0)
                CreateDWordField (Arg0, 0x08, PIO1)
                CreateDWordField (Arg0, 0x0C, DMA1)
                CreateDWordField (Arg0, 0x10, FLAG)
                Store (FLAG, Local4)
                Store (0x8000, Local0)
                If (And (Local4, 0x02))
                {
                    Or (Local0, 0x07, Local0)
                }

                If (And (Local4, 0x08))
                {
                    Or (Local0, 0x4000, Local0)
                    Or (Local0, 0x70, Local0)
                }

                If (LAnd (LLess (DMA0, PIO0), LNot (And (Local4, 0x01))))
                {
                    Or (Local0, 0x08, Local0)
                }

                If (LAnd (LLess (DMA1, PIO1), LNot (And (Local4, 0x04))))
                {
                    Or (Local0, 0x80, Local0)
                }

                If (PIO0)
                {
                    If (LLess (PIO0, 0x0384))
                    {
                        Or (Local0, 0x01, Local0)
                    }
                }

                If (PIO1)
                {
                    If (LLess (PIO1, 0x0384))
                    {
                        Or (Local0, 0x10, Local0)
                    }
                }

                If (And (Local4, 0x01))
                {
                    Store (PIO0, Local1)
                }
                Else
                {
                    Store (DMA0, Local1)
                }

                If (Local1)
                {
                    If (LLessEqual (Local1, 0x78))
                    {
                        Or (Local0, 0x2300, Local0)
                    }
                    Else
                    {
                        If (LLessEqual (Local1, 0xB4))
                        {
                            Or (Local0, 0x2100, Local0)
                        }
                        Else
                        {
                            If (LLessEqual (Local1, 0xF0))
                            {
                                Or (Local0, 0x1000, Local0)
                            }
                        }
                    }
                }

                Store (Local0, ITM)
                Store (Zero, Local0)
                If (And (Local4, 0x04))
                {
                    Store (PIO1, Local1)
                }
                Else
                {
                    Store (DMA1, Local1)
                }

                If (Local1)
                {
                    If (LLessEqual (Local1, 0x78))
                    {
                        Store (0x0B, Local0)
                    }
                    Else
                    {
                        If (LLessEqual (Local1, 0xB4))
                        {
                            Store (0x09, Local0)
                        }
                        Else
                        {
                            If (LLessEqual (Local1, 0xF0))
                            {
                                Store (0x04, Local0)
                            }
                        }
                    }
                }

                Store (Local0, SIT)
                Store (0x00, Local0)
                If (And (Local4, 0x01))
                {
                    Or (Local0, 0x01, Local0)
                }

                If (And (Local4, 0x04))
                {
                    Or (Local0, 0x02, Local0)
                }

                Store (Local0, UDC)
                Store (0x00, Local0)
                If (And (Local4, 0x01))
                {
                    If (LEqual (DMA0, 0x14))
                    {
                        Store (0x01, Local0)
                    }
                    Else
                    {
                        If (LLess (DMA0, 0x3C))
                        {
                            Divide (DMA0, 0x0F, , Local1)
                        }
                        Else
                        {
                            Divide (DMA0, 0x1E, , Local1)
                        }

                        Subtract (0x04, Local1, Local0)
                    }
                }

                If (And (Local4, 0x04))
                {
                    If (LEqual (DMA1, 0x14))
                    {
                        Store (0x01, Local1)
                    }
                    Else
                    {
                        If (LLess (DMA1, 0x3C))
                        {
                            Divide (DMA1, 0x0F, , Local1)
                        }
                        Else
                        {
                            Divide (DMA1, 0x1E, , Local1)
                        }

                        Subtract (0x04, Local1, Local1)
                    }

                    ShiftLeft (Local1, 0x04, Local1)
                    Or (Local0, Local1, Local0)
                }

                Store (Local0, UDT)
                Store (0x00, Local0)
                If (DMA0)
                {
                    If (LGreater (DMA0, 0x14))
                    {
                        If (LLess (DMA0, 0x3C))
                        {
                            Or (Local0, 0x01, Local0)
                        }
                    }
                }

                If (DMA1)
                {
                    If (LGreater (DMA1, 0x14))
                    {
                        If (LLess (DMA1, 0x3C))
                        {
                            Or (Local0, 0x02, Local0)
                        }
                    }
                }

                Store (Local0, ICF)
                Store (0x00, Local0)
                If (LEqual (DMA0, 0x14))
                {
                    Or (Local0, 0x01, Local0)
                }

                If (LEqual (DMA1, 0x14))
                {
                    Or (Local0, 0x02, Local0)
                }

                Store (Local0, FAS)
                Return (Local7)
            }

            Method (H15P, 1, NotSerialized)
            {
                Name (BUFF, Buffer (0x08)
                {
                    /* 0000 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00
                })
                Store (Arg0, Local0)
                Store (BUFF, Local1)
                Concatenate (Local0, Local1, Local7)
                CreateWordField (Local7, 0x02, CYL)
                CreateWordField (Local7, 0x06, HEAD)
                CreateWordField (Local7, 0x0C, SPT)
                If (LAnd (LGreaterEqual (HEAD, 0x10), LGreaterEqual (CYL, 0x2000)))
                {
                    Return (SPT)
                }
                Else
                {
                    Return (Zero)
                }
            }

            Method (GTF0, 7, NotSerialized)
            {
                Store (Buffer (0x07)
                    {
                        0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                    }, Local7)
                CreateByteField (Local7, 0x01, MODE)
                If (And (Arg2, 0x01))
                {
                    And (Arg3, 0x03, Local0)
                    If (And (Arg6, 0x01))
                    {
                        Add (Local0, 0x04, Local0)
                    }
                    Else
                    {
                        If (And (Arg4, 0x01))
                        {
                            Add (Local0, 0x02, Local0)
                        }
                    }

                    Or (Local0, 0x40, MODE)
                }
                Else
                {
                    Add (ShiftRight (And (Arg0, 0x0300), 0x08), ShiftRight (And (
                        Arg0, 0x3000), 0x0C), Local0)
                    If (LGreaterEqual (Local0, 0x05))
                    {
                        Store (0x22, MODE)
                    }
                    Else
                    {
                        If (LGreaterEqual (Local0, 0x03))
                        {
                            Store (0x21, MODE)
                        }
                        Else
                        {
                            Store (0x20, MODE)
                        }
                    }
                }

                Concatenate (Local7, Local7, Local6)
                If (LOr (And (Arg0, 0x08), LNot (And (Arg0, 0x01
                    ))))
                {
                    If (And (Arg0, 0x02))
                    {
                        Store (0x00, MODE)
                    }
                    Else
                    {
                        Store (0x01, MODE)
                    }
                }
                Else
                {
                    Add (ShiftRight (And (Arg0, 0x0300), 0x08), ShiftRight (And (
                        Arg0, 0x3000), 0x0C), Local0)
                    If (LGreaterEqual (Local0, 0x05))
                    {
                        Store (0x0C, MODE)
                    }
                    Else
                    {
                        If (LGreaterEqual (Local0, 0x03))
                        {
                            Store (0x0B, MODE)
                        }
                        Else
                        {
                            Store (0x0A, MODE)
                        }
                    }
                }

                Concatenate (Local6, Local7, Local5)
                If (Arg5)
                {
                    Store (Buffer (0x07)
                        {
                            0x00, 0x00, 0x00, 0x00, 0x00, 0xAE, 0x91
                        }, Local4)
                    CreateByteField (Local4, 0x01, SPT)
                    Store (Arg5, SPT)
                    Concatenate (Local5, Local4, Local6)
                    Return (Local6)
                }
                Else
                {
                    Return (Local5)
                }
            }

            Method (GTF1, 7, NotSerialized)
            {
                Store (Buffer (0x07)
                    {
                        0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                    }, Local7)
                CreateByteField (Local7, 0x01, MODE)
                If (And (Arg2, 0x02))
                {
                    ShiftRight (And (Arg3, 0x30), 0x04, Local0)
                    If (And (Arg6, 0x02))
                    {
                        Add (Local0, 0x04, Local0)
                    }
                    Else
                    {
                        If (And (Arg4, 0x02))
                        {
                            Add (Local0, 0x02, Local0)
                        }
                    }

                    Or (Local0, 0x40, MODE)
                }
                Else
                {
                    Add (ShiftRight (And (Arg1, 0x03), 0x02), And (Arg1, 
                        0x0C), Local0)
                    If (LGreaterEqual (Local0, 0x05))
                    {
                        Store (0x22, MODE)
                    }
                    Else
                    {
                        If (LGreaterEqual (Local0, 0x03))
                        {
                            Store (0x21, MODE)
                        }
                        Else
                        {
                            Store (0x20, MODE)
                        }
                    }
                }

                Concatenate (Local7, Local7, Local6)
                If (LOr (And (Arg0, 0x80), LNot (And (Arg0, 0x10
                    ))))
                {
                    If (And (Arg0, 0x20))
                    {
                        Store (0x00, MODE)
                    }
                    Else
                    {
                        Store (0x01, MODE)
                    }
                }
                Else
                {
                    Add (ShiftRight (And (Arg1, 0x03), 0x02), And (Arg1, 
                        0x0C), Local0)
                    If (LGreaterEqual (Local0, 0x05))
                    {
                        Store (0x0C, MODE)
                    }
                    Else
                    {
                        If (LGreaterEqual (Local0, 0x03))
                        {
                            Store (0x0B, MODE)
                        }
                        Else
                        {
                            Store (0x0A, MODE)
                        }
                    }
                }

                Concatenate (Local6, Local7, Local5)
                If (Arg5)
                {
                    Store (Buffer (0x07)
                        {
                            0x00, 0x00, 0x00, 0x00, 0x00, 0xBE, 0x91
                        }, Local4)
                    CreateByteField (Local4, 0x01, SPT)
                    Store (Arg5, SPT)
                    Concatenate (Local5, Local4, Local6)
                    Return (Local6)
                }
                Else
                {
                    Return (Local5)
                }
            }

            Device (PX43)
            {
                Name (_ADR, 0x001F0003)
                OperationRegion (PBAS, PCI_Config, 0x20, 0x02)
                Field (PBAS, ByteAcc, NoLock, Preserve)
                {
                    BAS0,   16
                }

                Method (SMBB, 0, NotSerialized)
                {
                    And (BAS0, 0xFFFE, Local0)
                    Return (Local0)
                }
            }

            Device (AZAL)
            {
                Name (_ADR, 0x001B0000)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (Package (0x02)
                    {
                        0x0D, 
                        0x05
                    })
                }
            }

            Name (BUFA, ResourceTemplate ()
            {
                IRQ (Level, ActiveLow, Shared, )
                    {3,4,5,6,7,9,10,11,12,14,15}
            })
            Name (BUFB, ResourceTemplate ()
            {
                IRQ (Level, ActiveLow, Shared, _Y0A)
                    {}
            })
            CreateWordField (BUFB, \_SB.PCI0._Y0A._INT, IRQV)
            Device (LNKA)
            {
                Name (_HID, EisaId ("PNP0C0F"))
                Name (_UID, 0x01)
                Method (_STA, 0, NotSerialized)
                {
                    And (PIRA, 0x80, Local0)
                    If (LEqual (Local0, 0x80))
                    {
                        Return (0x09)
                    }
                    Else
                    {
                        Return (0x0B)
                    }
                }

                Method (_PRS, 0, NotSerialized)
                {
                    Return (BUFA)
                }

                Method (_DIS, 0, NotSerialized)
                {
                    Or (PIRA, 0x80, PIRA)
                }

                Method (_CRS, 0, NotSerialized)
                {
                    And (PIRA, 0x0F, Local0)
                    ShiftLeft (0x01, Local0, IRQV)
                    Return (BUFB)
                }

                Method (_SRS, 1, NotSerialized)
                {
                    CreateWordField (Arg0, 0x01, IRQ1)
                    FindSetRightBit (IRQ1, Local0)
                    Decrement (Local0)
                    Store (Local0, PIRA)
                }
            }

            Device (LNKB)
            {
                Name (_HID, EisaId ("PNP0C0F"))
                Name (_UID, 0x02)
                Method (_STA, 0, NotSerialized)
                {
                    And (PIRB, 0x80, Local0)
                    If (LEqual (Local0, 0x80))
                    {
                        Return (0x09)
                    }
                    Else
                    {
                        Return (0x0B)
                    }
                }

                Method (_PRS, 0, NotSerialized)
                {
                    Return (BUFA)
                }

                Method (_DIS, 0, NotSerialized)
                {
                    Or (PIRB, 0x80, PIRB)
                }

                Method (_CRS, 0, NotSerialized)
                {
                    And (PIRB, 0x0F, Local0)
                    ShiftLeft (0x01, Local0, IRQV)
                    Return (BUFB)
                }

                Method (_SRS, 1, NotSerialized)
                {
                    CreateWordField (Arg0, 0x01, IRQ1)
                    FindSetRightBit (IRQ1, Local0)
                    Decrement (Local0)
                    Store (Local0, PIRB)
                }
            }

            Device (LNKC)
            {
                Name (_HID, EisaId ("PNP0C0F"))
                Name (_UID, 0x03)
                Method (_STA, 0, NotSerialized)
                {
                    And (PIRC, 0x80, Local0)
                    If (LEqual (Local0, 0x80))
                    {
                        Return (0x09)
                    }
                    Else
                    {
                        Return (0x0B)
                    }
                }

                Method (_PRS, 0, NotSerialized)
                {
                    Return (BUFA)
                }

                Method (_DIS, 0, NotSerialized)
                {
                    Or (PIRC, 0x80, PIRC)
                }

                Method (_CRS, 0, NotSerialized)
                {
                    And (PIRC, 0x0F, Local0)
                    ShiftLeft (0x01, Local0, IRQV)
                    Return (BUFB)
                }

                Method (_SRS, 1, NotSerialized)
                {
                    CreateWordField (Arg0, 0x01, IRQ1)
                    FindSetRightBit (IRQ1, Local0)
                    Decrement (Local0)
                    Store (Local0, PIRC)
                }
            }

            Device (LNKD)
            {
                Name (_HID, EisaId ("PNP0C0F"))
                Name (_UID, 0x04)
                Method (_STA, 0, NotSerialized)
                {
                    And (PIRD, 0x80, Local0)
                    If (LEqual (Local0, 0x80))
                    {
                        Return (0x09)
                    }
                    Else
                    {
                        Return (0x0B)
                    }
                }

                Method (_PRS, 0, NotSerialized)
                {
                    Return (BUFA)
                }

                Method (_DIS, 0, NotSerialized)
                {
                    Or (PIRD, 0x80, PIRD)
                }

                Method (_CRS, 0, NotSerialized)
                {
                    And (PIRD, 0x0F, Local0)
                    ShiftLeft (0x01, Local0, IRQV)
                    Return (BUFB)
                }

                Method (_SRS, 1, NotSerialized)
                {
                    CreateWordField (Arg0, 0x01, IRQ1)
                    FindSetRightBit (IRQ1, Local0)
                    Decrement (Local0)
                    Store (Local0, PIRD)
                }
            }

            Device (LNKE)
            {
                Name (_HID, EisaId ("PNP0C0F"))
                Name (_UID, 0x05)
                Method (_STA, 0, NotSerialized)
                {
                    And (PIRE, 0x80, Local0)
                    If (LEqual (Local0, 0x80))
                    {
                        Return (0x09)
                    }
                    Else
                    {
                        Return (0x0B)
                    }
                }

                Method (_PRS, 0, NotSerialized)
                {
                    Return (BUFA)
                }

                Method (_DIS, 0, NotSerialized)
                {
                    Or (PIRE, 0x80, PIRE)
                }

                Method (_CRS, 0, NotSerialized)
                {
                    And (PIRE, 0x0F, Local0)
                    ShiftLeft (0x01, Local0, IRQV)
                    Return (BUFB)
                }

                Method (_SRS, 1, NotSerialized)
                {
                    CreateWordField (Arg0, 0x01, IRQ1)
                    FindSetRightBit (IRQ1, Local0)
                    Decrement (Local0)
                    Store (Local0, PIRE)
                }
            }

            Device (LNKF)
            {
                Name (_HID, EisaId ("PNP0C0F"))
                Name (_UID, 0x06)
                Method (_STA, 0, NotSerialized)
                {
                    And (PIRF, 0x80, Local0)
                    If (LEqual (Local0, 0x80))
                    {
                        Return (0x09)
                    }
                    Else
                    {
                        Return (0x0B)
                    }
                }

                Method (_PRS, 0, NotSerialized)
                {
                    Return (BUFA)
                }

                Method (_DIS, 0, NotSerialized)
                {
                    Or (PIRF, 0x80, PIRF)
                }

                Method (_CRS, 0, NotSerialized)
                {
                    And (PIRF, 0x0F, Local0)
                    ShiftLeft (0x01, Local0, IRQV)
                    Return (BUFB)
                }

                Method (_SRS, 1, NotSerialized)
                {
                    CreateWordField (Arg0, 0x01, IRQ1)
                    FindSetRightBit (IRQ1, Local0)
                    Decrement (Local0)
                    Store (Local0, PIRF)
                }
            }

            Device (LNK0)
            {
                Name (_HID, EisaId ("PNP0C0F"))
                Name (_UID, 0x07)
                Method (_STA, 0, NotSerialized)
                {
                    And (PIRG, 0x80, Local0)
                    If (LEqual (Local0, 0x80))
                    {
                        Return (0x09)
                    }
                    Else
                    {
                        Return (0x0B)
                    }
                }

                Method (_PRS, 0, NotSerialized)
                {
                    Return (BUFA)
                }

                Method (_DIS, 0, NotSerialized)
                {
                    Or (PIRG, 0x80, PIRG)
                }

                Method (_CRS, 0, NotSerialized)
                {
                    And (PIRG, 0x0F, Local0)
                    ShiftLeft (0x01, Local0, IRQV)
                    Return (BUFB)
                }

                Method (_SRS, 1, NotSerialized)
                {
                    CreateWordField (Arg0, 0x01, IRQ1)
                    FindSetRightBit (IRQ1, Local0)
                    Decrement (Local0)
                    Store (Local0, PIRG)
                }
            }

            Device (LNK1)
            {
                Name (_HID, EisaId ("PNP0C0F"))
                Name (_UID, 0x08)
                Method (_STA, 0, NotSerialized)
                {
                    And (PIRH, 0x80, Local0)
                    If (LEqual (Local0, 0x80))
                    {
                        Return (0x09)
                    }
                    Else
                    {
                        Return (0x0B)
                    }
                }

                Method (_PRS, 0, NotSerialized)
                {
                    Return (BUFA)
                }

                Method (_DIS, 0, NotSerialized)
                {
                    Or (PIRH, 0x80, PIRH)
                }

                Method (_CRS, 0, NotSerialized)
                {
                    And (PIRH, 0x0F, Local0)
                    ShiftLeft (0x01, Local0, IRQV)
                    Return (BUFB)
                }

                Method (_SRS, 1, NotSerialized)
                {
                    CreateWordField (Arg0, 0x01, IRQ1)
                    FindSetRightBit (IRQ1, Local0)
                    Decrement (Local0)
                    Store (Local0, PIRH)
                }
            }

            Method (_PRW, 0, NotSerialized)
            {
                Return (Package (0x02)
                {
                    0x0B, 
                    0x05
                })
            }
        }

        Device (MEM)
        {
            Name (_HID, EisaId ("PNP0C01"))
            Method (_CRS, 0, NotSerialized)
            {
                Name (BUF0, ResourceTemplate ()
                {
                    Memory32Fixed (ReadWrite,
                        0x000F0000,         // Address Base
                        0x00004000,         // Address Length
                        _Y0C)
                    Memory32Fixed (ReadWrite,
                        0x000F4000,         // Address Base
                        0x00004000,         // Address Length
                        _Y0D)
                    Memory32Fixed (ReadWrite,
                        0x000F8000,         // Address Base
                        0x00004000,         // Address Length
                        _Y0E)
                    Memory32Fixed (ReadWrite,
                        0x000FC000,         // Address Base
                        0x00004000,         // Address Length
                        _Y0F)
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00010000,         // Address Length
                        _Y0B)
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x000A0000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0x00100000,         // Address Base
                        0x00000000,         // Address Length
                        _Y11)
                    Memory32Fixed (ReadWrite,
                        0xFEC00000,         // Address Base
                        0x00001000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED10000,         // Address Base
                        0x0000E000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED20000,         // Address Base
                        0x00070000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFEE00000,         // Address Base
                        0x00001000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFFB00000,         // Address Base
                        0x00080000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFFF00000,         // Address Base
                        0x00100000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0x000E0000,         // Address Base
                        0x00010000,         // Address Length
                        _Y10)
                })
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y0B._BAS, ACMM)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y0B._LEN, ASSM)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y0C._BAS, RMA1)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y0C._LEN, RSS1)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y0D._BAS, RMA2)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y0D._LEN, RSS2)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y0E._BAS, RMA3)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y0E._LEN, RSS3)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y0F._BAS, RMA4)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y0F._LEN, RSS4)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y10._BAS, ERMA)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y10._LEN, ERMS)
                CreateDWordField (BUF0, \_SB.MEM._CRS._Y11._LEN, EXTM)
                Subtract (AMEM, 0x00100000, EXTM)
                If (LNotEqual (ROM1, Zero))
                {
                    Store (RMA1, RMA2)
                    ShiftLeft (ROM1, 0x08, Local0)
                    Store (Local0, RMA1)
                    ShiftLeft (RMS1, 0x08, Local0)
                    Store (Local0, RSS1)
                    Store (0x8000, RSS2)
                }

                If (LNotEqual (ROM2, Zero))
                {
                    Store (RMA2, RMA3)
                    ShiftLeft (ROM2, 0x08, Local0)
                    Store (Local0, RMA2)
                    ShiftLeft (RMS2, 0x08, Local0)
                    Store (Local0, RSS2)
                    Store (0xC000, RSS3)
                }

                If (LNotEqual (ROM3, Zero))
                {
                    Store (RMA3, RMA4)
                    ShiftLeft (ROM3, 0x08, Local0)
                    Store (Local0, RMA3)
                    ShiftLeft (RMS3, 0x08, Local0)
                    Store (Local0, RSS3)
                    Store (0x00010000, RSS4)
                }

                Store (ERMA, Local1)
                If (LGreater (RMA1, 0x000D0000))
                {
                    If (LLess (RMA1, 0x000F0000))
                    {
                        Add (RMA1, RSS1, Local0)
                        If (LGreater (Local0, 0x000E0000))
                        {
                            If (LGreater (Local0, Local1))
                            {
                                Store (Local0, Local1)
                            }
                        }
                    }
                }

                If (LGreater (RMA2, 0x000D0000))
                {
                    If (LLess (RMA2, 0x000F0000))
                    {
                        Add (RMA2, RSS2, Local0)
                        If (LGreater (Local0, 0x000E0000))
                        {
                            If (LGreater (Local0, Local1))
                            {
                                Store (Local0, Local1)
                            }
                        }
                    }
                }

                If (LGreater (RMA3, 0x000D0000))
                {
                    If (LLess (RMA3, 0x000F0000))
                    {
                        Add (RMA3, RSS3, Local0)
                        If (LGreater (Local0, 0x000E0000))
                        {
                            If (LGreater (Local0, Local1))
                            {
                                Store (Local0, Local1)
                            }
                        }
                    }
                }

                If (LGreater (Local1, ERMA))
                {
                    Subtract (Local1, ERMA, Local0)
                    If (LLessEqual (Local0, 0x00010000))
                    {
                        Store (Local1, ERMA)
                        Subtract (0x00010000, Local0, ERMS)
                    }
                }

                Store (AMEM, ACMM)
                And (AMEM, 0x000FFFFF, Local0)
                Subtract (0x00100000, Local0, ASSM)
                Return (BUF0)
            }
        }

        Device (FWH)
        {
            Name (_HID, EisaId ("INT0800"))
            Method (_CRS, 0, NotSerialized)
            {
                Name (FWH0, ResourceTemplate ()
                {
                    Memory32Fixed (ReadWrite,
                        0xFFB80000,         // Address Base
                        0x00080000,         // Address Length
                        )
                })
                Return (FWH0)
            }
        }

        Device (\_SB.PCI0.EXPL)
        {
            Name (_HID, EisaId ("PNP0C02"))
            Name (_UID, 0x04)
            Method (_CRS, 0, NotSerialized)
            {
                Name (BUF0, ResourceTemplate ()
                {
                    Memory32Fixed (ReadWrite,
                        0xF0000000,         // Address Base
                        0x04000000,         // Address Length
                        )
                })
                Return (BUF0)
            }
        }
    }
}

```

 other than seeing it was compiled with a microsoft compiler and it has a reference to windows 2001, so I tried booting with 

acpi_osi="Windows 2001"

also tried "Linux" and "Windows 2006" but no change.

Considering the fact custom DSDT's no longer seem supported on current kernels, I guess this is a dead end?

---

### Post by zabsv on 2010-10-12
I had this problem a while ago and was able to slove it by changing my  bios settings. This was on an Asus P5K motherboard, so I can't guarantee  that it will work for you.
Anyway, when I set my FSB clock to manual I also set my FSB:CPU ratio to  manual. Changing the ratio setting to auto (and keeping the clock at manual) gave me the correct ratio  and made frequency scaling work.

For some reason Ubuntu now detects the CPU as running in 2.66GHz even  though it's running at 3.2Ghz. When the FSB:CPU ratio in bios was manual  Ubuntu detected the frequenct correctly.

To verify that it really runs at overclocked speed you can run: cat  /proc/cpuinfo|grep bogomips this value should change according to real  cpu speed.

---

### Post by P4man on 2010-10-13
thanks zabsv, that sounded promising. Unfortunately, it doesnt seem to work for me as my motherboard doesnt have an auto setting for that ratio. I can only select 6x or 8x ratios and both seem to result in 8x in linux.

Oh well.

---

### Post by tora201 on 2011-01-05
Did you ever solve this? Same problem here! I have the DS3 version of your Mobo. I also don't want to give up my overclock of 2.66 --> 4 gig. :-(

---

### Post by rookcifer on 2011-01-20
I have this same problem, though it is not with an Intel motherboard or CPU.  I am using an AMD Phenom II on a Gigabyte motherboard.  CPU frequency scaling simply does not work when i have my processor overclocked (Linux shows my clock speed as stock, even though it is not running at stock).  When I have the processor running at stock, the frequency scaling works fine.

As a guy pointed out in my thread, the motherboard makers don't care about Linux and only ensure their BIOS returns the correct settings to Windows.  This means they are not following proper ACPI protocols, so there is nothing we can do about it other than b*tch at the motherboard manufacturers.

---

### Post by psusi on 2011-01-21
Indeed.  I for one am fed up with the yahoos refusing to follow the ACPI standard for frequency and fan control.

---

