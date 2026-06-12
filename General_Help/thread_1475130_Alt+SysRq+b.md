---
title: "Alt+SysRq+b"
date: 2010-05-06
forum: General Help
---

### Post by dnguyen1963 on 2010-05-06
Hi,

For many of us, we have no idea what this key-sequence is for.  Thanks to Wilee-Nilee I do not have to shut down the computer by pushing the power button anymore.  The SysRq key shares the same location as the Print Scrn key on the keyboard.

There have been a rash of reports abut 10.04 freezes the computer requiring a hard re-boot (holding the power button until the system reboots).

This will not fix the freeze-problem, but it will help re-booting the computer easier.  Give it a try the next time 10.04 freezes on you.

Again, thanks to Wilee-Nilee.:guitar:

---

### Post by sisco311 on 2010-05-07
Alt+SysRq+b will immediately reboot the system without syncing or unmounting the partitions.

Holding down Alt and SysRq while slowly typing REISUB will get you safely reboot:

r - Switch the keyboard from raw mode to XLATE mode
e - Send the SIGTERM signal to all processes except init (PID 1)
i - Send the SIGKILL signal to all processes except init
s - Sync all mounted filesystems
u - Remount all mounted filesystems in read-only mode
b - Immediately reboot the system, without unmounting partitions or syncing

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

