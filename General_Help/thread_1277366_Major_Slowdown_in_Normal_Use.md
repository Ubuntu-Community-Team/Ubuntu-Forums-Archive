---
title: "Major Slowdown in Normal Use"
date: 2009-09-28
forum: General Help
---

### Post by Noit on 2009-09-28
I've been running Ubuntu on an old desktop PC for quite a while now with no real issues, but in the last few days it's gone from being a bit slow because it's running on a six year old processor to being unusably slow. What's foxed me is that it's not showing high RAM or CPU usage- it doesn't do much during the day apart from download torrents, and SSHing in I can see that the neither get much above 10% use most of the time. But even accessing it via SSH has become a real chore with serious lag.

My real worry at this point is that the processor is on it's very last legs, but it seems odd that this would manifest as slow-down rather than a complete failure. It's not that the HDD is full as there's still plenty of space left on it.

I'm at a bit of a loss really. Any help would be much appreciated.

---

### Post by Giblet5 on 2009-09-28
It's very possible that your disk drive is getting ready to die.

```
dmesg | less
```

Hit Shift-G. Are there lots of errors?

There may NOT be errors, and the disk drive could still be dying. Disk reads will retry around 256 times and, if it succeeds on the 254th try, you probably won't get any error. Now imagine that disk access just took 254 times longer to complete and you have a massive slowdown...

There are a lot of other things it could be, too.

Your friends: "top", "iostat", and "dmesg".

---

### Post by Giblet5 on 2009-09-28
It is also possible that you're low on disk space.

Once you fall below 10% free, new file creation (temp files, FIFOs, UNIX domain sockets, etc) will take longer and longer, until you run out of space and corrupt a bunch of files.

---

### Post by Bucky Ball on 2009-09-28
Giblet5

 [QUOTE=Noit]It's not that the HDD is full as there's still plenty of space left on it.[/QUOTE]

---

### Post by Noit on 2009-09-28
Dmesg shift+g results in this- ```

ession/Xsession" name2="default" pid=2287
[   19.154580] type=1505 audit(1254138016.596:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2291
[   19.154749] type=1505 audit(1254138016.596:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2291
[   19.154804] type=1505 audit(1254138016.596:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2291
[   19.154849] type=1505 audit(1254138016.596:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2291
[   19.308105] type=1505 audit(1254138016.752:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2296
[   19.308333] type=1505 audit(1254138016.752:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2296
[   19.352225] type=1505 audit(1254138016.796:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2300
[   19.382328] type=1505 audit(1254138016.824:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2304
[   19.548655] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.588264] nf_conntrack version 0.5.0 (16383 buckets, 65532 max)
[   19.588489] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   19.588491] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   19.588494] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   19.650705] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   28.230896] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   28.230901] vboxdrv: Successfully done.
[   28.230903] vboxdrv: Found 1 processor cores.
[   28.231007] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   28.231010] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   29.585955] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.585958] Bluetooth: BNEP filters: protocol multicast
[   29.606554] Bridge firewalling registered
[   35.016007] eth0: no link during initialization.
[   35.016551] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.595762] input: b43-phy0 as /devices/virtual/input/input7
[   35.628061] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   35.817731] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   35.862494] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   36.173994] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   36.313664] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   36.389792] Registered led device: b43-phy0::tx
[   36.389807] Registered led device: b43-phy0::rx
[   36.389822] Registered led device: b43-phy0::radio
[   36.404178] b43-phy0: Radio turned on by software
[   36.404490] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.249784] UDF-fs: Partition marked readonly; forcing readonly mount
[   63.274564] UDF-fs INFO UDF: Mounting volume 'SPACED', timestamp 2006/02/16 15:04 (1000)
[   64.548501] wlan0: authenticate with AP 00:1d:68:ef:44:71
[   64.550297] wlan0: authenticated
[   64.550301] wlan0: associate with AP 00:1d:68:ef:44:71
[   64.552963] wlan0: RX AssocResp from 00:1d:68:ef:44:71 (capab=0x411 status=0 aid=1)
[   64.552966] wlan0: associated
[   64.554683] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   75.392017] wlan0: no IPv6 routers present
[   93.060025] Clocksource tsc unstable (delta = -197965408 ns)
```

Which makes me think the RAM might be at fault? I did recently upgrade it from 1x 512mb stick to 2x 512mb stick, but one of those two was the original stick that was in there to start with, so it shouldn't have caused such a massive slowdown, should it? Admittedly the stick I added was reclaimed from a scrap PC. But it was fine for a good few weeks between adding the RAM and this slowdown issue.

top reveals nothing worrying- 

```
top - 15:33:34 up  2:53,  2 users,  load average: 0.16, 0.05, 0.01
Tasks: 141 total,   1 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.2%us,  0.8%sy,  0.1%ni, 95.6%id,  1.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   1026684k total,  1011344k used,    15340k free,     8676k buffers
Swap:  1510068k total,      608k used,  1509460k free,   743196k cached
```

Trying to get an iostat result but my connection keeps timing out. I suspect this is because the machine is having a fit rather than connection issues.

---

### Post by Noit on 2009-09-28
iostat result:

```

Linux 2.6.28-15-generic (jackson)       28/09/09        _i686_  (1 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           2.22    0.15    1.38    1.17    0.00   95.35

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               4.01       292.32        20.98    3211230     230456
sda1              4.01       292.14        20.87    3209246     229240
sda2              0.00         0.00         0.00          6          0
sda5              0.00         0.15         0.11       1658       1216
sr0               0.00         0.10         0.00       1084          0
sdd               0.01         0.19         0.00       2075          0
sdd1              0.01         0.11         0.00       1219          0
sdf               0.02         1.57         0.00      17282          0
sdf1              0.02         1.54         0.00      16938          0

```

Just thought of one more reason that it's most likely not disk related- typing in SSH often lags quite heavily as well, and there's no way that's going through the disk first.

---

### Post by P4man on 2009-09-28
thats odd.. I don't think I'll be much help, but Im pretty confident its NOT a ram issue (that would result in spontaneous reboots, freezes, kernel panics, but not slow downs). Its not a full disk either, unlike windows, ubuntu keeps working full speed right until the moment its disk is full.

A dying harddisk *could* be related to it, although I would expect to see something in dmesg. Likewise for a bad optical drive, ive seen machines choke constantly trying to read a cdrom that was faulty, but I would think your logs would show that.

Perhaps a weird suggestion, but try running "powertop" (may have to install it from the repo's). Its designed to optimize power consumption but it does an excellent job identifying all sort of problems.

**edit**: afterthought. Is it possible the CPU is overheating, and constantly throtteling to keep it from melting ? Pentium4s do that when there is a problem with cooling.

---

### Post by Noit on 2009-09-28
It's an AMD Athlon64 3200+ if that's any help. I've never really had an issue with it getting hot before, and the current temperature is listed as 31 degrees. I'm only going by what sensors say right now though, I'm not actually near the machine.

Powertop results:


 ```
PowerTOP 1.11   (C) 2007, 2008 Intel Corporation

Collecting data for 5 seconds
     PowerTOP version 1.11      (C) 2007 Intel Corporation

< Detailed C-state information is not P-states (frequencies)
                                        2.00 Ghz     0.0%
                                        1.80 Ghz     0.0%
                                        1000 Mhz   100.0%



Wakeups-from-idle per second : 413.4    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  38.2% (157.0)       <interrupt> : nvidia, b43
  24.5% (100.6)       <interrupt> : sata_nv, eth0
   6.4% ( 26.2)            deluge : schedule_hrtimeout_range (hrtimer_wakeup)
   5.0% ( 20.6)           deluged : schedule_hrtimeout_range (hrtimer_wakeup)
   4.1% ( 16.8)           deluged : schedule_timeout (process_timeout)
   3.5% ( 14.2)     <kernel core> : hrtimer_start (tick_sched_timer)
   3.3% ( 13.6)       <interrupt> : ehci_hcd:usb1
   3.1% ( 12.8)   USB device  1-4 : USB 2.0 Card Chip (Generic)
   2.3% (  9.6)       <interrupt> : ohci_hcd:usb2
   2.3% (  9.6)   USB device  2-2 : Microsoft Wireless Desktop Receiver 3.1 (Microsft)
   1.2% (  4.8)     <kernel core> : sk_reset_timer (tcp_delack_timer)
   0.8% (  3.2)           deluged : __nf_conntrack_confirm (death_by_timeout)
   0.7% (  2.8)           deluged : sk_reset_timer (tcp_write_timer)
   0.5% (  2.0)       <interrupt> : pata_amd
   0.5% (  2.0)           emerald : schedule_hrtimeout_range (hrtimer_wakeup)
   0.5% (  2.0)   hald-addon-stor : schedule_hrtimeout_range (hrtimer_wakeup)
   0.3% (  1.4)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0.3% (  1.4)   hald-addon-stor : blk_plug_device (blk_unplug_timeout)
   0.3% (  1.2)     <kernel core> : __nf_ct_refresh_acct (death_by_timeout)
   0.3% (  1.2)           usplash : scan_async (ehci_watchdog)
   0.2% (  1.0)    NetworkManager : queue_delayed_work (delayed_work_timer_fn)
   0.2% (  1.0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer)
   0.1% (  0.6)               b43 : ieee80211_authenticate (ieee80211_sta_timer)
   0.1% (  0.6)       compiz.real : schedule_hrtimeout_range (hrtimer_wakeup)
   0.1% (  0.6)            deluge : __nf_ct_refresh_acct (death_by_timeout)
   0.1% (  0.4)       gvfsd-trash : schedule_hrtimeout_range (hrtimer_wakeup)
   0.1% (  0.4)   update-notifier : schedule_hrtimeout_range (hrtimer_wakeup)
   0.1% (  0.4)   tracker-indexer : schedule_hrtimeout_range (hrtimer_wakeup)
   0.1% (  0.4)             conky : schedule_hrtimeout_range (hrtimer_wakeup)
   0.1% (  0.4)         kblockd/0 : blk_plug_device (blk_unplug_timeout)
   0.0% (  0.2)              sshd : sk_reset_timer (tcp_write_timer)
   0.0% (  0.2)    NetworkManager : schedule_hrtimeout_range (hrtimer_wakeup)
   0.0% (  0.2)    NetworkManager : nv_open (nv_do_stats_poll)
   0.0% (  0.2)       gnome-panel : schedule_hrtimeout_range (hrtimer_wakeup)
   0.0% (  0.2)          trackerd : schedule_hrtimeout_range (hrtimer_wakeup)
   0.0% (  0.2)   gvfs-hal-volume : schedule_hrtimeout_range (hrtimer_wakeup)
   0.0% (  0.2)   fast-user-switc : schedule_hrtimeout_range (hrtimer_wakeup)

Suggestion: Disable 'hal' from polling your cdrom with:
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

```

---

### Post by P4man on 2009-09-28
31°C is suspiciously low in fact, but A64's dont do thermal throtteling, so even if it were overheating, it wouldn't slow down. It will shut down if ever it gets critically hot.

That powertop output is sort of interesting in the sense that your cpu is constantly at 1GHz. Can you make the computer "work" over ssh somehow to see if it ever speeds up ? updating apt or something should do the trick. FWIW, my Core2duo doing absolutely nothing (just ff open) will still go to full speed about 5% of the time.

**edit**: closing ff I get 0% as well, and updating apt doesn't help, so try something else.  You could install the package "cpuburn" which you can execute with "burnK7" (uppercase K).

---

