---
title: "Takes too much time entering the desktop"
date: 2009-07-24
forum: General Help
---

### Post by zcbenz on 2009-07-24
I use ubuntu 9.04 on a laptop (hp 6530s).
Ubuntu boots well,but after I login,it takes about 30s to enter the desktop entirely.

Here is part of dmesg results,which I think may be the cause:
```
[   11.210123] type=1505 audit(1248488509.729:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2190
[   18.708492] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   18.708526] vboxdrv: Successfully done.

```

```
[   28.568078] wlan0: direct probe to AP 00:74:04:ee:28:3d try 3
[   28.768055] wlan0: direct probe to AP 00:74:04:ee:28:3d timed out
[   46.168386] CPU0 attaching NULL sched-domain.
[   46.168390] CPU1 attaching NULL sched-domain.
[   46.172114] CPU0 attaching sched-domain:
[   46.172119]  domain 0: span 0-1 level MC
[   46.172124]   groups: 0 1
[   46.172132] CPU1 attaching sched-domain:
[   46.172136]  domain 0: span 0-1 level MC
[   46.172140]   groups: 1 0

```

It seems that vbox service starts slowly and something related to CPU is wrong,can someone help me solve it?

Sorry for my bad English

---

### Post by Buttons840 on 2009-09-07
I can't help you, but you can probably help me.  What file did you paste that code from?

I have similar problems with login times ever increasing for no apparent reason.

---

### Post by XCan on 2009-09-07
I believe that is the log file of ```
 /var/log/dmesg 
```

---

