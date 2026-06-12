---
title: "Wierd suspend problem."
date: 2009-11-05
forum: General Help
---

### Post by chowno on 2009-11-05
Hello, I just found my compy in a really weird suspend state.  I have power management set to automatically suspend after an hour of idle time and it has worked really well, but when I came home today and opened my laptop lid there was only the console with kernel messages spewing out about a hung task.  I checked the logs and the system thought that it was going into suspend from the pm log but I was able to find the kernel message in the syslog.  I'll post it below.  Any ideas as what it means and what I can do to not have this happen again?  Thanks for your time! :D

Nov  5 08:47:36 lappy486 anacron[25355]: Anacron 2.3 started on 2009-11-05
Nov  5 08:47:36 lappy486 anacron[25355]: Normal exit (0 jobs run)
Nov  5 08:47:36 lappy486 NetworkManager: <info>  Sleeping...
Nov  5 08:47:36 lappy486 NetworkManager: <info>  (wlan0): now unmanaged
Nov  5 08:47:36 lappy486 NetworkManager: <info>  (wlan0): device state change: 8 -> 1 (reason 37)
Nov  5 08:47:36 lappy486 NetworkManager: <info>  (wlan0): deactivating device (reason: 37).
Nov  5 08:47:37 lappy486 NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 24658
Nov  5 08:47:37 lappy486 NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Nov  5 08:47:37 lappy486 NetworkManager: <info>  (wlan0): cleaning up...
Nov  5 08:47:37 lappy486 NetworkManager: <info>  (wlan0): taking down device.
Nov  5 08:47:37 lappy486 avahi-daemon[937]: Withdrawing address record for 192.168.1.100 on wlan0.
Nov  5 08:47:37 lappy486 avahi-daemon[937]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Nov  5 08:47:37 lappy486 kernel: [64060.549089] wlan0: deauthenticating by local choice (reason=3)
Nov  5 08:47:37 lappy486 NetworkManager: <info>  (eth0): now unmanaged
Nov  5 08:47:37 lappy486 NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Nov  5 08:47:37 lappy486 NetworkManager: <info>  (eth0): cleaning up...
Nov  5 08:47:37 lappy486 NetworkManager: <info>  (eth0): taking down device.
Nov  5 08:47:37 lappy486 kernel: [64060.679620] wlan0: disassociating by local choice (reason=3)
Nov  5 08:47:37 lappy486 avahi-daemon[937]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov  5 08:47:37 lappy486 avahi-daemon[937]: Withdrawing address record for fe80::21a:73ff:fec5:7e36 on wlan0.
Nov  5 08:49:57 lappy486 kernel: [64200.716121] INFO: task sync:25421 blocked for more than 120 seconds.
Nov  5 08:49:57 lappy486 kernel: [64200.716171] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  5 08:49:57 lappy486 kernel: [64200.716218] sync          D c08145c0     0 25421  25279 0x00000000
Nov  5 08:49:57 lappy486 kernel: [64200.716224]  cd6fdf2c 00000086 f68e0000 c08145c0 f625b4d8 c08145c0 607cfeb4 00003a43
Nov  5 08:49:57 lappy486 kernel: [64200.716233]  c08145c0 c08145c0 f625b4d8 c08145c0 00000001 00003a43 c08145c0 f609a1c0
Nov  5 08:49:57 lappy486 kernel: [64200.716240]  f625b240 cd6fdf60 f625b240 f4bf463c cd6fdf58 c0570515 fffeffff f5fb5c00
Nov  5 08:49:57 lappy486 kernel: [64200.716248] Call Trace:
Nov  5 08:49:57 lappy486 kernel: [64200.716258]  [<c0570515>] rwsem_down_failed_common+0x75/0x1a0
Nov  5 08:49:57 lappy486 kernel: [64200.716264]  [<c057068d>] rwsem_down_read_failed+0x1d/0x30
Nov  5 08:49:57 lappy486 kernel: [64200.716268]  [<c05706e7>] call_rwsem_down_read_failed+0x7/0x10
Nov  5 08:49:57 lappy486 kernel: [64200.716272]  [<c056fca7>] ? down_read+0x17/0x20
Nov  5 08:49:57 lappy486 kernel: [64200.716277]  [<c0207385>] sync_filesystems+0xb5/0x100
Nov  5 08:49:57 lappy486 kernel: [64200.716281]  [<c0207411>] sys_sync+0x11/0x40
Nov  5 08:49:57 lappy486 kernel: [64200.716285]  [<c010336c>] syscall_call+0x7/0xb

---

### Post by chowno on 2009-11-20
Update:  I figured NetworkManager was problem from the log and manually set my wireless network settings.  So far that has fixed the problem for the most part.

---

