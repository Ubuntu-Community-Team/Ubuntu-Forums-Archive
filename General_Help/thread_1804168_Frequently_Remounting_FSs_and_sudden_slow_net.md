---
title: "Frequently Remounting FSs and sudden slow net"
date: 2011-07-14
forum: General Help
---

### Post by vangop on 2011-07-14
Hi!
I started to notice that after a while the network suddenly starts to lag. LAN resources which normally ping 1-2ms ping 100-150ms, so are internet resources.
I tried networking restart, restart network-manager, reconnect to the router, relog - only full system reboot helps.
The only suspicious thing that shows in logs is 

```
[   41.046761] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   43.345994] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=600
[   46.901870] EXT4-fs (dm-2): re-mounted. Opts: commit=600
[   47.675334] EXT4-fs (dm-4): re-mounted. Opts: commit=600
[   47.915968] EXT4-fs (sda3): re-mounted. Opts: commit=600
```

I have quite frequent remounts in dmesg, and the net lag starts right after one of them.
Can someone suggest a solution?
Ubuntu 10.10 x64

---

### Post by vangop on 2011-07-15
And sometimes dmesg shows remounts with a different commit.
```
[12702.340232] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[12702.672907] EXT4-fs (dm-2): re-mounted. Opts: commit=0
[12702.675348] EXT4-fs (sda3): re-mounted. Opts: commit=0
[12702.684694] EXT4-fs (dm-4): re-mounted. Opts: commit=0

```

---

### Post by vangop on 2011-07-15
This always happens after the AC power disconnect from the laptop.
After I disconnect the cord, 
```
[33372.812189] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=600
[33373.109891] EXT4-fs (dm-2): re-mounted. Opts: commit=600
[33373.113530] EXT4-fs (sda3): re-mounted. Opts: commit=600
[33373.119212] EXT4-fs (dm-4): re-mounted. Opts: commit=600

```
and ping drops to 100+ ms,

after I connect 
```
[33395.324766] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[33395.412129] EXT4-fs (dm-2): re-mounted. Opts: commit=0
[33395.416019] EXT4-fs (sda3): re-mounted. Opts: commit=0
[33395.420799] EXT4-fs (dm-4): re-mounted. Opts: commit=0
[33395.732312] HP WMI: Unknown response received

```
And ping is back to 1-2 ms..

---

### Post by vangop on 2011-07-21
Filed a [bug]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/811552") for it. The solution now is ```
$ sudo chmod -x /usr/lib/pm-utils/power.d/wireless
```

---

