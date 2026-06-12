---
title: "log files eating drive space...please help."
date: 2009-12-05
forum: General Help
---

### Post by gordong11 on 2009-12-05
Hi,

I'm running 9.10 karmic 32-bit and for some reason I'm running out of drive space at like 100mb to 500mb a day! only have 1.5GB left on my 35GB drive.

I was digging around my filesystem and found these files (located in /var/log) are taking up like 75% of my drive space(25gb):

kern.log.1 = 12GB
kern.log = 6GB
messages.1 = 3gb
messages = 2gb
syslog = 1.5gb
syslog.1 = 1.5GB

What are these files doing? do I need them? can I reset them? should I alter them?

Thanks again....

Added: I did a clean install only 3 weeks ago at most, and I only surf the web and play Eternal Lands MMORPG game, since that install.

---

### Post by fluffman86 on 2009-12-05
You should definitely be able to delete those.  But they should also definitely not be that big.

---

### Post by lidex on 2009-12-05
Your system is logging some kind of error(s) repetitively. Need to look into those log files to find out what the problem is, then they can be deleted to free up your disk space.
Try this for starters - enter command in a terminal:
```
cd /var/log
```
Then
```
less kern.log
```

Much more info on log files here:
[https://help.ubuntu.com/community/LinuxLogFiles]("https://help.ubuntu.com/community/LinuxLogFiles")

---

### Post by gordong11 on 2009-12-05
Cool thanks so much!!! I tried opening the big file with gedit, took an hour and the failed. LOL

I then did:

 tail kern.log.1:

Nov 29 16:30:21 rob-desktop kernel: [ 3035.400653] CPU0: Temperature above threshold, cpu clock throttled (total events = 414347)
Nov 29 16:30:21 rob-desktop kernel: [ 3035.401242] CPU0: Temperature/speed normal
Nov 29 16:30:21 rob-desktop kernel: [ 3035.419143] CPU0: Temperature above threshold, cpu clock throttled (total events = 414348)
Nov 29 16:30:21 rob-desktop kernel: [ 3035.419736] CPU0: Temperature/speed normal
Nov 29 16:30:21 rob-desktop kernel: [ 3035.420950] CPU0: Temperature above threshold, cpu clock throttled (total events = 414349)
Nov 29 16:30:21 rob-desktop kernel: [ 3035.421545] CPU0: Temperature/speed normal
Nov 29 16:30:21 rob-desktop kernel: [ 3035.429316] CPU0: Temperature above threshold, cpu clock throttled (total events = 414350)
Nov 29 16:30:21 rob-desktop kernel: [ 3035.429905] CPU0: Temperature/speed normal
Nov 29 16:30:21 rob-desktop kernel: [ 3035.430822] CPU0: Temperature above threshold, cpu clock throttled (total events = 414351)
Nov 29 16:30:21 rob-desktop kernel: [ 3035.431412] CPU0: Temperature/speed normal


 here is another snippet:

.000000] KERNEL supported cpus:
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   Intel GenuineIntel
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   AMD AuthenticAMD
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   NSC Geode by NSC
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   Centaur CentaurHauls
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Nov 21 13:58:48 rob-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000] DMI present.
Nov 21 13:58:48 rob-desktop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Nov 21 13:58:48 rob-desktop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Nov 21 13:58:48 rob-desktop kernel: [    0.000000] last_pfn = 0x3ffb0 max_arch_pfn = 0x100000
Nov 21 13:58:48 rob-desktop kernel: [    0.000000] MTRR default type: uncachable
Nov 21 13:58:48 rob-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   00000-9FFFF write-back
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   A0000-DFFFF uncachable
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   E0000-EFFFF write-through
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   F0000-FFFFF write-protect
Nov 21 13:58:48 rob-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   1 disabled
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   2 disabled
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   3 disabled
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   4 disabled
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   5 disabled
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   6 disabled
Nov 21 13:58:48 rob-desktop kernel: [    0.000000]   7 disabled
Nov 21 13:58:48 rob-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 21 13:58:48 rob-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
___________________________________________________________________________________________________________________
I guess this is a bad thing, I have my CPU on a slight OC, i think just 5%, I'll set it to normal, see if that helps.
I have over 50,000 entries a day in this log.

How Do I delete the the data inside the log file, but not the file itself?



Thanks again

---

