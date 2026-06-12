---
title: "WiFi died after kernel update"
date: 2009-09-20
forum: General Help
---

### Post by Lockheed on 2009-09-20
I updated my kernel from 2.6.30.1 to 2.6.31 and now my WiFi is dead, but in a way I cannot solve it. The card is atheros and it used to run on ath5k on previous kernel.

1. I did not change any settings in kernel config, so all needed modules are there.
2. Contrary to my previous kernel, now wifi LED seems to work. It turns on just before starting GNOME but by the time desktop icons are shown, it is off again. On previous kernel, wifi light was ALWAYS off.
3. NetworkManager Applet in tray shows "Wireless netowrk" but it is grayed-out and I cannot tick it.
4. ```
$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

```
5. ```
$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 7591
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Unknown error 132
SIOCSIFFLAGS: Unknown error 132
Listening on LPF/wlan0/00:1c:26:02:c9:68
Sending on   LPF/wlan0/00:1c:26:02:c9:68
Listening on LPF/pan0/ea:3c:13:75:9e:94
Sending on   LPF/pan0/ea:3c:13:75:9e:94
Listening on LPF/eth0/00:16:36:62:5f:fa
Sending on   LPF/eth0/00:16:36:62:5f:fa
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPREQUEST of 192.168.1.134 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.134 from 192.168.1.254
bound to 192.168.1.134 -- renewal in 286083 seconds.

```
6. ```
$ lspci
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

```

Any ideas?

---

### Post by Lockheed on 2009-09-23
up

---

### Post by isaiasmy on 2009-09-24
I have the same problem, but I have an Intel 5300 AGN card !!!

If you can give some information in this thread of launchpad would be great !!!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435141](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435141)

---

### Post by Lockheed on 2009-09-24
I did some digging and it looks like all kernels past 2.6.30.7 are screwed for many wifi cards. I went back to the said version and everything is fine for now.

---

