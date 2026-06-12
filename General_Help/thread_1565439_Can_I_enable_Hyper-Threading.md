---
title: "Can I enable Hyper-Threading?"
date: 2010-08-31
forum: General Help
---

### Post by ron999 on 2010-08-31
Hi
I've checked my CPU specs and it says that Hyper-Threading is supported.
When I use command:-
```
dmesg | grep CPU
```
It tells me that Hyper-Threading is disabled.:confused:

When I looked in my BIOS settings there is no option there to enable/disable Hyper-Threading.
There are some threads on the UbuntuForums that suggest Hyper-Threading can be enabled by making an entry in the GRUB.
I think that these threads are out-dated now. I'm using a later version of GRUB.

So, has anybody been successful in enabling Hyper-Threading with Karmic Koala 9.10?

> ron@ubuntu:~$ dmesg | grep CPU
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1985000, static data 35612 bytes
[    0.000000] Initializing CPU#0
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.001962] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.001967] CPU: L2 cache: 256K
[    0.001972] [COLOR="Red"]CPU: Hyper-Threading is disabled[/COLOR]
[    0.001978] mce: CPU supports 4 MCE banks
[    0.002003] CPU0: Thermal monitoring enabled (TM1)
[    0.087381] CPU0: Intel(R) Celeron(R) CPU 2.26GHz stepping 01
[    0.088001] Brought up 1 CPUs
[    0.088001] CPU0 attaching NULL sched-domain.
[    0.519637] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node f700e150), AE_INVALID_TABLE_LENGTH
[    0.519762] processor LNXCPU:00: registered as cooling_device0
[    0.519770] ACPI: Processor [CPU0] (supports 16 throttling states)
[    0.696041] Switched to high resolution mode on CPU 0

---

### Post by mc4man on 2010-09-01
Can you post some info on the cpu you  have and or any other relevant info (manufacturer of computer, model ect.

never had a celeron, not sure if they are ht enabled ( you'd expect a bios setting if it was.

This may provide some info (use the blue, though sudo w/ lshw crashed my maverick it should be fine on karmic

```
[COLOR="Blue"]sudo[/COLOR] lshw -C cpu
```

For full pc info in a easy to browse form try this (look in home folder for the file

```
[COLOR="Blue"]sudo[/COLOR] lshw -html > hardware.html
```

---

### Post by pommie on 2010-09-01
According to Intel it is not a hyperthreading chip

[http://ark.intel.com/Product.aspx?id=27447](http://ark.intel.com/Product.aspx?id=27447)

Cheers David

---

### Post by jerome1232 on 2010-09-01
You just linked a Pentium 4 and he's got a Celeron so....

---

### Post by inso_741 on 2010-09-01
none of the celerons support HT(look [here]("http://www.intel.com/products/processor/celeron/specifications.htm"))
and if it did the linux kernel would detect it automatically, you dont have to configure it...;-)


Edit: I think [this]("http://ark.intel.com/Product.aspx?id=27105&processor=315&spec-codes=SL7KX,SL7WS,SL7XG,SL7XY,SL87K,SL8AW,SL8HH,SL93Q") is your processor

---

### Post by pommie on 2010-09-01
ooops

Same answer though

[http://ark.intel.com/Product.aspx?id=27182](http://ark.intel.com/Product.aspx?id=27182)

Cheers David

---

### Post by cascade9 on 2010-09-01
> **inso_741 said:**
> none of the celerons support HT(look [here]("http://www.intel.com/products/processor/celeron/specifications.htm"))
and if it did the linux kernel would detect it automatically, you dont have to configure it...;-)

Edit: I think [this]("http://ark.intel.com/Product.aspx?id=27105&processor=315&spec-codes=SL7KX,SL7WS,SL7XG,SL7XY,SL87K,SL8AW,SL8HH,SL93Q") is your processor

Actually, there is one celeron that does have hyperthreading (and its even on that linked list), the P1053 model-  

[http://ark.intel.com/Product.aspx?id=47647](http://ark.intel.com/Product.aspx?id=47647)

Intel disabled Hyperthreading on the P4 celerons, Core2 doesnt have hyperthreading, and the newest core iX based celerons are only just coming out now.......so unless its a very, very new CPU, celeron = no hyperthreading. 

BTW, I agree with what you think the actual CPU is (celeron 315D), though it could be a G1011 or a 570.

---

### Post by ron999 on 2010-09-01
Hi

@ mc4man
I've posted the CPU information here:-[http://pastebin.ca/1930348]("http://pastebin.ca/1930348")

This part of **cat /proc/cpuinfo** indicates Hyper-Threading:-
> flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss [COLOR="Red"]ht[/COLOR] tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr

This part of **sudo dmidecode -t 4** indicates Hyper-Threading:-
> HTT (Hyper-threading technology)

This part of cpuid indicates Hyper-Threading:-
> HT     Hyper Threading

@ inso_741
I think that your link is the correct one here:- [http://ark.intel.com/Product.aspx?id=27105&processor=315&spec-codes=SL7KX,SL7WS,SL7XG,SL7XY,SL87K,SL8AW,SL8HH,SL93Q]("http://ark.intel.com/Product.aspx?id=27105&processor=315&spec-codes=SL7KX,SL7WS,SL7XG,SL7XY,SL87K,SL8AW,SL8HH,SL93Q")
That document states:-
> Intel® Hyper-Threading Technology.....No

So probably the document is correct and the reports from **cpuinfo/dmidecode/cpuid** are errors.

In the handbook for my motherboard [eSys P4M800/478] it explains how to tinker with the BIOS settings.
It shows a picture with an option to enable/disable 'Hyper Threading Function' but on my screen the option isn't there. I assumed that it must be a different BIOS version. Maybe the option's not there because the CPU just doesn't support Hyper-Threading. 

In those old UbuntuForum threads it said that the Linux kernel wasn't turning on Hyper-Threading automatically and that it needed to be enabled some other way if required. But that was then - probably the kernel has been updated several times since.

Thanks for your help guys.:)
It looks like the CPU doesn't support Hyper-Threading after all.:(

---

### Post by inso_741 on 2010-09-01
the bios will display an option for HT only if the processor supports it....if you replace your processor with a P4-HT you'll get the option as the handbook suggests

---

