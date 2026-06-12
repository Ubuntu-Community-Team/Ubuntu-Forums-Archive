---
title: "Crash on suspend - sync_inodes_sb"
date: 2009-07-12
forum: General Help
---

### Post by philipa on 2009-07-12
Intrepid
Linux paston01 2.6.27-14-generic #1 SMP Tue Jun 30 19:57:39 UTC 2009 i686 GNU/Linux
Dell D620

For the last few months, I've experienced a regular crash on suspend.

[FONT=Courier New]Process sync ....

 Call Trace:
  sync_inodes_sb+0x7f/0xa0
  __sync_inodes+0x55/0xa0
  sync_inodes+0x20/0x30
  do_sync+0x42/0x80
  sys_sync+0x12/0x20
  sysenter_do_call+0x12/0x2f
  _spin_unlock_bh+0x10/0x20[/FONT] 

I've typed in the above trace by hand from a photograph, since when it
appears the only thing that works are SysRq keys. After reboot, there
is no evidence in the logs. I'd welcome advice on how I might capture
more information / debug further.

The problem occurs roughly 50% of the time I suspend when on battery.
It happens far less frequently when connected to power.

If I wind back to an older kernel (Linux paston01 2.6.27-11-generic #1
SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux), this problem goes
away and suspension works fine (but, of course, other things don't).

I've searched for quite a while trying to find similar problem reports, but I've seen nothing. Anyone else suffering from this?

Thanks for any pointers.

- Phil

---

