---
title: "Error When Booting Computer"
date: 2010-04-08
forum: General Help
---

### Post by pictureaperfectpicture on 2010-04-08
Hi all,

I'm still new at this so bare with me. 

I think I got some sort of error when I turned on the computer this morning. I wrote down by hand when appeared on the screen (is there an easier way of copying the information on the computer?). I am sorry if I post this in the wrong section.

I'm running karmic koala and the system has been running slow the past week.

[ 263 . 068006] ESI: c2047de0 EDI: c2047de8 EBP: f64f9e7c ESP: f64f9e64
[ 263 . 068006] DS: 997b ES: 007bfs: 00d8 GS: 00e0 SS: 0068
[ 263 . 068006] CR0: 8005003b CR2 00963ab0 CR3: 3648b000 CR4: 000006d0
[ 263 . 068006] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[ 263 . 068006] DR6: ffff0ff0 DR7: 00000400
[ 263 . 068006] Call trace:
[ 263 . 068006] [<c0209800>] ? invalidate_bh_lru+0x0/0x40
[ 263 . 068006] [<c016f5db>] smp_call_function_single+0x106/0x120
[ 263 . 068006] [<c0209800>] ? invalidate_bh_lru+0x0/0x40
[ 263 . 068006] [<c016f79c>] smp_call_function_many+0x1ac/0x1d0
[ 263 . 068006] [<c0209800>] ? invalidate_bh_lru+0x0/0x40
[ 263 . 068006] [<c0209800>] ? invalidate_bh_lru+0x0/0x40
[ 263 . 068006] [<c016f7df>] smp_call_function+0x1f/0x30
[ 263 . 068006] [<c014af0a>] on_each_cpu+0x1a/0x40
[ 263 . 068006] [<c02092d4>] invalidate_bh_lrus+0x14/0x20
[ 263 . 068006] [<c020ed1b>] kill_bedev+0x1b/0x30
[ 263 . 068006] [<c020f8e6>] __blkdev_put+0x86/0x150
[ 263 . 068006] [<c020f9ba>] blkdev_put+0xa/0x10
[ 263 . 068006] [<c020f9e1>] blkdev_close+0x21/0x50
[ 263 . 068006] [<c01e956a>] __fput+0xda/0x1f0
[ 263 . 068006] [<c01e9695>] fput+0x15/0x20
[ 263 . 068006] [<c01e5ab7>] filp_close+0x47/0x70
[ 263 . 068006] [<c01e5b53>] sys_close+0x73/0xb0
[ 263 . 068006] [<c01033ac>] syscall_call+0x7/0xb

I'm curious to know what it all means, and why it's acting up. I pressed and held the off button and then started it up in system recovery and, to my knowledge, it didn't do anything. When I restarted the system it worked fine.

---

