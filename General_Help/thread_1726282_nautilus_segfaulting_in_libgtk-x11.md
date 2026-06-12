---
title: "nautilus segfaulting in libgtk-x11"
date: 2011-04-10
forum: General Help
---

### Post by yavoh on 2011-04-10
Every once in a while (at least once a day; my computer is on 24/7) nautilus segfaults for no particular reason.  Relevant lines from kern.log:

```
[1025306.206524] nautilus[4932]: segfault at 14 ip 00007f21e272f681 sp 00007fff15d60020 error 4 in libgtk-x11-2.0.so.0.2200.0[7f21e266c000+412000]
[1036388.690123] nautilus[22488]: segfault at 14 ip 00007fdfac3f5bcf sp 00007ffffc3d0220 error 4 in libgtk-x11-2.0.so.0.2200.0[7fdfac336000+412000]
[1277941.447685] nautilus[6944]: segfault at 14 ip 00007f01c578b681 sp 00007fffb95aed40 error 4 in libgtk-x11-2.0.so.0.2200.0[7f01c56c8000+412000]
[1371769.157286] nautilus[2548]: segfault at 14 ip 00007fdb00325681 sp 00007fffe8df0bf0 error 4 in libgtk-x11-2.0.so.0.2200.0[7fdb00262000+412000]
```

I've read in some places that this can happen when unmounting a drive, but nautilus segfaults even when I haven't unmounted a drive.

Can someone help me investigate this further?

(Ubuntu 10.10 x64)

---

### Post by Yellow Pasque on 2011-04-11
Get backtrace and report bug on Launchpad: [https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

---

### Post by chenlao on 2011-07-27
I got this too. It happens randomly, hard to get backtrace.

---

### Post by bsmith1051 on 2011-10-01
Me three.  Giving up on Ubuntu, actually, and after 6 years of generally happy times.  Just too many bugs like this which never get fixed -- even when I report them.

---

