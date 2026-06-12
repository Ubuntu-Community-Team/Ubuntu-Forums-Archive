---
title: "Give up waiting for root device. Common Problems booting Ubuntu 11.10"
date: 2011-11-12
forum: General Help
---

### Post by bawbawbiscuit on 2011-11-12
-After Installing ubuntu using Wubi and rebooted


The following appeared:
```

Gave up waiting for root device. Common Problems:
-Boot args (cat /proc/cmdline)
 -Check rootdealy =(did the system wait long enough?)
 -Check root =(did the system wait for the right device?)
- Missing modules (cat /proc/modules; Is /dev)
ALERT! /dev/disk/by-uuid/0000-0f2e does not exits. Dropping to a shell!

BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in-shell (ash)
Enter 'help' for a list of built-in commands

```

---

### Post by Rubi1200 on 2011-11-12
Hi and welcome to the forums :)

We need to know the make/model of the computer, the specifications, and we need the results of the boot info script to help diagnose the problem.

There is a link at the bottom of my post with instructions.

---

### Post by bawbawbiscuit on 2011-11-12
How can I run boot info script in WinXP because the instruction at SourceForge to use Terminal and it only exists in Ubuntu

The specifications:

Operating system: Microsoft Windows XP Professional(5.1 Build 2600)
System Manufacturer: INTEL
System Model: P415Gx_PE
BIOS: Version 1.00
Processor: Intel(R)Pentium(R)4 CPU 2.40GHz
Memory: 1016 MB RAM

Partitions:

C: Capacity 37.15 GB Free Space: 3.15 GB File System: NTFS
E: Capacity 18.16 GB Free Space: 130 MB File System: FAT32
F: Capacity 37.27 GB Free Space: 5.55 GB File System: NTFS
D: Capacity 36.94 GB Free Space: 31.24 GB File System: FAT32

I installed Ubuntu on Drive D:

---

### Post by Rubi1200 on 2011-11-12
You need to create a LiveCD and boot the computer with it and then follow the instructions.

This is the download link with instructions to create and use a LiveCD:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Do not install, just try and then post the results of the script please.

---

### Post by bawbawbiscuit on 2011-11-12
Since my computer doesn't have a disk drive, Instead I booted ubuntu from a USB flash drive and chose Run Ubuntu

Actually I tried booting from the USB a while ago and after loading casper

It stops at this part:
```

[ 0.138423] system 00:01 [mem 0xfee00000-0xfee00ff] has been reserved
[ 0.138475] system 00:01 [mem 0xfee00000-0xfee00fff] has been reserved
[ 0.141060] pnp: PnP ACPI: found 12 devices
[ 0.141109] ACPI: ACPI bust type pnp unregistered
[ 0.141161] PnPBIOS: Disabled by ACPI PNP
[ 0.178971] Switching to clocksource acpi_pm
[ 0.179080] pci 0000:00:1f.1: BAR 5 assigned [mem 0.x40000000-0x400003ff]
[ 0.179138] pci 0000:00:1f.1: BAR 5 set to [mem 0x40000000-0x400003ff] (PCI address [0x40000000-0x400003ff])
[ 0.179203] pci 0000:001e.0: PCI Bridge to [bus 03-03]
[ 0.179254] pci 0000:001e.0: bridge window [io 0xc000-0xcfff]
[ 0.179309] pci 0000:001e.0: bridge window [mem 0xdfd00000-0xdfdfffff]
[ 0.179364] pci 0000:001e.0: bridge window [mem pref disabled]
[ 0.179530] NET: Registered protocol family2
[ 0.179692] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.179692] Switched to NOHz mode on CPU #0
[ 0.179692] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.179692] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.179692] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.179692] TCP reno registered
[ 0.179692] UDP hash table entries: 512 (order: 2, 16384 bytes)
[ 0.179692] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[ 0.180075] NET: Registered protocol family 1

```

I waited for 3 hours... and it never went past Registered protocol family 1

Then I tried using Wubi and downloaded and Installed it within windows and the obtained the Give up waiting for root device error

So I cant access the terminal in Ubuntu :(

---

### Post by Rubi1200 on 2011-11-16
Boot into Windows and then open the Disk Management utility. 

Report back whether the disks are labeled as Basic or Dynamic.

Thanks.

---

