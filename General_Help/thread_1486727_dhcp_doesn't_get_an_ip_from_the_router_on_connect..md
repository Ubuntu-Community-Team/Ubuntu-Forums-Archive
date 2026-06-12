---
title: "dhcp doesn't get an ip from the router on connect. how to run &quot;on connect&quot; scripts?"
date: 2010-05-18
forum: General Help
---

### Post by pavel__ on 2010-05-18
hi

the connection via wireless lan can easily be established under ubuntu 10.4, but sometimes dhcp fails to get an ip address. is there a way to perform an action (=run a shell script) every time the connection is established? then i could get the ip manually.


thanks!

---

### Post by dvlchd3 on 2010-05-18
Yes.  The /etc/network/if-up.d will execute all executable files (that only contain alphanumeric characters - no .,_- etc).

Create your script:
```

gksu gedit /etc/network/if-up.d/myscript

```

Save it, than make it executable:
```

sudo chmod a+x /etc/network/if-up.d/myscript

```

Now everytime your network interfaces are brought up, that script will run.

Or, you can just configure your computer to static ip:
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

---

### Post by pavel__ on 2010-05-18
thank you for the quick reply, i will try it out!

---

### Post by pavel__ on 2010-05-20
me again. seems not to help. found this line in dmesg:


```
[   24.328883] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

syslog shows about the time of startup:

```

May 21 00:42:46 slick NetworkManager: <info>  dhclient started with pid 1501
May 21 00:42:46 slick NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
May 21 00:42:46 slick NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May 21 00:42:46 slick NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
May 21 00:42:46 slick NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
May 21 00:42:46 slick dhclient: Internet Systems Consortium DHCP Client V3.1.3
May 21 00:42:46 slick dhclient: Copyright 2004-2009 Internet Systems Consortium.
May 21 00:42:46 slick dhclient: All rights reserved.
May 21 00:42:46 slick dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 21 00:42:46 slick dhclient: 
May 21 00:42:46 slick NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
May 21 00:42:46 slick dhclient: Listening on LPF/wlan0/00:13:02:0e:5b:e1
May 21 00:42:46 slick dhclient: Sending on   LPF/wlan0/00:13:02:0e:5b:e1
May 21 00:42:46 slick dhclient: Sending on   Socket/fallback
May 21 00:42:47 slick avahi-daemon[809]: Registering new address record for fe80::213:2ff:fe0e:5be1 on wlan0.*.
May 21 00:42:50 slick dhclient: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
May 21 00:42:50 slick dhclient: DHCPACK of 0.0.0.0 from 192.168.1.1
May 21 00:42:50 slick dhclient: bound to 0.0.0.0 -- renewal in 32707 seconds.


```

which means, that i again get that 0.0.0.0 ip address.

what can i do about that now?

---

