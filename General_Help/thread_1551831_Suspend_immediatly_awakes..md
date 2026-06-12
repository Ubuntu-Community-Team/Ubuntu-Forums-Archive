---
title: "Suspend immediatly awakes."
date: 2010-08-12
forum: General Help
---

### Post by Ric95 on 2010-08-12
Most of the time (~70%) when I want to suspend the system, it immediately re-awakens. 
What could cause this?

Xubuntu 10.04 /64bit on amd 4 core ,nvidia motherboard and video. 
Here is the var/lib/daemon.log at the time of a suspend attempt:
> Aug 12 06:08:21 ric-desktop avahi-daemon[1084]: Withdrawing address record for fe80::92e6:baff:fe03:f3a8 on eth0.
Aug 12 19:01:10 ric-desktop NetworkManager: <info>  Sleeping...
Aug 12 19:01:10 ric-desktop NetworkManager: <info>  (eth0): now unmanaged
Aug 12 19:01:10 ric-desktop NetworkManager: <info>  (eth0): device state change: 8 -> 1 (reason 37)
Aug 12 19:01:10 ric-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 37).
Aug 12 19:01:10 ric-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 32287
Aug 12 19:01:10 ric-desktop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Aug 12 19:01:10 ric-desktop avahi-daemon[1084]: Withdrawing address record for 192.168.2.3 on eth0.
Aug 12 19:01:10 ric-desktop avahi-daemon[1084]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.3.
Aug 12 19:01:10 ric-desktop avahi-daemon[1084]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 12 19:01:10 ric-desktop NetworkManager: <info>  (eth0): cleaning up...
Aug 12 19:01:10 ric-desktop NetworkManager: <info>  (eth0): taking down device.
Aug 12 19:01:10 ric-desktop avahi-daemon[1084]: Withdrawing address record for 2002:4641:e16e:1234:92e6:baff:fe03:f3a8 on eth0.
Aug 12 19:01:10 ric-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
Aug 12 19:01:31 ric-desktop rtkit-daemon[1672]: The canary thread is apparently starving. Taking action.
Aug 12 19:01:31 ric-desktop rtkit-daemon[1672]: Demoting known real-time threads.
Aug 12 19:01:31 ric-desktop rtkit-daemon[1672]: Successfully demoted thread 1729 of process 1670 (n/a).
Aug 12 19:01:31 ric-desktop rtkit-daemon[1672]: Successfully demoted thread 1727 of process 1670 (n/a).
Aug 12 19:01:31 ric-desktop rtkit-daemon[1672]: Successfully demoted thread 1670 of process 1670 (n/a).
Aug 12 19:01:31 ric-desktop rtkit-daemon[1672]: Demoted 3 threads.
Aug 12 19:01:32 ric-desktop acpid: client 1265[0:0] has disconnected
Aug 12 19:01:32 ric-desktop acpid: client 1265[0:0] has disconnected
Aug 12 19:01:32 ric-desktop acpid: client connected from 1265[0:0]
Aug 12 19:01:32 ric-desktop acpid: 1 client rule loaded
Aug 12 19:01:32 ric-desktop NetworkManager: <info>  Waking up...
Aug 12 19:01:32 ric-desktop NetworkManager: <info>  (eth0): now managed
Aug 12 19:01:32 ric-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Aug 12 19:01:32 ric-desktop NetworkManager: <info>  (eth0): bringing up device.
Aug 12 19:01:32 ric-desktop NetworkManager: <info>  (eth0): preparing device.
''''and awake


---

### Post by Ric95 on 2010-12-05
I've refined the bug. Each time I start Xubuntu it is able to suspend once. The next try it auto-unsuspends. 
is this worth reporting as a bug?

---

