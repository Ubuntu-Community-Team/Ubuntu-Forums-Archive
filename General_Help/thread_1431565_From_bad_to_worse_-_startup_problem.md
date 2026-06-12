---
title: "From bad to worse - startup problem"
date: 2010-03-16
forum: General Help
---

### Post by kanolsen on 2010-03-16
My 9.10 desktop failed in startup, first it stopped in NTP, and in recovery it stops at Starting Samba daemon.

I tried the following:
[SIZE="4"]1.[/SIZE] Restart with alternative kernel, and recovery mode - didn't get to the desktop. 

[SIZE="4"]2[/SIZE] sudo -i
mkdir /media/root
mount /dev/sda1 /media/root 
cd /media/root
for f in sys dev proc ; do mount -o bind /$f $f; done
chroot .
aptitude clean
aptitude update
aptitude full-upgrade -f
dpkg-reconfigure xserver-xorg
apt-get remove ntpdate

after this I didn't get the NTP stop, but now it stops at starting samba daemon. 

[SIZE="4"]3[/SIZE] Tried dpkg-reconfigure samba
set it up accordingly: * How do you want to run Samba? (Answer: daemons)
* Create samba password database? (Answer: Yes)

[SIZE="4"]4[/SIZE]  Tried: sudo mkdir /mnt/repair 

sudo mount /dev/sda1 /mnt/repair 

sudo chroot /mnt/repair su 

sudo apt-get update
sudo apt-get upgrade 
sudo aptitude upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get upgrade

Still I can't get it to work. I get just past the first ubuntu logo, and now I get a black screen with the cursor blinking seldom in the corner.

What else can I try?

Thanks in advance for taking the time.
Kanolsen

---

### Post by prodigy_ on 2010-03-16
So you can still boot, but GUI doesn't show - is this correct?

If so, try [reinstalling gdm](http://ubuntuforums.org/showpost.php?p=8973750&postcount=6).

---

### Post by soltanis on 2010-03-16
I think his problem is system hanging while upstart/init is starting up the daemons.

You could either choose to continually remove/reinstall them (by removing Samba), or perhaps just reinstall altogether and see if that fixes the problem.

By the way, what kind of system is this running on? Have you ever used Linux on it and has it had difficulties in the past?

---

### Post by kanolsen on 2010-03-16
Thanks for a quick reply. 
I am running ubuntu 9.10 desktop.

I can't get to a terminal, have to load a liveCD to work on it. It's just black screen. 
Started suddenly overnight after I installed some applications ([check link]("http://ubuntuforums.org/showthread.php?p=8973418#post8973418")), and got the NTP hang situation, but after I've tried to fix it, it's just has become worse!
It's just Ubuntu on it, and it's a relative fresh install (2months old)
Kanolsen

---

### Post by soltanis on 2010-03-16
If the liveCD works its safe to assume you're not Linux-allergic. NTP is not that important, it just syncs your computer to network time. But if you don't have an Internet connection (or if it is faulty) then that might be why it "hangs" (it's trying to get a connection). This would also happen if you are trying to get it to reach a server that is down.

I don't have a theory on why Samba is doing this as well. Unresponsive network programs usually point to DNS problems, though, can you reach the Internet when you boot into liveCD?

---

### Post by kanolsen on 2010-03-16
Yes, I have access to the Internet from all of my computers, including the problem child, when using the liveCD. until my last attempts I could also get access to the Ubuntu computer from my other computers, but not any more. 
I have uninstalled ntpdate, so that should not be an issue any longer. But still it won't work. 

Kanolsen

---

### Post by prodigy_ on 2010-03-16
I'd check logs, starting with **/var/log/syslog**. Because neither ntpd nor Samba by themselves can't completely stop system from booting (unless they're broken and trying to do something very wrong). At the very least you should be able to access CLI (for example, with Ctrl+Alt+F1).

---

### Post by soltanis on 2010-03-16
Really odd. Yeah, check the logs for more clues, because as is there's no way to pin down the problem short of the broad-spectrum strategy which is just reinstalling.

---

### Post by kanolsen on 2010-03-17
I'll check the logs and see, but I have tried CTRL-ALT-F1, but nothing happens at all, can&#7831; get to a terminal no matter what I do. 

Kanolsen

---

### Post by soltanis on 2010-03-17
I suggest you mount your drive from a live CD then look at the relevant log files.

---

### Post by prodigy_ on 2010-03-17
> **kanolsen said:**
> I'll check the logs
Just make sure that you're looking at the right logs. Mount your HDD partitions and use chroot.

---

### Post by kanolsen on 2010-03-17
I have started from a livecd, and looking at /var/log/syslog it was nothing which stands out for me, but then again I'm not that into dechiffering logfiles. But if anyone see something wring in it here is the /var/log/syslog

Mar 17 07:06:14 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="651" x-info="http://www.rsyslog.com"] (re)start
Mar 17 07:06:14 ubuntu rsyslogd: rsyslogd's groupid changed to 102
Mar 17 07:06:14 ubuntu rsyslogd: rsyslogd's userid changed to 101
Mar 17 07:06:14 ubuntu udev-configure-printer: add /devices/pnp0/00:0a/printer/lp0
Mar 17 07:06:14 ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 17 07:06:14 ubuntu udev-configure-printer: Failed to get parent
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Mar 17 07:06:14 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] DMI 2.2 present.
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Mar 17 07:06:14 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] last_pfn = 0x5fff0 max_arch_pfn = 0x100000
Mar 17 07:06:14 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Mar 17 07:06:14 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   C0000-CCFFF write-protect
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   CD000-FFFFF uncachable
Mar 17 07:06:14 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   1 base 040000000 mask FE0000000 write-back
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   2 base 0E0000000 mask FFC000000 write-combining
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   3 disabled
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   4 disabled
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   5 disabled
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   6 disabled
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   7 disabled
Mar 17 07:06:14 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Mar 17 07:06:14 ubuntu kernel: [    0.000000] modified physical RAM map:
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000005fff0000 (usable)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  modified: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  modified: 000000005fff3000 - 0000000060000000 (ACPI data)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Mar 17 07:06:14 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Mar 17 07:06:14 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Mar 17 07:06:14 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
Mar 17 07:06:14 ubuntu kernel: [    0.000000] RAMDISK: 378a1000 - 37fef93d
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 008b2000 - 0100093d
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Move RAMDISK from 00000000378a1000 - 0000000037fef93c to 008b2000 - 0100093c
Mar 17 07:06:14 ubuntu kernel: [    0.000000] ACPI: RSDP 000f7170 00014 (v00 AWARD )
Mar 17 07:06:14 ubuntu kernel: [    0.000000] ACPI: RSDT 5fff3000 00028 (v01 AWARD  AWRDACPI 42302E31 AWRD 00000000)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] ACPI: FACP 5fff3040 00074 (v01 AWARD  AWRDACPI 42302E31 AWRD 00000000)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] ACPI: DSDT 5fff30c0 036C2 (v01 AWARD  AWRDACPI 00001000 MSFT 0100000D)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] ACPI: FACS 5fff0000 00040
Mar 17 07:06:14 ubuntu kernel: [    0.000000] 647MB HIGHMEM available.
Mar 17 07:06:14 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Mar 17 07:06:14 ubuntu avahi-daemon[692]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Mar 17 07:06:14 ubuntu avahi-daemon[692]: Successfully dropped root privileges.
Mar 17 07:06:14 ubuntu avahi-daemon[692]: avahi-daemon 0.6.25 starting up.
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Mar 17 07:06:14 ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   #5 [00008ae000 - 00008b10a6]              BRK ==> [00008ae000 - 00008b10a6]
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   #7 [00008b2000 - 000100093d]      NEW RAMDISK ==> [00008b2000 - 000100093d]
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x0005fff0
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 17 07:06:14 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar 17 07:06:14 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar 17 07:06:14 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0005fff0
Mar 17 07:06:14 ubuntu kernel: [    0.000000] On node 0 totalpages: 393087
Mar 17 07:06:14 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c1001200
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   HighMem zone: 1296 pages used for memmap
Mar 17 07:06:14 ubuntu kernel: [    0.000000]   HighMem zone: 164578 pages, LIFO batch:31
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Using APIC driver default
Mar 17 07:06:14 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Mar 17 07:06:14 ubuntu kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Mar 17 07:06:14 ubuntu kernel: [    0.000000] APIC: disable apic facility
Mar 17 07:06:14 ubuntu NetworkManager: <info>  starting...
Mar 17 07:06:14 ubuntu avahi-daemon[692]: Successfully called chroot().
Mar 17 07:06:14 ubuntu avahi-daemon[692]: Successfully dropped remaining capabilities.
Mar 17 07:06:14 ubuntu kernel: [    0.000000] nr_irqs_gsi: 16
Mar 17 07:06:14 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 17 07:06:14 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Mar 17 07:06:14 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:9ec00000)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Mar 17 07:06:14 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages at c1c08000, static data 35612 bytes
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390015
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=8fd8abea-0804-41a2-9724-90f88ea19b30 ro single
Mar 17 07:06:14 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Initializing CPU#0
Mar 17 07:06:14 ubuntu kernel: [    0.000000] allocated 7863680 bytes of page_cgroup
Mar 17 07:06:14 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0005fff0)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Memory: 1535264k/1572800k available (4578k kernel code, 36228k reserved, 2146k data, 540k init, 663496k highmem)
Mar 17 07:06:14 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Mar 17 07:06:14 ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
Mar 17 07:06:14 ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
Mar 17 07:06:14 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 17 07:06:14 ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Mar 17 07:06:14 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Mar 17 07:06:14 ubuntu kernel: [    0.000000] Detected 2672.487 MHz processor.
Mar 17 07:06:14 ubuntu kernel: [    0.001726] Console: colour VGA+ 80x25
Mar 17 07:06:14 ubuntu kernel: [    0.001732] console [tty0] enabled
Mar 17 07:06:14 ubuntu kernel: [    0.004021] Calibrating delay loop (skipped), value calculated using timer frequency.. 5344.97 BogoMIPS (lpj=10689948)
Mar 17 07:06:14 ubuntu kernel: [    0.004172] Security Framework initialized
Mar 17 07:06:14 ubuntu kernel: [    0.004286] AppArmor: AppArmor initialized
Mar 17 07:06:14 ubuntu kernel: [    0.004355] Mount-cache hash table entries: 512
Mar 17 07:06:14 ubuntu kernel: [    0.004682] Initializing cgroup subsys ns
Mar 17 07:06:14 ubuntu kernel: [    0.004749] Initializing cgroup subsys cpuacct
Mar 17 07:06:14 ubuntu kernel: [    0.004809] Initializing cgroup subsys memory
Mar 17 07:06:14 ubuntu kernel: [    0.004878] Initializing cgroup subsys freezer
Mar 17 07:06:14 ubuntu kernel: [    0.004936] Initializing cgroup subsys net_cls
Mar 17 07:06:14 ubuntu kernel: [    0.005023] CPU: Trace cache: 12K uops, L1 D cache: 8K
Mar 17 07:06:14 ubuntu kernel: [    0.005125] CPU: L2 cache: 512K
Mar 17 07:06:14 ubuntu kernel: [    0.005181] CPU: Hyper-Threading is disabled
Mar 17 07:06:14 ubuntu kernel: [    0.005242] mce: CPU supports 4 MCE banks
Mar 17 07:06:14 ubuntu kernel: [    0.005310] ------------[ cut here ]------------
Mar 17 07:06:14 ubuntu kernel: [    0.005393] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/apic/apic.c:247 native_apic_write_dummy+0x33/0x40()
Mar 17 07:06:14 ubuntu kernel: [    0.005463] Hardware name:  
Mar 17 07:06:14 ubuntu kernel: [    0.005519] Modules linked in:
Mar 17 07:06:14 ubuntu kernel: [    0.005620] Pid: 0, comm: swapper Not tainted 2.6.31-20-generic #58-Ubuntu
Mar 17 07:06:14 ubuntu kernel: [    0.005679] Call Trace:
Mar 17 07:06:14 ubuntu kernel: [    0.005750]  [<c01450ad>] warn_slowpath_common+0x6d/0xa0
Mar 17 07:06:14 ubuntu kernel: [    0.005810]  [<c011d713>] ? native_apic_write_dummy+0x33/0x40
Mar 17 07:06:14 ubuntu kernel: [    0.005870]  [<c011d713>] ? native_apic_write_dummy+0x33/0x40
Mar 17 07:06:14 ubuntu kernel: [    0.005930]  [<c01450f5>] warn_slowpath_null+0x15/0x20
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Mar 17 07:06:14 ubuntu NetworkManager:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Mar 17 07:06:14 ubuntu avahi-daemon[692]: No service file found in /etc/avahi/services.
Mar 17 07:06:14 ubuntu avahi-daemon[692]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.0.10.
Mar 17 07:06:14 ubuntu avahi-daemon[692]: New relevant interface eth0.IPv4 for mDNS.
Mar 17 07:06:14 ubuntu kernel: [    0.005990]  [<c011d713>] native_apic_write_dummy+0x33/0x40
Mar 17 07:06:14 ubuntu kernel: [    0.006054]  [<c0112707>] intel_init_thermal+0x67/0x1b0
Mar 17 07:06:14 ubuntu kernel: [    0.006114]  [<c0111d7b>] mce_intel_feature_init+0xb/0x60
Mar 17 07:06:14 ubuntu avahi-daemon[692]: Network interface enumeration completed.
Mar 17 07:06:14 ubuntu kernel: [    0.006173]  [<c010fcb0>] mce_cpu_features+0x10/0x40
Mar 17 07:06:14 ubuntu kernel: [    0.006241]  [<c056e03c>] mcheck_init+0x14a/0x188
Mar 17 07:06:14 ubuntu kernel: [    0.006300]  [<c056c488>] ? init_hypervisor+0xb/0x2c
Mar 17 07:06:14 ubuntu kernel: [    0.006359]  [<c056c440>] identify_cpu+0x20e/0x21d
Mar 17 07:06:14 ubuntu kernel: [    0.006425]  [<c079972a>] identify_boot_cpu+0xd/0x23
Mar 17 07:06:14 ubuntu kernel: [    0.006484]  [<c07998c0>] check_bugs+0xb/0xe9
Mar 17 07:06:14 ubuntu avahi-daemon[692]: Registering new address record for fe80::230:1bff:fe29:47f0 on eth0.*.
Mar 17 07:06:14 ubuntu kernel: [    0.006542]  [<c07928b6>] start_kernel+0x2dc/0x2ec
Mar 17 07:06:14 ubuntu kernel: [    0.006601]  [<c0792406>] ? unknown_bootoption+0x0/0x19e
Mar 17 07:06:14 ubuntu avahi-daemon[692]: Registering new address record for 10.0.0.10 on eth0.IPv4.
Mar 17 07:06:14 ubuntu kernel: [    0.006666]  [<c079207c>] i386_start_kernel+0x7c/0x83
Mar 17 07:06:14 ubuntu avahi-daemon[692]: Registering HINFO record with values 'I686'/'LINUX'.
Mar 17 07:06:14 ubuntu kernel: [    0.006734] ---[ end trace a7919e7f17c0a725 ]---
Mar 17 07:06:14 ubuntu kernel: [    0.006793] CPU0: Thermal monitoring enabled (TM1)
Mar 17 07:06:14 ubuntu kernel: [    0.006870] Performance Counters: no PMU driver, software counters only.
Mar 17 07:06:14 ubuntu kernel: [    0.006981] Checking 'hlt' instruction... OK.
Mar 17 07:06:14 ubuntu kernel: [    0.021148] SMP alternatives: switching to UP code
Mar 17 07:06:14 ubuntu kernel: [    0.032048] Freeing SMP alternatives: 20k freed
Mar 17 07:06:14 ubuntu kernel: [    0.032165] ACPI: Core revision 20090521
Mar 17 07:06:14 ubuntu kernel: [    0.041379] ACPI: setting ELCR to 0200 (from 1e20)
Mar 17 07:06:14 ubuntu kernel: [    0.042930] weird, boot CPU (#0) not listed by the BIOS.
Mar 17 07:06:14 ubuntu kernel: [    0.042988] SMP motherboard not detected.
Mar 17 07:06:14 ubuntu kernel: [    0.043044] Local APIC not detected. Using dummy APIC emulation.
Mar 17 07:06:14 ubuntu kernel: [    0.043101] SMP disabled
Mar 17 07:06:14 ubuntu kernel: [    0.043485] Brought up 1 CPUs
Mar 17 07:06:14 ubuntu kernel: [    0.043546] Total of 1 processors activated (5344.97 BogoMIPS).
Mar 17 07:06:14 ubuntu kernel: [    0.043621] CPU0 attaching NULL sched-domain.
Mar 17 07:06:14 ubuntu kernel: [    0.043991] Booting paravirtualized kernel on bare hardware
Mar 17 07:06:14 ubuntu kernel: [    0.044298] regulator: core version 0.5
Mar 17 07:06:14 ubuntu kernel: [    0.044382] Time:  6:06:05  Date: 03/17/10
Mar 17 07:06:14 ubuntu kernel: [    0.044524] NET: Registered protocol family 16
Mar 17 07:06:14 ubuntu kernel: [    0.044786] EISA bus registered
Mar 17 07:06:14 ubuntu kernel: [    0.044866] ACPI: bus type pci registered
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin Option High-Speed
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin Sierra
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin Option
Mar 17 07:06:14 ubuntu kernel: [    0.057205] PCI: PCI BIOS revision 2.10 entry at 0xfb7f0, last bus=1
Mar 17 07:06:14 ubuntu kernel: [    0.057265] PCI: Using configuration type 1 for base access
Mar 17 07:06:14 ubuntu kernel: [    0.058627] bio: create slab <bio-0> at 0
Mar 17 07:06:14 ubuntu kernel: [    0.059371] ACPI: EC: Look up EC in DSDT
Mar 17 07:06:14 ubuntu kernel: [    0.065433] ACPI: Interpreter enabled
Mar 17 07:06:14 ubuntu kernel: [    0.065501] ACPI: (supports S0 S1 S4 S5)
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin Gobi
Mar 17 07:06:14 ubuntu kernel: [    0.065750] ACPI: Using PIC for interrupt routing
Mar 17 07:06:14 ubuntu kernel: [    0.070678] ACPI: No dock devices found.
Mar 17 07:06:14 ubuntu kernel: [    0.070879] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 17 07:06:14 ubuntu kernel: [    0.071004] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
Mar 17 07:06:14 ubuntu kernel: [    0.071182] pci 0000:00:02.0: Enabling SiS 96x SMBus
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin ZTE
Mar 17 07:06:14 ubuntu kernel: [    0.071294] pci 0000:00:02.1: reg 20 io port: [0x10c0-0x10df]
Mar 17 07:06:14 ubuntu kernel: [    0.071359] pci 0000:00:02.5: reg 10 io port: [0x1f0-0x1f7]
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin Ericsson MBM
Mar 17 07:06:14 ubuntu kernel: [    0.071368] pci 0000:00:02.5: reg 14 io port: [0x3f4-0x3f7]
Mar 17 07:06:14 ubuntu kernel: [    0.071376] pci 0000:00:02.5: reg 18 io port: [0x170-0x177]
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin Generic
Mar 17 07:06:14 ubuntu kernel: [    0.071385] pci 0000:00:02.5: reg 1c io port: [0x374-0x377]
Mar 17 07:06:14 ubuntu kernel: [    0.071393] pci 0000:00:02.5: reg 20 io port: [0x4000-0x400f]
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin Nokia
Mar 17 07:06:14 ubuntu kernel: [    0.071429] pci 0000:00:02.5: PME# supported from D3cold
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin Novatel
Mar 17 07:06:14 ubuntu kernel: [    0.071489] pci 0000:00:02.5: PME# disabled
Mar 17 07:06:14 ubuntu kernel: [    0.071587] pci 0000:00:02.7: reg 10 io port: [0xc000-0xc0ff]
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin Huawei
Mar 17 07:06:14 ubuntu kernel: [    0.071596] pci 0000:00:02.7: reg 14 io port: [0xc400-0xc47f]
Mar 17 07:06:14 ubuntu kernel: [    0.071648] pci 0000:00:02.7: supports D1 D2
Mar 17 07:06:14 ubuntu modem-manager: Loaded plugin MotoC
Mar 17 07:06:14 ubuntu kernel: [    0.071651] pci 0000:00:02.7: PME# supported from D3hot D3cold
Mar 17 07:06:14 ubuntu kernel: [    0.071710] pci 0000:00:02.7: PME# disabled
Mar 17 07:06:14 ubuntu kernel: [    0.071795] pci 0000:00:03.0: reg 10 32bit mmio: [0xe8004000-0xe8004fff]
Mar 17 07:06:14 ubuntu kernel: [    0.071861] pci 0000:00:03.1: reg 10 32bit mmio: [0xe8000000-0xe8000fff]
Mar 17 07:06:14 ubuntu kernel: [    0.071928] pci 0000:00:03.2: reg 10 32bit mmio: [0xe8001000-0xe8001fff]
Mar 17 07:06:14 ubuntu kernel: [    0.072029] pci 0000:00:03.3: reg 10 32bit mmio: [0xe8002000-0xe8002fff]
Mar 17 07:06:14 ubuntu kernel: [    0.072086] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
Mar 17 07:06:14 ubuntu kernel: [    0.072148] pci 0000:00:03.3: PME# disabled
Mar 17 07:06:14 ubuntu kernel: [    0.072261] pci 0000:00:0a.0: reg 10 io port: [0xc800-0xc807]
Mar 17 07:06:14 ubuntu kernel: [    0.072270] pci 0000:00:0a.0: reg 14 io port: [0xcc00-0xcc03]
Mar 17 07:06:14 ubuntu kernel: [    0.072278] pci 0000:00:0a.0: reg 18 io port: [0xd000-0xd007]
Mar 17 07:06:14 ubuntu kernel: [    0.072286] pci 0000:00:0a.0: reg 1c io port: [0xd400-0xd403]
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: addresses count: 1
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: No dns-nameserver configured in /etc/network/interfaces
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: autoconnect
Mar 17 07:06:14 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0f.0/net/eth0, iface: eth0)
Mar 17 07:06:14 ubuntu NetworkManager:    SCPluginIfupdown: locking wired connection setting
Mar 17 07:06:14 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 1
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: (140270320) ... get_connections.
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: (140270320) ... get_connections (managed=false): return empty list.
Mar 17 07:06:14 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 1
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 17 07:06:14 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Mar 17 07:06:14 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 17 07:06:14 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 17 07:06:14 ubuntu kernel: [    0.072295] pci 0000:00:0a.0: reg 20 io port: [0xd800-0xd80f]
Mar 17 07:06:14 ubuntu kernel: [    0.072304] pci 0000:00:0a.0: reg 24 32bit mmio: [0xe8003000-0xe80031ff]
Mar 17 07:06:14 ubuntu kernel: [    0.072312] pci 0000:00:0a.0: reg 30 32bit mmio: [0x000000-0x07ffff]
Mar 17 07:06:14 ubuntu kernel: [    0.072335] pci 0000:00:0a.0: supports D1 D2
Mar 17 07:06:14 ubuntu kernel: [    0.072385] pci 0000:00:0f.0: reg 10 io port: [0xdc00-0xdcff]
Mar 17 07:06:14 ubuntu kernel: [    0.072394] pci 0000:00:0f.0: reg 14 32bit mmio: [0xe8005000-0xe80050ff]
Mar 17 07:06:14 ubuntu kernel: [    0.072446] pci 0000:00:0f.0: supports D1 D2
Mar 17 07:06:14 ubuntu kernel: [    0.072449] pci 0000:00:0f.0: PME# supported from D1 D2 D3hot D3cold
Mar 17 07:06:14 ubuntu kernel: [    0.073597] pci 0000:00:0f.0: PME# disabled
Mar 17 07:06:14 ubuntu kernel: [    0.073695] pci 0000:00:10.0: reg 10 32bit mmio: [0xe8006000-0xe80067ff]
Mar 17 07:06:14 ubuntu kernel: [    0.073704] pci 0000:00:10.0: reg 14 io port: [0xe000-0xe07f]
Mar 17 07:06:14 ubuntu kernel: [    0.073758] pci 0000:00:10.0: supports D2
Mar 17 07:06:14 ubuntu kernel: [    0.073760] pci 0000:00:10.0: PME# supported from D2 D3hot D3cold
Mar 17 07:06:14 ubuntu kernel: [    0.073820] pci 0000:00:10.0: PME# disabled
Mar 17 07:06:14 ubuntu kernel: [    0.073957] pci 0000:01:00.0: reg 10 32bit mmio: [0xe4000000-0xe4ffffff]
Mar 17 07:06:14 ubuntu kernel: [    0.073967] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xdfffffff]
Mar 17 07:06:14 ubuntu kernel: [    0.073975] pci 0000:01:00.0: reg 18 32bit mmio: [0xe5000000-0xe5ffffff]
Mar 17 07:06:14 ubuntu kernel: [    0.073999] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
Mar 17 07:06:14 ubuntu kernel: [    0.074074] pci 0000:00:01.0: bridge 32bit mmio: [0xe4000000-0xe6ffffff]
Mar 17 07:06:14 ubuntu kernel: [    0.074080] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
Mar 17 07:06:14 ubuntu kernel: [    0.074091] pci_bus 0000:00: on NUMA node 0
Mar 17 07:06:14 ubuntu kernel: [    0.074097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 17 07:06:14 ubuntu kernel: [    0.096546] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
Mar 17 07:06:14 ubuntu kernel: [    0.097283] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Mar 17 07:06:14 ubuntu kernel: [    0.098012] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Mar 17 07:06:14 ubuntu kernel: [    0.098740] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Mar 17 07:06:14 ubuntu kernel: [    0.099469] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
Mar 17 07:06:14 ubuntu kernel: [    0.100173] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Mar 17 07:06:14 ubuntu kernel: [    0.100900] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Mar 17 07:06:14 ubuntu kernel: [    0.101628] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Mar 17 07:06:14 ubuntu kernel: [    0.102532] SCSI subsystem initialized
Mar 17 07:06:14 ubuntu kernel: [    0.102726] libata version 3.00 loaded.
Mar 17 07:06:14 ubuntu kernel: [    0.102847] usbcore: registered new interface driver usbfs
Mar 17 07:06:14 ubuntu kernel: [    0.102923] usbcore: registered new interface driver hub
Mar 17 07:06:14 ubuntu kernel: [    0.103013] usbcore: registered new device driver usb
Mar 17 07:06:14 ubuntu kernel: [    0.103265] ACPI: WMI: Mapper loaded
Mar 17 07:06:14 ubuntu kernel: [    0.103322] PCI: Using ACPI for IRQ routing
Mar 17 07:06:14 ubuntu kernel: [    0.103593] Bluetooth: Core ver 2.15
Mar 17 07:06:14 ubuntu kernel: [    0.103699] NET: Registered protocol family 31
Mar 17 07:06:14 ubuntu kernel: [    0.103756] Bluetooth: HCI device and connection manager initialized
Mar 17 07:06:14 ubuntu kernel: [    0.103816] Bluetooth: HCI socket layer initialized
Mar 17 07:06:14 ubuntu kernel: [    0.103872] NetLabel: Initializing
Mar 17 07:06:14 ubuntu kernel: [    0.103927] NetLabel:  domain hash size = 128
Mar 17 07:06:14 ubuntu kernel: [    0.104011] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 17 07:06:14 ubuntu kernel: [    0.104086] NetLabel:  unlabeled traffic allowed by default
Mar 17 07:06:14 ubuntu kernel: [    0.106890] pnp: PnP ACPI init
Mar 17 07:06:14 ubuntu kernel: [    0.107021] ACPI: bus type pnp registered
Mar 17 07:06:14 ubuntu kernel: [    0.110947] pnp: PnP ACPI: found 12 devices
Mar 17 07:06:14 ubuntu kernel: [    0.111009] ACPI: ACPI bus type pnp unregistered
Mar 17 07:06:14 ubuntu kernel: [    0.111069] PnPBIOS: Disabled by ACPI PNP
Mar 17 07:06:14 ubuntu kernel: [    0.111148] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Mar 17 07:06:14 ubuntu kernel: [    0.111207] system 00:02: ioport range 0x800-0x805 has been reserved
Mar 17 07:06:14 ubuntu NetworkManager: <info>  Wireless now enabled by radio killswitch
Mar 17 07:06:14 ubuntu NetworkManager: <info>  (eth0): carrier is ON
Mar 17 07:06:14 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too')
Mar 17 07:06:14 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar 17 07:06:14 ubuntu kernel: [    0.111266] system 00:02: ioport range 0x290-0x297 has been reserved
Mar 17 07:06:14 ubuntu kernel: [    0.146099] AppArmor: AppArmor Filesystem Enabled
Mar 17 07:06:14 ubuntu kernel: [    0.146202] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Mar 17 07:06:14 ubuntu kernel: [    0.146260] pci 0000:00:01.0:   IO window: disabled
Mar 17 07:06:14 ubuntu kernel: [    0.146322] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe6ffffff
Mar 17 07:06:14 ubuntu kernel: [    0.146382] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
Mar 17 07:06:14 ubuntu kernel: [    0.146462] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Mar 17 07:06:14 ubuntu kernel: [    0.146465] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Mar 17 07:06:14 ubuntu kernel: [    0.146469] pci_bus 0000:01: resource 1 mem: [0xe4000000-0xe6ffffff]
Mar 17 07:06:14 ubuntu kernel: [    0.146472] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
Mar 17 07:06:14 ubuntu kernel: [    0.146537] NET: Registered protocol family 2
Mar 17 07:06:14 ubuntu kernel: [    0.146733] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 17 07:06:14 ubuntu kernel: [    0.147345] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 17 07:06:14 ubuntu kernel: [    0.149168] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 17 07:06:14 ubuntu kernel: [    0.150283] TCP: Hash tables configured (established 131072 bind 65536)
Mar 17 07:06:14 ubuntu kernel: [    0.150354] TCP reno registered
Mar 17 07:06:14 ubuntu kernel: [    0.150694] NET: Registered protocol family 1
Mar 17 07:06:14 ubuntu kernel: [    0.150915] Trying to unpack rootfs image as initramfs...
Mar 17 07:06:14 ubuntu kernel: [    0.412083] Freeing initrd memory: 7482k freed
Mar 17 07:06:14 ubuntu kernel: [    0.426969] cpufreq-nforce2: No nForce2 chipset.
Mar 17 07:06:14 ubuntu kernel: [    0.427081] Scanning for low memory corruption every 60 seconds
Mar 17 07:06:14 ubuntu kernel: [    0.427363] audit: initializing netlink socket (disabled)
Mar 17 07:06:14 ubuntu kernel: [    0.427463] type=2000 audit(1268805965.424:1): initialized
Mar 17 07:06:14 ubuntu kernel: [    0.436164] highmem bounce pool size: 64 pages
Mar 17 07:06:14 ubuntu kernel: [    0.436237] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar 17 07:06:14 ubuntu kernel: [    0.437943] VFS: Disk quotas dquot_6.5.2
Mar 17 07:06:14 ubuntu kernel: [    0.438077] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 17 07:06:14 ubuntu kernel: [    0.438862] fuse init (API version 7.12)
Mar 17 07:06:14 ubuntu kernel: [    0.439027] msgmni has been set to 1719
Mar 17 07:06:14 ubuntu kernel: [    0.439406] alg: No test for stdrng (krng)
Mar 17 07:06:14 ubuntu kernel: [    0.439483] io scheduler noop registered
Mar 17 07:06:14 ubuntu kernel: [    0.439539] io scheduler anticipatory registered
Mar 17 07:06:14 ubuntu kernel: [    0.439594] io scheduler deadline registered
Mar 17 07:06:14 ubuntu kernel: [    0.439713] io scheduler cfq registered (default)
Mar 17 07:06:14 ubuntu kernel: [    0.524081] pci 0000:01:00.0: Boot video device
Mar 17 07:06:14 ubuntu kernel: [    0.524220] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 17 07:06:14 ubuntu kernel: [    0.524313] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar 17 07:06:14 ubuntu kernel: [    0.524558] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Mar 17 07:06:14 ubuntu kernel: [    0.524630] ACPI: Power Button [PWRF]
Mar 17 07:06:14 ubuntu kernel: [    0.524748] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Mar 17 07:06:14 ubuntu kernel: [    0.524815] ACPI: Power Button [PWRB]
Mar 17 07:06:14 ubuntu kernel: [    0.524929] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Mar 17 07:06:14 ubuntu kernel: [    0.525002] ACPI: Sleep Button [FUTS]
Mar 17 07:06:14 ubuntu kernel: [    0.525119] fan PNP0C0B:00: registered as cooling_device0
Mar 17 07:06:14 ubuntu kernel: [    0.525181] ACPI: Fan [FAN] (on)
Mar 17 07:06:14 ubuntu kernel: [    0.525500] processor LNXCPU:00: registered as cooling_device1
Mar 17 07:06:14 ubuntu kernel: [    0.528079] thermal LNXTHERM:01: registered as thermal_zone0
Mar 17 07:06:14 ubuntu kernel: [    0.528149] ACPI: Thermal Zone [THRM] (37 C)
Mar 17 07:06:14 ubuntu kernel: [    0.528270] isapnp: Scanning for PnP cards...
Mar 17 07:06:14 ubuntu kernel: [    0.676085] Switched to high resolution mode on CPU 0
Mar 17 07:06:14 ubuntu kernel: [    0.882175] isapnp: No Plug & Play device found
Mar 17 07:06:14 ubuntu kernel: [    0.883652] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar 17 07:06:14 ubuntu kernel: [    0.883860] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 17 07:06:14 ubuntu kernel: [    0.884057] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Mar 17 07:06:14 ubuntu kernel: [    0.884476] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 17 07:06:14 ubuntu kernel: [    0.884671] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Mar 17 07:06:14 ubuntu kernel: [    0.886001] brd: module loaded
Mar 17 07:06:14 ubuntu kernel: [    0.886620] loop: module loaded
Mar 17 07:06:14 ubuntu kernel: [    0.886817] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Mar 17 07:06:14 ubuntu kernel: [    0.887085] sata_sil 0000:00:0a.0: version 2.4
Mar 17 07:06:14 ubuntu kernel: [    0.887431] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Mar 17 07:06:14 ubuntu kernel: [    0.887492] PCI: setting IRQ 11 as level-triggered
Mar 17 07:06:14 ubuntu kernel: [    0.887497] sata_sil 0000:00:0a.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Mar 17 07:06:14 ubuntu kernel: [    0.887781] scsi0 : sata_sil
Mar 17 07:06:14 ubuntu kernel: [    0.888004] scsi1 : sata_sil
Mar 17 07:06:14 ubuntu kernel: [    0.888143] ata1: SATA max UDMA/100 mmio m512@0xe8003000 tf 0xe8003080 irq 11
Mar 17 07:06:14 ubuntu kernel: [    0.888205] ata2: SATA max UDMA/100 mmio m512@0xe8003000 tf 0xe80030c0 irq 11
Mar 17 07:06:14 ubuntu kernel: [    0.888820] pata_sis 0000:00:02.5: version 0.5.2
Mar 17 07:06:14 ubuntu kernel: [    0.889032] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 12
Mar 17 07:06:14 ubuntu kernel: [    0.889093] PCI: setting IRQ 12 as level-triggered
Mar 17 07:06:14 ubuntu kernel: [    0.889099] pata_sis 0000:00:02.5: PCI INT A -> Link[LNKA] -> GSI 12 (level, low) -> IRQ 12
Mar 17 07:06:14 ubuntu kernel: [    0.889441] scsi2 : pata_sis
Mar 17 07:06:14 ubuntu kernel: [    0.889609] scsi3 : pata_sis
Mar 17 07:06:14 ubuntu kernel: [    0.890614] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14
Mar 17 07:06:14 ubuntu kernel: [    0.890674] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15
Mar 17 07:06:14 ubuntu kernel: [    0.891183] Fixed MDIO Bus: probed
Mar 17 07:06:14 ubuntu kernel: [    0.891285] PPP generic driver version 2.4.2
Mar 17 07:06:14 ubuntu kernel: [    0.891522] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 17 07:06:14 ubuntu kernel: [    0.891800] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
Mar 17 07:06:14 ubuntu kernel: [    0.891860] PCI: setting IRQ 9 as level-triggered
Mar 17 07:06:14 ubuntu kernel: [    0.891865] ehci_hcd 0000:00:03.3: PCI INT D -> Link[LNKH] -> GSI 9 (level, low) -> IRQ 9
Mar 17 07:06:14 ubuntu kernel: [    0.891959] ehci_hcd 0000:00:03.3: EHCI Host Controller
Mar 17 07:06:14 ubuntu kernel: [    0.892356] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
Mar 17 07:06:14 ubuntu kernel: [    0.892484] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
Mar 17 07:06:14 ubuntu kernel: [    0.892500] ehci_hcd 0000:00:03.3: irq 9, io mem 0xe8002000
Mar 17 07:06:14 ubuntu kernel: [    0.904035] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
Mar 17 07:06:14 ubuntu kernel: [    0.904232] usb usb1: configuration #1 chosen from 1 choice
Mar 17 07:06:14 ubuntu kernel: [    0.904336] hub 1-0:1.0: USB hub found
Mar 17 07:06:14 ubuntu kernel: [    0.904404] hub 1-0:1.0: 6 ports detected
Mar 17 07:06:14 ubuntu kernel: [    0.904535] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 17 07:06:14 ubuntu kernel: [    0.904842] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 12
Mar 17 07:06:14 ubuntu kernel: [    0.904904] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 12 (level, low) -> IRQ 12
Mar 17 07:06:14 ubuntu kernel: [    0.904990] ohci_hcd 0000:00:03.0: OHCI Host Controller
Mar 17 07:06:14 ubuntu kernel: [    0.905115] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
Mar 17 07:06:14 ubuntu kernel: [    0.905205] ohci_hcd 0000:00:03.0: irq 12, io mem 0xe8004000
Mar 17 07:06:14 ubuntu kernel: [    0.962128] usb usb2: configuration #1 chosen from 1 choice
Mar 17 07:06:14 ubuntu kernel: [    0.962218] hub 2-0:1.0: USB hub found
Mar 17 07:06:14 ubuntu kernel: [    0.962287] hub 2-0:1.0: 2 ports detected
Mar 17 07:06:14 ubuntu kernel: [    0.962582] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
Mar 17 07:06:14 ubuntu kernel: [    0.962641] PCI: setting IRQ 10 as level-triggered
Mar 17 07:06:14 ubuntu kernel: [    0.962646] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
Mar 17 07:06:14 ubuntu kernel: [    0.962727] ohci_hcd 0000:00:03.1: OHCI Host Controller
Mar 17 07:06:14 ubuntu kernel: [    0.962834] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
Mar 17 07:06:14 ubuntu kernel: [    0.962919] ohci_hcd 0000:00:03.1: irq 10, io mem 0xe8000000
Mar 17 07:06:14 ubuntu kernel: [    1.018099] usb usb3: configuration #1 chosen from 1 choice
Mar 17 07:06:14 ubuntu kernel: [    1.018190] hub 3-0:1.0: USB hub found
Mar 17 07:06:14 ubuntu kernel: [    1.018257] hub 3-0:1.0: 2 ports detected
Mar 17 07:06:14 ubuntu kernel: [    1.018546] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
Mar 17 07:06:14 ubuntu kernel: [    1.018606] ohci_hcd 0000:00:03.2: PCI INT C -> Link[LNKG] -> GSI 11 (level, low) -> IRQ 11
Mar 17 07:06:14 ubuntu kernel: [    1.018688] ohci_hcd 0000:00:03.2: OHCI Host Controller
Mar 17 07:06:14 ubuntu kernel: [    1.018789] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
Mar 17 07:06:14 ubuntu kernel: [    1.018874] ohci_hcd 0000:00:03.2: irq 11, io mem 0xe8001000
Mar 17 07:06:14 ubuntu kernel: [    1.074112] usb usb4: configuration #1 chosen from 1 choice
Mar 17 07:06:14 ubuntu kernel: [    1.074201] hub 4-0:1.0: USB hub found
Mar 17 07:06:14 ubuntu kernel: [    1.074269] hub 4-0:1.0: 2 ports detected
Mar 17 07:06:14 ubuntu kernel: [    1.074389] uhci_hcd: USB Universal Host Controller Interface driver
Mar 17 07:06:14 ubuntu kernel: [    1.074602] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Mar 17 07:06:14 ubuntu kernel: [    1.074660] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Mar 17 07:06:14 ubuntu kernel: [    1.074834] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 17 07:06:14 ubuntu kernel: [    1.074981] mice: PS/2 mouse device common for all mice
Mar 17 07:06:14 ubuntu kernel: [    1.075181] rtc_cmos 00:04: RTC can wake from S4
Mar 17 07:06:14 ubuntu kernel: [    1.075290] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Mar 17 07:06:14 ubuntu kernel: [    1.075367] rtc0: alarms up to one year, 242 bytes nvram
Mar 17 07:06:14 ubuntu kernel: [    1.075552] device-mapper: uevent: version 1.0.3
Mar 17 07:06:14 ubuntu kernel: [    1.075789] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Mar 17 07:06:14 ubuntu kernel: [    1.075979] device-mapper: multipath: version 1.1.0 loaded
Mar 17 07:06:14 ubuntu kernel: [    1.076074] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar 17 07:06:14 ubuntu kernel: [    1.076317] EISA: Probing bus 0 at eisa.0
Mar 17 07:06:14 ubuntu kernel: [    1.076382] Cannot allocate resource for EISA slot 1
Mar 17 07:06:14 ubuntu kernel: [    1.076446] Cannot allocate resource for EISA slot 4
Mar 17 07:06:14 ubuntu kernel: [    1.076517] EISA: Detected 0 cards.
Mar 17 07:06:14 ubuntu kernel: [    1.076652] cpuidle: using governor ladder
Mar 17 07:06:14 ubuntu kernel: [    1.076709] cpuidle: using governor menu
Mar 17 07:06:14 ubuntu kernel: [    1.077468] TCP cubic registered
Mar 17 07:06:14 ubuntu kernel: [    1.077677] NET: Registered protocol family 10
Mar 17 07:06:14 ubuntu kernel: [    1.078275] lo: Disabled Privacy Extensions
Mar 17 07:06:14 ubuntu kernel: [    1.079832] NET: Registered protocol family 17
Mar 17 07:06:14 ubuntu kernel: [    1.079925] Bluetooth: L2CAP ver 2.13
Mar 17 07:06:14 ubuntu kernel: [    1.079980] Bluetooth: L2CAP socket layer initialized
Mar 17 07:06:14 ubuntu kernel: [    1.080073] Bluetooth: SCO (Voice Link) ver 0.6
Mar 17 07:06:14 ubuntu kernel: [    1.080129] Bluetooth: SCO socket layer initialized
Mar 17 07:06:14 ubuntu kernel: [    1.080257] Bluetooth: RFCOMM TTY layer initialized
Mar 17 07:06:14 ubuntu kernel: [    1.080316] Bluetooth: RFCOMM socket layer initialized
Mar 17 07:06:14 ubuntu kernel: [    1.080372] Bluetooth: RFCOMM ver 1.11
Mar 17 07:06:14 ubuntu kernel: [    1.080500] Using IPI No-Shortcut mode
Mar 17 07:06:14 ubuntu kernel: [    1.080672] PM: Resume from disk failed.
Mar 17 07:06:14 ubuntu kernel: [    1.080702] registered taskstats version 1
Mar 17 07:06:14 ubuntu NetworkManager: <info>  modem-manager is now available
Mar 17 07:06:14 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar 17 07:06:14 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Mar 17 07:06:14 ubuntu kernel: [    1.080910]   Magic number: 2:955:114
Mar 17 07:06:14 ubuntu kernel: [    1.081095] rtc_cmos 00:04: setting system clock to 2010-03-17 06:06:06 UTC (1268805966)
Mar 17 07:06:14 ubuntu kernel: [    1.081164] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 17 07:06:14 ubuntu kernel: [    1.081220] EDD information not available.
Mar 17 07:06:14 ubuntu kernel: [    1.095280] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Mar 17 07:06:14 ubuntu kernel: [    1.208055] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Mar 17 07:06:14 ubuntu kernel: [    1.216359] ata1.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
Mar 17 07:06:14 ubuntu kernel: [    1.216419] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 17 07:06:14 ubuntu kernel: [    1.224342] ata1.00: configured for UDMA/100
Mar 17 07:06:14 ubuntu kernel: [    1.224593] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
Mar 17 07:06:14 ubuntu kernel: [    1.224853] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 17 07:06:14 ubuntu kernel: [    1.224974] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Mar 17 07:06:14 ubuntu kernel: [    1.225099] sd 0:0:0:0: [sda] Write Protect is off
Mar 17 07:06:14 ubuntu kernel: [    1.225157] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 17 07:06:14 ubuntu kernel: [    1.225188] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 17 07:06:14 ubuntu kernel: [    1.225442]  sda: sda1 sda2 < sda5 >
Mar 17 07:06:14 ubuntu kernel: [    1.256687] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 17 07:06:14 ubuntu kernel: [    1.544051] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Mar 17 07:06:14 ubuntu kernel: [    1.552331] ata2.00: ATA-7: SAMSUNG HD103UJ, 1AA01109, max UDMA7
Mar 17 07:06:14 ubuntu kernel: [    1.552390] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 17 07:06:14 ubuntu kernel: [    1.560338] ata2.00: configured for UDMA/100
Mar 17 07:06:14 ubuntu kernel: [    1.560519] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
Mar 17 07:06:14 ubuntu kernel: [    1.560768] sd 1:0:0:0: Attached scsi generic sg1 type 0
Mar 17 07:06:14 ubuntu kernel: [    1.560878] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Mar 17 07:06:14 ubuntu kernel: [    1.561002] sd 1:0:0:0: [sdb] Write Protect is off
Mar 17 07:06:14 ubuntu kernel: [    1.561059] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Mar 17 07:06:14 ubuntu kernel: [    1.561089] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 17 07:06:14 ubuntu kernel: [    1.561327]  sdb: sdb1
Mar 17 07:06:14 ubuntu kernel: [    1.579396] sd 1:0:0:0: [sdb] Attached SCSI disk
Mar 17 07:06:14 ubuntu kernel: [    1.696035] usb 2-1: new full speed USB device using ohci_hcd and address 2
Mar 17 07:06:14 ubuntu kernel: [    1.724300] ata4.00: ATAPI: Optiarc DVD RW AD-5200A, 1.05, max UDMA/66
Mar 17 07:06:14 ubuntu kernel: [    1.740314] ata4.00: configured for UDMA/66
Mar 17 07:06:14 ubuntu kernel: [    1.742617] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-5200A  1.05 PQ: 0 ANSI: 5
Mar 17 07:06:14 ubuntu kernel: [    1.747528] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Mar 17 07:06:14 ubuntu kernel: [    1.747592] Uniform CD-ROM driver Revision: 3.20
Mar 17 07:06:14 ubuntu kernel: [    1.747786] sr 3:0:0:0: Attached scsi CD-ROM sr0
Mar 17 07:06:14 ubuntu kernel: [    1.747871] sr 3:0:0:0: Attached scsi generic sg2 type 5
Mar 17 07:06:14 ubuntu kernel: [    1.747973] Freeing unused kernel memory: 540k freed
Mar 17 07:06:14 ubuntu kernel: [    1.748973] Write protecting the kernel text: 4580k
Mar 17 07:06:14 ubuntu kernel: [    1.749061] Write protecting the kernel read-only data: 1840k
Mar 17 07:06:14 ubuntu kernel: [    2.020850] Linux agpgart interface v0.103
Mar 17 07:06:14 ubuntu kernel: [    2.046332] agpgart-sis 0000:00:00.0: SiS chipset [1039/0651]
Mar 17 07:06:14 ubuntu kernel: [    2.051160] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
Mar 17 07:06:14 ubuntu kernel: [    2.065211] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Mar 17 07:06:14 ubuntu kernel: [    2.065340] 8139cp 0000:00:0f.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Mar 17 07:06:14 ubuntu kernel: [    2.069367] 8139too Fast Ethernet driver 0.9.28
Mar 17 07:06:14 ubuntu kernel: [    2.069751] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
Mar 17 07:06:14 ubuntu kernel: [    2.069813] 8139too 0000:00:0f.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
Mar 17 07:06:14 ubuntu kernel: [    2.071053] eth0: RealTek RTL8139 at 0xdc00, 00:30:1b:29:47:f0, IRQ 10
Mar 17 07:06:14 ubuntu kernel: [    2.216978] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
Mar 17 07:06:14 ubuntu kernel: [    2.217049] PCI: setting IRQ 5 as level-triggered
Mar 17 07:06:14 ubuntu kernel: [    2.217056] ohci1394 0000:00:10.0: PCI INT A -> Link[LNKD] -> GSI 5 (level, low) -> IRQ 5
Mar 17 07:06:14 ubuntu kernel: [    2.220988] Floppy drive(s): fd0 is 1.44M
Mar 17 07:06:14 ubuntu kernel: [    2.239927] FDC 0 is a post-1991 82077
Mar 17 07:06:14 ubuntu kernel: [    2.275630] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[5]  MMIO=[e8006000-e80067ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Mar 17 07:06:14 ubuntu kernel: [    2.802797] PM: Starting manual resume from disk
Mar 17 07:06:14 ubuntu kernel: [    2.802870] PM: Resume from partition 8:5
Mar 17 07:06:14 ubuntu kernel: [    2.802873] PM: Checking hibernation image.
Mar 17 07:06:14 ubuntu kernel: [    2.803146] PM: Resume from disk failed.
Mar 17 07:06:14 ubuntu kernel: [    2.840378] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Mar 17 07:06:14 ubuntu kernel: [    2.840535] EXT4-fs (sda1): write access will be enabled during recovery
Mar 17 07:06:14 ubuntu kernel: [    2.857734] EXT4-fs (sda1): barriers enabled
Mar 17 07:06:14 ubuntu kernel: [    2.986178] kjournald2 starting: pid 345, dev sda1:8, commit interval 5 seconds
Mar 17 07:06:14 ubuntu kernel: [    2.986333] EXT4-fs (sda1): delayed allocation enabled
Mar 17 07:06:14 ubuntu kernel: [    2.986476] EXT4-fs: file extents enabled
Mar 17 07:06:14 ubuntu kernel: [    3.100934] EXT4-fs: mballoc enabled
Mar 17 07:06:14 ubuntu kernel: [    3.101051] EXT4-fs (sda1): recovery complete
Mar 17 07:06:14 ubuntu kernel: [    3.106087] EXT4-fs (sda1): mounted filesystem with ordered data mode
Mar 17 07:06:14 ubuntu kernel: [    3.568264] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000000301b1cad54]
Mar 17 07:06:14 ubuntu kernel: [    3.701590] type=1505 audit(1268805969.119:2): operation="profile_load" pid=372 name=/usr/share/gdm/guest-session/Xsession
Mar 17 07:06:14 ubuntu kernel: [    3.705925] type=1505 audit(1268805969.122:3): operation="profile_load" pid=373 name=/sbin/dhclient3
Mar 17 07:06:14 ubuntu kernel: [    3.706630] type=1505 audit(1268805969.122:4): operation="profile_load" pid=373 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 17 07:06:14 ubuntu kernel: [    3.707038] type=1505 audit(1268805969.122:5): operation="profile_load" pid=373 name=/usr/lib/connman/scripts/dhclient-script
Mar 17 07:06:14 ubuntu kernel: [    3.748290] type=1505 audit(1268805969.166:6): operation="profile_load" pid=374 name=/usr/bin/evince
Mar 17 07:06:14 ubuntu kernel: [    3.759539] type=1505 audit(1268805969.174:7): operation="profile_load" pid=374 name=/usr/bin/evince-previewer
Mar 17 07:06:14 ubuntu kernel: [    3.766073] type=1505 audit(1268805969.182:8): operation="profile_load" pid=374 name=/usr/bin/evince-thumbnailer
Mar 17 07:06:14 ubuntu kernel: [    3.795387] type=1505 audit(1268805969.210:9): operation="profile_load" pid=376 name=/usr/lib/cups/backend/cups-pdf
Mar 17 07:06:14 ubuntu kernel: [    3.796258] type=1505 audit(1268805969.214:10): operation="profile_load" pid=376 name=/usr/sbin/cupsd
Mar 17 07:06:14 ubuntu kernel: [    6.696056] ohci_hcd 0000:00:03.0: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
Mar 17 07:06:14 ubuntu kernel: [    7.567342] udev: starting version 147
Mar 17 07:06:14 ubuntu kernel: [    7.573998] Adding 1397612k swap on /dev/sda5.  Priority:-1 extents:1 across:1397612k 
Mar 17 07:06:14 ubuntu kernel: [    7.726634] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 17 07:06:14 ubuntu kernel: [    7.781292] lp: driver loaded but no devices found
Mar 17 07:06:14 ubuntu kernel: [    8.100350] EXT4-fs (sda1): internal journal on sda1:8
Mar 17 07:06:14 ubuntu kernel: [    8.212790] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Mar 17 07:06:14 ubuntu kernel: [    8.370162] nvidia: module license 'NVIDIA' taints kernel.
Mar 17 07:06:14 ubuntu kernel: [    8.370172] Disabling lock debugging due to kernel taint
Mar 17 07:06:14 ubuntu kernel: [    8.633187] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x10c0
Mar 17 07:06:14 ubuntu kernel: [    8.650081] parport_pc 00:0a: reported by Plug and Play ACPI
Mar 17 07:06:14 ubuntu kernel: [    8.650133] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Mar 17 07:06:14 ubuntu kernel: [    8.752678] lp0: using parport0 (interrupt-driven).
Mar 17 07:06:14 ubuntu kernel: [    8.810156] it87: Found IT8705F chip at 0x290, revision 2
Mar 17 07:06:14 ubuntu kernel: [    8.810229] ACPI: I/O resource it87 [0x295-0x296] conflicts with ACPI region IP__ [0x295-0x296]
Mar 17 07:06:14 ubuntu kernel: [    8.810307] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Mar 17 07:06:14 ubuntu kernel: [    8.886366] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 17 07:06:14 ubuntu kernel: [    8.889300] ppdev: user-space parallel port driver
Mar 17 07:06:14 ubuntu kernel: [    9.341076] Intel ICH 0000:00:02.7: PCI INT C -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
Mar 17 07:06:14 ubuntu kernel: [    9.535369] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 12 (level, low) -> IRQ 12
Mar 17 07:06:14 ubuntu kernel: [    9.536188] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
Mar 17 07:06:15 ubuntu kernel: [    9.672106] intel8x0_measure_ac97_clock: measured 52594 usecs (2530 samples)
Mar 17 07:06:15 ubuntu kernel: [    9.672112] intel8x0: clocking to 48000
Mar 17 07:06:15 ubuntu avahi-daemon[692]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3901413122.
Mar 17 07:06:15 ubuntu ntfs-3g[903]: Version 2009.4.4 external FUSE 27
Mar 17 07:06:15 ubuntu ntfs-3g[903]: Mounted /dev/sdb1 (Read-Write, label "1TBsamsung", NTFS 3.1)
Mar 17 07:06:15 ubuntu ntfs-3g[903]: Cmdline options: rw,locale=en_US.UTF-8
Mar 17 07:06:15 ubuntu ntfs-3g[903]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096
Mar 17 07:06:24 ubuntu kernel: [   18.976032] eth0: no IPv6 routers present

---

