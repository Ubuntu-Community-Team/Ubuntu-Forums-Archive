---
title: "Help! Huge problem: System won't boot!"
date: 2010-10-08
forum: General Help
---

### Post by techiewannabe on 2010-10-08
When I turn on my laptop, the system appears to begin booting as usual. It asks for the user id and password. However, after I input this data, it takes an unusually long time to boot into the GUI. Next, the desktop image, my wallpaper, shows up as expected. Unfortunately, however, there is nothing else! There are no icons, no task bar. Nothing. The mouse works, but that is all. I have no idea how to get this system working! Obviously, I am writing this from a different computer!

Please help! Even though I've been using Ubuntu Linux for a while, I still consider myself a newbie. I'm not real fluent with the command line, but I can certainly copy suggested command lines!

---

### Post by Rmantingh on 2010-10-09
There are various suggestions you could try:-
1) After you have logged in you could try Ctrl-Alt-F1 to switch to a terminal and log in as your normal user. Then issue the 'top' command (without quotes) to see what is running at that particular time. Perhaps that will give you some clues. You could also run 'dmesg' to see if there's anything in the log file that might shed light on the situation.
To get back to the GUI press Ctrl-Alt-F7.
2) If you have a Live CD of Ubuntu you could try and boot from that to see if you can run Ubuntu from the CD.
3) You could try to boot into RecoveryMode. See [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) (read the note at the bottom).

Some questions:-
- Did you change anything to the Ubuntu installation prior to these problems?
- Do the propblems seem to you that there is a process running that hogs the CPU? You said the system acted slow. Or does it look more like some process has crashed (perhaps gnome-panel or something like that)?

---

### Post by techiewannabe on 2010-10-09
Rmantingh:

Thanks for your note. Before my posting, I did each of the three things you suggested. However, I'm not tech savy enough to know what to do next. For example, I can get to the command line, but don't know what commands to enter. I've got a live CD, and I can run Ubuntu from it, but I don't know what to do after that. (As far as I know, I can't access my files while using the live CD.) 

As for your questions, I did not change anything to the install procedure. However, my system has been wanting to do a "check disk" at the start-up and I've always had to by-pass that because it would never work properly. (The process gets 'stuck' and never finishes the process, even if I leave it over night to do the check disk. I made a posting about that problem but never really got it resolved.) I by-pass that procedure by hitting the escape key.

I am not aware of anything crashing or running in the background.

I will explore the web sites that you referred me to, and any associated sites. 

I would be happy to hear any suggestions.

Thanks for you willingness to consider this problem.

---

### Post by Rmantingh on 2010-10-09
It seems to me that you may have problems with your hard drive which could also be the cause of the boot process stalling after log in (if certain files are corrupted, for instance).
The best thing to do is to boot from Live CD and rescue any files that you may have on your hard drive.
I can't remember exactly what booting into a Live CD looks like (I don't have one here to hand) but I thought the desktop would show icons for every drive (or partition) that was connected to your PC. If you double-click one of those the relevant disk will be locally mounted and a file browser will open showing the contents of the disk.
Once you have access to your local disk you can find your files under the /home/<username> directory (or whereever you have stored them) and you can copy/save them onto a USB stick (or burn them on a CD if you have a CD-burner).
After you have your files save and secure you can start to investigate what is happening with your disk:-
Open System -> Administration -> Disk Utility.
This will show you a list on the left with all connected drives.
Select the one that is giving you problems.
Then on the right it shows various information and possible actions that you can perform on the selected drive.
If your drive is S.M.A.R.T. enabled it will show you the health status of your drive. Click on the SMART Data button to see detailed information about the status/health of your drive.
If you do not have a S.M.A.R.T. enabled drive then you can still select the Check Filesystem button to have a manual check done on your disk (you may have to unmount the disk first - press the Unmount Volume button).
NB: Just be careful not to press any of the other buttons (Format/Edit/Delete, etc.) unless you know what you're doing and you have your files backed-up.
After all that, if you feel your drive is still healthy, I recommend you re-install Ubuntu from scratch and see if the problem of logging in still persists.

---

### Post by P4man on 2010-10-09
I agree with Rmantingh; it does seem like your harddisk is dying or has died. Follow the above advice. But if it turns out the disk is okay, you can also try this: while staring at the wallpaper, press control+alt+F1 as mentioned above. Log in (type the password blind, it doesnt appear on screen, nothing does while you type).

Once logged in, type in:

```
dmesg
```

Your screen will fill with stuff you probably dont understand. Dont worry, Im interested in the last lines. Is there something that repeats often or stands out as a potentially serious problem?

If you are lost then try saving the output to a file:

```
dmesg > dmesg.txt
```

(nothing will show, but the file will be created)
Now you have to copy that to an USB stick. Find out if and where your USB stick is mounted.

```
ls /media
```

(that is LS /MEDIA in lowercase). It will list all removable media. Lets assume the stick is /media/kingston. To copy the log file there type

```
cp dmesg.txt /media/kingston
```

Replace "kingston" with whatever your stick is called. Post the log here.

---

### Post by techiewannabe on 2010-10-10
Rmantingh and P4man:

Thanks to each of you for your suggestions and my apologies for the delay in getting back to you. (I was out of town and away from my computer.)

Rmantingh - thanks to your advice, I was able to use the Live CD and access all of my files. In fact, from the CD, my hard drive seems fine! However, I do not have the 'Disk Utility' program that you refer to, so I wasn't able to follow your advice with this. 

P4man - when I type in the dmesg command, I don't see anything alarming. When I try to copy the text, I get a "Permission denied" message. Perhaps I am using the wrong name for my media. (It is a SanDisk flash drive. I've tried using 'SanDisk,' 'U3,' 'cd-rom,' and 'cd-rom0,' all to no avail. When I use the 'ls' command, cdrom and cdrom0 are listed.)

Thanks to each of you for your willingness to look at this. I will be able to check for my messages more promptly now, as I am back in town!

I look forward to any suggestions you might have.

Techiewannabe

---

### Post by techiewannabe on 2010-10-10
P4man:
I realized that I could access the text for you after all. I simply went back to using the Live CD. I've attached the text as an RTF file.
Thanks for your help.
Techiewannabe

---

### Post by techiewannabe on 2010-10-10
P4man:
For some reason, it doesn't appear that I uploaded the file properly. Here is the text I tried to upload.
Thanks.


[PHP][    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-19-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #65-Ubuntu SMP Thu Sep 16 14:14:28 UTC 2010 (Ubuntu 2.6.28-19.65-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000047f70000 (usable)
[    0.000000]  BIOS-e820: 0000000047f70000 - 0000000047f7d000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000047f7d000 - 0000000047f80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000047f80000 - 0000000048000000 (reserved)
[    0.000000]  BIOS-e820: 0000000057f80000 - 0000000058000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x47f70 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 00000000000d8000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000047f70000 (usable)
[    0.000000]  modified: 0000000047f70000 - 0000000047f7d000 (ACPI data)
[    0.000000]  modified: 0000000047f7d000 - 0000000047f80000 (ACPI NVS)
[    0.000000]  modified: 0000000047f80000 - 0000000048000000 (reserved)
[    0.000000]  modified: 0000000057f80000 - 0000000058000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fefcf9
[    0.000000] Allocated new RAMDISK: 0087d000 - 00faecf9
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fefcf8 to 0087d000 - 00faecf8
[    0.000000] ACPI: RSDP 000F6500, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 47F79185, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 47F7CEED, 0074 (r1 HP     Chinook   6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 47F791B5, 3D38 (r1     HP    SB200  6040000 INTL 20030509)
[    0.000000] ACPI: FACS 47F7FFC0, 0040
[    0.000000] ACPI: APIC 47F7CF61, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: SSDT 47F7CFC9, 0037 (r1 PTLTD  ACPIHT    6040000  LTP        1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 267MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000faecf9]      NEW RAMDISK ==> [000087d000 - 0000faecf9]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f6470] 000f6470
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x00047f70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x00047f70
[    0.000000] On node 0 totalpages: 294645
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 535 pages used for memmap
[    0.000000]   HighMem zone: 67931 pages, LIFO batch:15
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000d8000
[    0.000000] PM: Registered nosave memory: 00000000000d8000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 58000000:a6c00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 292342
[    0.000000] Kernel command line: root=UUID=5e35398d-6744-401e-b0d4-c554d93f26b6 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3000.070 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 5895360 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1147060k/1179072k available (4116k kernel code, 30952k reserved, 2199k data, 532k init, 273864k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05051d1 - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05051d1   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004023] Calibrating delay loop (skipped), value calculated using timer frequency.. 6000.14 BogoMIPS (lpj=12000280)
[    0.004054] Security Framework initialized
[    0.004070] SELinux:  Disabled at boot.
[    0.004108] AppArmor: AppArmor initialized
[    0.004126] Mount-cache hash table entries: 512
[    0.004380] Initializing cgroup subsys ns
[    0.004388] Initializing cgroup subsys cpuacct
[    0.004391] Initializing cgroup subsys memory
[    0.004399] Initializing cgroup subsys freezer
[    0.004427] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004430] CPU: L2 cache: 1024K
[    0.004435] CPU: Physical Processor ID: 0
[    0.004437] CPU: Processor Core ID: 0
[    0.004443] using mwait in idle threads.
[    0.004464] Checking 'hlt' instruction... OK.
[    0.023776] ACPI: Core revision 20080926
[    0.027046] ACPI: Checking initramfs for custom DSDT
[    0.316511] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.320001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.320001] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.320001] ..... (found apic 0 pin 2) ...
[    0.360576] ....... works.
[    0.360579] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[    0.364001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6000.55 BogoMIPS (lpj=12001117)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.448411] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[    0.448439] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.452084] Brought up 2 CPUs
[    0.452090] Total of 2 processors activated (12000.69 BogoMIPS).
[    0.452129] CPU0 attaching sched-domain:
[    0.452133]  domain 0: span 0-1 level SIBLING
[    0.452136]   groups: 0 1
[    0.452144] CPU1 attaching sched-domain:
[    0.452147]  domain 0: span 0-1 level SIBLING
[    0.452150]   groups: 1 0
[    0.452278] net_namespace: 776 bytes
[    0.452295] Booting paravirtualized kernel on bare hardware
[    0.452533] Time: 22:03:25  Date: 10/10/10
[    0.452533] regulator: core version 0.5
[    0.452533] NET: Registered protocol family 16
[    0.452533] EISA bus registered
[    0.452533] ACPI: bus type pci registered
[    0.452533] PCI: PCI BIOS revision 2.10 entry at 0xfd968, last bus=2
[    0.452533] PCI: Using configuration type 1 for base access
[    0.453553] ACPI: EC: Look up EC in DSDT
[    0.462560] ACPI: Interpreter enabled
[    0.462571] ACPI: (supports S0 S3 S4 S5)
[    0.462597] ACPI: Using IOAPIC for interrupt routing
[    0.466310] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.528177] ACPI: EC: GPE = 0x6, I/O: command/status = 0x66, data = 0x62
[    0.528181] ACPI: EC: driver started in interrupt mode
[    0.528300] ACPI: No dock devices found.
[    0.528314] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.528371] pci 0000:00:00.0: reg 10 32bit mmio: [0xd2000000-0xd3ffffff]
[    0.528377] pci 0000:00:00.0: reg 14 32bit mmio: [0xd0000000-0xd0000fff]
[    0.528455] pci 0000:00:13.0: reg 10 32bit mmio: [0xd0001000-0xd0001fff]
[    0.528497] pci 0000:00:13.1: reg 10 32bit mmio: [0xd0002000-0xd0002fff]
[    0.528545] pci 0000:00:14.0: reg 10 io port: [0x8040-0x804f]
[    0.528552] pci 0000:00:14.0: reg 14 32bit mmio: [0x000000-0x0003ff]
[    0.528588] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.528594] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.528600] pci 0000:00:14.1: reg 18 io port: [0x170-0x177]
[    0.528606] pci 0000:00:14.1: reg 1c io port: [0x374-0x377]
[    0.528612] pci 0000:00:14.1: reg 20 io port: [0x8060-0x806f]
[    0.528699] pci 0000:00:14.5: reg 10 32bit mmio: [0xd0003000-0xd00030ff]
[    0.528739] pci 0000:00:14.6: reg 10 32bit mmio: [0xd0003400-0xd00034ff]
[    0.528815] pci 0000:01:05.0: reg 10 32bit mmio: [0xe0000000-0xefffffff]
[    0.528821] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.528827] pci 0000:01:05.0: reg 18 32bit mmio: [0xd0100000-0xd010ffff]
[    0.528845] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.528855] pci 0000:01:05.0: supports D1 D2
[    0.528892] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.528896] pci 0000:00:01.0: bridge 32bit mmio: [0xd0100000-0xd01fffff]
[    0.528901] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.528940] pci 0000:02:00.0: reg 10 32bit mmio: [0xd0208000-0xd02087ff]
[    0.528948] pci 0000:02:00.0: reg 14 32bit mmio: [0xd0200000-0xd0203fff]
[    0.528986] pci 0000:02:00.0: supports D1 D2
[    0.528988] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.528994] pci 0000:02:00.0: PME# disabled
[    0.529019] pci 0000:02:02.0: reg 10 32bit mmio: [0xd0204000-0xd0205fff]
[    0.529086] pci 0000:02:03.0: reg 10 io port: [0xa000-0xa0ff]
[    0.529094] pci 0000:02:03.0: reg 14 32bit mmio: [0xd0208800-0xd02088ff]
[    0.529130] pci 0000:02:03.0: supports D1 D2
[    0.529132] pci 0000:02:03.0: PME# supported from D1 D2 D3hot D3cold
[    0.529137] pci 0000:02:03.0: PME# disabled
[    0.529174] pci 0000:02:04.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.529185] pci 0000:02:04.0: supports D1 D2
[    0.529188] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.529192] pci 0000:02:04.0: PME# disabled
[    0.529230] pci 0000:02:04.1: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.529241] pci 0000:02:04.1: supports D1 D2
[    0.529243] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.529248] pci 0000:02:04.1: PME# disabled
[    0.529282] pci 0000:02:04.2: reg 10 io port: [0xa400-0xa43f]
[    0.529365] pci 0000:02:07.0: reg 10 32bit mmio: [0xd0206000-0xd0206fff]
[    0.529405] pci 0000:02:07.0: supports D1 D2
[    0.529408] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.529412] pci 0000:02:07.0: PME# disabled
[    0.529448] pci 0000:02:07.1: reg 10 32bit mmio: [0xd0207000-0xd0207fff]
[    0.529488] pci 0000:02:07.1: supports D1 D2
[    0.529490] pci 0000:02:07.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.529495] pci 0000:02:07.1: PME# disabled
[    0.529530] pci 0000:02:07.2: reg 10 32bit mmio: [0xd0208c00-0xd0208cff]
[    0.529571] pci 0000:02:07.2: supports D1 D2
[    0.529573] pci 0000:02:07.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.529578] pci 0000:02:07.2: PME# disabled
[    0.529622] pci 0000:00:14.4: transparent bridge
[    0.529628] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    0.529633] pci 0000:00:14.4: bridge 32bit mmio: [0xd0200000-0xd02fffff]
[    0.529680] bus 00 -> node 0
[    0.529687] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.529841] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.529969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.532265] ACPI: PCI Interrupt Link [LNK0] (IRQs 5 10 11) *0, disabled.
[    0.532406] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 10 11) *0, disabled.
[    0.532548] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 10 11) *0, disabled.
[    0.532687] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 10 11) *0, disabled.
[    0.532872] ACPI: WMI: Mapper loaded
[    0.532967] SCSI subsystem initialized
[    0.532967] libata version 3.00 loaded.
[    0.532967] usbcore: registered new interface driver usbfs
[    0.532967] usbcore: registered new interface driver hub
[    0.532967] usbcore: registered new device driver usb
[    0.532967] PCI: Using ACPI for IRQ routing
[    0.540016] Bluetooth: Core ver 2.13
[    0.540036] NET: Registered protocol family 31
[    0.540036] Bluetooth: HCI device and connection manager initialized
[    0.540036] Bluetooth: HCI socket layer initialized
[    0.540036] NET: Registered protocol family 8
[    0.540036] NET: Registered protocol family 20
[    0.540051] NetLabel: Initializing
[    0.540054] NetLabel:  domain hash size = 128
[    0.540056] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.540074] NetLabel:  unlabeled traffic allowed by default
[    0.540184] AppArmor: AppArmor Filesystem Enabled
[    0.544016] pnp: PnP ACPI init
[    0.544031] ACPI: bus type pnp registered
[    0.546011] pnp 00:07: io resource (0x8000-0x8068) overlaps 0000:00:14.1 BAR 4 (0x8060-0x806f), disabling
[    0.572036] pnp: PnP ACPI: found 10 devices
[    0.572039] ACPI: ACPI bus type pnp unregistered
[    0.572044] PnPBIOS: Disabled by ACPI PNP
[    0.572061] system 00:07: ioport range 0x200-0x20f has been reserved
[    0.572065] system 00:07: ioport range 0xc14-0xc14 has been reserved
[    0.572068] system 00:07: ioport range 0xc50-0xc52 has been reserved
[    0.572071] system 00:07: ioport range 0xc6c-0xc6c has been reserved
[    0.572074] system 00:07: ioport range 0xc6f-0xc6f has been reserved
[    0.572077] system 00:07: ioport range 0xcd6-0xcd7 has been reserved
[    0.572080] system 00:07: ioport range 0x1080-0x1080 has been reserved
[    0.572084] system 00:07: ioport range 0x8800-0x8800 has been reserved
[    0.572087] system 00:07: ioport range 0xfe00-0xfe00 has been reserved
[    0.572090] system 00:07: ioport range 0xfe10-0xfe11 has been reserved
[    0.572094] system 00:07: iomem range 0xe4000-0xfffff could not be reserved
[    0.572097] system 00:07: iomem range 0x100000-0x47ffffff could not be reserved
[    0.572100] system 00:07: iomem range 0xd0000000-0xd0000fff has been reserved
[    0.572104] system 00:07: iomem range 0xfff80000-0xffffffff has been reserved
[    0.606861] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.606866] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.606870] pci 0000:00:01.0:   MEM window: 0xd0100000-0xd01fffff
[    0.606875] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.606895] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[    0.606898] pci 0000:02:04.0:   IO window: 0x00a800-0x00a8ff
[    0.606903] pci 0000:02:04.0:   IO window: 0x00ac00-0x00acff
[    0.606908] pci 0000:02:04.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.606913] pci 0000:02:04.0:   MEM window: 0x6c000000-0x6fffffff
[    0.606918] pci 0000:02:04.1: CardBus bridge, secondary bus 0000:04
[    0.606920] pci 0000:02:04.1:   IO window: 0x001400-0x0014ff
[    0.606925] pci 0000:02:04.1:   IO window: 0x001800-0x0018ff
[    0.606930] pci 0000:02:04.1:   PREFETCH window: 0x64000000-0x67ffffff
[    0.606935] pci 0000:02:04.1:   MEM window: 0x70000000-0x73ffffff
[    0.606939] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.606943] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    0.606948] pci 0000:00:14.4:   MEM window: 0xd0200000-0xd02fffff
[    0.606952] pci 0000:00:14.4:   PREFETCH window: 0x00000060000000-0x00000067ffffff
[    0.606980] pci 0000:02:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.606994] pci 0000:02:04.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.607001] bus: 00 index 0 io port: [0x00-0xffff]
[    0.607004] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.607007] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.607009] bus: 01 index 1 mmio: [0xd0100000-0xd01fffff]
[    0.607012] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.607014] bus: 01 index 3 mmio: [0x0-0x0]
[    0.607017] bus: 02 index 0 io port: [0xa000-0xafff]
[    0.607019] bus: 02 index 1 mmio: [0xd0200000-0xd02fffff]
[    0.607021] bus: 02 index 2 mmio: [0x60000000-0x67ffffff]
[    0.607024] bus: 02 index 3 io port: [0x00-0xffff]
[    0.607026] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.607029] bus: 03 index 0 io port: [0xa800-0xa8ff]
[    0.607031] bus: 03 index 1 io port: [0xac00-0xacff]
[    0.607033] bus: 03 index 2 mmio: [0x60000000-0x63ffffff]
[    0.607036] bus: 03 index 3 mmio: [0x6c000000-0x6fffffff]
[    0.607038] bus: 04 index 0 io port: [0x1400-0x14ff]
[    0.607041] bus: 04 index 1 io port: [0x1800-0x18ff]
[    0.607043] bus: 04 index 2 mmio: [0x64000000-0x67ffffff]
[    0.607045] bus: 04 index 3 mmio: [0x70000000-0x73ffffff]
[    0.607056] NET: Registered protocol family 2
[    0.620090] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.620556] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.621536] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.622445] TCP: Hash tables configured (established 131072 bind 65536)
[    0.622449] TCP reno registered
[    0.628197] NET: Registered protocol family 1
[    0.628407] checking if image is initramfs... it is
[    1.104575] Switched to high resolution mode on CPU 1
[    1.108039] Switched to high resolution mode on CPU 0
[    1.234955] Freeing initrd memory: 7367k freed
[    1.235312] cpufreq: No nForce2 chipset.
[    1.235535] audit: initializing netlink socket (disabled)
[    1.235587] type=2000 audit(1286748205.233:1): initialized
[    1.243848] highmem bounce pool size: 64 pages
[    1.243856] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.245516] VFS: Disk quotas dquot_6.5.1
[    1.245599] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.246418] fuse init (API version 7.10)
[    1.246530] msgmni has been set to 1720
[    1.246778] alg: No test for stdrng (krng)
[    1.246807] io scheduler noop registered
[    1.246812] io scheduler anticipatory registered
[    1.246816] io scheduler deadline registered
[    1.246844] io scheduler cfq registered (default)
[    1.246918] pci 0000:01:05.0: Boot video device
[    1.296172] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.296185] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.298911] ACPI: AC Adapter [ACAD] (on-line)
[    1.496122] ACPI: Battery Slot [BAT1] (battery present)
[    1.496205] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.496209] ACPI: Power Button (FF) [PWRF]
[    1.496271] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.496323] ACPI: Lid Switch [LID]
[    1.496379] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.496383] ACPI: Power Button (CM) [PWRB]
[    1.496610] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.496642] processor ACPI_CPU:00: registered as cooling_device0
[    1.496691] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.496715] processor ACPI_CPU:01: registered as cooling_device1
[    1.531902] thermal LNXTHERM:01: registered as thermal_zone0
[    1.538049] ACPI: Thermal Zone [THRM] (66 C)
[    1.538110] isapnp: Scanning for PnP cards...
[    1.889768] isapnp: No Plug & Play device found
[    1.900171] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.900560] serial 0000:00:14.6: PCI INT B -> GSI 5 (level, low) -> IRQ 5
[    1.900567] serial 0000:00:14.6: PCI INT B disabled
[    1.901526] brd: module loaded
[    1.901975] loop: module loaded
[    1.902076] Fixed MDIO Bus: probed
[    1.902085] PPP generic driver version 2.4.2
[    1.902158] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.902200] Driver 'sd' needs updating - please use bus_type methods
[    1.902214] Driver 'sr' needs updating - please use bus_type methods
[    1.902578] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.902769] scsi0 : pata_atiixp
[    1.902902] scsi1 : pata_atiixp
[    1.904498] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8060 irq 14
[    1.904502] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8068 irq 15
[    2.068421] ata1.00: ATA-6: ST980815A,  3.ALE, max UDMA/100
[    2.068425] ata1.00: 156301488 sectors, multi 16: LBA48 
[    2.084399] ata1.00: configured for UDMA/100
[    2.272316] ata2.00: ATAPI: DV-W24EW, C.0D, max MWDMA2
[    2.328331] ata2.00: configured for MWDMA2
[    2.368956] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        n/a  PQ: 0 ANSI: 5
[    2.369092] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.369117] sd 0:0:0:0: [sda] Write Protect is off
[    2.369120] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.369158] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.369248] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.369268] sd 0:0:0:0: [sda] Write Protect is off
[    2.369272] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.369308] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.369313]  sda: sda1 sda2 < sda5 >
[    2.412482] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.412550] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.436748] scsi 1:0:0:0: CD-ROM            TEAC     DV-W24EW         C.0D PQ: 0 ANSI: 5
[    2.539365] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.539369] Uniform CD-ROM driver Revision: 3.20
[    2.539487] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.539540] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.540193] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.540232] ehci_hcd 0000:02:07.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.540269] ehci_hcd 0000:02:07.2: EHCI Host Controller
[    2.540364] ehci_hcd 0000:02:07.2: new USB bus registered, assigned bus number 1
[    2.564038] ehci_hcd 0000:02:07.2: irq 19, io mem 0xd0208c00
[    2.576012] ehci_hcd 0000:02:07.2: USB 2.0 started, EHCI 1.00
[    2.576102] usb usb1: configuration #1 chosen from 1 choice
[    2.576140] hub 1-0:1.0: USB hub found
[    2.576153] hub 1-0:1.0: 5 ports detected
[    2.576298] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.576316] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.576330] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.576385] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.576404] ohci_hcd 0000:00:13.0: irq 19, io mem 0xd0001000
[    2.636076] usb usb2: configuration #1 chosen from 1 choice
[    2.636110] hub 2-0:1.0: USB hub found
[    2.636123] hub 2-0:1.0: 3 ports detected
[    2.636231] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.636244] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.636317] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.636333] ohci_hcd 0000:00:13.1: irq 19, io mem 0xd0002000
[    2.696070] usb usb3: configuration #1 chosen from 1 choice
[    2.696103] hub 3-0:1.0: USB hub found
[    2.696116] hub 3-0:1.0: 3 ports detected
[    2.696231] ohci_hcd 0000:02:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.696244] ohci_hcd 0000:02:07.0: OHCI Host Controller
[    2.696299] ohci_hcd 0000:02:07.0: new USB bus registered, assigned bus number 4
[    2.696323] ohci_hcd 0000:02:07.0: irq 16, io mem 0xd0206000
[    2.781841] usb usb4: configuration #1 chosen from 1 choice
[    2.781879] hub 4-0:1.0: USB hub found
[    2.781892] hub 4-0:1.0: 3 ports detected
[    2.782003] ohci_hcd 0000:02:07.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.782015] ohci_hcd 0000:02:07.1: OHCI Host Controller
[    2.782084] ohci_hcd 0000:02:07.1: new USB bus registered, assigned bus number 5
[    2.782106] ohci_hcd 0000:02:07.1: irq 18, io mem 0xd0207000
[    2.865856] usb usb5: configuration #1 chosen from 1 choice
[    2.865890] hub 5-0:1.0: USB hub found
[    2.865902] hub 5-0:1.0: 2 ports detected
[    2.866013] uhci_hcd: USB Universal Host Controller Interface driver
[    2.866130] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.876980] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.884287] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.884296] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.884301] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.884306] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.884312] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.888058] mice: PS/2 mouse device common for all mice
[    2.904106] rtc_cmos 00:03: RTC can wake from S4
[    2.904155] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.904174] rtc0: alarms up to one day, 242 bytes nvram
[    2.904255] device-mapper: uevent: version 1.0.3
[    2.904403] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.904535] device-mapper: multipath: version 1.0.5 loaded
[    2.904539] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.904656] EISA: Probing bus 0 at eisa.0
[    2.904665] Cannot allocate resource for EISA slot 1
[    2.904686] Cannot allocate resource for EISA slot 8
[    2.904688] EISA: Detected 0 cards.
[    2.904827] cpuidle: using governor ladder
[    2.904912] cpuidle: using governor menu
[    2.905662] TCP cubic registered
[    2.905754] NET: Registered protocol family 10
[    2.906353] lo: Disabled Privacy Extensions
[    2.906867] NET: Registered protocol family 17
[    2.906894] Bluetooth: L2CAP ver 2.11
[    2.906897] Bluetooth: L2CAP socket layer initialized
[    2.906900] Bluetooth: SCO (Voice Link) ver 0.6
[    2.906902] Bluetooth: SCO socket layer initialized
[    2.906954] Bluetooth: RFCOMM socket layer initialized
[    2.906970] Bluetooth: RFCOMM TTY layer initialized
[    2.906972] Bluetooth: RFCOMM ver 1.10
[    2.907055] Using IPI No-Shortcut mode
[    2.907179] registered taskstats version 1
[    2.907323]   Magic number: 14:622:97
[    2.907424] rtc_cmos 00:03: setting system clock to 2010-10-10 22:03:28 UTC (1286748208)
[    2.907429] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.907431] EDD information not available.
[    2.908238] Freeing unused kernel memory: 532k freed
[    2.908403] Write protecting the kernel text: 4120k
[    2.908462] Write protecting the kernel read-only data: 1524k
[    2.927444] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.161081] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    3.378208] usb 4-1: configuration #1 chosen from 1 choice
[    3.388740] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.388796] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.397285] b43-pci-bridge 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.400763] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    3.403414] 8139too Fast Ethernet driver 0.9.28
[    3.403460] 8139too 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.405095] eth0: RealTek RTL8139 at 0xa000, 00:0f:b0:3e:e1:30, IRQ 19
[    3.405099] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.410737] ohci1394 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.460602] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d0208000-d02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.898710] usbcore: registered new interface driver hiddev
[    3.904592] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:14.4/0000:02:07.0/usb4/4-1/4-1:1.0/input/input5
[    3.909107] generic-usb 0003:045E:00CB.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:02:07.0-1/input0
[    3.909137] usbcore: registered new interface driver usbhid
[    3.909143] usbhid: v2.6:USB HID core driver
[    4.740197] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[4a3f020004854058]
[    6.236029] floppy0: no floppy controllers found
[    6.370848] PM: Starting manual resume from disk
[    6.370853] PM: Resume from partition 8:5
[    6.370855] PM: Checking hibernation image.
[    6.371051] PM: Resume from disk failed.
[    6.414510] kjournald starting.  Commit interval 5 seconds
[    6.414523] EXT3-fs: mounted filesystem with ordered data mode.
[   13.315319] udev: starting version 141
[   13.640533] parport_pc 00:09: reported by Plug and Play ACPI
[   13.640569] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   13.990390] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   14.012547] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input7
[   14.048261] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.053350] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.201116] ACPI: I/O resource piix4_smbus [0x8040-0x8047] conflicts with ACPI region PMIO [0x8020-0x805f]
[   14.201123] ACPI: Device needs an ACPI driver
[   14.201138] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[   14.255788] Linux agpgart interface v0.103
[   14.259206] agpgart-ati 0000:00:00.0: Ati IGP9100/M chipset
[   14.263125] agpgart-ati 0000:00:00.0: AGP aperture is 32M @ 0xd2000000
[   14.282233] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:006b]
[   14.282261] yenta_cardbus 0000:02:04.0: Enabling burst memory read transactions
[   14.282269] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   14.282273] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   14.282282] yenta_cardbus 0000:02:04.0: TI: mfunc 0x01111d22, devctl 0x64
[   14.316183] ppdev: user-space parallel port driver
[   14.398806] cfg80211: Calling CRDA to update world regulatory domain
[   14.440571] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.513216] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0e18, PCI irq 17
[   14.513221] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[   14.513230] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   14.513235] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: clean.
[   14.513530] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   14.513535] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x67ffffff
[   14.514000] yenta_cardbus 0000:02:04.1: CardBus bridge found [103c:006b]
[   14.514020] yenta_cardbus 0000:02:04.1: Using CSCINT to route CSC interrupts to PCI
[   14.514023] yenta_cardbus 0000:02:04.1: Routing CardBus interrupts to PCI
[   14.514029] yenta_cardbus 0000:02:04.1: TI: mfunc 0x01111d22, devctl 0x64
[   14.516288] cfg80211: World regulatory domain updated:
[   14.516292]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.516296]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.516299]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.516302]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.516305]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.516308]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.691166] b43-phy0: Broadcom 4306 WLAN found
[   14.740154] phy0: Selected rate control algorithm 'pid'
[   14.745200] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x0e18, PCI irq 16
[   14.745205] yenta_cardbus 0000:02:04.1: Socket status: 30000006
[   14.745211] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #04 to #07
[   14.745220] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   14.745225] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa000-0xafff: clean.
[   14.745521] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   14.745525] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x67ffffff
[   14.992824] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   14.993998] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[   14.994525] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   14.994968] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07
[   14.995550] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.032342] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   15.103045] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[   15.129512] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 5 (level, low) -> IRQ 5
[   15.144276] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   15.421651] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   15.422816] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[   15.423342] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   15.423786] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07
[   15.424398] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   15.649751] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 5 (level, low) -> IRQ 5
[   16.536028] floppy0: no floppy controllers found
[   16.707508] lp0: using parport0 (interrupt-driven).
[   16.827888] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   17.388743] EXT3 FS on sda1, internal journal
[   18.652099] type=1505 audit(1286748224.244:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2082
[   18.725931] type=1505 audit(1286748224.316:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2086
[   18.726166] type=1505 audit(1286748224.316:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2086
[   18.726231] type=1505 audit(1286748224.316:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2086
[   18.726292] type=1505 audit(1286748224.316:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2086
[   18.884305] type=1505 audit(1286748224.476:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2091
[   18.884655] type=1505 audit(1286748224.476:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2091
[   18.921287] type=1505 audit(1286748224.512:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2095
[   23.452110] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.452114] Bluetooth: BNEP filters: protocol multicast
[   23.492058] Bridge firewalling registered
[   24.666510] pci 0000:01:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.269857] [drm] Initialized drm 1.1.0 20060810
[   25.489405] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   25.699414] agpgart-ati 0000:00:00.0: AGP 3.0 bridge
[   25.699436] agpgart-ati 0000:00:00.0: putting AGP V3 device into 8x mode
[   25.699460] pci 0000:01:05.0: putting AGP V3 device into 8x mode
[   25.844557] [drm] Setting GART location based on new memory map
[   25.844566] [drm] Loading R200 Microcode
[   25.844612] [drm] writeback test succeeded in 1 usecs
[   28.408511] eth0: link down
[   28.408815] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.629147] input: b43-phy0 as /devices/virtual/input/input10
[   28.656037] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   28.833284] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   28.893019] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   28.979043] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   29.124027] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   29.185723] Registered led device: b43-phy0::tx
[   29.187430] Registered led device: b43-phy0::rx
[   29.187503] Registered led device: b43-phy0::radio
[   29.204030] b43-phy0: Radio turned on by software
[   29.204326] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.643381] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   41.643387] ata1.00: BMDMA stat 0x24
[   41.643396] ata1.00: cmd c8/00:d8:3f:b1:04/00:00:00:00:00/e0 tag 0 dma 110592 in
[   41.643397]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   41.643401] ata1.00: status: { DRDY ERR }
[   41.643404] ata1.00: error: { UNC }
[   41.680395] ata1.00: configured for UDMA/100
[   41.680408] ata1: EH complete
[   43.808153] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   43.808158] ata1.00: BMDMA stat 0x24
[   43.808166] ata1.00: cmd c8/00:d8:3f:b1:04/00:00:00:00:00/e0 tag 0 dma 110592 in
[   43.808167]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   43.808171] ata1.00: status: { DRDY ERR }
[   43.808173] ata1.00: error: { UNC }
[   43.832401] ata1.00: configured for UDMA/100
[   43.832411] ata1: EH complete
[   45.961897] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   45.961901] ata1.00: BMDMA stat 0x24
[   45.961908] ata1.00: cmd c8/00:d8:3f:b1:04/00:00:00:00:00/e0 tag 0 dma 110592 in
[   45.961910]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   45.961913] ata1.00: status: { DRDY ERR }
[   45.961916] ata1.00: error: { UNC }
[   46.000378] ata1.00: configured for UDMA/100
[   46.000389] ata1: EH complete
[   48.126678] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   48.126683] ata1.00: BMDMA stat 0x24
[   48.126689] ata1.00: cmd c8/00:d8:3f:b1:04/00:00:00:00:00/e0 tag 0 dma 110592 in
[   48.126691]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   48.126694] ata1.00: status: { DRDY ERR }
[   48.126697] ata1.00: error: { UNC }
[   48.148377] ata1.00: configured for UDMA/100
[   48.148388] ata1: EH complete
[   50.280367] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   50.280374] ata1.00: BMDMA stat 0x24
[   50.280381] ata1.00: cmd c8/00:d8:3f:b1:04/00:00:00:00:00/e0 tag 0 dma 110592 in
[   50.280382]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   50.280386] ata1.00: status: { DRDY ERR }
[   50.280388] ata1.00: error: { UNC }
[   50.320401] ata1.00: configured for UDMA/100
[   50.320419] ata1: EH complete
[   52.445135] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   52.445139] ata1.00: BMDMA stat 0x24
[   52.445147] ata1.00: cmd c8/00:d8:3f:b1:04/00:00:00:00:00/e0 tag 0 dma 110592 in
[   52.445148]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   52.445152] ata1.00: status: { DRDY ERR }
[   52.445154] ata1.00: error: { UNC }
[   52.468403] ata1.00: configured for UDMA/100
[   52.468420] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   52.468425] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   52.468433] Descriptor sense data with sense descriptors (in hex):
[   52.468435]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   52.468449]         00 04 b1 d3 
[   52.468454] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   52.468462] end_request: I/O error, dev sda, sector 307667
[   52.468490] ata1: EH complete
[   52.494590] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[   52.494748] sd 0:0:0:0: [sda] Write Protect is off
[   52.494753] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   52.495208] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   52.495579] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[   52.495708] sd 0:0:0:0: [sda] Write Protect is off
[   52.495711] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   52.495980] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   55.065064] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   55.065070] ata1.00: BMDMA stat 0x24
[   55.065078] ata1.00: cmd c8/00:08:cf:b1:04/00:00:00:00:00/e0 tag 0 dma 4096 in
[   55.065079]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   55.065083] ata1.00: status: { DRDY ERR }
[   55.065085] ata1.00: error: { UNC }
[   55.088399] ata1.00: configured for UDMA/100
[   55.088411] ata1: EH complete
[   57.218733] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   57.218739] ata1.00: BMDMA stat 0x24
[   57.218747] ata1.00: cmd c8/00:08:cf:b1:04/00:00:00:00:00/e0 tag 0 dma 4096 in
[   57.218748]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   57.218752] ata1.00: status: { DRDY ERR }
[   57.218755] ata1.00: error: { UNC }
[   57.256405] ata1.00: configured for UDMA/100
[   57.256416] ata1: EH complete
[   59.383501] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   59.383506] ata1.00: BMDMA stat 0x24
[   59.383513] ata1.00: cmd c8/00:08:cf:b1:04/00:00:00:00:00/e0 tag 0 dma 4096 in
[   59.383515]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   59.383518] ata1.00: status: { DRDY ERR }
[   59.383520] ata1.00: error: { UNC }
[   59.404401] ata1.00: configured for UDMA/100
[   59.404410] ata1: EH complete
[   61.526074] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   61.526078] ata1.00: BMDMA stat 0x24
[   61.526085] ata1.00: cmd c8/00:08:cf:b1:04/00:00:00:00:00/e0 tag 0 dma 4096 in
[   61.526087]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   61.526090] ata1.00: status: { DRDY ERR }
[   61.526093] ata1.00: error: { UNC }
[   61.548402] ata1.00: configured for UDMA/100
[   61.548412] ata1: EH complete
[   63.679730] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   63.679733] ata1.00: BMDMA stat 0x24
[   63.679739] ata1.00: cmd c8/00:08:cf:b1:04/00:00:00:00:00/e0 tag 0 dma 4096 in
[   63.679741]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   63.679744] ata1.00: status: { DRDY ERR }
[   63.679746] ata1.00: error: { UNC }
[   63.716402] ata1.00: configured for UDMA/100
[   63.716410] ata1: EH complete
[   65.833394] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   65.833398] ata1.00: BMDMA stat 0x24
[   65.833404] ata1.00: cmd c8/00:08:cf:b1:04/00:00:00:00:00/e0 tag 0 dma 4096 in
[   65.833405]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   65.833408] ata1.00: status: { DRDY ERR }
[   65.833411] ata1.00: error: { UNC }
[   65.872403] ata1.00: configured for UDMA/100
[   65.872415] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   65.872420] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   65.872427] Descriptor sense data with sense descriptors (in hex):
[   65.872430]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   65.872444]         00 04 b1 d3 
[   65.872450] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   65.872457] end_request: I/O error, dev sda, sector 307667
[   65.872477] ata1: EH complete
[   65.872741] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[   65.872870] sd 0:0:0:0: [sda] Write Protect is off
[   65.872874] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   65.873322] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   65.916697] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[   65.926084] sd 0:0:0:0: [sda] Write Protect is off
[   65.926088] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   65.939549] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   73.912907] wlan0: authenticate with AP 00:11:50:12:a2:87
[   73.914371] wlan0: authenticated
[   73.914377] wlan0: associate with AP 00:11:50:12:a2:87
[   73.917880] wlan0: RX AssocResp from 00:11:50:12:a2:87 (capab=0x411 status=0 aid=3)
[   73.917883] wlan0: associated
[   73.918225] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   84.604015] wlan0: no IPv6 routers present
[  153.564610] usb 4-1: USB disconnect, address 2
[  155.172017] usb 4-1: new low speed USB device using ohci_hcd and address 3
[  155.385920] usb 4-1: configuration #1 chosen from 1 choice
[  155.404082] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:14.4/0000:02:07.0/usb4/4-1/4-1:1.0/input/input11
[  155.430329] generic-usb 0003:045E:00CB.0002: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:02:07.0-1/input0
[  272.508020] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  272.641519] usb 1-3: configuration #1 chosen from 1 choice
[  273.761816] Initializing USB Mass Storage driver...
[  273.762050] scsi2 : SCSI emulation for USB Mass Storage devices
[  273.762264] usbcore: registered new interface driver usb-storage
[  273.762271] USB Mass Storage support registered.
[  273.762528] usb-storage: device found at 3
[  273.762532] usb-storage: waiting for device to settle before scanning
[  278.761499] usb-storage: device scan complete
[  278.761945] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[  278.762313] scsi 2:0:0:1: CD-ROM            SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0
[  278.763576] sd 2:0:0:0: [sdb] 15682559 512-byte hardware sectors: (8.02 GB/7.47 GiB)
[  278.765489] sd 2:0:0:0: [sdb] Write Protect is off
[  278.765497] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  278.765502] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  278.770608] sd 2:0:0:0: [sdb] 15682559 512-byte hardware sectors: (8.02 GB/7.47 GiB)
[  278.771268] sd 2:0:0:0: [sdb] Write Protect is off
[  278.771274] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  278.771279] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  278.771340]  sdb: sdb1
[  278.778087] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  278.778261] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  278.811812] sr1: scsi3-mmc drive: 48x/48x tray
[  278.812609] sr 2:0:0:1: Attached scsi CD-ROM sr1
[  278.812799] sr 2:0:0:1: Attached scsi generic sg3 type 5
[  374.526742] usb 1-3: USB disconnect, address 3
[  556.472019] usb 1-2: new high speed USB device using ehci_hcd and address 4
[  556.605035] usb 1-2: configuration #1 chosen from 1 choice
[  556.614968] scsi3 : SCSI emulation for USB Mass Storage devices
[  556.615433] usb-storage: device found at 4
[  556.615437] usb-storage: waiting for device to settle before scanning
[  561.612464] usb-storage: device scan complete
[  561.612926] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[  561.613481] scsi 3:0:0:1: CD-ROM            SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0
[  561.615415] sd 3:0:0:0: [sdb] 15682559 512-byte hardware sectors: (8.02 GB/7.47 GiB)
[  561.615921] sd 3:0:0:0: [sdb] Write Protect is off
[  561.615934] sd 3:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  561.615940] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  561.622416] sd 3:0:0:0: [sdb] 15682559 512-byte hardware sectors: (8.02 GB/7.47 GiB)
[  561.622905] sd 3:0:0:0: [sdb] Write Protect is off
[  561.622911] sd 3:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  561.622916] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  561.622995]  sdb: sdb1
[  561.624808] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  561.624979] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  561.630479] sr1: scsi3-mmc drive: 48x/48x tray
[  561.630697] sr 3:0:0:1: Attached scsi CD-ROM sr1
[  561.630855] sr 3:0:0:1: Attached scsi generic sg3 type 5
[  803.649314] usb 1-2: USB disconnect, address 4
[  826.808019] usb 1-2: new high speed USB device using ehci_hcd and address 5
[  826.940984] usb 1-2: configuration #1 chosen from 1 choice
[  826.949270] scsi4 : SCSI emulation for USB Mass Storage devices
[  826.949524] usb-storage: device found at 5
[  826.949528] usb-storage: waiting for device to settle before scanning
[  831.949060] usb-storage: device scan complete
[  831.949502] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[  831.949991] scsi 4:0:0:1: CD-ROM            SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0
[  831.953594] sd 4:0:0:0: [sdb] 15682559 512-byte hardware sectors: (8.02 GB/7.47 GiB)
[  831.954373] sd 4:0:0:0: [sdb] Write Protect is off
[  831.954379] sd 4:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  831.954383] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  831.956033] sd 4:0:0:0: [sdb] 15682559 512-byte hardware sectors: (8.02 GB/7.47 GiB)
[  831.959116] sd 4:0:0:0: [sdb] Write Protect is off
[  831.959124] sd 4:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  831.959128] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  831.959188]  sdb: sdb1
[  831.983220] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  831.983429] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  831.999612] sr1: scsi3-mmc drive: 48x/48x tray
[  831.999872] sr 4:0:0:1: Attached scsi CD-ROM sr1
[  832.000038] sr 4:0:0:1: Attached scsi generic sg3 type 5[/PHP]

---

### Post by P4man on 2010-10-11
You have a problem with the harddisk. Your log is full of media errors for sda like here:

[   48.126678] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   48.126683] ata1.00: BMDMA stat 0x24
[   48.126689] ata1.00: cmd c8/00:d8:3f:b1:04/00:00:00:00:00/e0 tag 0 dma 110592 in
[   48.126691]          res 51/40:00:d3:b1:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[   48.126694] ata1.00: status: { DRDY ERR }
[   48.126697] ata1.00: error: { UNC }

It could be a bad cable or a problem with the controller, but by far most likely is that the drive itself is dying/dead.

The "disk utility" with smart status the other poster mentioned is only included in Lucid (10.04) and newer, maybe from 9.10, but you seem to be using Jaunty (9.04).

Either grab a more recent ubuntu version and boot from the cd, or install smartmontools from your current livecd. Look here:
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

I suspect that will only serve to confirm you need to replace your harddrive.

---

### Post by bobmounger on 2010-10-11
I am seeing a very similar problem on an acer aspire netbook. I left a partition on the hard drive to run xp. & have been running jaunty/karmic/lucid with no trouble. Yesterday I set the update manager to normal updates & when maverick showed up I installed it. The install went fine, but at the restart step it wanted to check the hard drive & the rest is as techiewannabe describes. 
 
When I tried to follow this procedure, doing ls/media didn't show anything. when I went back into GUI mode there was an error message on the screen that said that I don't have the authority to mount a usb stick. I found the help on mounting & will probably roll back to 10.4

---

### Post by P4man on 2010-10-11
You mean mount a usb stick? 
I guess..

make a mountpoint:

```
sudo mkdir /media/usb
```

Find out what driver letter your stick got assigned. 

```
sudo fdisk -l
```

If you only have 1 harddisk, it will likely be /dev/sdb

then mount it

```
sudo mount /dev/sd**b**1 /media/usb
```

Replace 'b' with whatever matches your USB stick

But if your filesystem is mounted as read-only because of serious hdd trouble, then this wont work.

---

### Post by techiewannabe on 2010-10-11
P4man:

Thanks for your posting. When I get back from work this evening, I will boot from a Lucid CD and test the hard drive. If the drive is the problem, as you suggest, it may account for other problems I have experienced recently, including difficulties I had in using subsequent versions of Ubuntu. (I had tried upgrading to Lucid but had a lot of trouble and finally reverted to 9.04)

Thanks again. 

I'll post the outcome of my findings.

Techiewannabe

---

### Post by techiewannabe on 2010-10-11
P4man:

I was able to get to the system before going off to work. As you suggested, I inserted a Live CD of Lucid. I used the disk utility and clicked the "Check File System" for the hard drive. The report was: "File system is clean."

Ideas?

Thanks, again.

Techiewannabe

---

### Post by P4man on 2010-10-11
Its not the filesystem you have to check, its the SMART status that may reveal a dying disk

---

### Post by techiewannabe on 2010-10-11
P4man:

Thanks for your note. Per your suggestion, I went back into the Disk Utility. Apparently, my hard drive is not SMART compatible. 
....I think I'll be buying a new hard drive... :(

Thanks for your help.

Techiewannabe

---

### Post by P4man on 2010-10-12
There are (non smart) tools for every brand of harddrive. Check your manufacters website or use ultimate boot cd to check the harddrive.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

edit: you have a seagate harddrive. I think the tool for seagate is called seatools.

---

### Post by techiewannabe on 2010-10-12
P4man:
Thanks very much for your suggestion. I've downloaded a copy of SeaTools and will try it out when I get home from work this evening. I'll let you know how it goes.
You've been very helpful.
Techiewannabe

---

### Post by techiewannabe on 2010-10-13
After using the diagnostic software, it became obvious that it was a problem with the hard drive. Now, in hindsight, I recall a few times when the hard drive was making noises. (It was making a clicking sound while I was across the room, away from the computer. This happened a couple of times.) The drive was definitely on its way out. I have no idea why this is so. The drive was less than 18 months old, I think. On the other hand, we know that they are going to die sooner or later. 

I put in a new drive and it is being loaded as I type this note. I'll try Lucid on this drive. I had trouble with Lucid before but, perhaps the problem were related to the drive, itself.

Special thanks to P4man for your help. 

Techiewannabe

---

