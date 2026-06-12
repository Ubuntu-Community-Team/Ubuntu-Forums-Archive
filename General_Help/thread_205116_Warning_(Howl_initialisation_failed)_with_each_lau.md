---
title: "Warning (Howl initialisation failed) with each launch of Gobby."
date: 2006-06-28
forum: General Help
---

### Post by Buffalo Soldier on 2006-06-28
Installed Gobby (ver 0.3.0-1ubuntu3.1) from universe repo using synaptic. This error message window pops up everytime I launch Gobby.
> Howl initialisation failed. Probably you need to run mDNSResponder as root prior to Gobby. Zeroconf support is deactivated for this session.

---

### Post by Buffalo Soldier on 2006-08-15
Solved.
```
sudo apt-get install avahi-daemon
```

> **Avahi mDNS/DNS-SD daemon**

Avahi is a fully LGPL framework for Multicast DNS Service Discovery. It allows programs to publish and discover services and hosts running on a local network with no specific configuration. For example you can plug into a network and instantly find printers to
print to, files to look at and people to talk to.

This package contains the Avahi Daemon which represents your machine on the network and allows other applications to publish and resolve mDNS/DNS-SD records.

---

### Post by zoubidoo on 2007-02-01
This solution didn't work for me on Dapper.
Ahavi installed fine and appears to be running.
```
zbd@obelix:~$ ps aux |grep -i avahi
avahi     5516  0.0  0.0   2536  1316 ?        Ss   20:41   0:00 avahi-daemon: running [obelix.local]
avahi     5517  0.0  0.0   2536   432 ?        Ss   20:41   0:00 avahi-daemon: chroot helper process
zbd    5567  0.0  0.0   2892   852 pts/7    R+   20:51   0:00 grep -i avahi
zbd@obelix:~$

```

"Howl initialisation failed. Probably..."

---

### Post by theorem_hunter on 2007-03-17
also not working for me...
i have the same error

---

