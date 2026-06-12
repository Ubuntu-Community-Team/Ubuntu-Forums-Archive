---
title: "Virtual Machine without Ethernet on Ubuntu 9.04"
date: 2009-10-27
forum: General Help
---

### Post by Taurec on 2009-10-27
I have some virtual machines running on a few servers. After upgrading to VMWare Player 2.5.3 the machines running on Ubuntu 9.04 (64bit) fail to connect to eth0 devices. In /var/log/messages I find the error message

/dev/rtc open failed: -13

The virtual machines running on CentOS 5.4 as host are working fine without that error. Downgrading the version of VMWare Player running on Ubuntu give me ethernet access without errors again. There seems to be an incompatibility between the current versions of Ubuntu and VMWare. Are there any settings that would allow me to upgrade VMWare Player on Ubuntu?

---

### Post by dcstar on 2009-10-27
> **Taurec said:**
> I have some virtual machines running on a few servers. After upgrading to VMWare Player 2.5.3 the machines running on Ubuntu 9.04 (64bit) fail to connect to eth0 devices. In /var/log/messages I find the error message

/dev/rtc open failed: -13

The virtual machines running on CentOS 5.4 as host are working fine without that error. Downgrading the version of VMWare Player running on Ubuntu give me ethernet access without errors again. There seems to be an incompatibility between the current versions of Ubuntu and VMWare. Are there any settings that would allow me to upgrade VMWare Player on Ubuntu?

Look in the Virtualization forum.

---

