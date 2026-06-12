---
title: "Terrible Performance on Celeron D"
date: 2010-03-02
forum: General Help
---

### Post by Alaric on 2010-03-02
Hey guys,

I recently got a free 2.4 Ghz Celeron D computer with 1GB of ram as a result of an office switch at my workplace.  I intended to use it as an ubuntu based router.  Unfortunately, I was mortified to discover the horrifically slow performance on the computer with Ubuntu.  I have tested the system with text based livecd's, live usb's, and a complete installation.  The system takes about 10 minutes to even drop me to a login screen.  The system came with an XP sticker on the side and was originally running CentOS at decent speeds.  Currently, it seems to have trouble running top and a new login to sshd at the same time.  Simple commands seem to be unusably slow on the system.  My only lead at the moment is that perhaps the onboard graphics chip is having massive trouble handling output to the T.V. that I currently have it hooked up to.  Does anyone have any idea what would cause this horrific performance?

---

### Post by drdanielfc on 2010-03-02
> **Alaric said:**
> Hey guys,

I recently got a free 2.4 Ghz Celeron D computer with 1GB of ram as a result of an office switch at my workplace.  I intended to use it as an ubuntu based router.  Unfortunately, I was mortified to discover the horrifically slow performance on the computer with Ubuntu.  I have tested the system with text based livecd's, live usb's, and a complete installation.  The system takes about 10 minutes to even drop me to a login screen.  The system came with an XP sticker on the side and was originally running CentOS at decent speeds.  Currently, it seems to have trouble running top and a new login to sshd at the same time.  Simple commands seem to be unusably slow on the system.  My only lead at the moment is that perhaps the onboard graphics chip is having massive trouble handling output to the T.V. that I currently have it hooked up to.  Does anyone have any idea what would cause this horrific performance?

If you believe its the tv then have you tested using just a monitor?

---

### Post by Alaric on 2010-03-02
Unfortunately, I don't have a monitor available to me here.  I'm offsite from my regular workspace at the moment.  The only reason that I suspect this is that the TV is currently causing the server to run in 1366x768x32 with onboard graphics.  I'm currently trying to lower this with grub2 cheat codes.  However, the performance is crap even over SSH, so that's got me thinking that graphics performance is not the problem.  (To clarify, I am only trying to run a VGA console, no Gnome, no KDE, no GUI at all).

---

### Post by drdanielfc on 2010-03-02
> **Alaric said:**
> Unfortunately, I don't have a monitor available to me here.  I'm offsite from my regular workspace at the moment.  The only reason that I suspect this is that the TV is currently causing the server to run in 1366x768x32 with onboard graphics.  I'm currently trying to lower this with grub2 cheat codes.  However, the performance is crap even over SSH, so that's got me thinking that graphics performance is not the problem.  (To clarify, I am only trying to run a VGA console, no Gnome, no KDE, no GUI at all).

how old is your computer? did it come with xp? please clarify your situation

---

### Post by Alaric on 2010-03-02
Sorry if I was too vague.  Yes, it has an XP pro sticker on the side of it.  It looks like the Celeron D 2.4ghz came out sometime in 2004.  I knew that a computer from 2004 would be slow, but in this current state, it is outshined by my old 866mhz/512MB RAM "server".  I have installed 9.10 and to give an example of how slow the machine is working, it currently takes ubuntu more than a minute to realize that a command is not found.  Here's a bit more hardware info.

```
alaric@ubuntu:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)

```

alaric@ubuntu:~$  uname -r
2.6.31-14-generic-pae

I'm currently installing the regular generic kernel (I believe PAE was installed by default by the server installation CD).

(CPU Info on the way)

---

### Post by Alaric on 2010-03-02
Here's a bit more information:

While installing linux-image-2.6.31-19-generic:
```
alaric@ubuntu:~$ top | head --lines=15
top - 20:51:17 up 37 min,  2 users,  load average: 1.77, 1.38, 1.19
Tasks:  69 total,   2 running,  67 sleeping,   0 stopped,   0 zombie
Cpu(s): 63.2%us, 13.3%sy,  0.0%ni, 21.8%id,  0.4%wa,  0.1%hi,  1.2%si,  0.0%st
Mem:   1017780k total,   157244k used,   860536k free,    10596k buffers
Swap:  2441840k total,        0k used,  2441840k free,   100296k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 1076 root      20   0  4928 2076 1604 R 78.7  0.2   0:01.46 preinst           
 1074 alaric    20   0  2332 1008  784 R 25.3  0.1   0:01.18 top               
    1 root      20   0  2528 1396 1096 S  0.0  0.1   1:02.38 init              
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.05 kthreadd          
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0       
    4 root      15  -5     0    0    0 S  0.0  0.0   0:01.56 ksoftirqd/0       
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0        
    6 root      15  -5     0    0    0 S  0.0  0.0   0:01.83 events/0   
```

```
alaric@ubuntu:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Celeron(R) CPU 2.53GHz
stepping	: 9
cpu MHz		: 2527.140
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips	: 5054.28
clflush size	: 64
power management:

```
Looks like I was wrong, it's a 2.53Ghz processor.

---

### Post by drdanielfc on 2010-03-02
> **Alaric said:**
> Sorry if I was too vague.  Yes, it has an XP pro sticker on the side of it.  It looks like the Celeron D 2.4ghz came out sometime in 2004.  I knew that a computer from 2004 would be slow, but in this current state, it is outshined by my old 866mhz/512MB RAM "server".  I have installed 9.10 and to give an example of how slow the machine is working, it currently takes ubuntu more than a minute to realize that a command is not found.  Here's a bit more hardware info.

```
alaric@ubuntu:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)

```

alaric@ubuntu:~$  uname -r
2.6.31-14-generic-pae

I'm currently installing the regular generic kernel (I believe PAE was installed by default by the server installation CD).

(CPU Info on the way)

Well the celeron specs are pretty close to the laptop im running right now so that is probably not the problem. A quick google for "ubuntu celeron slow" returned a large number of results which leads me to believe that you didnt do very much research :p

It seems like [http://art.ubuntuforums.org/showthread.php?p=4043233](http://art.ubuntuforums.org/showthread.php?p=4043233) may help you, perhaps try a live cd from 2004 and see if it is a kernel issue?

edit: oh sorry forgot take a look at this site too: [http://ubuntuforums.org/showthread.php?t=134571](http://ubuntuforums.org/showthread.php?t=134571)

---

### Post by Alaric on 2010-03-02
Thanks, that's the sort of response that I was looking for I suppose.  I did spend about an hour searching google for results, but I tried "celeron d" (with quotes) in all of my searches.  The first thing that comes up currently for ubuntu slow "celeron d" is this page ;).  I'm currently attempting to install linux-image-686 from dapper via old apt repositories.  Unfortunately, this downgrade could take me about an hour :(.  Thanks for pointing me in (hopefully) the right direction.

---

### Post by drdanielfc on 2010-03-02
> **Alaric said:**
> Thanks, that's the sort of response that I was looking for I suppose.  I did spend about an hour searching google for results, but I tried "celeron d" (with quotes) in all of my searches.  The first thing that comes up currently for ubuntu slow "celeron d" is this page ;).  I'm currently attempting to install linux-image-686 from dapper via old apt repositories.  Unfortunately, this downgrade could take me about an hour :(.  Thanks for pointing me in (hopefully) the right direction.

personally i would use a dapper install and then upgrade,but thats just because ive had horrible luck with kernel downgrades :-). im calling it quits for tonite ill help u out tommorow please post any progress

---

### Post by Alaric on 2010-03-03
Hmm...  Judging by the crawling and glitchy loadbar on the Ubuntu liveusb 10 minutes after I started up the system... I'm calling this experiment a failure.  Unfortunately, it was inconclusive as I accidentally chose 6.10 (Edgy Eft) in unetbootin.  I doubt another 6 months on the kernel will resolve this problem, although Dapper was an LTS release.  I should note here that it's not only the text console that takes forever to load, but even GRUB seems nastily affected by this issue.  It appears to take grub a full 5-10 seconds to draw the menu when activated with the escape key.  I've even attempted disconnecting the monitor and running the computer headless via SSH, but the interface on the computer was not brought up even 5 minutes after I switched on the computer as a result of the speed problems I'm seeing.  I think tomorrow I'll attempt an XP installation just to verify that the processor and motherboard aren't damaged.  I'm open to any suggestions you may have.

---

### Post by rnerwein on 2010-03-03
hi
it's not your hardware it's the process "preinstall". as i know this has something to do with windoof.
1076 root      20   0  4928 2076 1604 R 78.7  0.2   0:01.46 preinst           
1074 alaric    20   0  2332 1008  784 R 25.3  0.1   0:01.18 top  
preinstall is eating up 76% of your cpu. what's going on with top - i don't know because it is not normal that
top is using a high amount of cpu usage.
ciao

---

### Post by drdanielfc on 2010-03-03
> **Alaric said:**
> Hmm...  Judging by the crawling and glitchy loadbar on the Ubuntu liveusb 10 minutes after I started up the system... I'm calling this experiment a failure.  Unfortunately, it was inconclusive as I accidentally chose 6.10 (Edgy Eft) in unetbootin.  I doubt another 6 months on the kernel will resolve this problem, although Dapper was an LTS release.  I should note here that it's not only the text console that takes forever to load, but even GRUB seems nastily affected by this issue.  It appears to take grub a full 5-10 seconds to draw the menu when activated with the escape key.  I've even attempted disconnecting the monitor and running the computer headless via SSH, but the interface on the computer was not brought up even 5 minutes after I switched on the computer as a result of the speed problems I'm seeing.  I think tomorrow I'll attempt an XP installation just to verify that the processor and motherboard aren't damaged.  I'm open to any suggestions you may have.

before you waste 3 hours of ur life, how does it run just on bios?

---

### Post by Alaric on 2010-03-03
> **rnerwein said:**
> hi
it's not your hardware it's the process "preinstall". as i know this has something to do with windoof.
1076 root      20   0  4928 2076 1604 R 78.7  0.2   0:01.46 preinst           
1074 alaric    20   0  2332 1008  784 R 25.3  0.1   0:01.18 top  
preinstall is eating up 76% of your cpu. what's going on with top - i don't know because it is not normal that
top is using a high amount of cpu usage.
ciao

The process preinstall is actually apt-get running a kernel upgrade as mentioned.  My old 866mhz Pentium III runs kernel upgrades like a champ and has enough power left over to allow things to run in the background.  When not running an apt-get, Top is the most intensive process running on the Celeron.  This was only meant to show how the processor load jumps with even light applications.  

> before you waste 3 hours of ur life, how does it run just on bios?

Not a bad idea.  I'll check when I get back to the computer.  My other idea is to reset the bios to factory defaults.  The previous owner had mentioned trying very hard to try to get the computer to cluster, and therefore may have changed a setting in the bios somewhere in his efforts.  Perhaps I'll also try a bios upgrade if dos runs acceptably slow.  (In case you're wondering, clustering seems impossible on Celerons due to the absence of virtualization technology on the CPU).

---

### Post by scouser73 on 2010-03-03
I too have an Intel Celeron D, 2.8GHz, 1Gb RAM, 80Gb HD and I can say that performance on it has been excellent.  Prior to running Ubuntu the PC was using Windows XP.

Defaulting the BIOS settings would be the best thing to do, and see how it goes from there.  Hope you manage to sort it.

---

### Post by Alaric on 2010-03-03
> **scouser73 said:**
> I too have an Intel Celeron D, 2.8GHz, 1Gb RAM, 80Gb HD and I can say that performance on it has been excellent.  Prior to running Ubuntu the PC was using Windows XP.

Defaulting the BIOS settings would be the best thing to do, and see how it goes from there.  Hope you manage to sort it.

Thank you scouser, I'll give it a shot in about half an hour as I still haven't made it back home yet.  Is there anyway you could provide me with the BIOS version that your celeron D is running?  I have a feeling that the version of the BIOS currently installed is different from what originally came with the PC.  I believe that from my short excursions into the bios so far I may remember seeing options for clustering within the bios.  This leads me to believe that the previous owner may have flashed them to an odd version in an attempt to enable clustering.

---

### Post by Alaric on 2010-03-03
> **Alaric said:**
> Thank you scouser, I'll give it a shot in about half an hour as I still haven't made it back home yet.  Is there anyway you could provide me with the BIOS version that your celeron D is running?  I have a feeling that the version of the BIOS currently installed is different from what originally came with the PC.  I believe that from my short excursions into the bios so far I may remember seeing options for clustering within the bios.  This leads me to believe that the previous owner may have flashed them to an odd version in an attempt to enable clustering.

Disregard this information.  I appear to have been mistaking the BIOS of this computer for the BIOS of another computer I am currently working with.  There is nothin in the BIOS that mentions clustering.  I am currently running Version A01 and the BIOS claims that the computer is a Dell DE051 Series.  I may still try to flash it if I can find newer BIOS.

P.S. I should also mention that there was no option in the BIOS to revert to factory defaults.

---

### Post by Alaric on 2010-03-03
The bus speed is being reported as 533Mhz, could this be the source of the problem?

---

### Post by Alaric on 2010-03-03
Using the service tag in the BIOS, I was able too look up the computer on support.dell.com.  Apparently it also goes by the name "Dell Dimension 1100/B110".  There don't appear to be any BIOS upgrades available.  The date registered for the A01 version of the BIOS is 2006, even newer than I thought.  I have yet to find a cause for this massively slow behavior.

---

### Post by tgalati4 on 2010-03-03
Have you looked through dmesg for any obvious problems?

dmesg | more

Clean out the machine and reseat the cards and power/ribbon connectors.

It could be a slow/dying disk that is throwing recoverable read errors.

Put in a fast disk and find a VGA monitor to do a proper test.

Run memtest overnight to ensure that the RAM is OK.

Also check the BIOS for any strange or unfamiliar settings.  At 2.5 GHz, Ubuntu flies.  Although the Celeron is generally poor compared to a true Pentium D for real performance.  I have both types of machines at that vintage, so I would donate the machine to a good cause, or turn it into a server.

---

### Post by Alaric on 2010-03-03
Here's a complete dmsg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic-pae (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 (Ubuntu 2.6.31-14.48-generic-pae)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f770000 (usable)
[    0.000000]  BIOS-e820: 000000003f770000 - 000000003f772000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f772000 - 000000003f793000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f793000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3f770 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges disabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F800000 mask FFF800000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f770000 (usable)
[    0.000000]  modified: 000000003f770000 - 000000003f772000 (ACPI NVS)
[    0.000000]  modified: 000000003f772000 - 000000003f793000 (ACPI data)
[    0.000000]  modified: 000000003f793000 - 000000003f800000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 7000-d000
[    0.000000] RAMDISK: 2f358000 - 2f9d3c85
[    0.000000] ACPI: RSDP 000feb90 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 000fd283 00034 (v01 DELL    DE051   00000008 ASL  00000061)
[    0.000000] ACPI: FACP 000fd2b7 00074 (v01 DELL    DE051   00000008 ASL  00000061)
[    0.000000] ACPI: DSDT fffcf83c 024C9 (v01   DELL    dt_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 3f770000 00040
[    0.000000] ACPI: SSDT fffd1e42 000BA (v01   DELL    st_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: APIC 000fd32b 0006C (v01 DELL    DE051   00000008 ASL  00000061)
[    0.000000] ACPI: BOOT 000fd397 00028 (v01 DELL    DE051   00000008 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 125MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00009000 - 0000ff40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad9a0]    TEXT DATA BSS ==> [0000100000 - 00008ad9a0]
[    0.000000]   #4 [002f358000 - 002f9d3c85]          RAMDISK ==> [002f358000 - 002f9d3c85]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008ae000 - 00008b4194]              BRK ==> [00008ae000 - 00008b4194]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x0003f770
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0003f770
[    0.000000] On node 0 totalpages: 259852
[    0.000000] free_area_init_node: node 0, pgdat c078bce0, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 251 pages used for memmap
[    0.000000]   HighMem zone: 31863 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf400000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257821
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=2ff976cc-4b92-4748-9ff2-4f85282e522e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5199040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:0003f770)
[    0.000000] Memory: 1010072k/1039808k available (4588k kernel code, 28808k reserved, 2148k data, 544k init, 128456k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc0795000 - 0xc081d000   ( 544 kB)
[    0.000000]       .data : 0xc057b314 - 0xc07946e8   (2148 kB)
[    0.000000]       .text : 0xc0100000 - 0xc057b314   (4588 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2527.140 MHz processor.
[    0.003408] Console: colour VGA+ 80x25
[    0.003916] console [tty0] enabled
[    0.004264] Calibrating delay loop (skipped), value calculated using timer frequency.. 5054.28 BogoMIPS (lpj=10108560)
[    0.006384] Security Framework initialized
[    0.010063] AppArmor: AppArmor initialized
[    0.011054] Mount-cache hash table entries: 512
[    0.024750] Initializing cgroup subsys ns
[    0.025249] Initializing cgroup subsys cpuacct
[    0.026190] Initializing cgroup subsys memory
[    0.027101] Initializing cgroup subsys freezer
[    0.027615] Initializing cgroup subsys net_cls
[    0.029382] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.030042] CPU: L2 cache: 256K
[    0.030452] CPU: Hyper-Threading is disabled
[    0.030986] mce: CPU supports 4 MCE banks
[    0.031606] CPU0: Thermal monitoring enabled (TM1)
[    0.032258] using mwait in idle threads.
[    0.032998] Performance Counters: no PMU driver, software counters only.
[    0.033756] Checking 'hlt' instruction... OK.
[    0.052250] SMP alternatives: switching to UP code
[    0.440229] ACPI: Core revision 20090521
[    0.707951] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.748658] CPU0: Intel(R) Celeron(R) CPU 2.53GHz stepping 09
[    0.756511] Brought up 1 CPUs
[    0.756996] Total of 1 processors activated (5054.28 BogoMIPS).
[    0.758716] CPU0 attaching NULL sched-domain.
[    0.784402] Booting paravirtualized kernel on bare hardware
[    0.829166] regulator: core version 0.5
[    0.830319] Time:  1:13:29  Date: 03/03/10
[    0.837203] NET: Registered protocol family 16
[    0.853693] EISA bus registered
[    0.854576] ACPI: bus type pci registered
[    0.901551] PCI: PCI BIOS revision 2.10 entry at 0xfbbf0, last bus=1
[    0.902138] PCI: Using configuration type 1 for base access
[    1.079294] bio: create slab <bio-0> at 0
[    1.146505] ACPI: EC: Look up EC in DSDT
[    1.976368] ACPI: Interpreter enabled
[    1.977045] ACPI: (supports S0 S1 S3 S4 S5)
[    1.982052] ACPI: Using IOAPIC for interrupt routing
[    2.732846] ACPI: No dock devices found.
[    2.769832] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    2.773806] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    2.774708] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    2.777855] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    2.778736] pci 0000:00:02.0: reg 14 32bit mmio: [0xfeb80000-0xfebfffff]
[    2.779596] pci 0000:00:02.0: reg 18 io port: [0xefa8-0xefaf]
[    2.782152] pci 0000:00:06.0: reg 10 32bit mmio: [0xfecf0000-0xfecf0fff]
[    2.786161] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    2.788699] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    2.791016] pci 0000:00:1d.3: reg 20 io port: [0xff20-0xff3f]
[    2.793647] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]
[    2.795571] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    2.796296] pci 0000:00:1d.7: PME# disabled
[    2.799407] pci 0000:00:1f.0: HPET at 0xfed00000
[    2.800481] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    2.801307] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    2.802898] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    2.803691] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    2.804463] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    2.805244] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    2.806025] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    2.806851] pci 0000:00:1f.1: reg 24 32bit mmio: [0xfeb7fc00-0xfeb7ffff]
[    2.809785] pci 0000:00:1f.3: reg 20 io port: [0xefe0-0xefff]
[    2.812933] pci 0000:01:08.0: reg 10 32bit mmio: [0xfeaff000-0xfeafffff]
[    2.813806] pci 0000:01:08.0: reg 14 io port: [0xdf40-0xdf7f]
[    2.815417] pci 0000:01:08.0: supports D1 D2
[    2.815995] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.816295] pci 0000:01:08.0: PME# disabled
[    2.817763] pci 0000:00:1e.0: transparent bridge
[    2.818405] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    2.819128] pci 0000:00:1e.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    2.820521] pci_bus 0000:00: on NUMA node 0
[    2.821301] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.856834] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    5.237920] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    5.252631] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    5.267093] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9 10 11 12 15)
[    5.281792] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    5.296470] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[    5.310655] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    5.325346] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    5.339973] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    5.365657] SCSI subsystem initialized
[    5.370555] libata version 3.00 loaded.
[    5.380573] usbcore: registered new interface driver usbfs
[    5.382880] usbcore: registered new interface driver hub
[    5.386823] usbcore: registered new device driver usb
[    5.405045] ACPI: WMI: Mapper loaded
[    5.405447] PCI: Using ACPI for IRQ routing
[    5.421416] Bluetooth: Core ver 2.15
[    5.424899] NET: Registered protocol family 31
[    5.425355] Bluetooth: HCI device and connection manager initialized
[    5.425931] Bluetooth: HCI socket layer initialized
[    5.426405] NetLabel: Initializing
[    5.426824] NetLabel:  domain hash size = 128
[    5.427267] NetLabel:  protocols = UNLABELED CIPSOv4
[    5.429250] NetLabel:  unlabeled traffic allowed by default
[    5.433667] hpet clockevent registered
[    5.434173] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    5.434866] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    5.435857] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    5.656465] pnp: PnP ACPI init
[    5.657472] ACPI: bus type pnp registered
[    5.936439] Switched to high resolution mode on CPU 0
[    6.079951] pnp 00:06: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    6.081353] pnp 00:06: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    6.136982] pnp: PnP ACPI: found 7 devices
[    6.137444] ACPI: ACPI bus type pnp unregistered
[    6.137994] PnPBIOS: Disabled by ACPI PNP
[    6.139248] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    6.140104] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    6.141350] system 00:00: iomem range 0x1000000-0x3f76ffff could not be reserved
[    6.142242] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
[    6.143147] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    6.144056] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    6.145300] system 00:00: iomem range 0xfed20000-0xfed8ffff has been reserved
[    6.146209] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
[    6.147118] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    6.148031] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
[    6.149867] system 00:06: ioport range 0xc00-0xc7f has been reserved
[    6.209907] AppArmor: AppArmor Filesystem Enabled
[    6.211842] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    6.212900] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    6.213630] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfeafffff
[    6.214287] pci 0000:00:1e.0:   PREFETCH window: disabled
[    6.215102] pci 0000:00:1e.0: setting latency timer to 64
[    6.215813] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    6.216902] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    6.217709] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    6.218457] pci_bus 0000:01: resource 1 mem: [0xfea00000-0xfeafffff]
[    6.219208] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    6.219948] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    6.225660] NET: Registered protocol family 2
[    6.243520] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    6.302960] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    6.494556] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    6.570931] TCP: Hash tables configured (established 131072 bind 65536)
[    6.571501] TCP reno registered
[    6.585160] NET: Registered protocol family 1
[    6.591438] Trying to unpack rootfs image as initramfs...
[   42.735457] Freeing initrd memory: 6639k freed
[   42.907559] Simple Boot Flag at 0x7a set to 0x1
[   42.922564] cpufreq-nforce2: No nForce2 chipset.
[   42.926654] Scanning for low memory corruption every 60 seconds
[   42.943106] audit: initializing netlink socket (disabled)
[   42.944051] type=2000 audit(1267578850.940:1): initialized
[   45.081100] highmem bounce pool size: 64 pages
[   45.081911] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[   45.387013] VFS: Disk quotas dquot_6.5.2
[   45.399665] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   45.514582] fuse init (API version 7.12)
[   45.531305] msgmni has been set to 1735
[   45.561153] alg: No test for stdrng (krng)
[   45.562812] io scheduler noop registered
[   45.563287] io scheduler anticipatory registered
[   45.563799] io scheduler deadline registered
[   45.573035] io scheduler cfq registered (default)
[   45.574160] pci 0000:00:02.0: Boot video device
[   45.578018] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[   45.588814] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.592896] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[   45.609736] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[   45.610455] ACPI: Power Button [PWRF]
[   45.618276] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[   45.619097] ACPI: Power Button [VBTN]
[   45.648592] processor LNXCPU:00: registered as cooling_device0
[   46.185022] isapnp: Scanning for PnP cards...
[   46.567782] isapnp: No Plug & Play device found
[   46.778696] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[   46.999222] brd: module loaded
[   47.094928] loop: module loaded
[   47.106756] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[   47.123229] ata_piix 0000:00:1f.1: version 2.13
[   47.123992]   alloc irq_desc for 18 on node -1
[   47.124196]   alloc kstat_irqs on node -1
[   47.125652] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   47.128927] ata_piix 0000:00:1f.1: setting latency timer to 64
[   47.133400] scsi0 : ata_piix
[   47.145469] scsi1 : ata_piix
[   47.151339] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   47.152084] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   47.315831] Fixed MDIO Bus: probed
[   47.323025] PPP generic driver version 2.4.2
[   47.330228] ata2.00: ATAPI: SONY CD-RW/DVD-ROM CRX310EE, SDK3, max UDMA/33
[   47.335989] ata1.00: ATA-5: ST360021A, 6.04, max UDMA/100
[   47.337059] ata1.00: 117231408 sectors, multi 8: LBA 
[   47.359175] ata2.00: configured for UDMA/33
[   47.367366] ata1.00: configured for UDMA/100
[   47.377559] scsi 0:0:0:0: Direct-Access     ATA      ST360021A        6.04 PQ: 0 ANSI: 5
[   47.395889] sd 0:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[   47.403115] sd 0:0:0:0: [sda] Write Protect is off
[   47.403780] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   47.407480] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.427719]  sda:
[   47.431315] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   47.433545]   alloc irq_desc for 23 on node -1
[   47.434051]   alloc kstat_irqs on node -1
[   47.434816] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   47.435942] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   47.436955] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   47.445116] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   47.453406]  sda1 sda2 <
[   47.464166] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   47.466708] scsi 1:0:0:0: CD-ROM            SONY     CDRWDVD CRX310EE SDK3 PQ: 0 ANSI: 5
[   47.485842]  sda5 >
[   47.505346] ehci_hcd 0000:00:1d.7: debug port 1
[   47.505990] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[   47.541470] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[   47.546727] sr0: scsi3-mmc drive: 0x/48x writer cd/rw xa/form2 cdda tray
[   47.547330] Uniform CD-ROM driver Revision: 3.20
[   47.558181] sd 0:0:0:0: [sda] Attached SCSI disk
[   47.562774] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   47.569763] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   47.581034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[   47.592023] usb usb1: configuration #1 chosen from 1 choice
[   47.597409] hub 1-0:1.0: USB hub found
[   47.598362] hub 1-0:1.0: 8 ports detected
[   47.606900] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   47.609862] uhci_hcd: USB Universal Host Controller Interface driver
[   47.615341]   alloc irq_desc for 16 on node -1
[   47.615840]   alloc kstat_irqs on node -1
[   47.616967] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   47.617830] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   47.618470] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   47.623385] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   47.625459] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[   47.638109] usb usb2: configuration #1 chosen from 1 choice
[   47.643150] hub 2-0:1.0: USB hub found
[   47.644082] hub 2-0:1.0: 2 ports detected
[   47.650650]   alloc irq_desc for 19 on node -1
[   47.651156]   alloc kstat_irqs on node -1
[   47.651924] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   47.653144] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   47.653785] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   47.658921] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   47.661179] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[   47.673754] usb usb3: configuration #1 chosen from 1 choice
[   47.679206] hub 3-0:1.0: USB hub found
[   47.680514] hub 3-0:1.0: 2 ports detected
[   47.686607] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   47.687455] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   47.688097] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   47.693438] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   47.694718] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[   47.709562] usb usb4: configuration #1 chosen from 1 choice
[   47.715026] hub 4-0:1.0: USB hub found
[   47.715963] hub 4-0:1.0: 2 ports detected
[   47.729492] PNP: No PS/2 controller found. Probing ports directly.
[   47.739553] serio: i8042 KBD port at 0x60,0x64 irq 1
[   47.740782] serio: i8042 AUX port at 0x60,0x64 irq 12
[   47.757522] mice: PS/2 mouse device common for all mice
[   47.770754] rtc_cmos 00:05: RTC can wake from S4
[   47.776713] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[   47.777836] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[   47.800059] device-mapper: uevent: version 1.0.3
[   47.816088] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[   47.825138] device-mapper: multipath: version 1.1.0 loaded
[   47.825696] device-mapper: multipath round-robin: version 1.0.0 loaded
[   47.846595] EISA: Probing bus 0 at eisa.0
[   47.849473] EISA: Detected 0 cards.
[   47.856620] cpuidle: using governor ladder
[   47.857096] cpuidle: using governor menu
[   47.974427] TCP cubic registered
[   48.003064] NET: Registered protocol family 10
[   48.105895] lo: Disabled Privacy Extensions
[   48.182613] NET: Registered protocol family 17
[   48.185536] Bluetooth: L2CAP ver 2.13
[   48.185930] Bluetooth: L2CAP socket layer initialized
[   48.186534] Bluetooth: SCO (Voice Link) ver 0.6
[   48.186984] Bluetooth: SCO socket layer initialized
[   48.190057] Bluetooth: RFCOMM TTY layer initialized
[   48.190645] Bluetooth: RFCOMM socket layer initialized
[   48.191144] Bluetooth: RFCOMM ver 1.11
[   48.193710] Using IPI No-Shortcut mode
[   48.203688] PM: Resume from disk failed.
[   48.205627] registered taskstats version 1
[   48.224748]   Magic number: 2:475:204
[   48.226840] rtc_cmos 00:05: setting system clock to 2010-03-03 01:14:17 UTC (1267578857)
[   48.227583] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   48.228448] EDD information not available.
[   48.236992] Freeing unused kernel memory: 544k freed
[   48.265045] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   48.280716] Write protecting the kernel text: 4592k
[   48.299127] Write protecting the kernel read-only data: 1836k
[   48.499589] usb 3-2: configuration #1 chosen from 1 choice
[  107.888899] usbcore: registered new interface driver hiddev
[  108.093491] input: Device USB Device as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3
[  108.109690] generic-usb 0003:05FE:2001.0001: input,hidraw0: USB HID v1.00 Keyboard [Device USB Device] on usb-0000:00:1d.1-2/input0
[  109.093516] input: Device USB Device as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input4
[  109.132134] generic-usb 0003:05FE:2001.0002: input,hidraw1: USB HID v1.00 Mouse [Device USB Device] on usb-0000:00:1d.1-2/input1
[  109.154149] usbcore: registered new interface driver usbhid
[  109.154774] usbhid: v2.6:USB HID core driver
[  109.899610] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[  109.900566] e100: Copyright(c) 1999-2006 Intel Corporation
[  109.920022]   alloc irq_desc for 20 on node -1
[  109.920208]   alloc kstat_irqs on node -1
[  109.921710] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  109.991519] e100 0000:01:08.0: PME# disabled
[  110.451254] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:16:76:5e:47:0f
[  124.781591] PM: Starting manual resume from disk
[  124.782113] PM: Resume from partition 8:5
[  124.782534] PM: Checking hibernation image.
[  124.784992] PM: Resume from disk failed.
[  125.151042] EXT4-fs (sda1): barriers enabled
[  125.172103] kjournald2 starting: pid 244, dev sda1:8, commit interval 5 seconds
[  125.173584] EXT4-fs (sda1): delayed allocation enabled
[  125.174200] EXT4-fs: file extents enabled
[  126.783196] EXT4-fs: mballoc enabled
[  126.785452] EXT4-fs (sda1): mounted filesystem with ordered data mode
[  130.479798] type=1505 audit(1267578939.749:2): operation="profile_load" pid=265 name=/sbin/dhclient3
[  130.510355] type=1505 audit(1267578939.781:3): operation="profile_load" pid=265 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  130.527892] type=1505 audit(1267578939.797:4): operation="profile_load" pid=265 name=/usr/lib/connman/scripts/dhclient-script
[  130.747090] type=1505 audit(1267578940.017:5): operation="profile_load" pid=266 name=/usr/sbin/named
[  130.936930] type=1505 audit(1267578940.209:6): operation="profile_load" pid=267 name=/usr/sbin/tcpdump
[  138.583239] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k 
[  139.956654] EXT4-fs (sda1): internal journal on sda1:8
[  141.389558] udev: starting version 147
[  180.677958] Linux agpgart interface v0.103
[  183.799733] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  184.642105] intel_rng: Firmware space is locked read-only. If you can't or
[  184.642522] intel_rng: don't want to disable this in firmware setup, and if
[  184.642940] intel_rng: you are certain that your system has a functional
[  184.643342] intel_rng: RNG, try using the 'no_fwh_detect' option.
[  187.624562] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[  196.887294] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[  197.019485] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[  198.163719] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[  209.762600] lp: driver loaded but no devices found
[  217.241402] dell-wmi: No known WMI GUID found
[  224.874722] ip_tables: (C) 2000-2006 Netfilter Core Team
[  244.695313] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  246.816919] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[  246.998409] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  247.808791] [drm] Initialized drm 1.1.0 20060810
[  257.704466] eth0: no IPv6 routers present
[  261.479419] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  261.480700] i915 0000:00:02.0: setting latency timer to 64
[  264.758329] [drm] fb0: inteldrmfb frame buffer device
[  264.759106] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[  274.101940] render error detected, EIR: 0x00000010
[  274.102380] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[  274.103138] render error detected, EIR: 0x00000010
[  274.121845] [drm] DAC-5: set mode 1360x768 14
[  280.020891] Console: switching to colour frame buffer device 170x48
[  291.465420] type=1505 audit(1267579100.737:7): operation="profile_replace" pid=582 name=/sbin/dhclient3
[  291.520158] type=1505 audit(1267579100.789:8): operation="profile_replace" pid=582 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  291.563268] type=1505 audit(1267579100.833:9): operation="profile_replace" pid=582 name=/usr/lib/connman/scripts/dhclient-script
[  291.828620] type=1505 audit(1267579101.097:10): operation="profile_replace" pid=583 name=/usr/sbin/named
[  292.059390] type=1505 audit(1267579101.329:11): operation="profile_replace" pid=584 name=/usr/sbin/tcpdump
```

I have to admit, I haven't looked at the dmesg too hard consider that GRUB takes about 30 seconds to draw the OS selection menu.  I'll try unplugging the hard drive and cd drive and running from onboard USB tonight, but for now I'm attempting the XP installation.  I'd agree that hardware failure is probably the best bet at this point.  Unfortunately, I don't have another monitor or hard drive to plug into at the moment.  The closest I can come is booting up headless and booting off USB, which as I stated earlier have not rectified the problem.  I would run a memtest, but when I tried it earlier it took about 3 minutes to complete the first (normally fast) test, which I believe was a result of terribly slow redraws.  I've been through every setting in the BIOS and I can't find anything that seems out of the ordinary (This BIOS version seems pretty limited in features). 

The XP installer seems to be running fairly normally... although file copying does seem to be going pretty slow at the moment.  Thanks for your suggestions tgalati4.

---

### Post by Alaric on 2010-03-03
I should mention that The line "[0.010063] AppArmor: AppArmor initialized" in dmesg shows up on the screen about 3-5 minutes after powering on the machine, so the problem must stem from something before this line.

---

### Post by scouser73 on 2010-03-03
> **Alaric said:**
> I should mention that The line "[0.010063] AppArmor: AppArmor initialized" in dmesg shows up on the screen about 3-5 minutes after powering on the machine, so the problem must stem from something before this line.

Hi Alaric, I think that this may be beneficial to you.  It's a guide for faster start times on Ubuntu & although it is dated 2005, it's still relevant [[COLOR="Red"]**Ubuntu Boot Times**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=89491") I swear by this guide as I have used it many times and I have noticed a significant increase in boot times.

The guide takes you through the services that are run when the computer is switched on and goes on to tell you what to stop and what to keep running.

Another guide I have used to further improve the performance is; [[COLOR="Red"]**Ubuntu Speed Up Tips**[/COLOR]]("http://www.chinwong.com/index.php?/site/article/ubuntu_speed_up_tips/") and finally [[COLOR="Red"]**Speed Up Your Ubuntu Linux Boot**[/COLOR]]("http://linux.aldeby.org/speed-up-your-ubuntu-linux-boot.html")

---

### Post by tgalati4 on 2010-03-03
This is a strange entry:
[   48.499589] usb 3-2: configuration #1 chosen from 1 choice
[  107.888899] usbcore: registered new interface driver hiddev
[  108.093491] input: Device USB Device as /devices/pci0000:00
It takes 50 seconds to activate some USB device that is hung off of your PCI bus.

Yes, you do have a sloooow boot.  Not sure what the issue is, because the rest of dmesg looks OK.

sudo apt-get install bootchart
man bootchart

bootchart will instrument your boot process and collect statistics that are helpful for determining what the bottlenecks are.

---

### Post by Alaric on 2010-03-03
Hey guys, booting isn't my only problem though.  As you can see from the top output below, the processor shoots through the roof with even simple tasks.  Top runs consistently at 25%, using apt-get to upgrade my kernel takes up 75%, and the upgrade process takes somewhere around half an hour to complete (even once top is stopped).  A PC processor from this decade should not take half an hour to install a kernel upgrade.  

> **Alaric said:**
> Here's a bit more information:

While installing linux-image-2.6.31-19-generic:
```
alaric@ubuntu:~$ top | head --lines=15
top - 20:51:17 up 37 min,  2 users,  load average: 1.77, 1.38, 1.19
Tasks:  69 total,   2 running,  67 sleeping,   0 stopped,   0 zombie
Cpu(s): 63.2%us, 13.3%sy,  0.0%ni, 21.8%id,  0.4%wa,  0.1%hi,  1.2%si,  0.0%st
Mem:   1017780k total,   157244k used,   860536k free,    10596k buffers
Swap:  2441840k total,        0k used,  2441840k free,   100296k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 1076 root      20   0  4928 2076 1604 R 78.7  0.2   0:01.46 preinst           
 1074 alaric    20   0  2332 1008  784 R 25.3  0.1   0:01.18 top               
    1 root      20   0  2528 1396 1096 S  0.0  0.1   1:02.38 init              
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.05 kthreadd          
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0       
    4 root      15  -5     0    0    0 S  0.0  0.0   0:01.56 ksoftirqd/0       
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0        
    6 root      15  -5     0    0    0 S  0.0  0.0   0:01.83 events/0   
```

```
alaric@ubuntu:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Celeron(R) CPU 2.53GHz
stepping	: 9
cpu MHz		: 2527.140
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips	: 5054.28
clflush size	: 64
power management:

```
Looks like I was wrong, it's a 2.53Ghz processor.

---

### Post by Alaric on 2010-03-03
The outcome of my XP install is fairly worrisome.  It was stuck copying files for about 5 hours... so I guess this problem has more to do with the hardware or BIOS.  Anybody willing to take a crack at helping me with the hardware, or should I switch this question to a more pertinent category like "hardware and laptops"?

P.S. The system still appears obscenely slow even with the hard disk and cd drive disconnected and running off of a Live USB.

---

### Post by Alaric on 2010-03-03
This computer apparently has a specific option in its BIOS (version A01) that toggles between "compatible" and "normal" mode.  This toggle is listed along side of information on the CPU, which I took to mean that the CPU was compatible with BIOS CPU information function.  Worsening this ambiguity was the fact that it was the only togglable item within the menu.  This meant that it looked just the same as static information within the menu.  Apparently the previous owner had enabled this mode in his attempts to cluster the computer.  Switching this mode from "compatible" to "normal" has solved the problem.  God ******!

---

### Post by tgalati4 on 2010-03-04
In most older PC's, compatible mode was for DOS game playing that required a known clock speed--Like 12 MHz for the original IBM PC.  So perhaps your machine was really running at 12 MHz.

That would explain the slowness.

---

### Post by dcstar on 2010-03-04
> **scouser73 said:**
> 
........
Defaulting the BIOS settings would be the best thing to do, and see how it goes from there..

Good advice, pity it wasn't taken as it would have saved wasting a lot of people's time.

---

### Post by tgalati4 on 2010-03-04
But then we would miss the drama.

---

