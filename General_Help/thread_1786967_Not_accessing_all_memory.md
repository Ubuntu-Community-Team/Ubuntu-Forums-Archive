---
title: "Not accessing all memory"
date: 2011-06-20
forum: General Help
---

### Post by KoolPenguin on 2011-06-20
I have 6GB of ram but only 4GB is being shown.  I tried both Ubuntu and Kubuntu 64 Bit/11.04 versions and no luck. Double checked my install and they are 64 Bit.  Anyone know why or how to fix this?

Thanks

---

### Post by galvatron408 on 2011-06-20
how do you know that 6gb has been installed and how do you know that only 4gb is being recognized?

---

### Post by psusi on 2011-06-20
What does dmesg show in the section listing the e820 memory map?

---

### Post by idoitprone on 2011-06-20
> **galvatron408 said:**
> how do you know that 6gb has been installed and how do you know that only 4gb is being recognized?


```
sudo lshw -C memory

free -m
```

---

### Post by KoolPenguin on 2011-06-20
> **galvatron408 said:**
> how do you know that 6gb has been installed and how do you know that only 4gb is being recognized?

I bought it from dell with 6GB of memory and when I used Vista64 it showed 6GB...KInfoCenter is only showing 4GB

> **psusi said:**
> What does dmesg show in the section listing the e820 memory map?

This is all I could find in the output in regards to e820:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=ac3fe2db-f1e9-45da-a2e5-0ef6bac40b2e ro quiet splash vt.handoff=7
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf790000 (usable)
[    0.000000]  BIOS-e820: 00000000bf790000 - 00000000bf79e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf79e000 - 00000000bf7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7d0000 - 00000000bf7e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf7ec000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Dell Inc. Studio XPS 435MT/0R849J, BIOS 1.1.4 12/21/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bf800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf790 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf790000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf790000 page 4k
[    0.000000] kernel direct mapping tables up to bf790000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M

> **idoitprone said:**
> ```
sudo lshw -C memory

free -m
```

Outputs of each:

  *-firmware              
       description: BIOS
       vendor: Winbond Electronics
       physical id: 0
       version: 1.1.4
       date: 12/21/2009
       size: 128KiB
       capacity: 1984KiB
       capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 1MiB
       capacity: 1MiB
       capabilities: internal write-back unified
  *-cache:2
       description: L3 cache
       physical id: 7
       slot: L3-Cache
       size: 8MiB
       capacity: 8MiB
       capabilities: internal write-back unified
  *-memory
       description: System Memory
       physical id: 29
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM 1066 MHz (0.9 ns) [empty]
          product: NT1GC64B88A0NF-BE
          vendor: Nanya
          physical id: 0
          serial: 47273D4D
          slot: DIMM1
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:1
          description: DIMM 1066 MHz (0.9 ns)
          product: NT1GC64B88A0NF-BE
          vendor: Nanya
          physical id: 1
          serial: 49273C57
          slot: DIMM2
          size: 1GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:2
          description: DIMM 1066 MHz (0.9 ns)
          product: NT1GC64B88A0NF-BE
          vendor: Nanya
          physical id: 2
          serial: 47273BC1
          slot: DIMM3
          size: 1GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:3
          description: DIMM 1066 MHz (0.9 ns) [empty]
          product: NT1GC64B88A0NF-BE
          vendor: Nanya
          physical id: 3
          serial: 47273D6B
          slot: DIMM4
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:4
          description: DIMM 1066 MHz (0.9 ns)
          product: NT1GC64B88A0NF-BE
          vendor: Nanya
          physical id: 4
          serial: 49273D4E
          slot: DIMM5
          size: 1GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:5
          description: DIMM 1066 MHz (0.9 ns)
          product: NT1GC64B88A0NF-BE
          vendor: Nanya
          physical id: 5
          serial: 46273C83
          slot: DIMM6
          size: 1GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)

and 'free -m':

             total       used       free     shared    buffers     cached
Mem:          3955       3090        864          0         21       2111
-/+ buffers/cache:        958       2996
Swap:         4084          2       4082

I was ill for for almost a couple of years and the computer sat.  I'm gonna crack the system open and check the banks.  Starting to think somebody might of ripped me off during this time.

Thanks

---

### Post by dFlyer on 2011-06-20
If you have been riped off as stated in your last post, please mark this a SOLVED.

---

### Post by KoolPenguin on 2011-06-20
Update; checked and all 6 banks have memory modules in them, 1GB each. So linux is not finding all of them.

---

### Post by dFlyer on 2011-06-20
From the command line what does this command say:

uname -a

---

### Post by idoitprone on 2011-06-20
```
sudo dmidecode -t memory
```this might give a better view

you should check the kernel

and do that memory test that ge preinstalled at the boot menu

---

### Post by pqwoerituytrueiwoq on 2011-06-20
are you sure all the ram is good?
are you sure all the slots on the mobo are good?
does the ram how up in the bios?

@dFlyer
[FONT=Courier New]uname -m[/FONT] will tell you what you wanted to know since yuo supects is is running 32bit

---

### Post by dFlyer on 2011-06-20
uname -a will also list the kernel version he is running, not just i686, or AMD64.

---

### Post by KoolPenguin on 2011-06-20
> **pqwoerituytrueiwoq said:**
> are you sure all the ram is good?
are you sure all the slots on the mobo are good?
does the ram how up in the bios?

@dFlyer
[FONT=Courier New]uname -m[/FONT] will tell you what you wanted to know since yuo supects is is running 32bit

I know it is 64 Bit I'm running and uname -m shows:

Linux chris-Studio-XPS-435MT 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

and from past experience usually if ram is bad the system will give an error and not boot.  I can reinstall Vista64 and see what it says but I prefer not too.  I run it in virtual box but that will only show the memory I give to it. I will check the bios next.

---

### Post by psusi on 2011-06-20
It's a BIOS bug or hardware limitation.  Your bios is not reporting any memory above the 5gb mark, and the chunk between 3gb and 4gb is not reported as either reserved or usable.  Normally it is reserved for memory mapped IO and the ram is hoisted above the 4gb mark.

---

### Post by KoolPenguin on 2011-06-20
@dFlyer... Thanks bud, I checked the BIOS and it only reported 4GB so I unplugged each one and cleaned the contacts and put them back in. Now I have my 6GB memory back!

Can't believe I missed that but I guess I'm still brain dead from not using a computer for a long time and being ill. :(

Thanks again!

Chris

---

