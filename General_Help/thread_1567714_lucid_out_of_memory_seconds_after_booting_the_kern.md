---
title: "lucid: out of memory seconds after booting the kernel"
date: 2010-09-04
forum: General Help
---

### Post by Disabled20240622 on 2010-09-04
Guys and/or gals,
help me figure out why my 10.04 install runs out of memory when it has hardly had chance to load the kernel.

The symptoms were that it sometimes will hang after the grub screen with a blinking cursor. My user space splash screen doesn't appear either, it was when I was trying to fix that that I spotted the problem:

from my dmesg file:
```

[    5.778823] lowmem_reserve[]: 0 0 24846 24846
[    5.778829] HighMem free:3204284kB min:512kB low:3852kB high:7196kB active_anon:192kB inactive_anon:256kB active_file:596kB inactive_file:2288kB unevictable:0kB isolated(anon):0kB isolated(file)
:0kB present:3180408kB mlocked:0kB dirty:0kB writeback:0kB mapped:1240kB shmem:144kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:356kB unstable:0kB bounce:0kB writeback_
tmp:0kB pages_scanned:0 all_unreclaimable? no
[    5.778834] lowmem_reserve[]: 0 0 0 0
[    5.778837] DMA: 4*4kB 3*8kB 5*16kB 4*32kB 3*64kB 2*128kB 3*256kB 2*512kB 1*1024kB 0*2048kB 0*4096kB = 3512kB
[    5.778844] Normal: 31*4kB 0*8kB 1*16kB 0*32kB 0*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3852kB
[    5.778851] HighMem: 116*4kB 101*8kB 52*16kB 44*32kB 16*64kB 11*128kB 10*256kB 4*512kB 3*1024kB 4*2048kB 777*4096kB = 3204408kB
[    5.778859] 806 total pagecache pages
[    5.778860] 0 pages in swap cache
[    5.778862] Swap cache stats: add 0, delete 0, find 0/0
[    5.778863] Free swap  = 0kB
[    5.778864] Total swap = 0kB
[    5.786831] 1277952 pages RAM
[    5.786833] 1050114 pages HighMem
[    5.786834] 265421 pages reserved
[    5.786835] 646 pages shared
[    5.786836] 206654 pages non-shared
[    5.786839] Out of memory: kill process 450 (plymouthd) score 38 or a child
[    5.786841] Killed process 450 (plymouthd)
[    5.788229] ureadahead invoked oom-killer: gfp_mask=0xd0, order=0, oom_adj=0
[    5.788235] ureadahead cpuset=/ mems_allowed=0
[    5.788241] Pid: 449, comm: ureadahead Not tainted 2.6.32-24-generic-pae #42-Ubuntu
[    5.788246] Call Trace:
[    5.788256]  [<c01d5724>] oom_kill_process+0xa4/0x2b0
[    5.788263]  [<c01d5d99>] ? select_bad_process+0xa9/0xe0
[    5.788270]  [<c01d5e21>] __out_of_memory+0x51/0xa0
[    5.788276]  [<c01d5ec8>] out_of_memory+0x58/0xb0
[    5.788283]  [<c01d8707>] __alloc_pages_slowpath+0x407/0x4a0
[    5.788291]  [<c01d88da>] __alloc_pages_nodemask+0x13a/0x170
[    5.788298]  [<c01d892c>] __get_free_pages+0x1c/0x30

```

this is a few seconds after loading the kernel.

---

### Post by kerry_s on 2010-09-04
bad ram?
how much ram do you have?

---

### Post by OpressedCalamity on 2010-09-04
Install gentoo.

---

### Post by kerry_s on 2010-09-04
> **OpressedCalamity said:**
> Install gentoo.

:lolflag: yeah that will fix it. ;)

---

### Post by Disabled20240622 on 2010-09-05
Don't feed the troll.

I have 4GB, will run a memtest tonight.

---

### Post by perspectoff on 2010-09-05
> **BigglesPiP said:**
> Guys and/or gals,
help me figure out why my 10.04 install runs out of memory when it has hardly had chance to load the kernel.

The symptoms were that it sometimes will hang after the grub screen with a blinking cursor. My user space splash screen doesn't appear either, it was when I was trying to fix that that I spotted the problem:

from my dmesg file:
```

[    5.778823] lowmem_reserve[]: 0 0 24846 24846
[    5.778829] HighMem free:3204284kB min:512kB low:3852kB high:7196kB active_anon:192kB inactive_anon:256kB active_file:596kB inactive_file:2288kB unevictable:0kB isolated(anon):0kB isolated(file)
:0kB present:3180408kB mlocked:0kB dirty:0kB writeback:0kB mapped:1240kB shmem:144kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:356kB unstable:0kB bounce:0kB writeback_
tmp:0kB pages_scanned:0 all_unreclaimable? no
[    5.778834] lowmem_reserve[]: 0 0 0 0
[    5.778837] DMA: 4*4kB 3*8kB 5*16kB 4*32kB 3*64kB 2*128kB 3*256kB 2*512kB 1*1024kB 0*2048kB 0*4096kB = 3512kB
[    5.778844] Normal: 31*4kB 0*8kB 1*16kB 0*32kB 0*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3852kB
[    5.778851] HighMem: 116*4kB 101*8kB 52*16kB 44*32kB 16*64kB 11*128kB 10*256kB 4*512kB 3*1024kB 4*2048kB 777*4096kB = 3204408kB
[    5.778859] 806 total pagecache pages
[    5.778860] 0 pages in swap cache
[    5.778862] Swap cache stats: add 0, delete 0, find 0/0
[    5.778863] Free swap  = 0kB
[    5.778864] Total swap = 0kB
[    5.786831] 1277952 pages RAM
[    5.786833] 1050114 pages HighMem
[    5.786834] 265421 pages reserved
[    5.786835] 646 pages shared
[    5.786836] 206654 pages non-shared
[    5.786839] Out of memory: kill process 450 (plymouthd) score 38 or a child
[    5.786841] Killed process 450 (plymouthd)
[    5.788229] ureadahead invoked oom-killer: gfp_mask=0xd0, order=0, oom_adj=0
[    5.788235] ureadahead cpuset=/ mems_allowed=0
[    5.788241] Pid: 449, comm: ureadahead Not tainted 2.6.32-24-generic-pae #42-Ubuntu
[    5.788246] Call Trace:
[    5.788256]  [<c01d5724>] oom_kill_process+0xa4/0x2b0
[    5.788263]  [<c01d5d99>] ? select_bad_process+0xa9/0xe0
[    5.788270]  [<c01d5e21>] __out_of_memory+0x51/0xa0
[    5.788276]  [<c01d5ec8>] out_of_memory+0x58/0xb0
[    5.788283]  [<c01d8707>] __alloc_pages_slowpath+0x407/0x4a0
[    5.788291]  [<c01d88da>] __alloc_pages_nodemask+0x13a/0x170
[    5.788298]  [<c01d892c>] __get_free_pages+0x1c/0x30

```

this is a few seconds after loading the kernel.

I have had each of these problems independently. The blank screen is the problem of the new Plymouth Splash screen manager, which doesn't work with a number of graphics cards.

On my computers that do this, if i am just patient for an extra minute or so, it moves on. I hate Plymouth, for this reason.

However, on one of my older computers, I can't use anything after Jaunty. In a series of Linux kernels was a bootup routine for temperature sensor checking. My older motherboards didn't have temperature sensors, so the Linux kernel generated an error every second, which was written to rsyslog, that filled up both RAM (and my hard drive) rather quickly. 

One way to check this is to check rsyslog and see if it is several Gb in size. If it is, you have some similar critical error.

I believe Ubuntu is ending its experiment with HAL (Hardware Abstraction Layer) which always seemed to me to be a buggy sort of layer, though perhaps in some ways a conceptually good idea.

I am always amused when people who complain about the Windows OS try to emulate a part of it and then find out later why the Windows OS is so kludgy. HAL seems to me to be one of those instances (but don't quote me).

---

### Post by Disabled20240622 on 2010-09-05
> **perspectoff said:**
> The blank screen is the problem of the new Plymouth Splash screen manager, which doesn't work with a number of graphics cards.

On my computers that do this, if i am just patient for an extra minute or so, it moves on. I hate Plymouth, for this reason.


I've not had that problem, to re-iterate, the times it does freeze I get a blinking cursor, and it *does not* boot, I've left it like that a long time.

---

### Post by Disabled20240622 on 2010-09-06
OK, all 4GiB of my RAM is fine.

---

### Post by satish_j on 2010-09-06
what makes you think that a blinking cursor means that your system is running out of memory??
Also,i see you are not using swap partition,which is highly recommended..

---

### Post by Disabled20240622 on 2010-09-06
I think it's running out of memory because when it doesn't freeze, it kills a bunch of prorams, as evidenced by my dmesg file. We could of course be looking at 2 separate issues, but it would be wise to fix the one I can see 1st, if it doesn't stop the other thing, I'll get hunting again.

I have a 4GiB swap partition, but it will never be mounted that soon in the boot process.

The root of the problem, I suspect, is that Linux has found a way to use 4GB of memory within seconds.

---

### Post by satish_j on 2010-09-06
Hmmm,so your swap partition is not getting detected..what is the type of filesystem for swap??
Iam confused as the 4GiB memory should not be entirely taken by Ubuntu even if there is no swap partition..seems to be some memory leak issue..
What's the version of kernel??

---

### Post by Disabled20240622 on 2010-09-06
The swap partition is mounted without issue, it is mounted right now. This issue occurs *before* the swap partition gets mounted, a few seconds after the kernel is loaded.

The problem is that the system is or thinks it is using all 4GiB of physical memory almost immediately.

I think the next logical step is to work out what process is using the memory. I seem to remember there's a booting analyser thing for linux, it starts at runlevel 1 then monitors the system, can anyone remember what is called?

---

### Post by Disabled20240622 on 2010-09-11
I've installed bootchart, but unfortunately it is killed alongside plymouth and a few other things before it ever has a chance to write anything down.

Does anyone know how I might work out what is using so much memory.

---

### Post by Disabled20240622 on 2010-09-15
Disabling the upstart job; "ureadahead" seems to have cured it, not sure if the program was trying to cache too much or just had a memory leak.

disabled by
```
mv /etc/init/ureadahead.conf /etc/init/ureadahead.conf.noexec
```

---

### Post by Disabled20240622 on 2010-09-17
Hello: [https://bugs.launchpad.net/ureadahead/+bug/491943](https://bugs.launchpad.net/ureadahead/+bug/491943)

Fix just arrived.

---

