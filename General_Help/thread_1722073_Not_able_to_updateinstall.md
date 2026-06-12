---
title: "Not able to update/install"
date: 2011-04-05
forum: General Help
---

### Post by xMaD on 2011-04-05
Hey guys,

I did some research in google but didnt find anything that could help me.
Im a newbie on ubuntu, I use it not very often and I dont know much, thats why I got this problem, I guess.
Well, heres my problem: if I want to update my ubuntu or install (e.g. java) something, it fails. I dont rly know how to fix this.
I reloaded the old dpkg, but now I got another error... :/
```
(Lese Datenbank ... 90%dpkg: nicht behebbarer fataler Fehler, Abbruch: 
 fehlgeschlagen in buffer_read(fd): Dateiliste des Paketes »bogofilter-common«: Is a directory
``` (@ Java)
I get the same error when I try to upgrade.
Hopefully you guys can help me, and can read my error (cause its german... I would sent you the english one but dont know how to set the output of the terminal to english. If you need this in english, please tell me how to fix it and Ill post it once again) and help me with this.

Greets,

xMaD

---

### Post by Rubi1200 on 2011-04-05
Hi and welcome to the forums :-)

Try these commands in the terminal:

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```

Run them one at a time. If they report errors, post it here please.

---

### Post by xMaD on 2011-04-05
Thanks =)

Didnt got an error at one of these, but if I try ```
sudo apt-get upgrade
``` it shows me the errors again...
Maybe this code helps a little. I dont know what I ve could changed so that none works.... I run Windows on this HD, too. Maybe its caused by it.
```
302 aktualisiert, 0 neu installiert, 0 zu entfernen und 3 nicht aktualisiert.
Es müssen noch 0B von 432MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 9.733kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Extrahiere Templates aus Paketen: 100%
Vorkonfiguration der Pakete ...
(Lese Datenbank ... 90%dpkg: nicht behebbarer fataler Fehler, Abbruch:
 fehlgeschlagen in buffer_read(fd): Dateiliste des Paketes »bogofilter-common«: Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by Krytarik on 2011-04-05
Try reinstalling the mentioned package:
```
sudo apt-get install --reinstall bogofilter-common
```
then again:```

sudo apt-get update
sudo apt-get upgrade
```
Greetings.

---

### Post by Rubi1200 on 2011-04-05
Okay, so give this a try and see if it helps:

```
sudo apt-get --reinstall install bogofilter-common
```Then try running updates or installs again.

edit: oops, beaten to the draw by Krytarik

---

### Post by xMaD on 2011-04-05
Tried reinstalling, terminal answered: 
```
0 aktualisiert, 0 neu installiert, 1 erneut installiert, 0 zu entfernen und 305 nicht aktualisiert.
Es müssen 144kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 0B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Hole:1 http://de.archive.ubuntu.com/ubuntu/ lucid-updates/main bogofilter-common 1.2.1-0ubuntu1.1 [144kB]
Es wurden 144kB in 0s geholt (187kB/s)   
(Lese Datenbank ... 90%dpkg: nicht behebbarer fataler Fehler, Abbruch:
 fehlgeschlagen in buffer_read(fd): Dateiliste des Paketes »bogofilter-common«: Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Update works fine, but at upgrade I get the same error as before.. :/

---

### Post by Krytarik on 2011-04-05
Try following the steps stated here:
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by xMaD on 2011-04-05
I did exactly what it told me but at step 4, the last command gives out:

```
ovider-info 20100716-1ubuntu0.1 [33.5kB]
Fetched 528MB in 26min 47s (328kB/s)                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 90%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `bogofilter-common': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

All of the other commands ran without any error...

---

### Post by Krytarik on 2011-04-05
There seems to be a faulty upgrade package.

Try "locking" its installed version with Synaptic, then try again to "upgrade", NOT "dist-upgrade" (because the "lock" doesn't get respected then).

---

### Post by xMaD on 2011-04-06
I dont really get something locked, Im very new to this os.... :/
But I got a question: my ubuntu starts more slow than before and it tells something of an HD error.
I dont know if its cause by the second HD which I put in some ago but didnt installed in the BIOS (well, I dont want it to be used right now). I couldnt read whats the matter because my screen just display a part of this message on login screen. IF it could be this, please tell me how to view the whole message. Then Ill post it and maybe my problem can be solved by this.
I did some research once again but just found some cache problem...mine seems to be ok (or at least it doesnt display any problem)

---

### Post by Krytarik on 2011-04-06
- See this guide on how to "lock" the version of a package:
[https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages](https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages)

- No, this completely unrelated. Check the log file "/var/log/messages" for the error message.

---

### Post by xMaD on 2011-04-08
Its very good that my HD aint the problem.

Well I thought maybe there is a way to replace the dpkg by a functional one... I dont get it where the error comes from.. :/
Are there some installations which dont use dpkg? So I could test whether they run or not.
If its "just" a dpkg problem, this should be fixable doesnt it?

---

### Post by xMaD on 2011-04-08
What would happen if I replaced the dpkg file by another? Would this be possible?
Anything I found about this stuff doesnt help... it just returns errors or tells the files would already exist. You think I still can rescue my system or do I need to kill it and rebuild it?

---

### Post by Krytarik on 2011-04-08
> **xMaD said:**
> You think I still can rescue my system or do I need to kill it and rebuild it?
Eh?! It's nothing serious at all! The chances are high that you don't even use it!
See description: [http://packages.ubuntu.com/maverick/bogofilter-common](http://packages.ubuntu.com/maverick/bogofilter-common)

You can either
a) "lock" its version like said, or even
b) remove it and the packages that depends on it

How about the other issue, did you check the log file?

---

### Post by Rubi1200 on 2011-04-08
I agree with Krytarik here.

First try locking the package as suggested and try to update.

If that still causes problems, then simply remove the offending package.

---

### Post by xMaD on 2011-04-09
I did my best to block it... but when I select (just klicking on it) my synaptic shuts down.

Tried to delete it but cant.... And I dont know how to do it by terminal (if possible)
Maybe u guys can tell me how I get rid of bogofilter common or which packets I need to lock (I tried it with just dpkg/dpkg and all bogofilterparts I could lock/just bogofilter... none worked)

In the error logfile there is none... or I didnt find a helpful thing :/ maybe u can tell me where I need to look for (probably I just searched the wrong error message and so I didnt see)

---

### Post by Krytarik on 2011-04-09
> **xMaD said:**
> I did my best to block it... but when I select (just klicking on it) my synaptic shuts down.That's unusual, and an issue! Are you experiencing any other issues like that?
> **xMaD said:**
> 
Tried to delete it but cant.... And I dont know how to do it by terminal (if possible)
Maybe u guys can tell me how I get rid of bogofilter common or which packets I need to lock (I tried it with just dpkg/dpkg and all bogofilterparts I could lock/just bogofilter... none worked)It's also described in the guide:
[https://help.ubuntu.com/community/PinningHowto#Apt/Dpkg](https://help.ubuntu.com/community/PinningHowto#Apt/Dpkg)

However, I suggest running this command instead:
```
echo bogofilter-common hold | sudo dpkg --set-selections
```It may be necessary to also lock the packages that are depending on it, to avoid any future "cannot be upgraded" thing:
- "bogofilter"
- "bogofilter-bdb"
> **xMaD said:**
> 
In the error logfile there is none... or I didnt find a helpful thing :/ maybe u can tell me where I need to look for (probably I just searched the wrong error message and so I didnt see)
Simply post the entire log, or attach the file, you may need to compress it therefore, because of the forums' file size limit of text files.

---

### Post by xMaD on 2011-04-09
bogofilter and bogofilter-bdb are blocked by synaptic, bogofilter-common should be locked by dpkg. When I try to upgrade I still get this error:

```
Möchten Sie fortfahren [J/n]? j
Extrahiere Templates aus Paketen: 100%
Vorkonfiguration der Pakete ...
(Lese Datenbank ... 90%dpkg: nicht behebbarer fataler Fehler, Abbruch:
 fehlgeschlagen in buffer_read(fd): Dateiliste des Paketes »bogofilter-common«: Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

The issue with synaptic is only bogofilter common, all the others I tried to select doesnt make any problems.

The log should be this: ```
Apr  9 12:39:45 ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr  9 12:39:45 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="968" x-info="http://www.rsyslog.com"] (re)start
Apr  9 12:39:45 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Apr  9 12:39:45 ubuntu rsyslogd: rsyslogd's userid changed to 101
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 (Ubuntu 2.6.32-24.42-generic 2.6.32.15+drm33.5)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
Apr  9 12:39:45 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Apr  9 12:39:45 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff70000 (usable)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000cff70000 - 00000000cff7e000 (ACPI data)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] DMI present.
Apr  9 12:39:45 ubuntu kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Apr  9 12:39:45 ubuntu kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  9 12:39:45 ubuntu kernel: [    0.000000] last_pfn = 0xcff70 max_arch_pfn = 0x400000000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Apr  9 12:39:45 ubuntu kernel: [    0.000000] modified physical RAM map:
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009e800 (usable)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 00000000cff70000 (usable)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 00000000cff70000 - 00000000cff7e000 (ACPI data)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Apr  9 12:39:45 ubuntu kernel: [    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cff70000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  9 12:39:45 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  9 12:39:45 ubuntu kernel: [    0.000000] RAMDISK: 377af000 - 37fef9d3
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000fb410 00014 (v00 ACPIAM)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: RSDT 00000000cff70000 0003C (v01 A_M_I_ OEMRSDT  12000803 MSFT 00000097)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: FACP 00000000cff70200 00084 (v02 A_M_I_ OEMFACP  12000803 MSFT 00000097)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: DSDT 00000000cff70440 096E2 (v01  A1012 A1012001 00000001 INTL 20060113)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: FACS 00000000cff7e000 00040
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: APIC 00000000cff70390 0006C (v01 A_M_I_ OEMAPIC  12000803 MSFT 00000097)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: MCFG 00000000cff70400 0003C (v01 A_M_I_ OEMMCFG  12000803 MSFT 00000097)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: OEMB 00000000cff7e040 00089 (v01 A_M_I_ AMI_OEM  12000803 MSFT 00000097)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: HPET 00000000cff79b30 00038 (v01 A_M_I_ OEMHPET  12000803 MSFT 00000097)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: OSFR 00000000cff79b70 000B0 (v01 A_M_I_ OEMOSFR  12000803 MSFT 00000097)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] No NUMA configuration found
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-0000000130000000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   NODE_DATA [0000000000015000 - 0000000000019fff]
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   bootmap [000000000001a000 -  000000000003ffff] pages 26
Apr  9 12:39:45 ubuntu kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   #2 [0001000000 - 0001a2fe64]    TEXT DATA BSS ==> [0001000000 - 0001a2fe64]
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   #3 [00377af000 - 0037fef9d3]          RAMDISK ==> [00377af000 - 0037fef9d3]
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   #4 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 - 0000100000]
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   #5 [0001a30000 - 0001a30284]              BRK ==> [0001a30000 - 0001a30284]
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   #7 [0000014000 - 0000015000]          PGTABLE ==> [0000014000 - 0000015000]
Apr  9 12:39:45 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Zone PFN ranges:
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Apr  9 12:39:45 ubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00130000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Apr  9 12:39:45 ubuntu kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr  9 12:39:45 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Apr  9 12:39:45 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x000cff70
Apr  9 12:39:45 ubuntu kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr  9 12:39:45 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  9 12:39:45 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000cff70000 - 00000000cff7e000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000cff7e000 - 00000000cffd0000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fee00000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ee00000)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  9 12:39:45 ubuntu kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
Apr  9 12:39:45 ubuntu kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Apr  9 12:39:45 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031189
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Policy zone: Normal
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Initializing CPU#0
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Checking aperture...
Apr  9 12:39:45 ubuntu kernel: [    0.000000] No AGP bridge found
Apr  9 12:39:45 ubuntu kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Memory: 4048312k/4980736k available (5422k kernel code, 787464k absent, 144960k reserved, 2979k data, 880k init)
Apr  9 12:39:45 ubuntu kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Apr  9 12:39:45 ubuntu kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Apr  9 12:39:45 ubuntu kernel: [    0.000000] console [tty0] enabled
Apr  9 12:39:45 ubuntu kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Apr  9 12:39:45 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  9 12:39:45 ubuntu kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Apr  9 12:39:45 ubuntu kernel: [    0.000000] Detected 3165.837 MHz processor.
Apr  9 12:39:45 ubuntu kernel: [    0.000006] Calibrating delay loop (skipped), value calculated using timer frequency.. 6331.67 BogoMIPS (lpj=31658370)
Apr  9 12:39:45 ubuntu kernel: [    0.000026] Security Framework initialized
Apr  9 12:39:45 ubuntu kernel: [    0.000043] AppArmor: AppArmor initialized
Apr  9 12:39:45 ubuntu kernel: [    0.000296] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr  9 12:39:45 ubuntu kernel: [    0.011627] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Apr  9 12:39:45 ubuntu kernel: [    0.012410] Mount-cache hash table entries: 256
Apr  9 12:39:45 ubuntu kernel: [    0.012523] Initializing cgroup subsys ns
Apr  9 12:39:45 ubuntu kernel: [    0.012527] Initializing cgroup subsys cpuacct
Apr  9 12:39:45 ubuntu kernel: [    0.012530] Initializing cgroup subsys memory
Apr  9 12:39:45 ubuntu kernel: [    0.012536] Initializing cgroup subsys devices
Apr  9 12:39:45 ubuntu kernel: [    0.012537] Initializing cgroup subsys freezer
Apr  9 12:39:45 ubuntu kernel: [    0.012539] Initializing cgroup subsys net_cls
Apr  9 12:39:45 ubuntu kernel: [    0.012555] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  9 12:39:45 ubuntu kernel: [    0.012557] CPU: L2 cache: 6144K
Apr  9 12:39:45 ubuntu kernel: [    0.012559] CPU 0/0x0 -> Node 0
Apr  9 12:39:45 ubuntu kernel: [    0.012561] CPU: Physical Processor ID: 0
Apr  9 12:39:45 ubuntu kernel: [    0.012562] CPU: Processor Core ID: 0
Apr  9 12:39:45 ubuntu kernel: [    0.012564] mce: CPU supports 6 MCE banks
Apr  9 12:39:45 ubuntu kernel: [    0.012571] CPU0: Thermal monitoring enabled (TM2)
Apr  9 12:39:45 ubuntu kernel: [    0.012574] using mwait in idle threads.
Apr  9 12:39:45 ubuntu kernel: [    0.012576] Performance Events: Core2 events, Intel PMU driver.
Apr  9 12:39:45 ubuntu kernel: [    0.012580] ... version:                2
Apr  9 12:39:45 ubuntu kernel: [    0.012581] ... bit width:              40
Apr  9 12:39:45 ubuntu kernel: [    0.012582] ... generic registers:      2
Apr  9 12:39:45 ubuntu kernel: [    0.012583] ... value mask:             000000ffffffffff
Apr  9 12:39:45 ubuntu kernel: [    0.012584] ... max period:             000000007fffffff
Apr  9 12:39:45 ubuntu kernel: [    0.012585] ... fixed-purpose events:   3
Apr  9 12:39:45 ubuntu kernel: [    0.012586] ... event mask:             0000000700000003
Apr  9 12:39:45 ubuntu kernel: [    0.014471] ACPI: Core revision 20090903
Apr  9 12:39:45 ubuntu kernel: [    0.030006] ftrace: converting mcount calls to 0f 1f 44 00 00
Apr  9 12:39:45 ubuntu kernel: [    0.030010] ftrace: allocating 22527 entries in 89 pages
Apr  9 12:39:45 ubuntu kernel: [    0.040038] Setting APIC routing to flat
Apr  9 12:39:45 ubuntu kernel: [    0.040333] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  9 12:39:45 ubuntu kernel: [    0.144210] CPU0: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz stepping 06
Apr  9 12:39:45 ubuntu kernel: [    0.150000] APIC calibration not consistent with PM-Timer: 109ms instead of 100ms
Apr  9 12:39:45 ubuntu kernel: [    0.150000] APIC delta adjusted to PM-Timer: 2083092 (2291399)
Apr  9 12:39:45 ubuntu kernel: [    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
Apr  9 12:39:45 ubuntu kernel: [    0.010000] Initializing CPU#1
Apr  9 12:39:45 ubuntu kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  9 12:39:45 ubuntu kernel: [    0.010000] CPU: L2 cache: 6144K
Apr  9 12:39:45 ubuntu kernel: [    0.010000] CPU 1/0x1 -> Node 0
Apr  9 12:39:45 ubuntu kernel: [    0.010000] CPU: Physical Processor ID: 0
Apr  9 12:39:45 ubuntu kernel: [    0.010000] CPU: Processor Core ID: 1
Apr  9 12:39:45 ubuntu kernel: [    0.010000] CPU1: Thermal monitoring enabled (TM2)
Apr  9 12:39:45 ubuntu kernel: [    0.300076] CPU1: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz stepping 06
Apr  9 12:39:45 ubuntu kernel: [    0.300081] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr  9 12:39:45 ubuntu kernel: [    0.310015] Brought up 2 CPUs
Apr  9 12:39:45 ubuntu kernel: [    0.310017] Total of 2 processors activated (12664.30 BogoMIPS).
Apr  9 12:39:45 ubuntu kernel: [    0.310818] devtmpfs: initialized
Apr  9 12:39:45 ubuntu kernel: [    0.310818] regulator: core version 0.5
Apr  9 12:39:45 ubuntu kernel: [    0.310818] Time: 12:39:29  Date: 04/09/11
Apr  9 12:39:45 ubuntu kernel: [    0.310818] NET: Registered protocol family 16
Apr  9 12:39:45 ubuntu kernel: [    0.310818] Trying to unpack rootfs image as initramfs...
Apr  9 12:39:45 ubuntu kernel: [    0.310818] ACPI: bus type pci registered
Apr  9 12:39:45 ubuntu kernel: [    0.310818] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr  9 12:39:45 ubuntu kernel: [    0.310818] PCI: Not using MMCONFIG.
Apr  9 12:39:45 ubuntu kernel: [    0.310818] PCI: Using configuration type 1 for base access
Apr  9 12:39:45 ubuntu kernel: [    0.310818] bio: create slab <bio-0> at 0
Apr  9 12:39:45 ubuntu kernel: [    0.313134] ACPI: Executed 1 blocks of module-level executable AML code
Apr  9 12:39:45 ubuntu kernel: [    0.322594] ACPI: Interpreter enabled
Apr  9 12:39:45 ubuntu kernel: [    0.322598] ACPI: (supports S0 S1 S3 S4 S5)
Apr  9 12:39:45 ubuntu kernel: [    0.322615] ACPI: Using IOAPIC for interrupt routing
Apr  9 12:39:45 ubuntu kernel: [    0.322654] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr  9 12:39:45 ubuntu kernel: [    0.324574] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Apr  9 12:39:45 ubuntu kernel: [    0.329179] PCI: Using MMCONFIG at e0000000 - efffffff
Apr  9 12:39:45 ubuntu kernel: [    0.334624] ACPI: No dock devices found.
Apr  9 12:39:45 ubuntu kernel: [    0.334736] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  9 12:39:45 ubuntu kernel: [    0.334811] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Apr  9 12:39:45 ubuntu kernel: [    0.334813] pci 0000:00:01.0: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.335077] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Apr  9 12:39:45 ubuntu kernel: [    0.335080] pci 0000:00:1a.7: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.335145] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr  9 12:39:45 ubuntu kernel: [    0.335148] pci 0000:00:1b.0: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.335195] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr  9 12:39:45 ubuntu kernel: [    0.335198] pci 0000:00:1c.0: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.335250] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Apr  9 12:39:45 ubuntu kernel: [    0.335252] pci 0000:00:1c.4: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.335301] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Apr  9 12:39:45 ubuntu kernel: [    0.335304] pci 0000:00:1c.5: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.335556] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr  9 12:39:45 ubuntu kernel: [    0.335560] pci 0000:00:1d.7: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.335659] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Apr  9 12:39:45 ubuntu kernel: [    0.335661] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
Apr  9 12:39:45 ubuntu kernel: [    0.335664] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
Apr  9 12:39:45 ubuntu kernel: [    0.335668] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 001f)
Apr  9 12:39:45 ubuntu kernel: [    0.335765] pci 0000:00:1f.2: PME# supported from D3hot
Apr  9 12:39:45 ubuntu kernel: [    0.335767] pci 0000:00:1f.2: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.336044] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
Apr  9 12:39:45 ubuntu kernel: [    0.336048] pci 0000:03:00.0: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.336194] pci 0000:02:00.0: PME# supported from D3hot D3cold
Apr  9 12:39:45 ubuntu kernel: [    0.336197] pci 0000:02:00.0: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.336313] pci 0000:05:01.0: PME# supported from D1 D2 D3hot D3cold
Apr  9 12:39:45 ubuntu kernel: [    0.336316] pci 0000:05:01.0: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.336382] pci 0000:05:03.0: PME# supported from D0 D1 D2 D3hot
Apr  9 12:39:45 ubuntu kernel: [    0.336385] pci 0000:05:03.0: PME# disabled
Apr  9 12:39:45 ubuntu kernel: [    0.336419] pci 0000:00:1e.0: transparent bridge
Apr  9 12:39:45 ubuntu kernel: [    0.347930] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Apr  9 12:39:45 ubuntu kernel: [    0.348010] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Apr  9 12:39:45 ubuntu kernel: [    0.348088] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Apr  9 12:39:45 ubuntu kernel: [    0.348167] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Apr  9 12:39:45 ubuntu kernel: [    0.348245] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Apr  9 12:39:45 ubuntu kernel: [    0.348324] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Apr  9 12:39:45 ubuntu kernel: [    0.348403] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
Apr  9 12:39:45 ubuntu kernel: [    0.348481] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Apr  9 12:39:45 ubuntu kernel: [    0.348568] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Apr  9 12:39:45 ubuntu kernel: [    0.348571] vgaarb: loaded
Apr  9 12:39:45 ubuntu kernel: [    0.348653] SCSI subsystem initialized
Apr  9 12:39:45 ubuntu kernel: [    0.348775] usbcore: registered new interface driver usbfs
Apr  9 12:39:45 ubuntu kernel: [    0.348784] usbcore: registered new interface driver hub
Apr  9 12:39:45 ubuntu kernel: [    0.348805] usbcore: registered new device driver usb
Apr  9 12:39:45 ubuntu kernel: [    0.348892] ACPI: WMI: Mapper loaded
Apr  9 12:39:45 ubuntu kernel: [    0.348893] PCI: Using ACPI for IRQ routing
Apr  9 12:39:45 ubuntu kernel: [    0.349018] NetLabel: Initializing
Apr  9 12:39:45 ubuntu kernel: [    0.349019] NetLabel:  domain hash size = 128
Apr  9 12:39:45 ubuntu kernel: [    0.349020] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  9 12:39:45 ubuntu kernel: [    0.349030] NetLabel:  unlabeled traffic allowed by default
Apr  9 12:39:45 ubuntu kernel: [    0.349051] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Apr  9 12:39:45 ubuntu kernel: [    0.349054] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Apr  9 12:39:45 ubuntu kernel: [    0.360049] Switching to clocksource tsc
Apr  9 12:39:45 ubuntu kernel: [    0.361271] AppArmor: AppArmor Filesystem Enabled
Apr  9 12:39:45 ubuntu kernel: [    0.361282] pnp: PnP ACPI init
Apr  9 12:39:45 ubuntu kernel: [    0.361292] ACPI: bus type pnp registered
Apr  9 12:39:45 ubuntu kernel: [    0.363273] pnp: PnP ACPI: found 14 devices
Apr  9 12:39:45 ubuntu kernel: [    0.363275] ACPI: ACPI bus type pnp unregistered
Apr  9 12:39:45 ubuntu kernel: [    0.363283] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363288] system 00:06: ioport range 0x290-0x29f has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363292] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363294] system 00:07: ioport range 0x800-0x87f has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363296] system 00:07: ioport range 0x500-0x57f could not be reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363298] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363299] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363301] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363303] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363310] system 00:0a: iomem range 0xffc00000-0xffefffff has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363314] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363316] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363319] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363322] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363324] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363326] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363328] system 00:0d: iomem range 0x100000-0xcfffffff could not be reserved
Apr  9 12:39:45 ubuntu kernel: [    0.363330] system 00:0d: iomem range 0xe0000000-0xffffffff could not be reserved
Apr  9 12:39:45 ubuntu kernel: [    0.367990] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Apr  9 12:39:45 ubuntu kernel: [    0.367992] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
Apr  9 12:39:45 ubuntu kernel: [    0.367994] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfe8fffff
Apr  9 12:39:45 ubuntu kernel: [    0.367997] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Apr  9 12:39:45 ubuntu kernel: [    0.367999] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
Apr  9 12:39:45 ubuntu kernel: [    0.368001] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Apr  9 12:39:45 ubuntu kernel: [    0.368005] pci 0000:00:1c.0:   MEM window: 0xf0000000-0xf03fffff
Apr  9 12:39:45 ubuntu kernel: [    0.368008] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
Apr  9 12:39:45 ubuntu kernel: [    0.368012] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
Apr  9 12:39:45 ubuntu kernel: [    0.368014] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
Apr  9 12:39:45 ubuntu kernel: [    0.368018] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
Apr  9 12:39:45 ubuntu kernel: [    0.368021] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0400000-0x000000f05fffff
Apr  9 12:39:45 ubuntu kernel: [    0.368025] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
Apr  9 12:39:45 ubuntu kernel: [    0.368027] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
Apr  9 12:39:45 ubuntu kernel: [    0.368031] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
Apr  9 12:39:45 ubuntu kernel: [    0.368033] pci 0000:00:1c.5:   PREFETCH window: 0x000000f0600000-0x000000f07fffff
Apr  9 12:39:45 ubuntu kernel: [    0.368038] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Apr  9 12:39:45 ubuntu kernel: [    0.368040] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
Apr  9 12:39:45 ubuntu kernel: [    0.368043] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
Apr  9 12:39:45 ubuntu kernel: [    0.368046] pci 0000:00:1e.0:   PREFETCH window: disabled
Apr  9 12:39:45 ubuntu kernel: [    0.368060] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  9 12:39:45 ubuntu kernel: [    0.368068] pci 0000:00:1c.0: enabling device (0106 -> 0107)
Apr  9 12:39:45 ubuntu kernel: [    0.368074] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  9 12:39:45 ubuntu kernel: [    0.368083] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  9 12:39:45 ubuntu kernel: [    0.368091] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Apr  9 12:39:45 ubuntu kernel: [    0.368149] NET: Registered protocol family 2
Apr  9 12:39:45 ubuntu kernel: [    0.368269] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Apr  9 12:39:45 ubuntu kernel: [    0.369104] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Apr  9 12:39:45 ubuntu kernel: [    0.372370] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr  9 12:39:45 ubuntu kernel: [    0.372804] TCP: Hash tables configured (established 524288 bind 65536)
Apr  9 12:39:45 ubuntu kernel: [    0.372806] TCP reno registered
Apr  9 12:39:45 ubuntu kernel: [    0.372898] NET: Registered protocol family 1
Apr  9 12:39:45 ubuntu kernel: [    0.373202] Scanning for low memory corruption every 60 seconds
Apr  9 12:39:45 ubuntu kernel: [    0.373308] audit: initializing netlink socket (disabled)
Apr  9 12:39:45 ubuntu kernel: [    0.373317] type=2000 audit(1302352769.369:1): initialized
Apr  9 12:39:45 ubuntu kernel: [    0.379778] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  9 12:39:45 ubuntu kernel: [    0.380686] VFS: Disk quotas dquot_6.5.2
Apr  9 12:39:45 ubuntu kernel: [    0.380723] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  9 12:39:45 ubuntu kernel: [    0.381121] fuse init (API version 7.13)
Apr  9 12:39:45 ubuntu kernel: [    0.381175] msgmni has been set to 7906
Apr  9 12:39:45 ubuntu kernel: [    0.381320] alg: No test for stdrng (krng)
Apr  9 12:39:45 ubuntu kernel: [    0.381358] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr  9 12:39:45 ubuntu kernel: [    0.381360] io scheduler noop registered
Apr  9 12:39:45 ubuntu kernel: [    0.381361] io scheduler anticipatory registered
Apr  9 12:39:45 ubuntu kernel: [    0.381363] io scheduler deadline registered
Apr  9 12:39:45 ubuntu kernel: [    0.381385] io scheduler cfq registered (default)
Apr  9 12:39:45 ubuntu kernel: [    0.381816] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  9 12:39:45 ubuntu kernel: [    0.381886] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  9 12:39:45 ubuntu kernel: [    0.381969] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Apr  9 12:39:45 ubuntu kernel: [    0.381972] ACPI: Power Button [PWRB]
Apr  9 12:39:45 ubuntu kernel: [    0.382001] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr  9 12:39:45 ubuntu kernel: [    0.382003] ACPI: Power Button [PWRF]
Apr  9 12:39:45 ubuntu kernel: [    0.382225] processor LNXCPU:00: registered as cooling_device0
Apr  9 12:39:45 ubuntu kernel: [    0.382249] processor LNXCPU:01: registered as cooling_device1
Apr  9 12:39:45 ubuntu kernel: [    0.384867] Linux agpgart interface v0.103
Apr  9 12:39:45 ubuntu kernel: [    0.384889] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr  9 12:39:45 ubuntu kernel: [    0.385747] brd: module loaded
Apr  9 12:39:45 ubuntu kernel: [    0.386062] loop: module loaded
Apr  9 12:39:45 ubuntu kernel: [    0.386112] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Apr  9 12:39:45 ubuntu kernel: [    0.386201] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  9 12:39:45 ubuntu kernel: [    0.386234] pata_acpi 0000:03:00.0: PCI INT A disabled
Apr  9 12:39:45 ubuntu kernel: [    0.386415] Fixed MDIO Bus: probed
Apr  9 12:39:45 ubuntu kernel: [    0.386438] PPP generic driver version 2.4.2
Apr  9 12:39:45 ubuntu kernel: [    0.386458] tun: Universal TUN/TAP device driver, 1.6
Apr  9 12:39:45 ubuntu kernel: [    0.386459] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  9 12:39:45 ubuntu kernel: [    0.386508] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  9 12:39:45 ubuntu kernel: [    0.386525] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  9 12:39:45 ubuntu kernel: [    0.386537] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr  9 12:39:45 ubuntu kernel: [    0.386559] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Apr  9 12:39:45 ubuntu kernel: [    0.386585] ehci_hcd 0000:00:1a.7: debug port 1
Apr  9 12:39:45 ubuntu kernel: [    0.390497] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
Apr  9 12:39:45 ubuntu kernel: [    0.409692] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Apr  9 12:39:45 ubuntu kernel: [    0.409777] usb usb1: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    0.409799] hub 1-0:1.0: USB hub found
Apr  9 12:39:45 ubuntu kernel: [    0.409807] hub 1-0:1.0: 6 ports detected
Apr  9 12:39:45 ubuntu kernel: [    0.409866] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  9 12:39:45 ubuntu kernel: [    0.409886] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  9 12:39:45 ubuntu kernel: [    0.409910] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Apr  9 12:39:45 ubuntu kernel: [    0.409930] ehci_hcd 0000:00:1d.7: debug port 1
Apr  9 12:39:45 ubuntu kernel: [    0.413813] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
Apr  9 12:39:45 ubuntu kernel: [    0.429695] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr  9 12:39:45 ubuntu kernel: [    0.429776] usb usb2: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    0.429795] hub 2-0:1.0: USB hub found
Apr  9 12:39:45 ubuntu kernel: [    0.429802] hub 2-0:1.0: 6 ports detected
Apr  9 12:39:45 ubuntu kernel: [    0.429851] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  9 12:39:45 ubuntu kernel: [    0.429864] uhci_hcd: USB Universal Host Controller Interface driver
Apr  9 12:39:45 ubuntu kernel: [    0.429898] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  9 12:39:45 ubuntu kernel: [    0.429906] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr  9 12:39:45 ubuntu kernel: [    0.429935] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Apr  9 12:39:45 ubuntu kernel: [    0.429963] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
Apr  9 12:39:45 ubuntu kernel: [    0.430018] usb usb3: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    0.430035] hub 3-0:1.0: USB hub found
Apr  9 12:39:45 ubuntu kernel: [    0.430039] hub 3-0:1.0: 2 ports detected
Apr  9 12:39:45 ubuntu kernel: [    0.430075] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr  9 12:39:45 ubuntu kernel: [    0.430080] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr  9 12:39:45 ubuntu kernel: [    0.430104] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Apr  9 12:39:45 ubuntu kernel: [    0.430127] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
Apr  9 12:39:45 ubuntu kernel: [    0.430182] usb usb4: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    0.430199] hub 4-0:1.0: USB hub found
Apr  9 12:39:45 ubuntu kernel: [    0.430205] hub 4-0:1.0: 2 ports detected
Apr  9 12:39:45 ubuntu kernel: [    0.430236] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  9 12:39:45 ubuntu kernel: [    0.430241] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Apr  9 12:39:45 ubuntu kernel: [    0.430267] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Apr  9 12:39:45 ubuntu kernel: [    0.430285] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00
Apr  9 12:39:45 ubuntu kernel: [    0.430340] usb usb5: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    0.430356] hub 5-0:1.0: USB hub found
Apr  9 12:39:45 ubuntu kernel: [    0.430359] hub 5-0:1.0: 2 ports detected
Apr  9 12:39:45 ubuntu kernel: [    0.430392] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  9 12:39:45 ubuntu kernel: [    0.430398] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  9 12:39:45 ubuntu kernel: [    0.430423] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Apr  9 12:39:45 ubuntu kernel: [    0.430442] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
Apr  9 12:39:45 ubuntu kernel: [    0.430495] usb usb6: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    0.430511] hub 6-0:1.0: USB hub found
Apr  9 12:39:45 ubuntu kernel: [    0.430514] hub 6-0:1.0: 2 ports detected
Apr  9 12:39:45 ubuntu kernel: [    0.430548] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  9 12:39:45 ubuntu kernel: [    0.430553] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  9 12:39:45 ubuntu kernel: [    0.430572] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Apr  9 12:39:45 ubuntu kernel: [    0.430597] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
Apr  9 12:39:45 ubuntu kernel: [    0.430654] usb usb7: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    0.430669] hub 7-0:1.0: USB hub found
Apr  9 12:39:45 ubuntu kernel: [    0.430673] hub 7-0:1.0: 2 ports detected
Apr  9 12:39:45 ubuntu kernel: [    0.430702] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  9 12:39:45 ubuntu kernel: [    0.430708] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  9 12:39:45 ubuntu kernel: [    0.430730] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Apr  9 12:39:45 ubuntu kernel: [    0.430748] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
Apr  9 12:39:45 ubuntu kernel: [    0.430803] usb usb8: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    0.430820] hub 8-0:1.0: USB hub found
Apr  9 12:39:45 ubuntu kernel: [    0.430826] hub 8-0:1.0: 2 ports detected
Apr  9 12:39:45 ubuntu kernel: [    0.430895] PNP: No PS/2 controller found. Probing ports directly.
Apr  9 12:39:45 ubuntu kernel: [    0.433668] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  9 12:39:45 ubuntu kernel: [    0.433673] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  9 12:39:45 ubuntu kernel: [    0.433758] mice: PS/2 mouse device common for all mice
Apr  9 12:39:45 ubuntu kernel: [    0.433831] rtc_cmos 00:03: RTC can wake from S4
Apr  9 12:39:45 ubuntu kernel: [    0.433862] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Apr  9 12:39:45 ubuntu kernel: [    0.433882] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr  9 12:39:45 ubuntu kernel: [    0.433962] device-mapper: uevent: version 1.0.3
Apr  9 12:39:45 ubuntu kernel: [    0.434038] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Apr  9 12:39:45 ubuntu kernel: [    0.434079] device-mapper: multipath: version 1.1.0 loaded
Apr  9 12:39:45 ubuntu kernel: [    0.434082] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr  9 12:39:45 ubuntu kernel: [    0.434182] cpuidle: using governor ladder
Apr  9 12:39:45 ubuntu kernel: [    0.434183] cpuidle: using governor menu
Apr  9 12:39:45 ubuntu kernel: [    0.434413] TCP cubic registered
Apr  9 12:39:45 ubuntu kernel: [    0.434489] NET: Registered protocol family 10
Apr  9 12:39:45 ubuntu kernel: [    0.434790] lo: Disabled Privacy Extensions
Apr  9 12:39:45 ubuntu kernel: [    0.434967] NET: Registered protocol family 17
Apr  9 12:39:45 ubuntu kernel: [    0.435064] registered taskstats version 1
Apr  9 12:39:45 ubuntu kernel: [    0.435378]   Magic number: 7:68:683
Apr  9 12:39:45 ubuntu kernel: [    0.435448] rtc_cmos 00:03: setting system clock to 2011-04-09 12:39:30 UTC (1302352770)
Apr  9 12:39:45 ubuntu kernel: [    0.435450] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  9 12:39:45 ubuntu kernel: [    0.435451] EDD information not available.
Apr  9 12:39:45 ubuntu kernel: [    0.440096] Freeing initrd memory: 8450k freed
Apr  9 12:39:45 ubuntu kernel: [    0.442318] Freeing unused kernel memory: 880k freed
Apr  9 12:39:45 ubuntu kernel: [    0.442583] Write protecting the kernel read-only data: 7696k
Apr  9 12:39:45 ubuntu kernel: [    0.451776] udev: starting version 151
Apr  9 12:39:45 ubuntu kernel: [    0.488950] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  9 12:39:45 ubuntu kernel: [    0.489025] ahci: SSS flag set, parallel bus scan disabled
Apr  9 12:39:45 ubuntu kernel: [    0.489053] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Apr  9 12:39:45 ubuntu kernel: [    0.489055] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
Apr  9 12:39:45 ubuntu kernel: [    0.514955] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  9 12:39:45 ubuntu kernel: [    0.518417] ohci1394 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr  9 12:39:45 ubuntu kernel: [    0.571851] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febfe000-febfe7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Apr  9 12:39:45 ubuntu kernel: [    0.579755] scsi0 : ahci
Apr  9 12:39:45 ubuntu kernel: [    0.579851] scsi1 : ahci
Apr  9 12:39:45 ubuntu kernel: [    0.579889] scsi2 : ahci
Apr  9 12:39:45 ubuntu kernel: [    0.579927] scsi3 : ahci
Apr  9 12:39:45 ubuntu kernel: [    0.579963] scsi4 : ahci
Apr  9 12:39:45 ubuntu kernel: [    0.580000] scsi5 : ahci
Apr  9 12:39:45 ubuntu kernel: [    0.580117] ata1: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe900 irq 28
Apr  9 12:39:45 ubuntu kernel: [    0.580119] ata2: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe980 irq 28
Apr  9 12:39:45 ubuntu kernel: [    0.580121] ata3: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea00 irq 28
Apr  9 12:39:45 ubuntu kernel: [    0.580123] ata4: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea80 irq 28
Apr  9 12:39:45 ubuntu kernel: [    0.580125] ata5: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb00 irq 28
Apr  9 12:39:45 ubuntu kernel: [    0.580127] ata6: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb80 irq 28
Apr  9 12:39:45 ubuntu kernel: [    0.749745] usb 2-3: new high speed USB device using ehci_hcd and address 2
Apr  9 12:39:45 ubuntu kernel: [    0.902142] usb 2-3: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    0.906100] Initializing USB Mass Storage driver...
Apr  9 12:39:45 ubuntu kernel: [    0.906169] scsi6 : SCSI emulation for USB Mass Storage devices
Apr  9 12:39:45 ubuntu kernel: [    0.906239] usbcore: registered new interface driver usb-storage
Apr  9 12:39:45 ubuntu kernel: [    0.906241] USB Mass Storage support registered.
Apr  9 12:39:45 ubuntu kernel: [    1.110016] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 12:39:45 ubuntu kernel: [    1.116377] ata1.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
Apr  9 12:39:45 ubuntu kernel: [    1.116379] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  9 12:39:45 ubuntu kernel: [    1.122793] ata1.00: configured for UDMA/133
Apr  9 12:39:45 ubuntu kernel: [    1.140103] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
Apr  9 12:39:45 ubuntu kernel: [    1.140203] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  9 12:39:45 ubuntu kernel: [    1.140216] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Apr  9 12:39:45 ubuntu kernel: [    1.140253] sd 0:0:0:0: [sda] Write Protect is off
Apr  9 12:39:45 ubuntu kernel: [    1.140315] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 12:39:45 ubuntu kernel: [    1.140568]  sda: sda1
Apr  9 12:39:45 ubuntu kernel: [    1.150494] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  9 12:39:45 ubuntu kernel: [    1.420020] usb 8-1: new full speed USB device using uhci_hcd and address 2
Apr  9 12:39:45 ubuntu kernel: [    1.647067] usb 8-1: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    1.654674] usbcore: registered new interface driver hiddev
Apr  9 12:39:45 ubuntu kernel: [    1.655690] generic-usb: probe of 0003:058F:6364.0001 failed with error -22
Apr  9 12:39:45 ubuntu kernel: [    1.660195] input: Microsoft MicrosoftÂ® SiderWinderTM X6 Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input3
Apr  9 12:39:45 ubuntu kernel: [    1.660253] generic-usb 0003:045E:074B.0002: input,hidraw0: USB HID v1.11 Keyboard [Microsoft MicrosoftÂ® SiderWinderTM X6 Keyboard] on usb-0000:00:1d.2-1/input0
Apr  9 12:39:45 ubuntu kernel: [    1.673070] input: Microsoft MicrosoftÂ® SiderWinderTM X6 Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input4
Apr  9 12:39:45 ubuntu kernel: [    1.673116] generic-usb 0003:045E:074B.0003: input,hidraw1: USB HID v1.11 Device [Microsoft MicrosoftÂ® SiderWinderTM X6 Keyboard] on usb-0000:00:1d.2-1/input1
Apr  9 12:39:45 ubuntu kernel: [    1.673136] usbcore: registered new interface driver usbhid
Apr  9 12:39:45 ubuntu kernel: [    1.673138] usbhid: v2.6:USB HID core driver
Apr  9 12:39:45 ubuntu kernel: [    1.888237] EXT4-fs (loop0): mounted filesystem with ordered data mode
Apr  9 12:39:45 ubuntu kernel: [    1.930018] usb 8-2: new full speed USB device using uhci_hcd and address 3
Apr  9 12:39:45 ubuntu kernel: [    2.070021] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 12:39:45 ubuntu kernel: [    2.120125] usb 8-2: configuration #1 chosen from 1 choice
Apr  9 12:39:45 ubuntu kernel: [    2.130237] input: Logitech G9 Laser Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input5
Apr  9 12:39:45 ubuntu kernel: [    2.130291] generic-usb 0003:046D:C048.0004: input,hidraw2: USB HID v1.11 Mouse [Logitech G9 Laser Mouse] on usb-0000:00:1d.2-2/input0
Apr  9 12:39:45 ubuntu kernel: [    2.139144] input: Logitech G9 Laser Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.1/input/input6
Apr  9 12:39:45 ubuntu kernel: [    2.139208] generic-usb 0003:046D:C048.0005: input,hiddev96,hidraw3: USB HID v1.11 Keyboard [Logitech G9 Laser Mouse] on usb-0000:00:1d.2-2/input1
Apr  9 12:39:45 ubuntu kernel: [    2.527365] ata2.00: ATA-8: WDC WD5000AADS-00S9B0, 01.00A01, max UDMA/133
Apr  9 12:39:45 ubuntu kernel: [    2.527368] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Apr  9 12:39:45 ubuntu kernel: [    2.528532] ata2.00: configured for UDMA/133
Apr  9 12:39:45 ubuntu kernel: [    2.540100] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AADS-0 01.0 PQ: 0 ANSI: 5
Apr  9 12:39:45 ubuntu kernel: [    2.540222] sd 1:0:0:0: Attached scsi generic sg1 type 0
Apr  9 12:39:45 ubuntu kernel: [    2.540284] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Apr  9 12:39:45 ubuntu kernel: [    2.540315] sd 1:0:0:0: [sdb] Write Protect is off
Apr  9 12:39:45 ubuntu kernel: [    2.540333] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 12:39:45 ubuntu kernel: [    2.540428]  sdb: unknown partition table
Apr  9 12:39:45 ubuntu kernel: [    2.569003] sd 1:0:0:0: [sdb] Attached SCSI disk
Apr  9 12:39:45 ubuntu kernel: [    2.890025] ata3: SATA link down (SStatus 0 SControl 300)
Apr  9 12:39:45 ubuntu kernel: [    3.840019] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  9 12:39:45 ubuntu kernel: [    3.840725] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB02, max UDMA/100, ATAPI AN
Apr  9 12:39:45 ubuntu kernel: [    3.841661] ata4.00: configured for UDMA/100
Apr  9 12:39:45 ubuntu kernel: [    3.860569] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB02 PQ: 0 ANSI: 5
Apr  9 12:39:45 ubuntu kernel: [    3.863678] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Apr  9 12:39:45 ubuntu kernel: [    3.863682] Uniform CD-ROM driver Revision: 3.20
Apr  9 12:39:45 ubuntu kernel: [    3.863836] sr 3:0:0:0: Attached scsi generic sg2 type 5
Apr  9 12:39:45 ubuntu kernel: [    4.210020] ata5: SATA link down (SStatus 0 SControl 300)
Apr  9 12:39:45 ubuntu kernel: [    4.580021] ata6: SATA link down (SStatus 0 SControl 300)
Apr  9 12:39:45 ubuntu kernel: [    5.902080] scsi 6:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
Apr  9 12:39:45 ubuntu kernel: [    5.902574] scsi 6:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
Apr  9 12:39:45 ubuntu kernel: [    5.903074] scsi 6:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
Apr  9 12:39:45 ubuntu kernel: [    5.903718] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
Apr  9 12:39:45 ubuntu kernel: [    5.904057] sd 6:0:0:0: Attached scsi generic sg3 type 0
Apr  9 12:39:45 ubuntu kernel: [    5.904145] sd 6:0:0:1: Attached scsi generic sg4 type 0
Apr  9 12:39:45 ubuntu kernel: [    5.904223] sd 6:0:0:2: Attached scsi generic sg5 type 0
Apr  9 12:39:45 ubuntu kernel: [    5.904311] sd 6:0:0:3: Attached scsi generic sg6 type 0
Apr  9 12:39:45 ubuntu kernel: [    5.907694] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Apr  9 12:39:45 ubuntu kernel: [    5.908440] sd 6:0:0:1: [sdd] Attached SCSI removable disk
Apr  9 12:39:45 ubuntu kernel: [    5.909191] sd 6:0:0:2: [sde] Attached SCSI removable disk
Apr  9 12:39:45 ubuntu kernel: [    5.909939] sd 6:0:0:3: [sdf] Attached SCSI removable disk
Apr  9 12:39:45 ubuntu kernel: [   10.340119] udev: starting version 151
Apr  9 12:39:45 ubuntu kernel: [   10.425095] lp: driver loaded but no devices found
Apr  9 12:39:45 ubuntu kernel: [   10.431219] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  9 12:39:45 ubuntu kernel: [   10.459353] scsi7 : pata_marvell
Apr  9 12:39:45 ubuntu kernel: [   10.486297] scsi8 : pata_marvell
Apr  9 12:39:45 ubuntu kernel: [   10.486348] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
Apr  9 12:39:45 ubuntu kernel: [   10.486350] ata8: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
Apr  9 12:39:45 ubuntu kernel: [   10.488300] type=1505 audit(1302345580.544:2):  operation="profile_load" pid=692 name="/sbin/dhclient3"
Apr  9 12:39:45 ubuntu kernel: [   10.488724] type=1505 audit(1302345580.544:3):  operation="profile_load" pid=692 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr  9 12:39:45 ubuntu kernel: [   10.488949] type=1505 audit(1302345580.544:4):  operation="profile_load" pid=692 name="/usr/lib/connman/scripts/dhclient-script"
Apr  9 12:39:45 ubuntu kernel: [   10.528828] cfg80211: Calling CRDA to update world regulatory domain
Apr  9 12:39:45 ubuntu kernel: [   10.597556] cfg80211: World regulatory domain updated:
Apr  9 12:39:45 ubuntu kernel: [   10.597558]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  9 12:39:45 ubuntu kernel: [   10.597560]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  9 12:39:45 ubuntu kernel: [   10.597562]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  9 12:39:45 ubuntu kernel: [   10.597564]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  9 12:39:45 ubuntu kernel: [   10.597565]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  9 12:39:45 ubuntu kernel: [   10.597567]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  9 12:39:45 ubuntu kernel: [   10.841958] vga16fb: mapped to 0xffff8800000a0000
Apr  9 12:39:45 ubuntu kernel: [   10.842001] fb0: VGA16 VGA frame buffer device
Apr  9 12:39:45 ubuntu kernel: [   10.862208] nvidia: module license 'NVIDIA' taints kernel.
Apr  9 12:39:45 ubuntu kernel: [   10.862211] Disabling lock debugging due to kernel taint
Apr  9 12:39:45 ubuntu kernel: [   11.090895] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261112k 
Apr  9 12:39:45 ubuntu kernel: [   11.130612] rtl8180 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  9 12:39:45 ubuntu kernel: [   11.291964] phy0: hwaddr 00:11:6b:63:f5:b9, RTL8185vD + rtl8225z2
Apr  9 12:39:45 ubuntu kernel: [   11.310889] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr  9 12:39:45 ubuntu kernel: [   11.369533] Console: switching to colour frame buffer device 80x30
Apr  9 12:39:45 ubuntu kernel: [   11.372215] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  9 12:39:45 ubuntu kernel: [   11.372226] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Apr  9 12:39:45 ubuntu kernel: [   11.372562] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Apr  9 12:39:45 ubuntu kernel: [   11.486042] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
Apr  9 12:39:45 ubuntu kernel: [   14.952245] EXT4-fs (loop0): warning: mounting fs with errors, running e2fsck is recommended
Apr  9 12:39:45 ubuntu kernel: [   15.041938] type=1505 audit(1302345585.105:5):  operation="profile_load" pid=994 name="/usr/share/gdm/guest-session/Xsession"
Apr  9 12:39:45 ubuntu kernel: [   15.042922] type=1505 audit(1302345585.105:6):  operation="profile_replace" pid=997 name="/sbin/dhclient3"
Apr  9 12:39:45 ubuntu kernel: [   15.043349] type=1505 audit(1302345585.105:7):  operation="profile_replace" pid=997 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr  9 12:39:45 ubuntu kernel: [   15.043579] type=1505 audit(1302345585.105:8):  operation="profile_replace" pid=997 name="/usr/lib/connman/scripts/dhclient-script"
Apr  9 12:39:45 ubuntu kernel: [   15.045485] type=1505 audit(1302345585.105:9):  operation="profile_load" pid=999 name="/usr/bin/evince"
Apr  9 12:39:45 ubuntu kernel: [   15.050917] type=1505 audit(1302345585.105:10):  operation="profile_load" pid=999 name="/usr/bin/evince-previewer"
Apr  9 12:39:45 ubuntu kernel: [   15.057557] type=1505 audit(1302345585.115:11):  operation="profile_load" pid=999 name="/usr/bin/evince-thumbnailer"
Apr  9 12:39:45 ubuntu kernel: [   15.058768] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  9 12:39:53 ubuntu kernel: [   23.530386] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  9 12:39:53 ubuntu kernel: [   23.584731] ppdev: user-space parallel port driver
Apr  9 12:46:09 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="968" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr  9 12:50:41 ubuntu kernel: [  671.500939] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  9 12:50:49 ubuntu kernel: [  679.580382] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  9 12:53:43 ubuntu kernel: [  853.463806] ATL1E 0000:02:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
Apr  9 12:53:43 ubuntu kernel: [  853.464148] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  9 12:54:05 ubuntu kernel: [  875.456311] ATL1E 0000:02:00.0: ATL1E: eth0 NIC Link is Down
Apr  9 12:54:07 ubuntu kernel: [  877.075642] ATL1E 0000:02:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
Apr  9 13:17:33 ubuntu pulseaudio[1539]: ratelimit.c: 2 events suppressed

```

I thought only the log of this day would be interessting... I got this error everytime I login so it should be in here too.

---

### Post by Krytarik on 2011-04-09
I just yet tested the "hold" command with a currently upgradable package , and it works. Although I find it somewhat annoying and disturbing that Synaptic apparently doesn't reflect the "hold", but it definitely works for "apt-get".

So, if you still don't seem to get the package on hold, simply try to purge it, along with its dependend packages:
```
sudo apt-get purge bogofilter-common
```Regarding the other issue, I didn't notice any relevant error messages in the log. But now that you say that you see the error message upon login, you should also check "/var/log/Xorg.0.log" and "~/.xsession-errors".

---

### Post by xMaD on 2011-04-11
Well, there is a little problem with apt-get: 
```
lbxdm@ubuntu:~$ sudo apt-get purge bogofilter-common
[sudo] password for lbxdm: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Die folgenden Pakete werden ENTFERNT:
  bogofilter* bogofilter-bdb* bogofilter-common*
Die folgenden gehaltenen Pakete werden verändert:
  bogofilter-common
0 aktualisiert, 0 neu installiert, 3 zu entfernen und 310 nicht aktualisiert.
Nach dieser Operation werden 1.188kB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 90%dpkg: nicht behebbarer fataler Fehler, Abbruch:
 fehlgeschlagen in buffer_read(fd): Dateiliste des Paketes »bogofilter-common«: Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Seems like dpkg would be damaged too.... I read that apt-get works with dpkg :|

I read Xorg.0.log but I didnt found any error. ".xession-errors" doesnt exist. ( searched with ctrl+h too)

---

### Post by Krytarik on 2011-04-11
> **xMaD said:**
> Seems like dpkg would be damaged too....
No, not really, it's just the same stubborn error like each time.

Are you sure that you properly run all the commands of the previously posted guide?

We may try a more uncommon and undocumented approach:
- Check if there is indeed a directory with the name "bogofilter-common.*" in "/var/lib/dpkg/info".
- Backup and remove all occurrences with that pattern in that directory.
- Try againg to reinstall it:
```
sudo apt-get install --reinstall bogofilter-common
```> **xMaD said:**
> ".xession-errors" doesnt exist. ( searched with ctrl+h too)
It's a hidden file at the toplevel of your home directory, and it's called ".x[COLOR=Red]**s**[/COLOR]ession-errors". And it definitely exists.

---

### Post by QLee on 2011-04-11
xMaD,
Is it anything like this bug?
[https://bugs.launchpad.net/ubuntu/+source/bogofilter/+bug/638567](https://bugs.launchpad.net/ubuntu/+source/bogofilter/+bug/638567)

You don't have to option your system to output in English, presumably you speak German since your system does and you appear to write English well, you could translate.

---

### Post by xMaD on 2011-04-12
> **Krytarik said:**
> 
Are you sure that you properly run all the commands of the previously posted guide?

Yep, I am. I worked the whole list all the way down. Just at the end I got the same error as I always get. The other things didnt gave out any errors.

> **Krytarik said:**
> 
We may try a more uncommon and undocumented approach:
- Check if there is indeed a directory with the name "bogofilter-common.*" in "/var/lib/dpkg/info".


There is: "bogofilter-common.conffiles", "bogofilter-common.md5sums" and a folder "bogofilter-common.list"

> **Krytarik said:**
> 
- Backup and remove all occurrences with that pattern in that directory.

I did a backup of those files but I cannot remove then. As I told you, Im newbie on this so maybe you can tell me how to delete those files. The "delete" option is disables in this folders and I havent got a idea how to enable them.


In the xsession-errors file (I searched at the wrong place so I couldnt find it :P) there are several samba errors, a proxy error and a dpkg error
```
could not load face 'file:///var/lib/dpkg/info/wireless-tools.preinst': unknown file format
Nautilus-Share-Message: Called "net usershare info" but it failed: Â»net usershareÂ« gab den Fehler 255 zurÃ¼ck: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing
```Dont think its useful but maybe it helps.

Maybe we could try to solve this problem via skype or irc so it would be more directly and so on. I dont know how you think about this but it might be easier. (just a suggestion)

@ QLee: I dont think its like the reported bug. There it goes "corrupted filesystem tarfile - corrupted package archive" and I never had such an error. It's not just the bogofilter which cant be installed, none cant be installed. "Apt-get update" works, "apt-get upgrade" doesnt. Any installation fails.

---

### Post by Krytarik on 2011-04-12
> **xMaD said:**
> 
There is: "bogofilter-common.conffiles", "bogofilter-common.md5sums" and a folder "bogofilter-common.list"

I did a backup of those files but I cannot remove then. As I told you, Im newbie on this so maybe you can tell me how to delete those files. The "delete" option is disables in this folders and I havent got a idea how to enable them.
Cool, I feel that we are nearing the solution! You need to gain root access to remove those files/dir.

To run Nautilus as root:
```
gksu nautilus
```[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Then, like said, reinstall those package.
> **xMaD said:**
> 
```
[COLOR=Blue]**could not load face 'file:///var/lib/dpkg/info/wireless-tools.preinst': unknown file format**[/COLOR]
Nautilus-Share-Message: Called "net usershare info" but it failed: Â»net usershareÂ« gab den Fehler 255 zurÃ¼ck: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing
```
Try reinstalling the mentioned package as well:
```
sudo apt-get install --reinstall wireless-tools
```

---

### Post by xMaD on 2011-04-14
Ok, I was able to remove those packages. It gave out the following message:
```
lbxdm@ubuntu:~$ gksu nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: »net usershare« gab den Fehler 255 zurück: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

could not load face 'file:///var/lib/dpkg/info/wireless-tools.preinst': unknown file format
                    
** (nautilus:1802): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files

```

But it seems to be deleted now.

I get another error right now:
```
lbxdm@ubuntu:~$ sudo apt-get install --reinstall bogofilter-common
[sudo] password for lbxdm: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```
I tried  'sudo dpkg --configure -a' - as it says- and tried the same installing again. It returned the same error :|

---

### Post by Krytarik on 2011-04-14
First, I didn't say that you should *remove* "wireless-tools". And since you are still getting the same error message, that apparently didn't help. Also, as it turned out, the error message only appears when you run Nautilus as root, like the other error messages, which are not really serious, but common. So, I guess you can safely ignore those error message, and reinstall the package.

When you try to 'upgrade' now, are you still getting an error?
If so, put the files "bogofilter-common.conffiles" and "bogofilter-common.md5sums" back in place, and add the file "bogofilter-common.list" I attached to this post, I appended ".txt" to be able to do so. This is again another uncommon/undocumented approach.

---

### Post by xMaD on 2011-04-15
Thanks damn lots :)
Im so uber happy :D
I replaced my bogofilter-common.list file with yourse and what did I get? A full working ubuntu!
So it was "just" that replacing of my error file with your clean file that blocked everything, thanks for this again!
Now I can sleep well :P
Uhm by the way: how do I mark this as solved?

You did a great job!

Greets,
xMaD

---

### Post by Krytarik on 2011-04-15
Great! I'm happy now, too! :-)

You're welcome!
> **xMaD said:**
> 
how do I mark this as solved?

See my signature, or just click at "Thread Tools" above.

---

