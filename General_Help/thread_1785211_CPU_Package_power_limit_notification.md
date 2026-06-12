---
title: "CPU Package power limit notification"
date: 2011-06-18
forum: General Help
---

### Post by Zaelyx on 2011-06-18
I recently bought a Toshiba A665-S5187, which has the new i7-2630QM Sandy Bridge Processor. My dmesg output is a bit strange, and I see messages that I am not sure what to think of. I am using kernel version 2.6.39-3-generic.

```

[20793.149764] CPU0: Package power limit notification (total events = 1)
[20793.149770] CPU4: Package power limit notification (total events = 1)
[20793.149776] CPU3: Package power limit notification (total events = 1)
[20793.149778] CPU2: Package power limit notification (total events = 1)
[20793.149786] CPU7: Package power limit notification (total events = 1)
[20793.149788] CPU6: Package power limit notification (total events = 1)
[20793.149788] Disabling lock debugging due to kernel taint
[20793.149794] CPU5: Package power limit notification (total events = 1)
[20793.149799] CPU1: Package power limit notification (total events = 1)
[20793.150318] CPU5: Package power limit normal
[20793.150327] CPU2: Package power limit normal
[20793.150328] CPU4: Package power limit normal
[20793.150331] CPU0: Package power limit normal
[20793.150336] CPU3: Package power limit normal
[20793.150334] CPU7: Package power limit normal
[20793.150337] CPU1: Package power limit normal
[20793.150340] CPU6: Package power limit normal
[21000.040090] [Hardware Error]: Machine check events logged
[37051.061157] CPU4: Package power limit notification (total events = 10)
[37051.061163] CPU0: Package power limit notification (total events = 10)
[37051.061165] CPU7: Package power limit notification (total events = 10)
[37051.061166] CPU6: Package power limit notification (total events = 10)
[37051.061173] CPU2: Package power limit notification (total events = 10)
[37051.061177] CPU5: Package power limit notification (total events = 10)
[37051.061182] CPU3: Package power limit notification (total events = 10)
[37051.061181] CPU1: Package power limit notification (total events = 10)
[37051.068955] CPU2: Package power limit normal
[37051.068958] CPU5: Package power limit normal
[37051.068964] CPU0: Package power limit normal
[37051.068965] CPU7: Package power limit normal
[37051.068965] CPU6: Package power limit normal
[37051.068972] CPU3: Package power limit normal
[37051.068973] CPU4: Package power limit normal
[37051.068973] CPU1: Package power limit normal
[37200.890072] [Hardware Error]: Machine check events logged

```

I also get this message:
```

[   53.150123] [drm:pch_irq_handler] *ERROR* PCH poison interrupt

```

I have the CPU Frequency Scaling Governer set to Conservative, if it makes any difference.
What does this mean? The system does not kernel panic or anything, but I would like to know why I am getting these strange messages. Thanks!

Edit: Mcelog output:
```

HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 0
CPU 3 THERMAL EVENT TSC 25c4a18bf580 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 3 below trip temperature. Throttling disabled
STATUS c0000000882d0c08 MCGSTATUS 0
MCGCAP c09 APICID 6 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 1
CPU 2 THERMAL EVENT TSC 25c4a18c1681 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 2 below trip temperature. Throttling disabled
STATUS c0000000882d0c08 MCGSTATUS 0
MCGCAP c09 APICID 4 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 2
CPU 7 THERMAL EVENT TSC 25c4a18c2dcc 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 7 below trip temperature. Throttling disabled
STATUS c0000000882d0c08 MCGSTATUS 0
MCGCAP c09 APICID 7 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 3
CPU 6 THERMAL EVENT TSC 25c4a18c4b24 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 6 below trip temperature. Throttling disabled
STATUS c0000000882d0c08 MCGSTATUS 0
MCGCAP c09 APICID 5 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 4
CPU 4 THERMAL EVENT TSC 25c4a18c5588 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 4 below trip temperature. Throttling disabled
STATUS c0000000882d0c08 MCGSTATUS 0
MCGCAP c09 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 5
CPU 5 THERMAL EVENT TSC 25c4a18c7964 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 5 below trip temperature. Throttling disabled
STATUS c0000000882d0c08 MCGSTATUS 0
MCGCAP c09 APICID 3 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 6
CPU 1 THERMAL EVENT TSC 25c4a18c8a68 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 1 below trip temperature. Throttling disabled
STATUS c0000000882d0c08 MCGSTATUS 0
MCGCAP c09 APICID 2 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 7
CPU 0 THERMAL EVENT TSC 25c4a14f88f8 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 0 below trip temperature. Throttling disabled
STATUS c0000000882d0c08 MCGSTATUS 0
MCGCAP c09 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 8
CPU 2 THERMAL EVENT TSC 25c4a19c972e 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 2 below trip temperature. Throttling disabled
STATUS c0000000882d0808 MCGSTATUS 0
MCGCAP c09 APICID 4 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 9
CPU 4 THERMAL EVENT TSC 25c4a19cabf9 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 4 below trip temperature. Throttling disabled
STATUS c0000000882d0808 MCGSTATUS 0
MCGCAP c09 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 10
CPU 0 THERMAL EVENT TSC 25c4a15fb2e2 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 0 below trip temperature. Throttling disabled
STATUS c0000000882d0808 MCGSTATUS 0
MCGCAP c09 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 11
CPU 3 THERMAL EVENT TSC 25c4a19cd269 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 3 below trip temperature. Throttling disabled
STATUS c0000000882d0808 MCGSTATUS 0
MCGCAP c09 APICID 6 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 12
CPU 7 THERMAL EVENT TSC 25c4a19ce136 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 7 below trip temperature. Throttling disabled
STATUS c0000000882d0808 MCGSTATUS 0
MCGCAP c09 APICID 7 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 13
CPU 1 THERMAL EVENT TSC 25c4a19cf24a 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 1 below trip temperature. Throttling disabled
STATUS c0000000882d0808 MCGSTATUS 0
MCGCAP c09 APICID 2 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 14
CPU 6 THERMAL EVENT TSC 25c4a19d03b0 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 6 below trip temperature. Throttling disabled
STATUS c0000000882d0808 MCGSTATUS 0
MCGCAP c09 APICID 5 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 15
CPU 5 THERMAL EVENT TSC 25c4a19d0833 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 5 below trip temperature. Throttling disabled
STATUS c0000000882d0808 MCGSTATUS 0
MCGCAP c09 APICID 3 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 16
CPU 0 THERMAL EVENT TSC 4346268dd78b 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 0 below trip temperature. Throttling disabled
STATUS c000000088280c08 MCGSTATUS 0
MCGCAP c09 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 17
CPU 7 THERMAL EVENT TSC 434626cafdc2 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 7 below trip temperature. Throttling disabled
STATUS c000000088280c08 MCGSTATUS 0
MCGCAP c09 APICID 7 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 18
CPU 6 THERMAL EVENT TSC 434626cb1e3d 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 6 below trip temperature. Throttling disabled
STATUS c000000088280c08 MCGSTATUS 0
MCGCAP c09 APICID 5 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 19
CPU 2 THERMAL EVENT TSC 434626cb398e 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 2 below trip temperature. Throttling disabled
STATUS c000000088280c08 MCGSTATUS 0
MCGCAP c09 APICID 4 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 20
CPU 5 THERMAL EVENT TSC 434626cb5d88 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 5 below trip temperature. Throttling disabled
STATUS c000000088280c08 MCGSTATUS 0
MCGCAP c09 APICID 3 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 21
CPU 3 THERMAL EVENT TSC 434626cb74d2 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 3 below trip temperature. Throttling disabled
STATUS c000000088280c08 MCGSTATUS 0
MCGCAP c09 APICID 6 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 22
CPU 1 THERMAL EVENT TSC 434626cb8dfe 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 1 below trip temperature. Throttling disabled
STATUS c000000088280c08 MCGSTATUS 0
MCGCAP c09 APICID 2 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 23
CPU 4 THERMAL EVENT TSC 434626cbb3f2 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 4 below trip temperature. Throttling disabled
STATUS c000000088280c08 MCGSTATUS 0
MCGCAP c09 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 24
CPU 5 THERMAL EVENT TSC 434627b85edd 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 5 below trip temperature. Throttling disabled
STATUS c000000088280808 MCGSTATUS 0
MCGCAP c09 APICID 3 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 25
CPU 0 THERMAL EVENT TSC 4346277b6cf6 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 0 below trip temperature. Throttling disabled
STATUS c000000088280808 MCGSTATUS 0
MCGCAP c09 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 26
CPU 7 THERMAL EVENT TSC 434627b891b4 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 7 below trip temperature. Throttling disabled
STATUS c000000088280808 MCGSTATUS 0
MCGCAP c09 APICID 7 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 27
CPU 6 THERMAL EVENT TSC 434627b8a50e 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 6 below trip temperature. Throttling disabled
STATUS c000000088280808 MCGSTATUS 0
MCGCAP c09 APICID 5 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 28
CPU 3 THERMAL EVENT TSC 434627b8b964 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 3 below trip temperature. Throttling disabled
STATUS c000000088280808 MCGSTATUS 0
MCGCAP c09 APICID 6 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 29
CPU 4 THERMAL EVENT TSC 434627b8ce29 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 4 below trip temperature. Throttling disabled
STATUS c000000088280808 MCGSTATUS 0
MCGCAP c09 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 30
CPU 1 THERMAL EVENT TSC 434627b8e15b 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 1 below trip temperature. Throttling disabled
STATUS c000000088280808 MCGSTATUS 0
MCGCAP c09 APICID 2 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 31
CPU 2 THERMAL EVENT TSC 434627b8e574 
TIME 1308369807 Sat Jun 18 00:03:27 2011
Processor 2 below trip temperature. Throttling disabled
STATUS c000000088280808 MCGSTATUS 0
MCGCAP c09 APICID 4 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42

```

---

### Post by wildmanne39 on 2011-06-18
Hi, do not know, but it does not look good. You could have a failure coming on, or it may be the kernel you are using, you know that is the one for testing it is not meant to be used for a production machine.

---

### Post by VValdo on 2011-06-20
I am seeing the exact same thing with a thinkpad with the same chip...  

using

Linux laptop 2.6.39-0-generic

I don't know what to think either but it's kinda freaking me out.

Maybe it's bogus?  See this [bug report]("http://marc.info/?l=linux-kernel&m=130606930631131&w=2").  I got some of these while it was idle and cool.  But some I got while compiling (as a test) so i'm not sure..

---

### Post by djstrong on 2012-02-28
The same here on Asus X53S with i7-2670QM.
```
mcelog: failed to prefill DIMM database from DMI data
Kernel does not support page offline interface
mcelog: mcelog read: No such device
Hardware event. This is not a software error.
MCE 0
CPU 1 THERMAL EVENT TSC 1bbb8d6c72
TIME 1326639580 Sun Jan 15 15:59:40 2012
Processor 1 below trip temperature. Throttling disabled
STATUS c0000000881e0c00 MCGSTATUS 0
MCGCAP c09 APICID 2 SOCKETID 0
CPUID Vendor Intel Family 6 Model 42
Hardware event. This is not a software error.
MCE 1
CPU 7 THERMAL EVENT TSC 1bbb8d8f1e
TIME 1326639580 Sun Jan 15 15:59:40 2012
Processor 7 below trip temperature. Throttling disabled
STATUS c0000000881e0c00 MCGSTATUS 0
MCGCAP c09 APICID 7 SOCKETID 0
CPUID Vendor Intel Family 6 Model 42
Hardware event. This is not a software error.
MCE 2
CPU 5 THERMAL EVENT TSC 1bbb8daec1
TIME 1326639580 Sun Jan 15 15:59:40 2012
Processor 5 below trip temperature. Throttling disabled
STATUS c0000000881e0c00 MCGSTATUS 0
MCGCAP c09 APICID 3 SOCKETID 0
CPUID Vendor Intel Family 6 Model 42
Hardware event. This is not a software error.
```

```
[32589.818393] [Hardware Error]: Machine check events logged
[32928.317294] CPU7: Package power limit notification (total events = 1431)
[32928.317298] CPU0: Package power limit notification (total events = 1431)
[32928.317302] CPU2: Package power limit notification (total events = 1431)
[32928.317306] CPU3: Package power limit notification (total events = 1431)
[32928.317309] CPU6: Package power limit notification (total events = 1431)
[32928.317313] CPU1: Package power limit notification (total events = 1431)
[32928.317317] CPU4: Package power limit notification (total events = 1431)
[32928.317320] CPU5: Package power limit notification (total events = 1431)
[32928.328307] CPU0: Package power limit normal
[32928.328316] CPU4: Package power limit normal
[32928.328327] CPU5: Package power limit normal
[32928.328335] CPU1: Package power limit normal
[32928.328353] CPU2: Package power limit normal
[32928.328363] CPU6: Package power limit normal
[32928.328374] CPU7: Package power limit normal
[32928.328382] CPU3: Package power limit normal
[33039.324489] [Hardware Error]: Machine check events logged
```

I have Ubuntu 11.10 (3.0.0-16-generic) and have some random crashes (may be related to chrome). On Windows 7 I don't see any problems.

---

### Post by Stonecold1995 on 2012-06-23
I'm getting the exact same thing on my MainGear ex-L 15 (i7-2760QM).  Of course, I also run Folding@home 24/7, and that keeps my CPU at 100%, but this is a gaming laptop, and is built to withstand huge CPU load.  However, I'm pretty sure I get this same error even when the CPU is idle.

The output of "uname -a" is:
```
Linux kubuntu 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

I've never had any problems with overheating, I've never had a kernel panic (well, I did once when I tested a fork-bomb on my computer), and I haven't overclocked/overvoltaged it at all.

I don't really worry about it, but it is starting to concern me, because this is a $3,000+ laptop...

---

### Post by Redblade20XX on 2012-06-23
Isn't there a power bug in the kernel about the sandybridge processors that have them running at full capacity all the time. Maybe this has something to do with your problems.

-Red

---

### Post by Giacecco on 2012-07-14
Some problem here with 12.04 on a Lenovo X220 laptop. I get a series of messages like this every five minutes:

```
Jul 14 17:32:16 giaceccos-x220 kernel: [ 8180.004993] CPU3: Package power limit notification (total events = 6921)
Jul 14 17:32:16 giaceccos-x220 kernel: [ 8180.004997] CPU2: Package power limit notification (total events = 6921)
Jul 14 17:32:16 giaceccos-x220 kernel: [ 8180.005000] CPU1: Package power limit notification (total events = 6938)
Jul 14 17:32:16 giaceccos-x220 kernel: [ 8180.005003] CPU0: Package power limit notification (total events = 6938)
Jul 14 17:32:16 giaceccos-x220 kernel: [ 8180.005527] CPU1: Package power limit normal
Jul 14 17:32:16 giaceccos-x220 kernel: [ 8180.005530] CPU3: Package power limit normal
Jul 14 17:32:16 giaceccos-x220 kernel: [ 8180.005532] CPU2: Package power limit normal
Jul 14 17:32:16 giaceccos-x220 kernel: [ 8180.005534] CPU0: Package power limit normal
```

The computer is behaving normally and I would not have noticed if I did not snoop into the syslog. The kernel version is:

```
giacecco@giaceccos-x220:~$ uname -a
Linux giaceccos-x220 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

```

---

### Post by humilleitor on 2012-10-06
Same thing here with a Toshiba Portege, Intel i5-2467 Sandybridge. Get the message every forty or sixty minutes. I'm sure it's nothing to worry about: my CPU is perfectly cool, running at low speed. What really annoyes me is that this message jumps into my tty and garbles the console, messing up whatever task I was doing.

Does anyone know how to prevent these messages from bothering me in the tty console?

---

### Post by Stonecold1995 on 2012-10-06
> **humilleitor said:**
> Same thing here with a Toshiba Portege, Intel i5-2467 Sandybridge. Get the message every forty or sixty minutes. I'm sure it's nothing to worry about: my CPU is perfectly cool, running at low speed. What really annoyes me is that this message jumps into my tty and garbles the console, messing up whatever task I was doing.

Does anyone know how to prevent these messages from bothering me in the tty console?

Lucky!  I get it every couple minutes!  It also completely fills up my syslog.

---

### Post by The Bright Side on 2012-12-14
Hey guys, I am starting to get the same thing on my laptop. I installed psensor and it turns out my 4 cores run at 51-53°C each when IDLE (that's about 130 F).

I get the messages when booting. When I then turn the PC off and reboot, everything is fine.

It's an Intel Core i7 - 2670QM at 2.2 GHz.

How are you guys dealing with this?

---

### Post by Stonecold1995 on 2012-12-14
> **The Bright Side said:**
> Hey guys, I am starting to get the same thing on my laptop. I installed psensor and it turns out my 4 cores run at 51-53°C each when IDLE (that's about 130 F).

I get the messages when booting. When I then turn the PC off and reboot, everything is fine.

It's an Intel Core i7 - 2670QM at 2.2 GHz.

How are you guys dealing with this?

I just try to use Konsole for command line because messages like that aren't displayed there.

---

### Post by The Bright Side on 2012-12-15
Tried the same, but "startx" didn't work from another console. I just went back to 12.04, like I had previously done on my desktop PC, too. 12.10 is pretty badly broken, but now I'm back on 12.04, everything's working fine. Thanks!

---

### Post by cucisan on 2012-12-17
hi guys,

this is due to the bios, which throttles the cpu - only seen that on laptops with core i5/7 with nvidia cards... the same problem exists on windows (where a programm was created to defeat this: google: throttlestop)

imho there is not much you can do about that... except trying to play with msr tools.

good luck

---

### Post by jupeter on 2013-02-18
Hi, 

i have same problem Samsung Series 9 - NP900X3C. 
CPU: Intel i7 3517U
Graphic: Intel HD Graphics 4000

Linux 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

cucisan: what do you meen about playing with msr tools?

My mcelog:
> 
mcelog: Unsupported new Family 6 Model 3a CPU: only decoding architectural errors
mcelog: failed to prefill DIMM database from DMI data
mcelog: Unsupported new Family 6 Model 3a CPU: only decoding architectural errors
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 4
TIME 1360239379 Thu Feb  7 13:16:19 2013
MCG status:
MCi status:
Uncorrected error
Error enabled
Processor context corrupt
MCA: Internal unclassified error: 402
STATUS b200000000100402 MCGSTATUS 0
MCGCAP c07 APICID 0 SOCKETID 0
CPUID Vendor Intel Family 6 Model 58
mcelog: Unsupported new Family 6 Model 3a CPU: only decoding architectural errors
mcelog: failed to prefill DIMM database from DMI data
mcelog: Unsupported new Family 6 Model 3a CPU: only decoding architectural errors
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 4
TIME 1360962986 Fri Feb 15 22:16:26 2013
MCG status:
MCi status:
Uncorrected error
Error enabled
Processor context corrupt
MCA: Internal unclassified error: 402
STATUS b200000000100402 MCGSTATUS 0
MCGCAP c07 APICID 0 SOCKETID 0
CPUID Vendor Intel Family 6 Model 58


I found Bug report: [https://bugzilla.kernel.org/show_bug.cgi?id=36182](https://bugzilla.kernel.org/show_bug.cgi?id=36182)

---

### Post by VitasLoWang on 2013-07-01
It happened to me too! And I found out because my pc is suddendly quite slow. Download a program Sysinfo and check your current CPU frequency. I found out that my thinkpad T420 with Intel core i5 2.6GHz is now running just on 800MHz! No idea why! I will try restarting a computer
EDIT: CPU temperature is 56°C so no reason to slow down.

---

### Post by VitasLoWang on 2013-07-01
after restart it was at 1000MHz! WTH? And I found out what was happening. It was because of the malfunctioning laptop-mode package which I installed a long time ago to enable hibernation (I think). Even when CONTROL_CPU_FREQUENCY="auto" it was slowing down my CPU both on battery and on AC power. Really cool power saving feature :-\ After setting it to 0 in /etc/laptop-mode/conf.d/cpufreq.conf it magically runs on 2600MHz again.

---

### Post by JohnReid on 2013-07-05
Sysinfo says the 8 Intel(R) Core(TM) i7-3720QM CPU @ 2.60GHz on my Thinkpad W530 are running at frequency 1200.00 Mhz even when on AC power. So I guess my CPUs are being throttled. I don't have laptop-mode installed though so what can I do? Mess with the BIOS?

---

### Post by Pyppe on 2013-08-12
I've managed to tackle the CPU-scaling issues by overriding the on-demand throttling limit. With Ubuntu 13.04 the default value seems to be 95 which for me is way too high => CPU frequency is always at 800MHz. By lowering this (I've used 70) using file [FONT=courier new]/sys/devices/system/cpu/cpufreq/ondemand/up_threshold[/FONT], the scaling works as intended.

See [https://gist.github.com/Pyppe/6028707](https://gist.github.com/Pyppe/6028707) as an example.

My setup is Ubuntu 13.04 with Levono X1 Carbon.

P.S. I've still seeing the "Package power limit notification" messages, but at least the scaling seems to be working.

---

### Post by 3rdalbum on 2013-08-12
> **VitasLoWang said:**
> It happened to me too! And I found out because my pc is suddendly quite slow. Download a program Sysinfo and check your current CPU frequency. I found out that my thinkpad T420 with Intel core i5 2.6GHz is now running just on 800MHz! No idea why! I will try restarting a computer
EDIT: CPU temperature is 56°C so no reason to slow down.

Your "problem" is perfectly normal and intended behaviour.

CPUs don't just decelerate when they overheat, they also decelerate when they are not under heavy load. It's a power-saving feature of all CPUs since the Core 2 and maybe even earlier. Even when on AC your CPU will run slowly when little is happening and speed up automatically when needed.

---

