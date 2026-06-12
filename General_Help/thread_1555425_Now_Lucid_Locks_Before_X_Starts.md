---
title: "Now Lucid Locks Before X Starts"
date: 2010-08-18
forum: General Help
---

### Post by clevertomato on 2010-08-18
I have a Lucid installation that just began freezing hard at boot-up with the Ubuntu logo in the center of the screen. No key combination gets any response, including alt-sysreq-REISUB. I can only power down at that point (using the power button).

I'm running kernel 32-24.39 and things have been just fine for as long as I can remember. This installation was fresh (not distro-upgrade) when Lucid was released, and I've updated regularly since. The last batch of updates seemed insignificant to this problem... language packs if I remember. Also, I haven't done anything "risky" lately that I can recall (no new video drivers, etc).

I've looked through some log files, but I don't know much about what I'm looking at. The only suspicious thing I've found is in /var/log/kern.log . The last (i.e. most recent) several lines follow:
```
Aug 17 19:45:54 shawn-laptop kernel: [    9.622588]   alloc irq_desc for 31 on node -1
Aug 17 19:45:54 shawn-laptop kernel: [    9.622592]   alloc kstat_irqs on node -1
Aug 17 19:45:54 shawn-laptop kernel: [    9.622614] tg3 0000:08:00.0: irq 31 for MSI/MSI-X
Aug 17 19:45:54 shawn-laptop kernel: [    9.743267] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 17 19:45:54 shawn-laptop kernel: [    9.758541] type=1505 audit(1282092354.610:14):  operation="profile_load" pid=925 name="/usr/sbin/tcpdump"
Aug 17 19:51:41 shawn-laptop kernel: [  356.918302] tg3: eth0: Link is up at 1000 Mbps, full duplex.
Aug 17 19:51:41 shawn-laptop kernel: [  356.918305] tg3: eth0: Flow control is o
n for TX and on for RX.
Aug 17 19:51:41 shawn-laptop kernel: [  356.918771] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug 17 19:51:51 shawn-laptop kernel: [  367.210102] eth0: no IPv6 routers present
Aug 17 20:18:04 shawn-laptop kernel: [ 1940.720278] CE: hpet increasing min_delta_ns to 15000 nsec
Aug 17 20:20:21 shawn-laptop kernel: [ 2077.720215] CE: hpet increasing min_delta_ns to 22500 nsec
Aug 17 21:06:22 shawn-laptop kernel: Kernel logging (proc) stopped.
Aug 17 23:07:50 shawn-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug 17 23:07:50 shawn-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 17 23:07:50 shawn-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 17 23:07:50 shawn-laptop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
Aug 17 23:07:50 shawn-laptop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=44d38f43-be21-4781-a371-d96a7a307215 ro quiet splash
Aug 17
```So, apparently it is freezing when or after the kernel loads. Any help would be much appreciated. I don't know what else to try. I'd really rather avoid a reinstall if possible (this is bringing back old memories of running Windows).

---

### Post by Peter09 on 2010-08-18
As soon as the system begins to boot hit the escape key, you should see the textual boot which may give you a better clue as to what is happening.
 
Other options are to hold the shift key down and when the grub menu comes up select recovery mode. The menu there give you options to repair broken packages and also to reconfigure your graphics drivers.

---

### Post by clevertomato on 2010-08-18
Thanks for tip. I thought it was freezing way too early to be video related, but booted into root CLI using grub, uninstalled ATI proprietary fglrx driver, rebooted successfully using normal grub choice (it went into low resolution), and reinstalled the same ATI fglrx driver. All seems fine again.

I think it was a fluke. I hadn't been having problems. Sometimes I run my notebook on AC without a battery. Maybe there was a dip in power and it caused some failure. Who knows.

---

