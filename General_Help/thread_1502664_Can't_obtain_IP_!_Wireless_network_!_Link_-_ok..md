---
title: "Can't obtain IP ! Wireless network ! Link - ok."
date: 2010-06-05
forum: General Help
---

### Post by susimakalaves on 2010-06-05
Hi to all ! Can I ask questions ? If yes then I would like to talk with someone who is experienced within wireless networks. Actually I can't connect to wep/wpa/open wireless networks AT ALL ! I'm using alfa awus036h I think problem is lying under my dhcpd config do I need to create dhcpd.wlan0.leases config for different networks ? 


 --- cat /var/log/syslog ---
 
```

 
Jun  6 03:47:09 bt dhclient: Bind socket to interface: No such device
Jun  6 03:47:10 bt kernel: rtl8187: Card successfully reset
Jun  6 03:47:10 bt kernel: rtl8187: RR:84 BRSR: f1ff
Jun  6 03:47:14 bt kernel: rtl8187: NIC in promisc mode
Jun  6 03:47:14 bt kernel: Linking with "xxx" rate: 11 MBit
Jun  6 03:47:14 bt kernel: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Jun  6 03:47:14 bt kernel: rtl8187: NIC in promisc mode
Jun  6 03:47:14 bt kernel: rtl8187: NIC in promisc mode
Jun  6 03:47:14 bt kernel: Linking with "xxx" rate: 11 MBit
Jun  6 03:47:14 bt dhclient: Internet Systems Consortium DHCP Client V3.1.1
Jun  6 03:47:14 bt dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jun  6 03:47:14 bt dhclient: All rights reserved.
Jun  6 03:47:14 bt dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jun  6 03:47:14 bt dhclient:
Jun  6 03:47:15 bt dhclient: Listening on LPF/wlan1/00:0d:c4:17:c0:cb
Jun  6 03:47:15 bt dhclient: Sending on   LPF/wlan1/00:0d:c4:17:c0:cb
Jun  6 03:47:15 bt dhclient: Sending on   Socket/fallback
Jun  6 03:47:17 bt kernel: Linking with "xxx" rate: 11 MBit
Jun  6 03:47:19 bt dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 4
Jun  6 03:47:19 bt kernel: Linking with "xxx" rate: 11 MBit
Jun  6 03:47:22 bt kernel: Linking with "xxx" rate: 11 MBit
Jun  6 03:47:23 bt dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
Jun  6 03:47:24 bt kernel: Linking with "xxx" rate: 11 MBit
Jun  6 03:47:29 bt last message repeated 2 times
Jun  6 03:47:31 bt dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 19
Jun  6 03:47:32 bt kernel: Linking with "xxx" rate: 11 MBit
Jun  6 03:47:47 bt last message repeated 6 times
Jun  6 03:47:50 bt dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 20
Jun  6 03:47:50 bt kernel: Linking with "xxx" rate: 11 MBit
Jun  6 03:48:08 bt last message repeated 7 times
Jun  6 03:48:10 bt dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
Jun  6 03:48:10 bt kernel: Linking with "xxx" rate: 11 MBit
Jun  6 03:48:18 bt last message repeated 3 times
Jun  6 03:48:20 bt dhclient: No DHCPOFFERS received.
Jun  6 03:48:20 bt dhclient: No working leases in persistent database - sleeping.
Jun  6 03:48:21 bt kernel: Linking with "xxx" rate: 11 MBit
Jun  6 03:48:54 bt last message repeated 13 times




```


r8187/Stacks-ieee80211 (ref. ALFA-AWUS036h)   Actually tried mac80211, but no difference...  What kind of info should I read to solve this problem ?   Please replay as fast as you can, because it's quite important.  If you need any other info - just ask. Can't solve this problem for a long period... Getting nervous :/ Thousands thanks for all you reading and replaying to this thread !

---

