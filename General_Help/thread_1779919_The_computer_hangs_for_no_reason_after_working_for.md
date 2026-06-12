---
title: "The computer hangs for no reason after working for about a minute"
date: 2011-06-11
forum: General Help
---

### Post by DNDCB on 2011-06-11
Hi all,
After I've upgraded to 11.04 this issue came up.
The computer can run for month if I don't touch it (all it does is running Transmission daemon and accessing it using ssh). When I come home and start using it as a normal computer, some web browsing or just opening the Banshee player after working for less then a minute it hangs and the screen goes messy with the colors and I can't do anything but booting it.

Today I tried something, connected with putty, ran the top command and then gone to the computer and tried to use it, after less then a minute it died, as always. I went back to the machine that runs the putty client and noticed it:


```
  802 root      20   0 89436  44m 9324 R 94.5  2.2   9:47.87 Xorg
  967 steve     20   0 41776  10m 2100 S  7.6  0.5   3:11.89 transmission-da
    1 root      20   0  3056 1856 1268 S  0.0  0.1   0:00.61 init
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S  0.0  0.0   0:04.08 ksoftirqd/0
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper

```

Xorg process kills the CPU. The memory is fine.
Any idea?

Thanks in advance! ;)

BTW,
there is one zombie task.

Update:
After killing Xorg, it's still stuck. Even through putty it takes ages to execute a "ls" command.

---

