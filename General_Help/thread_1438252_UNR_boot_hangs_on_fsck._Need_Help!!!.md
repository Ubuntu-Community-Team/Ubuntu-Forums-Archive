---
title: "UNR boot hangs on fsck. Need Help!!!"
date: 2010-03-24
forum: General Help
---

### Post by da1337ninja on 2010-03-24
Hi. My Acer Aspire One hangs on the boot screen at fsck. I did update it before I shut down. Is there a way to fix this? Any help will be appreciated.

---

### Post by quixote on 2010-03-26
Try booting with a LiveUSB (or LiveCD if the Aspire has a CD).  Make sure the hard drive is UNmounted by typing the following in a terminal (Applications > Accessories > Terminal):```
sudo umount /dev/your-drive-designation
``` If you don't know what it is, list all drives with ```
sudo fdisk -l
```look at the sizes of the drives and note which one is your HD.  It'll look like /dev/sda1 or something similar.

Once you're sure the HD is unmounted, run ```
sudo e2fsck -p /dev/your-drive-designation
```

If we're lucky, that'll fix it.  If we're not so lucky, we keep plugging away. ;)

---

### Post by da1337ninja on 2010-03-27
Thanks a lot for the help quixote. I tried e2fsck but i don't think it worked. It now gets past fsck but now the output looks like this
```

fsck from util-linux-ng 2.16
/dev/sda1: clean, 177336/468640 files, 815625/1871564 blocks
init: rsyslog-kmsg main process (504) killed by BUS signal
init: rsyslog-kmsg main process ended, respawning
modem-managerL Loaded plugin Sierra
modem-managerL Loaded plugin Ericsson MBM
modem-managerL Loaded plugin Option High-Speed
modem-managerL Loaded plugin Nokia
modem-managerL Loaded plugin Generic
modem-managerL Loaded plugin Huawei
modem-managerL Loaded plugin Option
modem-managerL Loaded plugin ZTE
modem-managerL Loaded plugin MotoC
modem-managerL Loaded plugin Gobi
modem-managerL Loaded plugin Novatel

```

I have no idea what this means. Any help is greatly appreciated.

EDIT:
I was able to start the computer in recovery mode. Is there something terminalish I could do to fix it?

---

### Post by quixote on 2010-03-28
Erm, I don't know what any of that means either. :redface:  Are those the only messages you get or is that just as many as you had the energy for?  The ones you listed look harmless to me (but, as I say, I don't know much about this!).  The one init process killed is respawned with no further backchat, and the others are just a boatload of modem drivers or something.  

(Do you need them all?  Turning off the ones you don't need might be a good idea, because you never know when some unnecessary something will step on something you do need.  I think you blacklist them in /etc/modprobe.d/blacklist.conf or something.  Search for the message, eg "modem-managerL Loaded plugin Nokia" in the forums.)  

And sda1 is clean.  What could be nicer?  Well, if it booted properly, I guess....  The only terminal-y thing I can think of offhand is to try:```
sudo dpkg --configure -a
``` which tells all broken packages to fix themselves.  But I suspect it's some kind of settings that have gone wrong in your case, not a package, so that won't help.  Still, worth a try.

---

### Post by da1337ninja on 2010-03-28
That was the complete list of errors that i got back. I tried repairing the packages and then the system hung for a bit after the startup splash screen, output A TON of stuff, and then hung again. I would type everything out to show you, but it's just WAY too much. (UPDATE) As i was typing this out, i decided to try run it again. And I got a new message:
```

fsck from util-linux-ng 2.16
/dev/sda1: clean, 177336/468640 files, 815625/1871564 blocks
modem-managerL Loaded plugin Sierra
modem-managerL Loaded plugin Ericsson MBM
modem-managerL Loaded plugin Option High-Speed
modem-managerL Loaded plugin Nokia
modem-managerL Loaded plugin Generic
modem-managerL Loaded plugin Huawei
modem-managerL Loaded plugin Option
modem-managerL Loaded plugin ZTE
modem-managerL Loaded plugin MotoC
modem-managerL Loaded plugin Gobi
modem-managerL Loaded plugin Novatel
init: rsyslog-kmsg main process (504) killed by BUS signal
init: rsyslog-kmsg main process ended, respawning
* Starting AppArmor profiles

```

I've been looking through the forums for about a week now and it appears that other netbook users having been having this problem. Apparently on the the updates does not finish before it restarts. I told my system not to restart on update completion though... 

I've used linux off and on for about a year and I have to say this is the most frustrated I've ever been with it. I've never experienced this many problems with it. I really appreciate your time and help.

UPDATE2: Ok i just tried it again and now I get a bunch of stuff, the last line being:
```

43.356567] end_request: I/O error, dev sda, sector 267255

```

---

### Post by john newbuntu on 2010-03-28
That looks like a filesystem error.  Even though your first fsck said the partition is clean, force it one more time via liveCD:

sudo e2fsck -C0 -p -f -v /dev/sda1

assuming that /dev/sda1 is where your linux root partition is (please check with sudo fdisk -l)

---

### Post by da1337ninja on 2010-03-28
hey john thanks for you help. I tried to do what you wrote but it told me but now it hangs on the loading of the modem drivers (described above). What the heck is going on? Thanks so much for your help. I really appreciate it.

---

### Post by john newbuntu on 2010-03-28
That is a zero after -C.  It should just print a completion/progress bar.  If "0" does not work, try 3.

---

### Post by da1337ninja on 2010-03-28
Yeah, sorry my bad I wrote the wrong command. It still did not fix it though. If you read my post above it still hangs on the loading of modem drivers. Again, thanks for your help. The ubuntu community is the best

---

### Post by john newbuntu on 2010-03-28
Do you use a modem?  If so, do you want to disconnect it first and then try rebooting ubuntu.  Just a shot.

---

### Post by da1337ninja on 2010-03-28
No i don't. Just wifi and ethernet. Should I disable the drivers? Will this cause problems later? If not, how do I disable them? Thanks.

---

### Post by wanabewired on 2010-03-28
I'm having this problem too.. I can however log in via SSH and everything seems to be running as normal.

I'm running the AMD64 Server version of:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"

Annoyingly I'm not able to switch to another tty with the usual Alt + F2

I can't find anything amiss in the logs either:

```

Mar 28 16:32:43 ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Mar 28 16:32:43 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="784" x-info="http://www.rsyslog.com"] (re)start
Mar 28 16:32:43 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Mar 28 16:32:43 ubuntu rsyslogd: rsyslogd's userid changed to 101
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Linux version 2.6.32-16-server (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-3ubuntu1) ) #25-Ubuntu SMP Tue Mar 9 17:40:50 UTC 2010 (Ubuntu 2.6.32-16.25-server)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-16-server root=UUID=65103638-35a2-440e-802f-6f986f95a3ac ro quiet splash
Mar 28 16:32:43 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Mar 28 16:32:43 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] DMI 2.2 present.
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Mar 28 16:32:43 ubuntu kernel: [    0.000000] last_pfn = 0x7fff0 max_arch_pfn = 0x400000000
Mar 28 16:32:43 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Mar 28 16:32:43 ubuntu kernel: [    0.000000] modified physical RAM map:
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000007fff0000 (usable)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  modified: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  modified: 000000007fff3000 - 0000000080000000 (ACPI data)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Mar 28 16:32:43 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007fff0000
Mar 28 16:32:43 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Mar 28 16:32:43 ubuntu kernel: [    0.000000] RAMDISK: 3782e000 - 37fef271
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000f7e40 00014 (v00 Nvidia)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: RSDT 000000007fff3040 00030 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: FACP 000000007fff30c0 00074 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: DSDT 000000007fff3180 05FC8 (v01 NVIDIA AWRDACPI 00001000 MSFT 0100000E)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: FACS 000000007fff0000 00040
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: MCFG 000000007fff92c0 0003C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: APIC 000000007fff91c0 00098 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Mar 28 16:32:43 ubuntu kernel: [    0.000000] No NUMA configuration found
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007fff0000
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007fff0000
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   bootmap [0000000000017000 -  0000000000026fff] pages 10
Mar 28 16:32:43 ubuntu kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007fff0000]
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   #2 [0001000000 - 0001a7bca4]    TEXT DATA BSS ==> [0001000000 - 0001a7bca4]
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   #3 [003782e000 - 0037fef271]          RAMDISK ==> [003782e000 - 0037fef271]
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   #5 [0001a7c000 - 0001a7c06a]              BRK ==> [0001a7c000 - 0001a7c06a]
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Mar 28 16:32:43 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f3d40] f3d40
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Mar 28 16:32:43 ubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 28 16:32:43 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar 28 16:32:43 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar 28 16:32:43 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007fff0
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Mar 28 16:32:43 ubuntu kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Mar 28 16:32:43 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 28 16:32:43 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Mar 28 16:32:43 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 28 16:32:43 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Mar 28 16:32:43 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Mar 28 16:32:43 ubuntu kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Mar 28 16:32:43 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91352 r8192 d23336 u524288
Mar 28 16:32:43 ubuntu kernel: [    0.000000] pcpu-alloc: s91352 r8192 d23336 u524288 alloc=1*2097152
Mar 28 16:32:43 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516890
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Policy zone: DMA32
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-16-server root=UUID=65103638-35a2-440e-802f-6f986f95a3ac ro quiet splash
Mar 28 16:32:43 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Initializing CPU#0
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Checking aperture...
Mar 28 16:32:43 ubuntu kernel: [    0.000000] No AGP bridge found
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Node 0: aperture @ 344000000 size 32 MB
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Memory: 2048496k/2097088k available (5586k kernel code, 452k absent, 48140k reserved, 3204k data, 800k init)
Mar 28 16:32:43 ubuntu kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Mar 28 16:32:43 ubuntu kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Mar 28 16:32:43 ubuntu kernel: [    0.000000] console [tty0] enabled
Mar 28 16:32:43 ubuntu kernel: [    0.000000] allocated 20971520 bytes of page_cgroup
Mar 28 16:32:43 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Mar 28 16:32:43 ubuntu kernel: [    0.000000] Detected 2010.165 MHz processor.
Mar 28 16:32:43 ubuntu kernel: [    0.010007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4020.33 BogoMIPS (lpj=20101650)
Mar 28 16:32:43 ubuntu kernel: [    0.010044] Security Framework initialized
Mar 28 16:32:43 ubuntu kernel: [    0.010070] AppArmor: AppArmor initialized
Mar 28 16:32:43 ubuntu kernel: [    0.010303] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Mar 28 16:32:43 ubuntu kernel: [    0.021574] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 28 16:32:43 ubuntu kernel: [    0.022619] Mount-cache hash table entries: 256
Mar 28 16:32:43 ubuntu kernel: [    0.022827] Initializing cgroup subsys ns
Mar 28 16:32:43 ubuntu kernel: [    0.022831] Initializing cgroup subsys cpuacct
Mar 28 16:32:43 ubuntu kernel: [    0.022836] Initializing cgroup subsys memory
Mar 28 16:32:43 ubuntu kernel: [    0.022847] Initializing cgroup subsys devices
Mar 28 16:32:43 ubuntu kernel: [    0.022850] Initializing cgroup subsys freezer
Mar 28 16:32:43 ubuntu kernel: [    0.022852] Initializing cgroup subsys net_cls
Mar 28 16:32:43 ubuntu kernel: [    0.022879] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar 28 16:32:43 ubuntu kernel: [    0.022881] CPU: L2 Cache: 512K (64 bytes/line)
Mar 28 16:32:43 ubuntu kernel: [    0.022884] CPU 0/0x0 -> Node 0
Mar 28 16:32:43 ubuntu kernel: [    0.022906] mce: CPU supports 5 MCE banks
Mar 28 16:32:43 ubuntu kernel: [    0.022920] Performance Events: AMD PMU driver.
Mar 28 16:32:43 ubuntu kernel: [    0.022926] ... version:                0
Mar 28 16:32:43 ubuntu kernel: [    0.022927] ... bit width:              48
Mar 28 16:32:43 ubuntu kernel: [    0.022929] ... generic registers:      4
Mar 28 16:32:43 ubuntu kernel: [    0.022931] ... value mask:             0000ffffffffffff
Mar 28 16:32:43 ubuntu kernel: [    0.022933] ... max period:             00007fffffffffff
Mar 28 16:32:43 ubuntu kernel: [    0.022935] ... fixed-purpose events:   0
Mar 28 16:32:43 ubuntu kernel: [    0.022936] ... event mask:             000000000000000f
Mar 28 16:32:43 ubuntu kernel: [    0.022951] SMP alternatives: switching to UP code
Mar 28 16:32:43 ubuntu kernel: [    0.033201] ACPI: Core revision 20090903
Mar 28 16:32:43 ubuntu kernel: [    0.042689] ftrace: converting mcount calls to 0f 1f 44 00 00
Mar 28 16:32:43 ubuntu kernel: [    0.042696] ftrace: allocating 23222 entries in 92 pages
Mar 28 16:32:43 ubuntu kernel: [    0.048966] Setting APIC routing to flat
Mar 28 16:32:43 ubuntu kernel: [    0.049289] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Mar 28 16:32:43 ubuntu kernel: [    0.149308] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 02
Mar 28 16:32:43 ubuntu kernel: [    0.150000] Brought up 1 CPUs
Mar 28 16:32:43 ubuntu kernel: [    0.150000] Total of 1 processors activated (4020.33 BogoMIPS).
Mar 28 16:32:43 ubuntu kernel: [    0.150000] devtmpfs: initialized
Mar 28 16:32:43 ubuntu kernel: [    0.150000] regulator: core version 0.5
Mar 28 16:32:43 ubuntu kernel: [    0.150000] Time: 15:32:33  Date: 03/28/10
Mar 28 16:32:43 ubuntu kernel: [    0.150000] NET: Registered protocol family 16
Mar 28 16:32:43 ubuntu kernel: [    0.150000] TOM: 0000000080000000 aka 2048M
Mar 28 16:32:43 ubuntu kernel: [    0.150000] ACPI: bus type pci registered
Mar 28 16:32:43 ubuntu kernel: [    0.150000] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Mar 28 16:32:43 ubuntu kernel: [    0.150000] PCI: MCFG area at e0000000 reserved in E820
Mar 28 16:32:43 ubuntu kernel: [    0.150000] PCI: Using MMCONFIG at e0000000 - efffffff
Mar 28 16:32:43 ubuntu kernel: [    0.150000] PCI: Using configuration type 1 for base access
Mar 28 16:32:43 ubuntu kernel: [    0.150000] bio: create slab <bio-0> at 0
Mar 28 16:32:43 ubuntu kernel: [    0.154469] ACPI Warning: Package List length (0x6) larger than NumElements count (0x3), truncated
Mar 28 16:32:43 ubuntu kernel: [    0.154474]  (20090903/dsobject-515)
Mar 28 16:32:43 ubuntu kernel: [    0.158491] ACPI: Interpreter enabled
Mar 28 16:32:43 ubuntu kernel: [    0.158495] ACPI: (supports S0 S1 S4 S5)
Mar 28 16:32:43 ubuntu kernel: [    0.158521] ACPI: Using IOAPIC for interrupt routing
Mar 28 16:32:43 ubuntu kernel: [    0.167334] ACPI: No dock devices found.
Mar 28 16:32:43 ubuntu kernel: [    0.168378] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 28 16:32:43 ubuntu kernel: [    0.168491] HPET not enabled in BIOS. You might try hpet=force boot option
Mar 28 16:32:43 ubuntu kernel: [    0.168533] pci 0000:00:01.1: PME# supported from D3hot D3cold
Mar 28 16:32:43 ubuntu kernel: [    0.168536] pci 0000:00:01.1: PME# disabled
Mar 28 16:32:43 ubuntu kernel: [    0.168578] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 28 16:32:43 ubuntu kernel: [    0.168581] pci 0000:00:02.0: PME# disabled
Mar 28 16:32:43 ubuntu kernel: [    0.168625] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar 28 16:32:43 ubuntu kernel: [    0.168628] pci 0000:00:02.1: PME# disabled
Mar 28 16:32:43 ubuntu kernel: [    0.168809] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 28 16:32:43 ubuntu kernel: [    0.168812] pci 0000:00:0a.0: PME# disabled
Mar 28 16:32:43 ubuntu kernel: [    0.168846] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 28 16:32:43 ubuntu kernel: [    0.168848] pci 0000:00:0b.0: PME# disabled
Mar 28 16:32:43 ubuntu kernel: [    0.168884] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 28 16:32:43 ubuntu kernel: [    0.168887] pci 0000:00:0c.0: PME# disabled
Mar 28 16:32:43 ubuntu kernel: [    0.168922] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 28 16:32:43 ubuntu kernel: [    0.168925] pci 0000:00:0d.0: PME# disabled
Mar 28 16:32:43 ubuntu kernel: [    0.168959] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 28 16:32:43 ubuntu kernel: [    0.168962] pci 0000:00:0e.0: PME# disabled
Mar 28 16:32:43 ubuntu kernel: [    0.169113] pci 0000:01:06.0: PME# supported from D2 D3hot D3cold
Mar 28 16:32:43 ubuntu kernel: [    0.169116] pci 0000:01:06.0: PME# disabled
Mar 28 16:32:43 ubuntu kernel: [    0.169229] pci 0000:01:08.0: PME# supported from D1 D2 D3hot D3cold
Mar 28 16:32:43 ubuntu kernel: [    0.169233] pci 0000:01:08.0: PME# disabled
Mar 28 16:32:43 ubuntu kernel: [    0.169308] pci 0000:00:09.0: transparent bridge
Mar 28 16:32:43 ubuntu kernel: [    0.244923] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Mar 28 16:32:43 ubuntu kernel: [    0.245118] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 *12 14 15)
Mar 28 16:32:43 ubuntu kernel: [    0.245306] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Mar 28 16:32:43 ubuntu kernel: [    0.245494] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Mar 28 16:32:43 ubuntu kernel: [    0.245679] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.245867] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Mar 28 16:32:43 ubuntu kernel: [    0.246053] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.246241] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 11 *12 14 15)
Mar 28 16:32:43 ubuntu kernel: [    0.246433] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.246620] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.246807] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Mar 28 16:32:43 ubuntu kernel: [    0.246995] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Mar 28 16:32:43 ubuntu kernel: [    0.247185] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.247382] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Mar 28 16:32:43 ubuntu kernel: [    0.247582] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Mar 28 16:32:43 ubuntu kernel: [    0.247782] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.247995] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Mar 28 16:32:43 ubuntu kernel: [    0.248202] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
Mar 28 16:32:43 ubuntu kernel: [    0.248408] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Mar 28 16:32:43 ubuntu kernel: [    0.248615] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
Mar 28 16:32:43 ubuntu kernel: [    0.248748] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.248966] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Mar 28 16:32:43 ubuntu kernel: [    0.249182] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.249403] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Mar 28 16:32:43 ubuntu kernel: [    0.249620] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.249836] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.250069] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Mar 28 16:32:43 ubuntu kernel: [    0.250286] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Mar 28 16:32:43 ubuntu kernel: [    0.250501] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.250727] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Mar 28 16:32:43 ubuntu kernel: [    0.250952] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Mar 28 16:32:43 ubuntu kernel: [    0.251177] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
Mar 28 16:32:43 ubuntu kernel: [    0.251323] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
Mar 28 16:32:43 ubuntu kernel: [    0.251326] vgaarb: loaded
Mar 28 16:32:43 ubuntu kernel: [    0.251455] SCSI subsystem initialized
Mar 28 16:32:43 ubuntu kernel: [    0.251627] usbcore: registered new interface driver usbfs
Mar 28 16:32:43 ubuntu kernel: [    0.251638] usbcore: registered new interface driver hub
Mar 28 16:32:43 ubuntu kernel: [    0.251670] usbcore: registered new device driver usb
Mar 28 16:32:43 ubuntu kernel: [    0.251804] ACPI: WMI: Mapper loaded
Mar 28 16:32:43 ubuntu kernel: [    0.251806] PCI: Using ACPI for IRQ routing
Mar 28 16:32:43 ubuntu kernel: [    0.251954] NetLabel: Initializing
Mar 28 16:32:43 ubuntu kernel: [    0.251956] NetLabel:  domain hash size = 128
Mar 28 16:32:43 ubuntu kernel: [    0.251958] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 28 16:32:43 ubuntu kernel: [    0.251973] NetLabel:  unlabeled traffic allowed by default
Mar 28 16:32:43 ubuntu kernel: [    0.252007] Switching to clocksource jiffies
Mar 28 16:32:43 ubuntu kernel: [    0.253935] AppArmor: AppArmor Filesystem Enabled
Mar 28 16:32:43 ubuntu kernel: [    0.253960] pnp: PnP ACPI init
Mar 28 16:32:43 ubuntu kernel: [    0.253979] ACPI: bus type pnp registered
Mar 28 16:32:43 ubuntu kernel: [    0.260069] pnp: PnP ACPI: found 13 devices
Mar 28 16:32:43 ubuntu kernel: [    0.260071] ACPI: ACPI bus type pnp unregistered
Mar 28 16:32:43 ubuntu kernel: [    0.260083] system 00:00: ioport range 0x4000-0x407f has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260086] system 00:00: ioport range 0x4080-0x40ff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260089] system 00:00: ioport range 0x4400-0x447f has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260092] system 00:00: ioport range 0x4480-0x44ff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260095] system 00:00: ioport range 0x4800-0x487f has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260098] system 00:00: ioport range 0x4880-0x48ff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260104] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260107] system 00:02: ioport range 0x800-0x805 has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260110] system 00:02: ioport range 0x290-0x30f has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260113] system 00:02: ioport range 0x290-0x297 has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260120] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260123] system 00:0c: iomem range 0xd5800-0xd7fff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260126] system 00:0c: iomem range 0xf0000-0xfbfff could not be reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260129] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260132] system 00:0c: iomem range 0x7fff0000-0x7fffffff could not be reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260136] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260143] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260146] system 00:0c: iomem range 0x100000-0x7ffeffff could not be reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260149] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260152] system 00:0c: iomem range 0xfee00000-0xfeefffff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260155] system 00:0c: iomem range 0xfefff000-0xfeffffff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260158] system 00:0c: iomem range 0xfff80000-0xfff80fff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260162] system 00:0c: iomem range 0xfff90000-0xfffbffff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.260165] system 00:0c: iomem range 0xfffed000-0xfffeffff has been reserved
Mar 28 16:32:43 ubuntu kernel: [    0.264861] Switching to clocksource acpi_pm
Mar 28 16:32:43 ubuntu kernel: [    0.265005] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01
Mar 28 16:32:43 ubuntu kernel: [    0.265008] pci 0000:00:09.0:   IO window: 0xa000-0xafff
Mar 28 16:32:43 ubuntu kernel: [    0.265011] pci 0000:00:09.0:   MEM window: 0xfe900000-0xfe9fffff
Mar 28 16:32:43 ubuntu kernel: [    0.265014] pci 0000:00:09.0:   PREFETCH window: 0xfea00000-0xfeafffff
Mar 28 16:32:43 ubuntu kernel: [    0.265018] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
Mar 28 16:32:43 ubuntu kernel: [    0.265021] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff
Mar 28 16:32:43 ubuntu kernel: [    0.265024] pci 0000:00:0b.0:   MEM window: 0xfe800000-0xfe8fffff
Mar 28 16:32:43 ubuntu kernel: [    0.265027] pci 0000:00:0b.0:   PREFETCH window: 0x000000fe700000-0x000000fe7fffff
Mar 28 16:32:43 ubuntu kernel: [    0.265031] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
Mar 28 16:32:43 ubuntu kernel: [    0.265034] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff
Mar 28 16:32:43 ubuntu kernel: [    0.265037] pci 0000:00:0c.0:   MEM window: 0xfe600000-0xfe6fffff
Mar 28 16:32:43 ubuntu kernel: [    0.265040] pci 0000:00:0c.0:   PREFETCH window: 0x000000fe500000-0x000000fe5fffff
Mar 28 16:32:43 ubuntu kernel: [    0.265044] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
Mar 28 16:32:43 ubuntu kernel: [    0.265046] pci 0000:00:0d.0:   IO window: 0x7000-0x7fff
Mar 28 16:32:43 ubuntu kernel: [    0.265050] pci 0000:00:0d.0:   MEM window: 0xfe400000-0xfe4fffff
Mar 28 16:32:43 ubuntu kernel: [    0.265053] pci 0000:00:0d.0:   PREFETCH window: 0x000000fe300000-0x000000fe3fffff
Mar 28 16:32:43 ubuntu kernel: [    0.265057] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:05
Mar 28 16:32:43 ubuntu kernel: [    0.265060] pci 0000:00:0e.0:   IO window: 0x6000-0x6fff
Mar 28 16:32:43 ubuntu kernel: [    0.265063] pci 0000:00:0e.0:   MEM window: 0xfe200000-0xfe2fffff
Mar 28 16:32:43 ubuntu kernel: [    0.265066] pci 0000:00:0e.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
Mar 28 16:32:43 ubuntu kernel: [    0.265193] NET: Registered protocol family 2
Mar 28 16:32:43 ubuntu kernel: [    0.265340] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Mar 28 16:32:43 ubuntu kernel: [    0.266411] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Mar 28 16:32:43 ubuntu kernel: [    0.269994] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Mar 28 16:32:43 ubuntu kernel: [    0.269994] TCP: Hash tables configured (established 262144 bind 65536)
Mar 28 16:32:43 ubuntu kernel: [    0.269994] TCP reno registered
Mar 28 16:32:43 ubuntu kernel: [    0.269994] NET: Registered protocol family 1
Mar 28 16:32:43 ubuntu kernel: [    0.290080] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290086] pci 0000:00:0b.0: Found disabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290094] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290097] pci 0000:00:0b.0: Linking AER extended capability
Mar 28 16:32:43 ubuntu kernel: [    0.290134] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290140] pci 0000:00:0c.0: Found disabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290147] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290149] pci 0000:00:0c.0: Linking AER extended capability
Mar 28 16:32:43 ubuntu kernel: [    0.290190] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290196] pci 0000:00:0d.0: Found disabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290203] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290205] pci 0000:00:0d.0: Linking AER extended capability
Mar 28 16:32:43 ubuntu kernel: [    0.290249] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290255] pci 0000:00:0e.0: Found disabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290262] pci 0000:00:00.0: Found enabled HT MSI Mapping
Mar 28 16:32:43 ubuntu kernel: [    0.290264] pci 0000:00:0e.0: Linking AER extended capability
Mar 28 16:32:43 ubuntu kernel: [    0.290584] Scanning for low memory corruption every 60 seconds
Mar 28 16:32:43 ubuntu kernel: [    0.290726] audit: initializing netlink socket (disabled)
Mar 28 16:32:43 ubuntu kernel: [    0.290739] type=2000 audit(1269790353.290:1): initialized
Mar 28 16:32:43 ubuntu kernel: [    0.300316] Trying to unpack rootfs image as initramfs...
Mar 28 16:32:43 ubuntu kernel: [    0.320230] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Mar 28 16:32:43 ubuntu kernel: [    0.321764] VFS: Disk quotas dquot_6.5.2
Mar 28 16:32:43 ubuntu kernel: [    0.321830] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Mar 28 16:32:43 ubuntu kernel: [    0.322526] fuse init (API version 7.13)
Mar 28 16:32:43 ubuntu kernel: [    0.322619] msgmni has been set to 4000
Mar 28 16:32:43 ubuntu kernel: [    0.322862] alg: No test for stdrng (krng)
Mar 28 16:32:43 ubuntu kernel: [    0.322874] io scheduler noop registered
Mar 28 16:32:43 ubuntu kernel: [    0.322876] io scheduler anticipatory registered
Mar 28 16:32:43 ubuntu kernel: [    0.322878] io scheduler deadline registered (default)
Mar 28 16:32:43 ubuntu kernel: [    0.322924] io scheduler cfq registered
Mar 28 16:32:43 ubuntu kernel: [    0.330803] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 28 16:32:43 ubuntu kernel: [    0.330829] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar 28 16:32:43 ubuntu kernel: [    0.330951] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Mar 28 16:32:43 ubuntu kernel: [    0.330956] ACPI: Power Button [PWRB]
Mar 28 16:32:43 ubuntu kernel: [    0.331017] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Mar 28 16:32:43 ubuntu kernel: [    0.331019] ACPI: Power Button [PWRF]
Mar 28 16:32:43 ubuntu kernel: [    0.331073] fan PNP0C0B:00: registered as cooling_device0
Mar 28 16:32:43 ubuntu kernel: [    0.331081] ACPI: Fan [FAN] (on)
Mar 28 16:32:43 ubuntu kernel: [    0.331687] processor LNXCPU:00: registered as cooling_device1
Mar 28 16:32:43 ubuntu kernel: [    0.336348] thermal LNXTHERM:01: registered as thermal_zone0
Mar 28 16:32:43 ubuntu kernel: [    0.336356] ACPI: Thermal Zone [THRM] (40 C)
Mar 28 16:32:43 ubuntu kernel: [    0.337682] Linux agpgart interface v0.103
Mar 28 16:32:43 ubuntu kernel: [    0.337728] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar 28 16:32:43 ubuntu kernel: [    0.337827] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 28 16:32:43 ubuntu kernel: [    0.337914] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Mar 28 16:32:43 ubuntu kernel: [    0.338150] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 28 16:32:43 ubuntu kernel: [    0.339175] brd: module loaded
Mar 28 16:32:43 ubuntu kernel: [    0.339635] loop: module loaded
Mar 28 16:32:43 ubuntu kernel: [    0.339739] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Mar 28 16:32:43 ubuntu kernel: [    0.350551] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Mar 28 16:32:43 ubuntu kernel: [    0.350571] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Mar 28 16:32:43 ubuntu kernel: [    0.350733] scsi0 : sata_nv
Mar 28 16:32:43 ubuntu kernel: [    0.350874] scsi1 : sata_nv
Mar 28 16:32:43 ubuntu kernel: [    0.351062] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 23
Mar 28 16:32:43 ubuntu kernel: [    0.351065] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 23
Mar 28 16:32:43 ubuntu kernel: [    0.351574] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
Mar 28 16:32:43 ubuntu kernel: [    0.351586] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
Mar 28 16:32:43 ubuntu kernel: [    0.360288] scsi2 : sata_nv
Mar 28 16:32:43 ubuntu kernel: [    0.360411] scsi3 : sata_nv
Mar 28 16:32:43 ubuntu kernel: [    0.360630] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 22
Mar 28 16:32:43 ubuntu kernel: [    0.360633] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 22
Mar 28 16:32:43 ubuntu kernel: [    0.360986] scsi4 : pata_amd
Mar 28 16:32:43 ubuntu kernel: [    0.361051] scsi5 : pata_amd
Mar 28 16:32:43 ubuntu kernel: [    0.361859] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Mar 28 16:32:43 ubuntu kernel: [    0.361862] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Mar 28 16:32:43 ubuntu kernel: [    0.362504] Fixed MDIO Bus: probed
Mar 28 16:32:43 ubuntu kernel: [    0.362544] PPP generic driver version 2.4.2
Mar 28 16:32:43 ubuntu kernel: [    0.362609] tun: Universal TUN/TAP device driver, 1.6
Mar 28 16:32:43 ubuntu kernel: [    0.362611] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Mar 28 16:32:43 ubuntu kernel: [    0.362734] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 28 16:32:43 ubuntu kernel: [    0.363184] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Mar 28 16:32:43 ubuntu kernel: [    0.363202] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
Mar 28 16:32:43 ubuntu kernel: [    0.363224] ehci_hcd 0000:00:02.1: EHCI Host Controller
Mar 28 16:32:43 ubuntu kernel: [    0.363266] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Mar 28 16:32:43 ubuntu kernel: [    0.363299] ehci_hcd 0000:00:02.1: debug port 1
Mar 28 16:32:43 ubuntu kernel: [    0.363325] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfebfe000
Mar 28 16:32:43 ubuntu kernel: [    0.380134] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Mar 28 16:32:43 ubuntu kernel: [    0.380284] usb usb1: configuration #1 chosen from 1 choice
Mar 28 16:32:43 ubuntu kernel: [    0.380314] hub 1-0:1.0: USB hub found
Mar 28 16:32:43 ubuntu kernel: [    0.380327] hub 1-0:1.0: 10 ports detected
Mar 28 16:32:43 ubuntu kernel: [    0.380436] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 28 16:32:43 ubuntu kernel: [    0.390551] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
Mar 28 16:32:43 ubuntu kernel: [    0.390573] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
Mar 28 16:32:43 ubuntu kernel: [    0.390601] ohci_hcd 0000:00:02.0: OHCI Host Controller
Mar 28 16:32:43 ubuntu kernel: [    0.390708] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Mar 28 16:32:43 ubuntu kernel: [    0.390745] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfebff000
Mar 28 16:32:43 ubuntu kernel: [    0.452411] usb usb2: configuration #1 chosen from 1 choice
Mar 28 16:32:43 ubuntu kernel: [    0.452443] hub 2-0:1.0: USB hub found
Mar 28 16:32:43 ubuntu kernel: [    0.452457] hub 2-0:1.0: 10 ports detected
Mar 28 16:32:43 ubuntu kernel: [    0.452561] uhci_hcd: USB Universal Host Controller Interface driver
Mar 28 16:32:43 ubuntu kernel: [    0.452672] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Mar 28 16:32:43 ubuntu kernel: [    0.452674] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Mar 28 16:32:43 ubuntu kernel: [    0.453471] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 28 16:32:43 ubuntu kernel: [    0.453568] mice: PS/2 mouse device common for all mice
Mar 28 16:32:43 ubuntu kernel: [    0.453667] rtc_cmos 00:04: RTC can wake from S4
Mar 28 16:32:43 ubuntu kernel: [    0.453718] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Mar 28 16:32:43 ubuntu kernel: [    0.453742] rtc0: alarms up to one year, y3k, 242 bytes nvram
Mar 28 16:32:43 ubuntu kernel: [    0.453876] device-mapper: uevent: version 1.0.3
Mar 28 16:32:43 ubuntu kernel: [    0.457339] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Mar 28 16:32:43 ubuntu kernel: [    0.458252] device-mapper: multipath: version 1.1.0 loaded
Mar 28 16:32:43 ubuntu kernel: [    0.458256] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar 28 16:32:43 ubuntu kernel: [    0.462579] cpuidle: using governor ladder
Mar 28 16:32:43 ubuntu kernel: [    0.462583] cpuidle: using governor menu
Mar 28 16:32:43 ubuntu kernel: [    0.463111] TCP cubic registered
Mar 28 16:32:43 ubuntu kernel: [    0.463244] NET: Registered protocol family 10
Mar 28 16:32:43 ubuntu kernel: [    0.463805] lo: Disabled Privacy Extensions
Mar 28 16:32:43 ubuntu kernel: [    0.464103] NET: Registered protocol family 17
Mar 28 16:32:43 ubuntu kernel: [    0.464152] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
Mar 28 16:32:43 ubuntu kernel: [    0.464206] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6
Mar 28 16:32:43 ubuntu kernel: [    0.464208] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8
Mar 28 16:32:43 ubuntu kernel: [    0.464210] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
Mar 28 16:32:43 ubuntu kernel: [    0.464362] registered taskstats version 1
Mar 28 16:32:43 ubuntu kernel: [    0.464677]   Magic number: 2:155:539
Mar 28 16:32:43 ubuntu kernel: [    0.464778] rtc_cmos 00:04: setting system clock to 2010-03-28 15:32:34 UTC (1269790354)
Mar 28 16:32:43 ubuntu kernel: [    0.464782] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 28 16:32:43 ubuntu kernel: [    0.464783] EDD information not available.
Mar 28 16:32:43 ubuntu kernel: [    0.473674] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Mar 28 16:32:43 ubuntu kernel: [    0.532745] Freeing initrd memory: 7940k freed
Mar 28 16:32:43 ubuntu kernel: [    0.540410] ata5.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB02, max UDMA/33
Mar 28 16:32:43 ubuntu kernel: [    0.580204] ata5.00: configured for UDMA/33
Mar 28 16:32:43 ubuntu kernel: [    0.840032] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 28 16:32:43 ubuntu kernel: [    0.850022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 28 16:32:43 ubuntu kernel: [    0.860337] ata1.00: ATA-7: WDC WD800JD-00MSA1, 10.01E01, max UDMA/133
Mar 28 16:32:43 ubuntu kernel: [    0.860340] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 28 16:32:43 ubuntu kernel: [    0.861063] ata3.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
Mar 28 16:32:43 ubuntu kernel: [    0.861066] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 28 16:32:43 ubuntu kernel: [    0.880295] ata1.00: configured for UDMA/133
Mar 28 16:32:43 ubuntu kernel: [    0.880437] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JD-00MS 10.0 PQ: 0 ANSI: 5
Mar 28 16:32:43 ubuntu kernel: [    0.880647] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 28 16:32:43 ubuntu kernel: [    0.880722] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Mar 28 16:32:43 ubuntu kernel: [    0.880769] sd 0:0:0:0: [sda] Write Protect is off
Mar 28 16:32:43 ubuntu kernel: [    0.880796] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 28 16:32:43 ubuntu kernel: [    0.880936]  sda: sda1 sda2 <
Mar 28 16:32:43 ubuntu kernel: [    0.901122] ata3.00: configured for UDMA/133
Mar 28 16:32:43 ubuntu kernel: [    0.921200]  sda5 >
Mar 28 16:32:43 ubuntu kernel: [    0.921486] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 28 16:32:43 ubuntu kernel: [    1.370028] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 28 16:32:43 ubuntu kernel: [    1.390799] ata2.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
Mar 28 16:32:43 ubuntu kernel: [    1.390802] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 28 16:32:43 ubuntu kernel: [    1.430859] ata2.00: configured for UDMA/133
Mar 28 16:32:43 ubuntu kernel: [    1.430921] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
Mar 28 16:32:43 ubuntu kernel: [    1.431057] sd 1:0:0:0: Attached scsi generic sg1 type 0
Mar 28 16:32:43 ubuntu kernel: [    1.431127] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
Mar 28 16:32:43 ubuntu kernel: [    1.431229] sd 2:0:0:0: Attached scsi generic sg2 type 0
Mar 28 16:32:43 ubuntu kernel: [    1.431282] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Mar 28 16:32:43 ubuntu kernel: [    1.431327] sd 2:0:0:0: [sdc] Write Protect is off
Mar 28 16:32:43 ubuntu kernel: [    1.431355] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Mar 28 16:32:43 ubuntu kernel: [    1.431379] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 28 16:32:43 ubuntu kernel: [    1.431468] sd 1:0:0:0: [sdb] Write Protect is off
Mar 28 16:32:43 ubuntu kernel: [    1.431493] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 28 16:32:43 ubuntu kernel: [    1.431651]  sdc:
Mar 28 16:32:43 ubuntu kernel: [    1.431754]  sdb: sdc1
Mar 28 16:32:43 ubuntu kernel: [    1.441732] sd 2:0:0:0: [sdc] Attached SCSI disk
Mar 28 16:32:43 ubuntu kernel: [    1.444313]  sdb1
Mar 28 16:32:43 ubuntu kernel: [    1.444481] sd 1:0:0:0: [sdb] Attached SCSI disk
Mar 28 16:32:43 ubuntu kernel: [    1.760022] ata4: SATA link down (SStatus 0 SControl 300)
Mar 28 16:32:43 ubuntu kernel: [    1.760841] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB02 PQ: 0 ANSI: 5
Mar 28 16:32:43 ubuntu kernel: [    1.768213] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 28 16:32:43 ubuntu kernel: [    1.768216] Uniform CD-ROM driver Revision: 3.20
Mar 28 16:32:43 ubuntu kernel: [    1.768366] sr 4:0:0:0: Attached scsi generic sg3 type 5
Mar 28 16:32:43 ubuntu kernel: [    1.930932] Freeing unused kernel memory: 800k freed
Mar 28 16:32:43 ubuntu kernel: [    1.931527] Write protecting the kernel read-only data: 7936k
Mar 28 16:32:43 ubuntu kernel: [    1.954824] udev: starting version 151
Mar 28 16:32:43 ubuntu kernel: [    1.983473] md: linear personality registered for level -1
Mar 28 16:32:43 ubuntu kernel: [    2.041751] md: multipath personality registered for level -4
Mar 28 16:32:43 ubuntu kernel: [    2.140384] md: raid0 personality registered for level 0
Mar 28 16:32:43 ubuntu kernel: [    2.167803] FDC 0 is a post-1991 82077
Mar 28 16:32:43 ubuntu kernel: [    2.204521] md: bind<sdc1>
Mar 28 16:32:43 ubuntu kernel: [    2.232872] md: bind<sdb1>
Mar 28 16:32:43 ubuntu kernel: [    2.248268] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Mar 28 16:32:43 ubuntu kernel: [    2.248636] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Mar 28 16:32:43 ubuntu kernel: [    2.248642] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Mar 28 16:32:43 ubuntu kernel: [    2.254056] md: raid1 personality registered for level 1
Mar 28 16:32:43 ubuntu kernel: [    2.265131] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Mar 28 16:32:43 ubuntu kernel: [    2.265417] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Mar 28 16:32:43 ubuntu kernel: [    2.265436] r8169 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Mar 28 16:32:43 ubuntu kernel: [    2.265470] r8169 0000:01:08.0: no PCI Express capability
Mar 28 16:32:43 ubuntu kernel: [    2.266119] eth0: RTL8110s at 0xffffc90010962000, 00:0b:2b:17:22:8f, XID 04000000 IRQ 16
Mar 28 16:32:43 ubuntu kernel: [    2.269587] raid1: raid set md0 active with 2 out of 2 mirrors
Mar 28 16:32:43 ubuntu kernel: [    2.269616] md0: detected capacity change from 0 to 1000203026432
Mar 28 16:32:43 ubuntu kernel: [    2.271410]  md0: unknown partition table
Mar 28 16:32:43 ubuntu kernel: [    2.277487] async_tx: api initialized (async)
Mar 28 16:32:43 ubuntu kernel: [    2.284415] xor: automatically using best checksumming function: generic_sse
Mar 28 16:32:43 ubuntu kernel: [    2.330012]    generic_sse:  6584.000 MB/sec
Mar 28 16:32:43 ubuntu kernel: [    2.330014] xor: using function: generic_sse (6584.000 MB/sec)
Mar 28 16:32:43 ubuntu kernel: [    2.330740] ohci1394 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Mar 28 16:32:43 ubuntu kernel: [    2.500039] raid6: int64x1   1679 MB/s
Mar 28 16:32:43 ubuntu kernel: [    2.670029] raid6: int64x2   2173 MB/s
Mar 28 16:32:43 ubuntu kernel: [    2.840031] raid6: int64x4   1478 MB/s
Mar 28 16:32:43 ubuntu kernel: [    3.010011] raid6: int64x8   1462 MB/s
Mar 28 16:32:43 ubuntu kernel: [    3.180014] raid6: sse2x1    2336 MB/s
Mar 28 16:32:43 ubuntu kernel: [    3.350026] raid6: sse2x2    3196 MB/s
Mar 28 16:32:43 ubuntu kernel: [    3.520014] raid6: sse2x4    3420 MB/s
Mar 28 16:32:43 ubuntu kernel: [    3.520016] raid6: using algorithm sse2x4 (3420 MB/s)
Mar 28 16:32:43 ubuntu kernel: [    3.522412] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe9ff000-fe9ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Mar 28 16:32:43 ubuntu kernel: [    3.534997] md: raid6 personality registered for level 6
Mar 28 16:32:43 ubuntu kernel: [    3.535000] md: raid5 personality registered for level 5
Mar 28 16:32:43 ubuntu kernel: [    3.535002] md: raid4 personality registered for level 4
Mar 28 16:32:43 ubuntu kernel: [    3.541185] forcedeth 0000:00:0a.0: ifname eth1, PHY OUI 0x3f1 @ 1, addr 00:01:29:d2:f0:ed
Mar 28 16:32:43 ubuntu kernel: [    3.541190] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
Mar 28 16:32:43 ubuntu kernel: [    3.545776] md: raid10 personality registered for level 10
Mar 28 16:32:43 ubuntu kernel: [    3.634517] EXT4-fs (sda1): mounted filesystem with ordered data mode
Mar 28 16:32:43 ubuntu kernel: [    7.759646] Adding 3227640k swap on /dev/sda5.  Priority:-1 extents:1 across:3227640k 
Mar 28 16:32:43 ubuntu kernel: [    7.781421] udev: starting version 151
Mar 28 16:32:43 ubuntu kernel: [    7.904571] parport_pc 00:0a: reported by Plug and Play ACPI
Mar 28 16:32:43 ubuntu kernel: [    7.904614] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Mar 28 16:32:43 ubuntu kernel: [    8.000107] lp: driver loaded but no devices found
Mar 28 16:32:43 ubuntu kernel: [    8.004468] i2c i2c-0: nForce2 SMBus adapter at 0x4c40
Mar 28 16:32:43 ubuntu kernel: [    8.004490] i2c i2c-1: nForce2 SMBus adapter at 0x4c00
Mar 28 16:32:43 ubuntu kernel: [    8.028874] [drm] Initialized drm 1.1.0 20060810
Mar 28 16:32:43 ubuntu kernel: [    8.077854] EDAC MC: Ver: 2.1.0 Mar  9 2010
Mar 28 16:32:43 ubuntu kernel: [    8.097135] cfg80211: Calling CRDA to update world regulatory domain
Mar 28 16:32:43 ubuntu kernel: [    8.150277] lp0: using parport0 (interrupt-driven).
Mar 28 16:32:43 ubuntu kernel: [    8.258429] ppdev: user-space parallel port driver
Mar 28 16:32:43 ubuntu kernel: [    8.283060] EDAC amd64_edac:  Ver: 3.2.0 Mar  9 2010
Mar 28 16:32:43 ubuntu kernel: [    8.300843] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
Mar 28 16:32:43 ubuntu kernel: [    8.300850] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Mar 28 16:32:43 ubuntu kernel: [    8.300852]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Mar 28 16:32:43 ubuntu kernel: [    8.300854]  (Note that use of the override may cause unknown side effects.)
Mar 28 16:32:43 ubuntu kernel: [    8.300880] amd64_edac: probe of 0000:00:18.2 failed with error -22
Mar 28 16:32:43 ubuntu kernel: [    8.302515] cfg80211: World regulatory domain updated:
Mar 28 16:32:43 ubuntu kernel: [    8.302520] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 28 16:32:43 ubuntu kernel: [    8.302523] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 28 16:32:43 ubuntu kernel: [    8.302526] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 28 16:32:43 ubuntu kernel: [    8.302529] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 28 16:32:43 ubuntu kernel: [    8.302531] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 28 16:32:43 ubuntu kernel: [    8.302534] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 28 16:32:43 ubuntu kernel: [    8.436128] type=1505 audit(1269790362.465:2):  operation="profile_load" pid=636 name="/sbin/dhclient3"
Mar 28 16:32:43 ubuntu kernel: [    8.436415] type=1505 audit(1269790362.465:3):  operation="profile_load" pid=636 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Mar 28 16:32:43 ubuntu kernel: [    8.436574] type=1505 audit(1269790362.465:4):  operation="profile_load" pid=636 name="/usr/lib/connman/scripts/dhclient-script"
Mar 28 16:32:43 ubuntu kernel: [    8.524893] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Mar 28 16:32:43 ubuntu kernel: [    8.524914] ath5k 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
Mar 28 16:32:43 ubuntu kernel: [    8.524978] ath5k 0000:01:09.0: registered as 'phy0'
Mar 28 16:32:43 ubuntu kernel: [    9.136732] [drm] radeon defaulting to kernel modesetting.
Mar 28 16:32:43 ubuntu kernel: [    9.136736] [drm] radeon kernel modesetting enabled.
Mar 28 16:32:43 ubuntu kernel: [    9.199754] r8169: eth0: link up
Mar 28 16:32:43 ubuntu kernel: [    9.204933] eth1: no link during initialization.
Mar 28 16:32:43 ubuntu kernel: [    9.206748] ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 28 16:32:43 ubuntu kernel: [    9.222375] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Mar 28 16:32:43 ubuntu kernel: [    9.222397] radeon 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Mar 28 16:32:43 ubuntu kernel: [    9.227183] [drm] radeon: Initializing kernel modesetting.
Mar 28 16:32:43 ubuntu kernel: [    9.248381] [drm] register mmio base: 0xFE2F0000
Mar 28 16:32:43 ubuntu kernel: [    9.248385] [drm] register mmio size: 65536
Mar 28 16:32:43 ubuntu kernel: [    9.248868] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
Mar 28 16:32:43 ubuntu kernel: [    9.248894] [drm] Generation 2 PCI interface, using max accessible memory
Mar 28 16:32:43 ubuntu kernel: [    9.248897] [drm] radeon: VRAM 128M
Mar 28 16:32:43 ubuntu kernel: [    9.248899] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
Mar 28 16:32:43 ubuntu kernel: [    9.248901] [drm] radeon: GTT 512M
Mar 28 16:32:43 ubuntu kernel: [    9.248903] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
Mar 28 16:32:43 ubuntu kernel: [    9.248956] [drm] radeon: using MSI.
Mar 28 16:32:43 ubuntu kernel: [    9.248991] [drm] radeon: irq initialized.
Mar 28 16:32:43 ubuntu kernel: [    9.249197] [drm] Detected VRAM RAM=128M, BAR=128M
Mar 28 16:32:43 ubuntu kernel: [    9.249202] [drm] RAM width 64bits DDR
Mar 28 16:32:43 ubuntu kernel: [    9.254661] [TTM] Zone  kernel: Available graphics memory: 1028620 kiB.
Mar 28 16:32:43 ubuntu kernel: [    9.254686] [drm] radeon: 128M of VRAM memory ready
Mar 28 16:32:43 ubuntu kernel: [    9.254688] [drm] radeon: 512M of GTT memory ready.
Mar 28 16:32:43 ubuntu kernel: [    9.254708] [drm] GART: num cpu pages 131072, num gpu pages 131072
Mar 28 16:32:43 ubuntu kernel: [    9.256812] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Mar 28 16:32:43 ubuntu kernel: [    9.256860] [drm] PCIE GART of 512M enabled (table at 0x00040000).
Mar 28 16:32:43 ubuntu kernel: [    9.256871] [drm] radeon: cp idle (0x10000C03)
Mar 28 16:32:43 ubuntu kernel: [    9.256944] [drm] Loading R300 Microcode
Mar 28 16:32:43 ubuntu kernel: [    9.256948] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
Mar 28 16:32:43 ubuntu kernel: [    9.271131] [drm] radeon: ring at 0x0000000020000000
Mar 28 16:32:43 ubuntu kernel: [    9.271154] [drm] ring test succeeded in 1 usecs
Mar 28 16:32:43 ubuntu kernel: [    9.271294] [drm] radeon: ib pool ready.
Mar 28 16:32:43 ubuntu kernel: [    9.271398] [drm] ib test succeeded in 0 usecs
Mar 28 16:32:43 ubuntu kernel: [    9.271506] [drm] Default TV standard: PAL
Mar 28 16:32:43 ubuntu kernel: [    9.271508] [drm] 27.000000000 MHz TV ref clk
Mar 28 16:32:43 ubuntu kernel: [    9.271512] [drm] DFP table revision: 4
Mar 28 16:32:43 ubuntu kernel: [    9.271564] [drm] Default TV standard: PAL
Mar 28 16:32:43 ubuntu kernel: [    9.271566] [drm] 27.000000000 MHz TV ref clk
Mar 28 16:32:43 ubuntu kernel: [    9.271595] [drm] Radeon Display Connectors
Mar 28 16:32:43 ubuntu kernel: [    9.271596] [drm] Connector 0:
Mar 28 16:32:43 ubuntu kernel: [    9.271598] [drm]   VGA
Mar 28 16:32:43 ubuntu kernel: [    9.271600] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Mar 28 16:32:43 ubuntu kernel: [    9.271602] [drm]   Encoders:
Mar 28 16:32:43 ubuntu kernel: [    9.271603] [drm]     CRT1: INTERNAL_DAC1
Mar 28 16:32:43 ubuntu kernel: [    9.271605] [drm] Connector 1:
Mar 28 16:32:43 ubuntu kernel: [    9.271606] [drm]   DVI-I
Mar 28 16:32:43 ubuntu kernel: [    9.271607] [drm]   HPD1
Mar 28 16:32:43 ubuntu kernel: [    9.271609] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Mar 28 16:32:43 ubuntu kernel: [    9.271611] [drm]   Encoders:
Mar 28 16:32:43 ubuntu kernel: [    9.271612] [drm]     CRT2: INTERNAL_DAC2
Mar 28 16:32:43 ubuntu kernel: [    9.271614] [drm]     DFP1: INTERNAL_TMDS1
Mar 28 16:32:43 ubuntu kernel: [    9.271616] [drm] Connector 2:
Mar 28 16:32:43 ubuntu kernel: [    9.271617] [drm]   S-video
Mar 28 16:32:43 ubuntu kernel: [    9.271618] [drm]   Encoders:
Mar 28 16:32:43 ubuntu kernel: [    9.271620] [drm]     TV1: INTERNAL_DAC2
Mar 28 16:32:43 ubuntu kernel: [    9.458475] type=1505 audit(1269790363.485:5):  operation="profile_replace" pid=822 name="/sbin/dhclient3"
Mar 28 16:32:43 ubuntu kernel: [    9.458780] type=1505 audit(1269790363.485:6):  operation="profile_replace" pid=822 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Mar 28 16:32:43 ubuntu kernel: [    9.480747] type=1505 audit(1269790363.515:7):  operation="profile_replace" pid=822 name="/usr/lib/connman/scripts/dhclient-script"
Mar 28 16:32:43 ubuntu kernel: [    9.493750] type=1505 audit(1269790363.525:8):  operation="profile_load" pid=825 name="/usr/sbin/mysqld"
Mar 28 16:32:43 ubuntu kernel: [    9.499108] type=1505 audit(1269790363.525:9):  operation="profile_load" pid=827 name="/usr/sbin/tcpdump"
Mar 28 16:32:43 ubuntu kernel: [    9.793238] [drm] fb mappable at 0xD80C0000
Mar 28 16:32:43 ubuntu kernel: [    9.793242] [drm] vram apper at 0xD8000000
Mar 28 16:32:43 ubuntu kernel: [    9.793244] [drm] size 4177920
Mar 28 16:32:43 ubuntu kernel: [    9.793245] [drm] fb depth is 24
Mar 28 16:32:43 ubuntu kernel: [    9.793247] [drm]    pitch is 5440
Mar 28 16:32:43 ubuntu kernel: [    9.793345] fb0: radeondrmfb frame buffer device
Mar 28 16:32:43 ubuntu kernel: [    9.793346] registered panic notifier
Mar 28 16:32:43 ubuntu kernel: [    9.793352] [drm] Initialized radeon 2.0.0 20080528 for 0000:05:00.0 on minor 0
Mar 28 16:32:43 ubuntu kernel: [    9.795543] vga16fb: mapped to 0xffff8800000a0000
Mar 28 16:32:43 ubuntu kernel: [    9.795613] fb1: VGA16 VGA frame buffer device
Mar 28 16:32:43 ubuntu kernel: [    9.871888] Console: switching to colour frame buffer device 170x48
Mar 28 16:32:43 ubuntu kernel: [   10.215348] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
Mar 28 16:32:43 ubuntu kernel: [   10.215523] cfg80211: Calling CRDA for country: US
Mar 28 16:32:43 ubuntu kernel: [   10.222140] cfg80211: Regulatory domain changed to country: US
Mar 28 16:32:43 ubuntu kernel: [   10.222143] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 28 16:32:43 ubuntu kernel: [   10.222146] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Mar 28 16:32:43 ubuntu kernel: [   10.222149] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Mar 28 16:32:43 ubuntu kernel: [   10.222152] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 28 16:32:43 ubuntu kernel: [   10.222154] 	(5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 28 16:32:43 ubuntu kernel: [   10.222157] 	(5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 28 16:32:43 ubuntu kernel: [   10.222159] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Mar 28 16:32:43 ubuntu kernel: [   10.223284] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Mar 28 16:32:43 ubuntu kernel: [   10.223306] C-Media PCI 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
Mar 28 16:33:44 ubuntu kernel: [   70.640027] Clocksource tsc unstable (delta = -119967996 ns)


```

---

### Post by da1337ninja on 2010-03-28
So, is there anything i can do to fix this? Or do I just have to reinstall?

---

### Post by Dr Goldberg on 2010-03-31
I am since many years a happy newbie on Ubuntu and Linux.  I recently changed my fourth computer to Ubuntu from XP.

This time I had same problem with fsck at startup after the first (huge) update on my otherwise completely fresh 9.10 installation. The update was performed over wireless. I then re-installed the hole thing, but this time I updated over wireline. It worked flawlessly. 

If you did your last update over wireless, maybe one solution is to somehow, revert back your latest updates, and then redo them over wireline.

---

### Post by Goatrancer on 2010-05-05
Im having similar issues, with 9.10 on an Acer AspireOne.
I restarted after trying to restart my mouse via the terminal, and I think there have been some updates since the last restart.

the message I get on startup is:

```
fcsk from util-linux-ng 2.16
/dev/sda1: clean, 231509/14901248 files, 6897183/59289093 blocks (check in 5 mounts
```

followed by a blinking cursor which responds to input, indicating that it is not frozen.
I will try making a live USB and booting from it and report what happens.
edit: this happens in both regular and recovery mode.

---

### Post by Goatrancer on 2010-05-05
And to make matters worse the computer does not go into hibernate when closed. I closed the lid in frustration, packed up and went home. Opened my backpack just now to find a burning hot computer. I hope it's ok :o

---

### Post by quixote on 2010-05-05
Yeah.  Just packing an "on" computer is a bad idea.  Force it by holding down the off button for five seconds if you have to, but don't pack it "on."

As to what's going on: ???

---

### Post by Goatrancer on 2010-05-08
Well the computer seems to have survived, but I got tired of trying to figure thus business out and just said screw it and reformatted my hard drive and installed lucid. Now regretting that decision since I had just gotten everything working in karmic and now Im going through the agony of a new release and the bugs that come with it.

---

