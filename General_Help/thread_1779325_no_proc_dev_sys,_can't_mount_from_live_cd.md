---
title: "no /proc /dev /sys, can't mount from live cd"
date: 2011-06-10
forum: General Help
---

### Post by elwon20 on 2011-06-10
Hi, I'm running ubuntu 10.10 (from a live cd right now). I booted up my laptop with a flat battery and the power came out mid boot. Laptop instantly died as you'd expect. Upon replacing the power cable and rebooting I received an error stating that the system couldn't find /proc /dev or /sys. I immediately thought grub error and booted to a live cd to reinstall grub. unfortunately I cannot mount my filesystem to repair it. so now i'm thinking maybe it isn't grub. I ran the boot info script which failed so I ran it from another distro and this is the output:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4e364903

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   179,911,934   179,911,872   7 NTFS / exFAT / HPFS
/dev/sda2         179,911,935   625,137,344   445,225,410   5 Extended
/dev/sda5         179,911,998   607,032,089   427,120,092  83 Linux
/dev/sda6         607,032,153   625,137,344    18,105,192  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6C5004665004397A                       ntfs       
/dev/sda5        da1fb084-0264-46ed-a26b-784dd7c818a6   ext4       
/dev/sda6        5fa9e2e2-fe16-42a6-afab-62299205e694   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /mnt/sda1                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sr0         /mnt/sr0                 iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file

```

Is there any way I can repair this or get it to mount? Or is it completely screwed? Because I'd really rather avoid a complete fresh install if at all possible.

Thanks in advance!

---

### Post by psusi on 2011-06-10
Apparently whatever distro you did this from is so old that it doesn't understand ext4.  Use the Ubuntu livecd instead.

---

### Post by elwon20 on 2011-06-10
I did it from a fully up to date copy of slax. As I said, it wouldn't work on the live cd. It just stops at sda5. So I searched the forum and found someone with the same problem, they were recommended to try running the script from slax, the person didn't bother though they just reinstalled. But I took that advice and used slax.

---

### Post by psusi on 2011-06-10
Try running sudo e2fsck /dev/sda5 from the Ubuntu livecd then instead of the boot info script.

---

### Post by elwon20 on 2011-06-10
Rebooted, straight into live CD opened terminal pasted ran command.

```
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda5
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?

```I haven't attempted to mount it or anything. Ideas?

In case it helps:
```
ubuntu@ubuntu:~$ umount /dev/sda5
umount: /dev/sda5 is not mounted (according to mtab)

```

---

### Post by psusi on 2011-06-10
Try it again or cat /proc/mounts?  Also check dmesg.

---

### Post by elwon20 on 2011-06-10
Tried again, same result. cat /proc/mounts/ no sda5 as far as i can see.
```
ubuntu@ubuntu:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=1539616k,nr_inodes=211984,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /cow tmpfs rw,noatime,mode=755 0 0
aufs / aufs rw,noatime,si=97a2afdd 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0

```
dmesg is very long and seems to just be repeated logs of my wlan0 disconnecting and reconnecting. I can paste it if you like?

---

### Post by elwon20 on 2011-06-10
Rebooted copied whole of dmesg. Don't know if it's of any use but here it is in case it helps:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda5
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e400 (usable)
[    0.000000]  BIOS-e820: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9bd000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9bd000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd65000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd65000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xbfd65 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BFE00000 mask FFFE00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e400 (usable)
[    0.000000]  modified: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  modified: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  modified: 00000000bf8a7000 - 00000000bf9bd000 (usable)
[    0.000000]  modified: 00000000bf9bd000 - 00000000bfa0f000 (reserved)
[    0.000000]  modified: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  modified: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  modified: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  modified: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  modified: 00000000bfd1f000 - 00000000bfd65000 (usable)
[    0.000000]  modified: 00000000bfd65000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  modified: 00000000bfd9f000 - 00000000bfe00000 (ACPI data)
[    0.000000]  modified: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f7320] f7320
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 7f51e000 - 80000000
[    0.000000] Allocated new RAMDISK: 009a5000 - 0148698f
[    0.000000] Move RAMDISK from 000000007f51e000 - 000000007ffff98e to 009a5000 - 0148698e
[    0.000000] ACPI: RSDP 000f7280 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bfdf8314 0006C (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfde8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfde9000 06876 (v02 Intel  CANTIGA  06040000 INTL 20050624)
[    0.000000] ACPI: FACS bfd9efc0 00040
[    0.000000] ACPI: HPET bfdfed86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfdfedbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bfdfedfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfdfee62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bfdfee8a 00176 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT bfde7000 005F9 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2181MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfd65
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9bd
[    0.000000]     0: 0x000bfa0f -> 0x000bfb08
[    0.000000]     0: 0x000bfd0f -> 0x000bfd18
[    0.000000]     0: 0x000bfd1f -> 0x000bfd65
[    0.000000] On node 0 totalpages: 785037
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1488200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4363 pages used for memmap
[    0.000000]   HighMem zone: 553462 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s36416 r0 d20928 u2097152
[    0.000000] early_res array is doubled to 128 at [16800 - 177ff]
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 778898
[    0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15714980 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (63 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a1000 - 00009a41b8]             BRK
[    0.000000]   #4 [00000f7330 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f7320 - 00000f7330]    MP-table mpf
[    0.000000]   #6 [000009e400 - 000009e871]   BIOS reserved
[    0.000000]   #7 [000009e9fd - 00000f7320]   BIOS reserved
[    0.000000]   #8 [000009e871 - 000009e9fd]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a5000 - 0001487000]     NEW RAMDISK
[    0.000000]   #13 [0001487000 - 0001488000]         BOOTMEM
[    0.000000]   #14 [0001488000 - 0002c88000]         BOOTMEM
[    0.000000]   #15 [0002c88000 - 0002c88004]         BOOTMEM
[    0.000000]   #16 [0002c88040 - 0002c88100]         BOOTMEM
[    0.000000]   #17 [0002c88100 - 0002c88154]         BOOTMEM
[    0.000000]   #18 [0002c88180 - 0002c8b180]         BOOTMEM
[    0.000000]   #19 [0002c8b180 - 0002c8b250]         BOOTMEM
[    0.000000]   #20 [0002c8b280 - 0002c97280]         BOOTMEM
[    0.000000]   #21 [0002c97280 - 0002c972a5]         BOOTMEM
[    0.000000]   #22 [0002c972c0 - 0002c972e7]         BOOTMEM
[    0.000000]   #23 [0002c97300 - 0002c975bc]         BOOTMEM
[    0.000000]   #24 [0002c975c0 - 0002c97600]         BOOTMEM
[    0.000000]   #25 [0002c97600 - 0002c97640]         BOOTMEM
[    0.000000]   #26 [0002c97640 - 0002c97680]         BOOTMEM
[    0.000000]   #27 [0002c97680 - 0002c976c0]         BOOTMEM
[    0.000000]   #28 [0002c976c0 - 0002c97700]         BOOTMEM
[    0.000000]   #29 [0002c97700 - 0002c97740]         BOOTMEM
[    0.000000]   #30 [0002c97740 - 0002c97780]         BOOTMEM
[    0.000000]   #31 [0002c97780 - 0002c977c0]         BOOTMEM
[    0.000000]   #32 [0002c977c0 - 0002c97800]         BOOTMEM
[    0.000000]   #33 [0002c97800 - 0002c97840]         BOOTMEM
[    0.000000]   #34 [0002c97840 - 0002c97880]         BOOTMEM
[    0.000000]   #35 [0002c97880 - 0002c978c0]         BOOTMEM
[    0.000000]   #36 [0002c978c0 - 0002c97900]         BOOTMEM
[    0.000000]   #37 [0002c97900 - 0002c97940]         BOOTMEM
[    0.000000]   #38 [0002c97940 - 0002c97980]         BOOTMEM
[    0.000000]   #39 [0002c97980 - 0002c979c0]         BOOTMEM
[    0.000000]   #40 [0002c979c0 - 0002c97a00]         BOOTMEM
[    0.000000]   #41 [0002c97a00 - 0002c97a40]         BOOTMEM
[    0.000000]   #42 [0002c97a40 - 0002c97a80]         BOOTMEM
[    0.000000]   #43 [0002c97a80 - 0002c97ac0]         BOOTMEM
[    0.000000]   #44 [0002c97ac0 - 0002c97b00]         BOOTMEM
[    0.000000]   #45 [0002c97b00 - 0002c97b40]         BOOTMEM
[    0.000000]   #46 [0002c97b40 - 0002c97b80]         BOOTMEM
[    0.000000]   #47 [0002c97b80 - 0002c97bc0]         BOOTMEM
[    0.000000]   #48 [0002c97bc0 - 0002c97bd0]         BOOTMEM
[    0.000000]   #49 [0002c97c00 - 0002c97c64]         BOOTMEM
[    0.000000]   #50 [0002c97c80 - 0002c97ce4]         BOOTMEM
[    0.000000]   #51 [0003000000 - 000300e000]         BOOTMEM
[    0.000000]   #52 [0003200000 - 000320e000]         BOOTMEM
[    0.000000]   #53 [0002c99d00 - 0002c99d04]         BOOTMEM
[    0.000000]   #54 [0002c99d40 - 0002c99d44]         BOOTMEM
[    0.000000]   #55 [0002c99d80 - 0002c99d88]         BOOTMEM
[    0.000000]   #56 [0002c99dc0 - 0002c99dc8]         BOOTMEM
[    0.000000]   #57 [0002c99e00 - 0002c99ea8]         BOOTMEM
[    0.000000]   #58 [0002c99ec0 - 0002c99f28]         BOOTMEM
[    0.000000]   #59 [0002c99f40 - 0002c9df40]         BOOTMEM
[    0.000000]   #60 [0002c9df40 - 0002d1df40]         BOOTMEM
[    0.000000]   #61 [0002d1df40 - 0002d5df40]         BOOTMEM
[    0.000000]   #62 [000320e000 - 000410aaa4]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfd65)
[    0.000000] Memory: 3079236k/3143060k available (4928k kernel code, 60912k reserved, 2336k data, 684k init, 2231300k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.020 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.04 BogoMIPS (lpj=7980080)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004032] Security Framework initialized
[    0.004049] AppArmor: AppArmor initialized
[    0.004052] Yama: becoming mindful.
[    0.004108] Mount-cache hash table entries: 512
[    0.004247] Initializing cgroup subsys ns
[    0.004252] Initializing cgroup subsys cpuacct
[    0.004257] Initializing cgroup subsys memory
[    0.004266] Initializing cgroup subsys devices
[    0.004268] Initializing cgroup subsys freezer
[    0.004270] Initializing cgroup subsys net_cls
[    0.004299] CPU: Physical Processor ID: 0
[    0.004302] CPU: Processor Core ID: 0
[    0.004304] mce: CPU supports 6 MCE banks
[    0.004314] CPU0: Thermal monitoring enabled (TM2)
[    0.004318] using mwait in idle threads.
[    0.004326] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.004332] PEBS disabled due to CPU errata.
[    0.004339] ... version:                2
[    0.004341] ... bit width:              40
[    0.004343] ... generic registers:      2
[    0.004345] ... value mask:             000000ffffffffff
[    0.004347] ... max period:             000000007fffffff
[    0.004349] ... fixed-purpose events:   3
[    0.004350] ... event mask:             0000000700000003
[    0.007251] ACPI: Core revision 20100428
[    0.020011] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.020015] ftrace: allocating 21758 entries in 43 pages
[    0.024057] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024421] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066577] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[    0.068000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.156016] Brought up 2 CPUs
[    0.156019] Total of 2 processors activated (7979.95 BogoMIPS).
[    0.156533] devtmpfs: initialized
[    0.157032] regulator: core version 0.5
[    0.157063] Time: 21:02:56  Date: 06/10/11
[    0.157106] NET: Registered protocol family 16
[    0.157129] Trying to unpack rootfs image as initramfs...
[    0.157241] EISA bus registered
[    0.157250] ACPI: bus type pci registered
[    0.157331] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.157335] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.157337] PCI: Using MMCONFIG for extended config space
[    0.157339] PCI: Using configuration type 1 for base access
[    1.156172] bio: create slab <bio-0> at 0
[    1.158312] ACPI: EC: Look up EC in DSDT
[    1.163622] ACPI: BIOS _OSI(Linux) query ignored
[    1.165853] ACPI: SSDT bfd1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    1.166425] ACPI: Dynamic OEM Table Load:
[    1.166429] ACPI: SSDT (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    1.166978] ACPI: SSDT bfd18020 00C78 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    1.167527] ACPI: Dynamic OEM Table Load:
[    1.167531] ACPI: SSDT (null) 00C78 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    1.168359] ACPI: SSDT bfd19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    1.168954] ACPI: Dynamic OEM Table Load:
[    1.168958] ACPI: SSDT (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    1.169143] ACPI: SSDT bfd19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    1.169710] ACPI: Dynamic OEM Table Load:
[    1.169714] ACPI: SSDT (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    1.170410] ACPI: Interpreter enabled
[    1.170410] ACPI: (supports S0 S3 S4 S5)
[    1.170410] ACPI: Using IOAPIC for interrupt routing
[    1.170410] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    1.178219] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.178219] ACPI: Power Resource [FN00] (off)
[    1.178219] ACPI: Power Resource [FN01] (off)
[    1.178219] ACPI: No dock devices found.
[    1.178219] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.180021] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.181152] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.181156] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.181159] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.181163] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    1.181166] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    1.181170] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    1.181273] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.181277] pci 0000:00:01.0: PME# disabled
[    1.181379] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    1.181477] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    1.181576] pci 0000:00:1a.2: reg 20: [io  0x1840-0x185f]
[    1.181667] pci 0000:00:1a.7: reg 10: [mem 0xfc204800-0xfc204bff]
[    1.181741] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.181747] pci 0000:00:1a.7: PME# disabled
[    1.181799] pci 0000:00:1b.0: reg 10: [mem 0xfc200000-0xfc203fff 64bit]
[    1.181867] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.181872] pci 0000:00:1b.0: PME# disabled
[    1.181981] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.181986] pci 0000:00:1c.0: PME# disabled
[    1.182100] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.182105] pci 0000:00:1c.2: PME# disabled
[    1.182217] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.182222] pci 0000:00:1c.3: PME# disabled
[    1.182302] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
[    1.182400] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
[    1.182500] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
[    1.182595] pci 0000:00:1d.7: reg 10: [mem 0xfc204c00-0xfc204fff]
[    1.182669] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.182675] pci 0000:00:1d.7: PME# disabled
[    1.182930] pci 0000:00:1f.2: reg 10: [io  0x18f0-0x18f7]
[    1.182939] pci 0000:00:1f.2: reg 14: [io  0x18e4-0x18e7]
[    1.182948] pci 0000:00:1f.2: reg 18: [io  0x18e8-0x18ef]
[    1.182957] pci 0000:00:1f.2: reg 1c: [io  0x18e0-0x18e3]
[    1.182966] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18df]
[    1.182975] pci 0000:00:1f.2: reg 24: [mem 0xfc204000-0xfc2047ff]
[    1.183029] pci 0000:00:1f.2: PME# supported from D3hot
[    1.183034] pci 0000:00:1f.2: PME# disabled
[    1.183078] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff 64bit]
[    1.183099] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    1.183210] pci 0000:01:00.0: reg 10: [mem 0xce000000-0xceffffff]
[    1.183228] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.183246] pci 0000:01:00.0: reg 1c: [mem 0xcc000000-0xcdffffff 64bit]
[    1.183256] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    1.183266] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    1.188023] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.188028] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    1.188032] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    1.188038] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.188154] pci 0000:02:00.0: reg 10: [mem 0xf6000000-0xf600ffff 64bit]
[    1.188254] pci 0000:02:00.0: PME# supported from D3hot
[    1.188261] pci 0000:02:00.0: PME# disabled
[    1.188295] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.188309] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    1.188314] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    1.188320] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    1.188329] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    1.188397] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    1.188402] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    1.188408] pci 0000:00:1c.2:   bridge window [mem 0xf8000000-0xf9ffffff]
[    1.188417] pci 0000:00:1c.2:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    1.188791] pci 0000:06:00.0: reg 10: [mem 0xfa000000-0xfa003fff 64bit]
[    1.188842] pci 0000:06:00.0: reg 18: [io  0x5000-0x50ff]
[    1.189042] pci 0000:06:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    1.189367] pci 0000:06:00.0: supports D1 D2
[    1.189370] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.189395] pci 0000:06:00.0: PME# disabled
[    1.196078] pci 0000:00:1c.3: PCI bridge to [bus 06-07]
[    1.196084] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    1.196089] pci 0000:00:1c.3:   bridge window [mem 0xfa000000-0xfbffffff]
[    1.196098] pci 0000:00:1c.3:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    1.196194] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
[    1.196200] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.196205] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.196214] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.196217] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.196220] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.196223] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.196226] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    1.196228] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    1.196231] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    1.196265] pci_bus 0000:00: on NUMA node 0
[    1.196273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.196550] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    1.196728] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.196837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.196930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.210270] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[    1.210389] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    1.210505] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
[    1.210621] ACPI: PCI Interrupt Link [LNKD] (IRQs *5)
[    1.210736] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[    1.210856] ACPI: PCI Interrupt Link [LNKF] (IRQs *10)
[    1.210972] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
[    1.211087] ACPI: PCI Interrupt Link [LNKH] (IRQs *5)
[    1.211137] HEST: Table is not found!
[    1.211247] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.211251] vgaarb: loaded
[    1.211422] SCSI subsystem initialized
[    1.211499] libata version 3.00 loaded.
[    1.211557] usbcore: registered new interface driver usbfs
[    1.211571] usbcore: registered new interface driver hub
[    1.211598] usbcore: registered new device driver usb
[    1.211739] ACPI: WMI: Mapper loaded
[    1.211742] PCI: Using ACPI for IRQ routing
[    1.211744] PCI: pci_cache_line_size set to 64 bytes
[    1.211903] reserve RAM buffer: 000000000009e400 - 000000000009ffff 
[    1.211906] reserve RAM buffer: 00000000bf8a1000 - 00000000bfffffff 
[    1.211911] reserve RAM buffer: 00000000bf9bd000 - 00000000bfffffff 
[    1.211915] reserve RAM buffer: 00000000bfb08000 - 00000000bfffffff 
[    1.211919] reserve RAM buffer: 00000000bfd18000 - 00000000bfffffff 
[    1.211922] reserve RAM buffer: 00000000bfd65000 - 00000000bfffffff 
[    1.212029] NetLabel: Initializing
[    1.212031] NetLabel:  domain hash size = 128
[    1.212033] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.212046] NetLabel:  unlabeled traffic allowed by default
[    1.212079] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    1.212087] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.212093] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    2.340051] Switching to clocksource tsc
[    2.353740] AppArmor: AppArmor Filesystem Enabled
[    2.353767] pnp: PnP ACPI init
[    2.353804] ACPI: bus type pnp registered
[    2.355322] pnp 00:05: disabling [io  0x5000-0x500f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x5000-0x5fff]
[    2.355349] pnp 00:05: disabling [io  0x5000-0x500f disabled] because it overlaps 0000:06:00.0 BAR 2 [io  0x5000-0x50ff]
[    2.356780] pnp: PnP ACPI: found 11 devices
[    2.356786] ACPI: ACPI bus type pnp unregistered
[    2.356792] PnPBIOS: Disabled by ACPI PNP
[    2.356815] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    2.356826] system 00:05: [io  0x0680-0x069f] has been reserved
[    2.356829] system 00:05: [io  0x0480-0x048f] has been reserved
[    2.356833] system 00:05: [io  0xffff] has been reserved
[    2.356836] system 00:05: [io  0xffff] has been reserved
[    2.356839] system 00:05: [io  0x0400-0x047f] has been reserved
[    2.356842] system 00:05: [io  0x0480-0x048f] has been reserved
[    2.356845] system 00:05: [io  0x1180-0x11ff] has been reserved
[    2.356848] system 00:05: [io  0x164e-0x164f] has been reserved
[    2.356851] system 00:05: [io  0xfe00] has been reserved
[    2.356857] system 00:06: [io  0x06a0-0x06af] has been reserved
[    2.356860] system 00:06: [io  0x06b0-0x06ff] has been reserved
[    2.356868] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    2.356871] system 00:0a: [mem 0xfed10000-0xfed13fff] has been reserved
[    2.356874] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    2.356877] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    2.356881] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    2.356884] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    2.356887] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    2.356890] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    2.393205] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0000000-0xc00000ff 64bit]
[    2.393217] pci 0000:00:1f.3: BAR 0: set to [mem 0xc0000000-0xc00000ff 64bit] (PCI address [0xc0000000-0xc00000ff]
[    2.393221] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    2.393224] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.393228] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    2.393233] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    2.393237] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.393243] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    2.393247] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    2.393254] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    2.393260] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    2.393269] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    2.393273] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    2.393280] pci 0000:00:1c.2:   bridge window [mem 0xf8000000-0xf9ffffff]
[    2.393286] pci 0000:00:1c.2:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    2.393295] pci 0000:06:00.0: BAR 6: assigned [mem 0xf4000000-0xf401ffff pref]
[    2.393298] pci 0000:00:1c.3: PCI bridge to [bus 06-07]
[    2.393302] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    2.393309] pci 0000:00:1c.3:   bridge window [mem 0xfa000000-0xfbffffff]
[    2.393315] pci 0000:00:1c.3:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    2.393324] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[    2.393326] pci 0000:00:1e.0:   bridge window [io  disabled]
[    2.393332] pci 0000:00:1e.0:   bridge window [mem disabled]
[    2.393337] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    2.393358]   alloc irq_desc for 16 on node -1
[    2.393361]   alloc kstat_irqs on node -1
[    2.393369] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.393374] pci 0000:00:01.0: setting latency timer to 64
[    2.393385]   alloc irq_desc for 17 on node -1
[    2.393387]   alloc kstat_irqs on node -1
[    2.393392] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.393397] pci 0000:00:1c.0: setting latency timer to 64
[    2.393412]   alloc irq_desc for 18 on node -1
[    2.393414]   alloc kstat_irqs on node -1
[    2.393418] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.393424] pci 0000:00:1c.2: setting latency timer to 64
[    2.393437]   alloc irq_desc for 19 on node -1
[    2.393439]   alloc kstat_irqs on node -1
[    2.393443] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.393448] pci 0000:00:1c.3: setting latency timer to 64
[    2.393459] pci 0000:00:1e.0: setting latency timer to 64
[    2.393464] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.393467] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.393469] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.393472] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    2.393474] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    2.393477] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xfebfffff]
[    2.393480] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    2.393482] pci_bus 0000:01: resource 1 [mem 0xcc000000-0xceffffff]
[    2.393485] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.393488] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    2.393490] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf7ffffff]
[    2.393493] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    2.393496] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    2.393499] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xf9ffffff]
[    2.393502] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    2.393504] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    2.393507] pci_bus 0000:06: resource 1 [mem 0xfa000000-0xfbffffff]
[    2.393510] pci_bus 0000:06: resource 2 [mem 0xf4000000-0xf5ffffff 64bit pref]
[    2.393512] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    2.393515] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    2.393518] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    2.393520] pci_bus 0000:08: resource 7 [mem 0x000d4000-0x000d7fff]
[    2.393523] pci_bus 0000:08: resource 8 [mem 0x000d8000-0x000dbfff]
[    2.393526] pci_bus 0000:08: resource 9 [mem 0xc0000000-0xfebfffff]
[    2.393572] NET: Registered protocol family 2
[    2.393649] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.393930] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.394331] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.394511] TCP: Hash tables configured (established 131072 bind 65536)
[    2.394514] TCP reno registered
[    2.394517] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    2.394525] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    2.394618] NET: Registered protocol family 1
[    2.394856] pci 0000:01:00.0: Boot video device
[    2.394895] PCI: CLS 64 bytes, default 64
[    2.394925] Simple Boot Flag at 0x37 set to 0x1
[    2.395137] cpufreq-nforce2: No nForce2 chipset.
[    2.395169] Scanning for low memory corruption every 60 seconds
[    2.395296] audit: initializing netlink socket (disabled)
[    2.395308] type=2000 audit(1307739778.392:1): initialized
[    2.406478] highmem bounce pool size: 64 pages
[    2.406484] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.408087] VFS: Disk quotas dquot_6.5.2
[    2.408155] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.408801] fuse init (API version 7.14)
[    2.408897] msgmni has been set to 1656
[    2.410580] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.410584] io scheduler noop registered
[    2.410586] io scheduler deadline registered
[    2.410601] io scheduler cfq registered (default)
[    2.410726] pcieport 0000:00:01.0: setting latency timer to 64
[    2.410760]   alloc irq_desc for 40 on node -1
[    2.410762]   alloc kstat_irqs on node -1
[    2.410772] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    2.410860] pcieport 0000:00:1c.0: setting latency timer to 64
[    2.410912]   alloc irq_desc for 41 on node -1
[    2.410915]   alloc kstat_irqs on node -1
[    2.410925] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    2.411039] pcieport 0000:00:1c.2: setting latency timer to 64
[    2.411091]   alloc irq_desc for 42 on node -1
[    2.411093]   alloc kstat_irqs on node -1
[    2.411103] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    2.411215] pcieport 0000:00:1c.3: setting latency timer to 64
[    2.411268]   alloc irq_desc for 43 on node -1
[    2.411270]   alloc kstat_irqs on node -1
[    2.411280] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    2.411412] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.411569] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.411676] intel_idle: MWAIT substates: 0x22220
[    2.411678] intel_idle: does not run on family 6 model 15
[    2.411958] ACPI: AC Adapter [ADP1] (on-line)
[    2.412054] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    2.412099] ACPI: Lid Switch [LID0]
[    2.412147] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    2.412158] ACPI: Power Button [PWRB]
[    2.412206] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    2.412210] ACPI: Sleep Button [SLPB]
[    2.412257] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    2.412261] ACPI: Power Button [PWRF]
[    2.412403] ACPI: Fan [FAN0] (off)
[    2.412505] ACPI: Fan [FAN1] (off)
[    2.412874] ACPI: acpi_idle registered with cpuidle
[    2.415796] Monitor-Mwait will be used to enter C-1 state
[    2.415825] Monitor-Mwait will be used to enter C-2 state
[    2.415831] Marking TSC unstable due to TSC halts in idle
[    2.416250] Switching to clocksource hpet
[    2.660885] thermal LNXTHERM:01: registered as thermal_zone0
[    2.660896] ACPI: Thermal Zone [TZ00] (70 C)
[    2.661702] thermal LNXTHERM:02: registered as thermal_zone1
[    2.661714] ACPI: Thermal Zone [TZ01] (70 C)
[    2.661845] ERST: Table is not found!
[    2.662219] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.663930] brd: module loaded
[    2.664542] loop: module loaded
[    2.665126] Fixed MDIO Bus: probed
[    2.665162] PPP generic driver version 2.4.2
[    2.665203] tun: Universal TUN/TAP device driver, 1.6
[    2.665206] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.665288] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.665318] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.665338] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.665342] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.665378] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.665412] ehci_hcd 0000:00:1a.7: debug port 1
[    2.666324] Freeing initrd memory: 11144k freed
[    2.669314] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    2.669414] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfc204800
[    2.673136] isapnp: Scanning for PnP cards...
[    2.685015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.685207] hub 1-0:1.0: USB hub found
[    2.685212] hub 1-0:1.0: 6 ports detected
[    2.685314]   alloc irq_desc for 23 on node -1
[    2.685317]   alloc kstat_irqs on node -1
[    2.685326] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.685349] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.685353] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.685405] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.685440] ehci_hcd 0000:00:1d.7: debug port 1
[    2.689324] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    2.689347] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc204c00
[    2.705014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.705164] hub 2-0:1.0: USB hub found
[    2.705172] hub 2-0:1.0: 6 ports detected
[    2.705270] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.705291] uhci_hcd: USB Universal Host Controller Interface driver
[    2.705333] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.705341] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.705345] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.705380] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.705421] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    2.705550] hub 3-0:1.0: USB hub found
[    2.705556] hub 3-0:1.0: 2 ports detected
[    2.705624]   alloc irq_desc for 21 on node -1
[    2.705626]   alloc kstat_irqs on node -1
[    2.705632] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.705639] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.705642] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.705677] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.705716] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    2.705852] hub 4-0:1.0: USB hub found
[    2.705857] hub 4-0:1.0: 2 ports detected
[    2.705924] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.705932] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.705936] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.705978] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    2.706007] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    2.706132] hub 5-0:1.0: USB hub found
[    2.706136] hub 5-0:1.0: 2 ports detected
[    2.706207] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.706215] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.706219] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.706253] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.706283] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    2.706412] hub 6-0:1.0: USB hub found
[    2.706416] hub 6-0:1.0: 2 ports detected
[    2.706484] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.706491] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.706495] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.706530] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    2.706558] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    2.706687] hub 7-0:1.0: USB hub found
[    2.706691] hub 7-0:1.0: 2 ports detected
[    2.706768] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.706775] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.706779] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.706813] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    2.706852] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    2.706983] hub 8-0:1.0: USB hub found
[    2.706987] hub 8-0:1.0: 2 ports detected
[    2.707127] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.709623] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.709629] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.709748] mice: PS/2 mouse device common for all mice
[    2.709988] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.710022] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.710144] device-mapper: uevent: version 1.0.3
[    2.710264] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    2.710333] device-mapper: multipath: version 1.1.1 loaded
[    2.710336] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.710457] EISA: Probing bus 0 at eisa.0
[    2.710460] EISA: Cannot allocate resource for mainboard
[    2.710462] Cannot allocate resource for EISA slot 1
[    2.710464] Cannot allocate resource for EISA slot 2
[    2.710467] Cannot allocate resource for EISA slot 3
[    2.710469] Cannot allocate resource for EISA slot 4
[    2.710471] Cannot allocate resource for EISA slot 5
[    2.710473] Cannot allocate resource for EISA slot 6
[    2.710475] Cannot allocate resource for EISA slot 7
[    2.710477] Cannot allocate resource for EISA slot 8
[    2.710479] EISA: Detected 0 cards.
[    2.710612] cpuidle: using governor ladder
[    2.710701] cpuidle: using governor menu
[    2.711056] TCP cubic registered
[    2.711195] NET: Registered protocol family 10
[    2.711606] lo: Disabled Privacy Extensions
[    2.711872] NET: Registered protocol family 17
[    2.712606] Using IPI No-Shortcut mode
[    2.712689] PM: Resume from disk failed.
[    2.712703] registered taskstats version 1
[    2.713216]   Magic number: 15:938:44
[    2.713314] rtc_cmos 00:07: setting system clock to 2011-06-10 21:02:59 UTC (1307739779)
[    2.713317] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.713319] EDD information not available.
[    2.733383] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.739551] ACPI: Battery Slot [BAT1] (battery present)
[    3.021024] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    3.029307] isapnp: No Plug & Play device found
[    3.029327] Freeing unused kernel memory: 684k freed
[    3.029770] Write protecting the kernel text: 4932k
[    3.029824] Write protecting the kernel read-only data: 1976k
[    3.051619] udev[86]: starting version 163
[    3.124356] sky2: driver version 1.28
[    3.124464] sky2 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.124507] sky2 0000:06:00.0: setting latency timer to 64
[    3.124587] sky2 0000:06:00.0: Yukon-2 EC Ultra chip revision 3
[    3.145154] Linux agpgart interface v0.103
[    3.281316]   alloc irq_desc for 44 on node -1
[    3.281320]   alloc kstat_irqs on node -1
[    3.281402] sky2 0000:06:00.0: irq 44 for MSI/MSI-X
[    3.282269] sky2 0000:06:00.0: eth0: addr 00:13:77:93:67:a1
[    3.286083] ahci 0000:00:1f.2: version 3.0
[    3.286108] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.286168]   alloc irq_desc for 45 on node -1
[    3.286171]   alloc kstat_irqs on node -1
[    3.286184] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    3.286262] ahci: SSS flag set, parallel bus scan disabled
[    3.286308] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    3.286312] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    3.286318] ahci 0000:00:1f.2: setting latency timer to 64
[    3.326739] scsi0 : ahci
[    3.327453] [drm] Initialized drm 1.1.0 20060810
[    3.329794] scsi1 : ahci
[    3.329899] scsi2 : ahci
[    3.329970] scsi3 : ahci
[    3.335555] scsi4 : ahci
[    3.336089] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    3.337220] acpi device:02: registered as cooling_device4
[    3.337804] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input5
[    3.337896] ACPI: Video Device [NVID] (multi-head: yes  rom: no  post: no)
[    3.343141] scsi5 : ahci
[    3.343215] ata1: SATA max UDMA/133 abar m2048@0xfc204000 port 0xfc204100 irq 45
[    3.343219] ata2: SATA max UDMA/133 abar m2048@0xfc204000 port 0xfc204180 irq 45
[    3.343221] ata3: DUMMY
[    3.343223] ata4: DUMMY
[    3.343227] ata5: SATA max UDMA/133 abar m2048@0xfc204000 port 0xfc204300 irq 45
[    3.343230] ata6: SATA max UDMA/133 abar m2048@0xfc204000 port 0xfc204380 irq 45
[    3.660063] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.661182] ata1.00: ATA-8: Hitachi HTS543232L9A300, FB4OC40C, max UDMA/133
[    3.661189] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.662564] ata1.00: configured for UDMA/133
[    3.676283] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54323 FB4O PQ: 0 ANSI: 5
[    3.676461] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.676559] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    3.676615] sd 0:0:0:0: [sda] Write Protect is off
[    3.676618] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.676642] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.676791]  sda: sda1 sda2 < sda5 sda6 >
[    4.073103] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.360043] usb 8-2: new full speed USB device using uhci_hcd and address 2
[    4.400079] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.400523] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633L, SC01, max UDMA/100
[    4.400553] ata2.00: applying bridge limits
[    4.401428] ata2.00: configured for UDMA/100
[    4.416958] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633L  SC01 PQ: 0 ANSI: 5
[    4.422237] sr0: scsi3-mmc drive: 31x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.422244] Uniform CD-ROM driver Revision: 3.20
[    4.422440] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.422527] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.740060] ata5: SATA link down (SStatus 0 SControl 300)
[    5.076055] ata6: SATA link down (SStatus 0 SControl 300)
[    5.110454] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.110469] nouveau 0000:01:00.0: setting latency timer to 64
[    5.113951] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x298400a2)
[    5.121123] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[    5.226996] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    5.227002] [drm] nouveau 0000:01:00.0: BIT BIOS found
[    5.227005] [drm] nouveau 0000:01:00.0: Bios version 62.98.3c.00
[    5.227010] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
[    5.227013] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[    5.227016] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000323 00010034
[    5.227020] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02011300 00000028
[    5.227023] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04022332 00020010
[    5.227025] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 0000000e 00000000
[    5.227029] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[    5.227032] [drm] nouveau 0000:01:00.0:   0: 0x00000040: type 0x40 idx 0 tag 0xff
[    5.227035] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[    5.227038] [drm] nouveau 0000:01:00.0:   2: 0x00001261: type 0x61 idx 2 tag 0x07
[    5.227056] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD751
[    5.277161] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xDB03
[    5.301056] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE2C9
[    5.301080] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE3BB
[    5.308167] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE5C7
[    5.308173] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xE62C
[    5.332374] [drm] nouveau 0000:01:00.0: 0xE62C: Condition still not met after 20ms, skipping following opcodes
[    5.332398] [drm] nouveau 0000:01:00.0: 0xC2F2: parsing output script 0
[    5.332406] [drm] nouveau 0000:01:00.0: 0xC716: parsing output script 0
[    5.332436] [drm] nouveau 0000:01:00.0: Detected 256MiB VRAM
[    5.492577] [TTM] Zone  kernel: Available graphics memory: 429882 kiB.
[    5.492579] [TTM] Zone highmem: Available graphics memory: 1545532 kiB.
[    5.492582] [TTM] Initializing pool allocator.
[    5.531358] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[    5.532331] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[    5.540690] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[    5.541926] [drm] nouveau 0000:01:00.0: Detected a LVDS output
[    5.541939] [drm] nouveau 0000:01:00.0: Detected a DAC output
[    5.541942] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[    5.541945] [drm] nouveau 0000:01:00.0: Detected a LVDS connector
[    5.660520] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[    5.660564] [drm] nouveau 0000:01:00.0: Detected a HDMI connector
[    6.774085] [drm] nouveau 0000:01:00.0: allocated 1280x800 fb: 0x40250000, bo f6aa1400
[    6.777970] Console: switching to colour frame buffer device 160x50
[    6.777993] [drm] nouveau 0000:01:00.0: 0xC2F6: parsing output script 1
[    6.778033] [drm] nouveau 0000:01:00.0: 0xC165: parsing clock script 0
[    6.780307] fb0: nouveaufb frame buffer device
[    6.780309] drm: registered panic notifier
[    6.780363] Slow work thread pool: Starting up
[    6.780420] Slow work thread pool: Ready
[    6.780426] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[    7.003479] Btrfs loaded
[    7.009194] xor: automatically using best checksumming function: pIII_sse
[    7.028011]    pIII_sse  :  7328.000 MB/sec
[    7.028013] xor: using function: pIII_sse (7328.000 MB/sec)
[    7.030773] device-mapper: dm-raid45: initialized v0.2594b
[    7.038342] [drm] nouveau 0000:01:00.0: 0xC2ED: parsing clock script 1
[    7.602109] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    7.602115] EXT4-fs (sda5): write access will be enabled during recovery
[    7.640788] EXT4-fs warning (device sda5): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[    7.640798] EXT4-fs warning (device sda5): ext4_clear_journal_err: Marking fs in need of filesystem check.
[    7.640815] BUG: unable to handle kernel paging request at 02745000
[    7.640824] IP: [<c036228a>] __percpu_counter_sum+0x2a/0x70
[    7.640838] *pde = 00000000 
[    7.640845] Oops: 0000 [#1] SMP 
[    7.640851] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/uevent
[    7.640858] Modules linked in: dm_raid45 xor btrfs zlib_deflate crc32c libcrc32c nouveau ttm drm_kms_helper drm ahci video intel_agp libahci output sky2 i2c_algo_bit agpgart
[    7.640892] 
[    7.640899] Pid: 455, comm: exe Not tainted 2.6.35-22-generic #33-Ubuntu Q210/P210                  /Q210/P210                  
[    7.640909] EIP: 0060:[<c036228a>] EFLAGS: 00010293 CPU: 0
[    7.640913] EIP is at __percpu_counter_sum+0x2a/0x70
[    7.640915] EAX: 00000000 EBX: 00000000 ECX: 02745000 EDX: 00000000
[    7.640918] ESI: 00000000 EDI: c1076094 EBP: f6ac7d6c ESP: f6ac7d60
[    7.640921]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[    7.640924] Process exe (pid: 455, ti=f6ac6000 task=c118b2c0 task.ti=f6ac6000)
[    7.640926] Stack:
[    7.640928]  c10edc00 5d34239f 00000000 f6ac7da0 c02ad8b6 c2c98400 f6ac7d88 c05c6468
[    7.640936] <0> 00000001 c2c98400 5d34239b 00000000 f6448a48 c10edc00 f6a6dc00 c2c98400
[    7.640943] <0> f6ac7dd8 c02ada83 c10edc00 c05e91b5 c0730c54 c073dd3e f6a6dc00 f6ac7dd8
[    7.640952] Call Trace:
[    7.640959]  [<c02ad8b6>] ? ext4_commit_super+0xd6/0x1d0
[    7.640964]  [<c05c6468>] ? printk+0x2d/0x35
[    7.640968]  [<c02ada83>] ? ext4_clear_journal_err+0xa3/0xd0
[    7.640974]  [<c02d7ffc>] ? jbd2_journal_load+0x6c/0xd0
[    7.640977]  [<c02ad669>] ? ext4_msg+0x49/0x50
[    7.640981]  [<c02b0cff>] ? ext4_load_journal+0x14f/0x2e0
[    7.640985]  [<c02b219d>] ? ext4_fill_super+0x11fd/0x1a40
[    7.640990]  [<c03585b5>] ? vsnprintf+0xb5/0x430
[    7.640995]  [<c021b552>] ? get_sb_bdev+0x162/0x1a0
[    7.640999]  [<c02b0fa0>] ? ext4_fill_super+0x0/0x1a40
[    7.641003]  [<c02ac1d6>] ? ext4_get_sb+0x26/0x30
[    7.641007]  [<c02b0fa0>] ? ext4_fill_super+0x0/0x1a40
[    7.641010]  [<c021aee4>] ? vfs_kern_mount+0x74/0x1c0
[    7.641015]  [<c022f493>] ? get_fs_type+0x33/0xb0
[    7.641018]  [<c021b08e>] ? do_kern_mount+0x3e/0xe0
[    7.641022]  [<c023260c>] ? do_mount+0x1dc/0x220
[    7.641025]  [<c02326bb>] ? sys_mount+0x6b/0xa0
[    7.641029]  [<c05c90a4>] ? syscall_call+0x7/0xb
[    7.641032] Code: 00 55 89 e5 57 89 c7 56 53 e8 f3 68 26 00 8b 5f 04 b8 ff ff ff ff 8b 77 08 eb 1c 8d b6 00 00 00 00 8b 0c 85 80 56 81 c0 8b 57 14 <8b> 14 0a 89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 6c 93 5d c0 ba 
[    7.641077] EIP: [<c036228a>] __percpu_counter_sum+0x2a/0x70 SS:ESP 0068:f6ac7d60
[    7.641083] CR2: 0000000002745000
[    7.641086] ---[ end trace 4303201bebfc00c9 ]---
[    9.705289] ISO 9660 Extensions: Microsoft Joliet Level 3
[    9.765155] ISO 9660 Extensions: RRIP_1991A
[   10.040715] aufs 2-standalone.tree-35-rcN-20100705
[   10.159906] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   67.719881] Adding 9052592k swap on /dev/sda6.  Priority:-1 extents:1 across:9052592k 
[   69.311985] udev[1354]: starting version 163
[   74.119974] Bluetooth: Core ver 2.15
[   74.120044] NET: Registered protocol family 31
[   74.120046] Bluetooth: HCI device and connection manager initialized
[   74.120050] Bluetooth: HCI socket layer initialized
[   74.506718] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04711/0xa00000/0x0
[   74.540336] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   74.861481] Linux video capture interface: v2.00
[   74.873345] cfg80211: Calling CRDA to update world regulatory domain
[   75.376162] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   75.376900] usbcore: registered new interface driver btusb
[   75.383525] uvcvideo: Found UVC 1.00 device USB2.0 UVC PC Camera (174f:5931)
[   75.443400] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   75.466555] usbcore: registered new interface driver uvcvideo
[   75.466561] USB Video Class driver (v0.1.0)
[   77.354834] ath5k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   77.354849] ath5k 0000:02:00.0: setting latency timer to 64
[   77.354904] ath5k 0000:02:00.0: registered as 'phy0'
[   77.866042] ath: EEPROM regdomain: 0x65
[   77.866045] ath: EEPROM indicates we should expect a direct regpair map
[   77.866049] ath: Country alpha2 being used: 00
[   77.866051] ath: Regpair used: 0x65
[   78.422925] Bluetooth: L2CAP ver 2.14
[   78.422928] Bluetooth: L2CAP socket layer initialized
[   79.653877] cfg80211: World regulatory domain updated:
[   79.653881]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   79.653885]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   79.653888]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   79.653891]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   79.653894]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   79.653897]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   79.952703] phy0: Selected rate control algorithm 'minstrel'
[   79.953425] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   80.242994] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   80.242999] Bluetooth: BNEP filters: protocol multicast
[   80.832540] Bluetooth: SCO (Voice Link) ver 0.6
[   80.832544] Bluetooth: SCO socket layer initialized
[   81.599289] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   81.614000] sky2 0000:06:00.0: eth0: enabling interface
[   81.615082] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   82.153898] Bluetooth: RFCOMM TTY layer initialized
[   82.153904] Bluetooth: RFCOMM socket layer initialized
[   82.153907] Bluetooth: RFCOMM ver 1.11
[   82.684105]   alloc irq_desc for 22 on node -1
[   82.684109]   alloc kstat_irqs on node -1
[   82.684117] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   82.684185]   alloc irq_desc for 46 on node -1
[   82.684187]   alloc kstat_irqs on node -1
[   82.684200] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   82.684243] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   83.495816] hda_codec: ALC262: BIOS auto-probing.
[   83.751020] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   85.475794] lp: driver loaded but no devices found
[   85.965338] ppdev: user-space parallel port driver
[   97.560756] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
[   97.569316] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
[  165.013174] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 2
[  166.090069] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
[  166.098287] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
[  229.929044] CE: hpet increased min_delta_ns to 7500 nsec
[  307.762906] wlan0: authenticate with 00:1c:df:13:1b:96 (try 1)
[  307.764803] wlan0: authenticated
[  307.764834] wlan0: associate with 00:1c:df:13:1b:96 (try 1)
[  307.767077] wlan0: RX AssocResp from 00:1c:df:13:1b:96 (capab=0x411 status=0 aid=3)
[  307.767083] wlan0: associated
[  307.768243] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  308.000783] padlock: VIA PadLock not detected.
[  317.905019] wlan0: no IPv6 routers present
[  380.288046] No probe response from AP 00:1c:df:13:1b:96 after 500ms, disconnecting.
[  380.313065] cfg80211: All devices are disconnected, going to restore regulatory settings
[  380.313074] cfg80211: Restoring regulatory settings
[  380.313081] cfg80211: Calling CRDA to update world regulatory domain
[  380.321439] cfg80211: World regulatory domain updated:
[  380.321445]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  380.321452]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  380.321459]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  380.321465]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  380.321471]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  380.321477]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  381.342439] wlan0: authenticate with 00:1c:df:13:1b:96 (try 1)
[  381.344059] wlan0: authenticated
[  381.344084] wlan0: associate with 00:1c:df:13:1b:96 (try 1)
[  381.346599] wlan0: RX AssocResp from 00:1c:df:13:1b:96 (capab=0x411 status=0 aid=3)
[  381.346605] wlan0: associated
ubuntu@ubuntu:~$ 

```

Any chance of saving this install at all?

---

### Post by psusi on 2011-06-10
It looks like you have hit a kernel bug:

BUG: unable to handle kernel paging request at 02745000

Please file a bug report by running apport-bug linux.

It appears to be triggered by some sort of damage to the fs.  To help debug it, an image will be very helpful.  Please run the following command and attach the file to the bug:

```

sudo e2image -r /dev/sda5 - | bzip2 > sda5.e2i.bz2

```

---

### Post by WorMzy on 2011-06-10
Try running
```
sudo swapoff
```
before fsck'ing.

Sometimes having a mounted swap partition in the same extended partition as the problematic partition can cause trouble; and liveCDs tend to mount any swap partitions they encounter automagically.

---

### Post by psusi on 2011-06-10
> **WorMzy said:**
> Try running
```
sudo swapoff
```
before fsck'ing.

Sometimes having a mounted swap partition in the same extended partition as the problematic partition can cause trouble; and liveCDs tend to mount any swap partitions they encounter automagically.

Different partition, doesn't matter for fsck; you are thinking resize.

---

### Post by WorMzy on 2011-06-10
I'm not. I've never actually confirmed that this error is caused by the swap partition being automagically mounted, but I've had at least a couple of people on these forums report that unmounting the swap partition stops the error from occurring. In both cases (that I can remember right now), the need-to-fsck partition was always in the same extended partition as the mounted swap partition.

---

### Post by psusi on 2011-06-10
> **WorMzy said:**
> I'm not. I've never actually confirmed that this error is caused by the swap partition being automagically mounted, but I've had at least a couple of people on these forums report that unmounting the swap partition stops the error from occurring. In both cases (that I can remember right now), the partition was always in the same extended partition as the mounted swap partition.

Well fsck does not know or care whether another partition is mounted.  This problem is because the kernel is crashing when trying to mount the partition in question, and leaving it stuck in a mounted, but not really mounted state.

---

### Post by elwon20 on 2011-06-11
In the name of experiment I did sudo swapoff, which
returned the usage for swapoff so I did sudo swapoff -a and then repeated fsck, and the results were the same as before.
In the process of making an image to report this bug now.

Couple of questions, will this image contain the entire filesystem inc personal files etc or just the required information?

Also is there any way of retrieving this install now, or should I just reinstall? If a fresh install is in any way avoidable I'm willing to go to some hassle to save the install. If not then most of my personal files are backed up to Ubuntu One, so a fresh install isn't completely out of the question just not preferable.

One more thing, sorry to be a pain, but how long should e2image take? It seems to have stopped reading from the hard drive and is just sitting there. The bz2 file isn't growing either it's stopped at 12.5MB.

Edit:
My apologies it is growing, very slowly about 1mb every 10 mins.

---

### Post by psusi on 2011-06-11
It will only save the fs metadata, not the actual files.

You could try booting an older version of Ubuntu and see if that can manage to fsck it.  Unless you try to open the drive from the places menu, it shouldn't even be trying to mount it in the first place though, so this is very strange.

Also you might try booting the livecd into a rescue root shell.  When the keyboard icon comes up at the bottom of the screen, touch a key to get the boot menu.  Press F6 to edit the boot options.  Press escape to get rid of the pop up menu.  Add the word "single" to the command line before the "--" and hit enter.  At the rescue menu, choose to drop to a root shell prompt.  Now try to fsck the disk.

---

### Post by psusi on 2011-06-12
Did you get the bug filed?  I'll take a look and see if I can reproduce the bug and/or see what is wrong with the fs.

---

