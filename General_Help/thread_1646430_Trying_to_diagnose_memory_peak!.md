---
title: "Trying to diagnose memory peak!"
date: 2010-12-15
forum: General Help
---

### Post by aldmy on 2010-12-15
Hi,

My server crashed last week and I'm trying to diagnose why.

**/var/log/messages** contains the following error messages, which indicate that the server's memory peaked.

I would like to discover what process caused the memory peak. Being that "**httpd invoked oom-killer**", can I conclude that httpd was the cause of the memory peak?

```
Dec  9 09:47:52 ZZZZ kernel: httpd invoked oom-killer: gfp_mask=0xa01d2, order=0, oomkilladj=0
Dec  9 09:47:52 ZZZZ kernel:  [<c0464ed2>] out_of_memory+0x69/0x1a7
Dec  9 09:47:52 ZZZZ kernel:  [<c0466546>] __alloc_pages+0x21b/0x2a2
Dec  9 09:47:52 ZZZZ kernel:  [<c0467c96>] __do_page_cache_readahead+0xe2/0x1ff
Dec  9 09:47:52 ZZZZ kernel:  [<c045d399>] delayacct_end+0x70/0x77
Dec  9 09:47:52 ZZZZ kernel:  [<c0462444>] sync_page+0x0/0x41
Dec  9 09:47:52 ZZZZ kernel:  [<c045d480>] __delayacct_blkio_end+0x5b/0x5f
Dec  9 09:47:52 ZZZZ kernel:  [<c061c743>] __wait_on_bit_lock+0x4b/0x52
Dec  9 09:47:52 ZZZZ kernel:  [<c0462436>] __lock_page+0x58/0x5e
Dec  9 09:47:52 ZZZZ kernel:  [<c04680ba>] do_page_cache_readahead+0x49/0x53
Dec  9 09:47:52 ZZZZ kernel:  [<c0464330>] filemap_fault+0x188/0x37d
Dec  9 09:47:52 ZZZZ kernel:  [<c046c3f4>] __do_fault+0x59/0x394
Dec  9 09:47:52 ZZZZ kernel:  [<c046ea76>] handle_mm_fault+0x3a0/0x78b
Dec  9 09:47:52 ZZZZ kernel:  [<c0435210>] recalc_sigpending+0xb/0x1d
Dec  9 09:47:52 ZZZZ kernel:  [<c0404cf8>] do_notify_resume+0x589/0x6d8
Dec  9 09:47:52 ZZZZ kernel:  [<c061ed84>] do_page_fault+0x26a/0x5ef
Dec  9 09:47:52 ZZZZ kernel:  [<c0435210>] recalc_sigpending+0xb/0x1d
Dec  9 09:47:52 ZZZZ kernel:  [<c04352c3>] sigprocmask+0xa1/0xc7
Dec  9 09:47:52 ZZZZ kernel:  [<c061eb1a>] do_page_fault+0x0/0x5ef
Dec  9 09:47:52 ZZZZ kernel:  [<c061d802>] error_code+0x72/0x78
Dec  9 09:47:52 ZZZZ kernel:  [<c0610000>] xfrm_send_policy_notify+0x270/0x4fd
Dec  9 09:47:52 ZZZZ kernel:  =======================
Dec  9 09:47:52 ZZZZ kernel: Mem-info:
Dec  9 09:47:52 ZZZZ kernel: DMA per-cpu:
Dec  9 09:47:52 ZZZZ kernel: CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Dec  9 09:47:52 ZZZZ kernel: CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Dec  9 09:47:52 ZZZZ kernel: Normal per-cpu:
Dec  9 09:47:52 ZZZZ kernel: CPU    0: Hot: hi:  186, btch:  31 usd:   2   Cold: hi:   62, btch:  15 usd:  51
Dec  9 09:47:52 ZZZZ kernel: CPU    1: Hot: hi:  186, btch:  31 usd:  32   Cold: hi:   62, btch:  15 usd:  49
Dec  9 09:47:52 ZZZZ kernel: HighMem per-cpu:
Dec  9 09:47:52 ZZZZ kernel: CPU    0: Hot: hi:  186, btch:  31 usd:   2   Cold: hi:   62, btch:  15 usd:  37
Dec  9 09:47:52 ZZZZ kernel: CPU    1: Hot: hi:  186, btch:  31 usd:  30   Cold: hi:   62, btch:  15 usd:  59
Dec  9 09:47:52 ZZZZ kernel: Active:156442 inactive:309903 dirty:0 writeback:0 unstable:0
Dec  9 09:47:52 ZZZZ kernel:  free:12139 slab:6146 mapped:611 pagetables:24919 bounce:0

```

---

### Post by aldmy on 2010-12-15
Here's some additional, interesting information:

Of 2,073,156k RAM available, 1,983,352k is being used. That seems very high.

On the other hand, of the 2,096,472k Swap available, only 60k is being used. Is that reasonable?

As you can see below, there are three - four apache processes running, with each of their memory readouts. These are the most significant memory usages.

```
[root@ZZZZ /]# top
top - 21:28:15 up 1 day,  5:43,  1 user,  load average: 0.21, 0.38, 0.37
Tasks: 150 total,   2 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.1%us,  1.7%sy,  0.0%ni, 89.1%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   2073156k total,  1983352k used,    89804k free,   421796k buffers
Swap:  2096472k total,       60k used,  2096412k free,   883288k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
28926 apache    20   0 74012  36m 6852 R   14  1.8   2:50.38 httpd
28958 apache    20   0 70436  32m 6800 S    5  1.6   2:55.39 httpd
28937 apache    20   0 79460  41m 6736 S    1  2.0   3:10.58 httpd
 2338 mysql     20   0  193m  87m 5036 S    1  4.3 162:36.88 mysqld

```

---

### Post by mmsmc on 2010-12-15
swap peaks are how many tabs you have open, the crash can be caused by how much you were pushing it to, if it is working ok now than you are fine. and your ram is determined how many proccess are going on, this can be affected by what you are running and by cookies
this crash depends on what you were running and seeing that you were running 150 tasks, that explains your ram and very high ram = slow computer = eventual crash

---

