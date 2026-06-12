---
title: "ntp.keys not read/understood?"
date: 2010-07-13
forum: General Help
---

### Post by el_baby on 2010-07-13
Hi,

I'm trying to implement ntp orphan mode in case my servers get disconnected from internet for too long.

I have 3 identical servers, all running hardy (8.04.4).

They get external time reference (when everything works fine) from internet. They also provide ntp service to an internal network that doesn't have internet access.

The problem is that I want the servers to peer among themselves using a simple key and, for some weird reason, the key doesn't seem to be read.

All servers have the following **/etc/ntp.conf** file:
```

# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift

# Enable this if you want statistics to be logged.
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
#server ntp.ubuntu.com
# pool.ntp.org maps to more than 100 low-stratum NTP servers.
# Your server will pick a different set every time it starts up.
#  *** Please consider joining the pool! ***
#  ***  <http://www.pool.ntp.org/#join>  ***
server 0.pool.ntp.org iburst
server 1.pool.ntp.org iburst
server 2.pool.ntp.org iburst
server 3.pool.ntp.org iburst

# orphan mode: http://fixunix.com/ntp/67929-orphan-mode-configuration.html
keys /etc/ntp/keys
tos orphan 8
broadcastclient
broadcast 10.101.32.255 key 1

#peer server-00
#peer server-01
#peer server-02

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery


# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict -6 ::1

```

The following is the content of **/etc/ntp/keys**:
```

1 M smthing

```

However, after restarting ntpd, my syslog is full of:
```

Jul 14 01:16:46 server-00 ntpd[10948]: transmit: 10.101.32.255 key 1 not found
Jul 14 01:17:51 server-00 ntpd[10948]: transmit: 10.101.32.255 key 1 not found
Jul 14 01:18:57 server-00 ntpd[10948]: transmit: 10.101.32.255 key 1 not found
Jul 14 01:20:02 server-00 ntpd[10948]: transmit: 10.101.32.255 key 1 not found
Jul 14 01:21:08 server-00 ntpd[10948]: transmit: 10.101.32.255 key 1 not found

```

I tried everything I could think of.

I restricted ownership and permissions in /etc/ntp/keys like this:
```

admin@server-00:~$ ls -la /etc/ntp
total 12
drwxr-xr-x  2 ntp  ntp  4096 2010-07-13 23:09 .
drwxr-xr-x 73 root root 4096 2010-07-13 23:39 ..
-rw-------  1 ntp  ntp    25 2010-07-13 23:09 keys

```

Any hints?

---

